#### tcp连接
```C#
modbusFactory = new ModbusFactory();
master_plc = modbusFactory.CreateMaster(new TcpClient(IP地址，502));
//设置读取超时时间
master_plc.Transport.ReadTimeout = 1000;
master_plc.Transport.Retries = 3;
master_plc.Transport.WriteTimeout = 1000;
```
#### 读多个输入和输出
`返回值 = master_plc.ReadInputs(站号, 开始地址, 读取个数);`<br>
`返回值 = master_plc.ReadCoils(站号, 开始地址, 读取个数);`

#### 读和写多个寄存器
`返回值 = master_plc.ReadHoldingRegisters(站号, 开始地址, 读取个数);`

写操作记得加锁
```C#
lock (obj)
{
       master_plc.WriteMultipleRegisters(站号, 开始地址, data);
}
```
#### 写单个寄存器
`master_plc.WriteSingleRegisterAsync(站号, 开始地址, data);`

#### 写线圈（实际中不要用，可能会破坏plc编程正常运行）
`master_plc.WriteSingleCoilAsync(站号, 开始地址, ONOFF);`<br>
`master_plc.WriteMultipleCoilsAsync(站号, 开始地址, ONOFF);`