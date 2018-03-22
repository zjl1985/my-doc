# 如果sql最大内存设置成了0解决办法

`cd D:\Microsoft SQL Server\MSSQL11.MSSQLSERVER\MSSQL\Binn`


`sqlservr.exe -sMSSQLSERVER -mSQLCMD –c -f -m`

> 窗口不要关闭

另开一个cmd

`sqlcmd -E`

>注意命名实例需要开启SQL server Browser服务，才能连接

```
EXEC sys.sp_configure N'show advanced options', N'1'  RECONFIGURE WITH OVERRIDE
GO
EXEC sys.sp_configure N'max server memory (MB)', N'5000'
GO
RECONFIGURE WITH OVERRIDE
GO
EXEC sys.sp_configure N'show advanced options', N'0'  RECONFIGURE WITH OVERRIDE
GO
```

[原文](http://www.mamicode.com/info-detail-1910981.html)
