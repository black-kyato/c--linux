#### 网盘第五期说明

- 由于第四期写的存在bug，故基于第三期版本的功能实现多点下载
- 客户端发送gets命令，主服务器检查是否存在该文件，发送对应的md5码和文件大小给客户端
- 下载文件时，客户端从主服务器获取文件服务器的ip地址和端口，然后给每个文件服务器发送对应的文件下载信息，包括文件的md5码，文件大小和文件偏移
- 客户端先创建一个空文件，大小等于要下载的文件大小，然后mmap一块大内存，把对应的内存偏移地址和tcp套接字传给文件下载线程，每个文件下载线程接收并写内存（mmap机制自动写文件）
- 文件服务器启动后等待连接，有新的连接后启动文件下载线程传输文件
- 文件下载线程接收文件md5码，打开文件，接收文件偏移量，定位文件指针，接收要下载的大小，传输对应大小的文件
- fileServer1.exe,fileServer1.exe,fileServer.exe1为三个文件服务器，地址和端口使用宏定义表示，serverc.exe是主服务器，clientc.exe是客户端程序，对应的.c文件为源码