### 数据帧结构

数据帧由帧起始，仲裁段、控制段、数据段、CRC段、应答段、帧结段构成

根据仲裁段里的数据帧ID决定是否接受该报文

![imagepng](./pictures/42dbb293470748b99f41f84d93bad358tplv-k3u1fbpfcp-watermark.png)

根据控制段里的DLC判断由数据长度由多少个字节

![imagepng](./pictures/45bc1a2d652b4ce893bf23c304ac2331tplv-k3u1fbpfcp-watermark.png)

接收端会在ACK段的ACK槽使电平的值为1，用来回应发送端成功接收信息。

![imagepng](./pictures/3fcb867777d24ee9a2982c69b9ccbb0etplv-k3u1fbpfcp-watermark.png)
