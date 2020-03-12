# Microsoft.Extensions.Caching.SqlServerInMemory
SQL Server In Memory OLTP Table compatible version of IDistributedCache implementation

# Related to the following Github Issues

[Add support for “in-memory tables” in Microsoft.Extensions.Caching.SqlServer](https://github.com/dotnet/extensions/issues/1894)

[sql-cache command line is not compatible with In Memory SQL Tables](https://github.com/dotnet/aspnetcore/issues/17640)

Example Table Creation SQL Script:

```
SET ANSI_NULLS ON
GO

SET QUOTED_IDENTIFIER ON
GO

CREATE TABLE [dbo].[CoreCache_Example]
(
	[Id] [nvarchar](449) COLLATE SQL_Latin1_General_CP1_CI_AS NOT NULL,
	[Value] [varbinary](max) NOT NULL,
	[ExpiresAtTime] [datetime2](7) NOT NULL,
	[SlidingExpirationInSeconds] [bigint] NULL,
	[AbsoluteExpiration] [datetime2](7) NULL,

 PRIMARY KEY NONCLUSTERED HASH 
(
	[Id]
)WITH ( BUCKET_COUNT = 33554432)
)WITH ( MEMORY_OPTIMIZED = ON , DURABILITY = SCHEMA_ONLY )
GO
```
