数据库的是协助提供及时和可靠的信息，以支持组织的日常运营，但数据库只是一个存储数据的地方。要处理和获取数据，还有数据库前端用户界面 (UI)，也就是用户要通过它访问数据库并与之交互，有用于处理和分析数据库中数据的应用程序，以及用于创建这些应用程序的软件开发工具。同时还有被称为中间件的通信软件工具，这些工具支持本地、广域或全球通信网络上的数据传输和数据库处理。更高级的数据库系统还包括支持业务决策的数据分析功能。

为了描述数据库及其相关组件（数据库引擎、用户界面、应用程序和中间件），即支持处理和获取的组件，我们将这些统称为数据库系统，也叫做数据库管理系统 (DBMS)。

一开始时使用的是集中式数据库系统的配置，其中所有处理都在一台计算机中完成，所有数据都存储在同一台计算机的辅助存储器中。而随着分布式处理的引入，今天的大多数数据库系统都是基于分布式处理的概念构建的，它将数据库操作与数据存储功能分开。分布式数据库系统不仅允许通过在通信网络中的不同计算机中存储和管理进程和数据来实现进程和数据的物理分离，还允许将特定进程或数据文件划分为驻留在不同站点的较小单元。一个分布式数据库系统的配置通常包括以下组件：
- 构成系统各个站点（也称为节点）的计算机、操作系统和数据库系统软件。
- Network cards and software 安装在计算机中的网卡和软件，使它们能够相互交互和交换数据，而不管它们各自的配置如何。
- 将数据从一台计算机传输到另一台计算机的通信网络协议（例如，传输控制协议/互联网协议 [TCP/IP]）。
- data processor / data manager，它是存储和检索位于特定站点的数据的数据库引擎。事务处理器，它是每台计算机中从自己的数据库和其他数据库请求数据的软件。
- The transaction processor事务处理器，也称为事务管理器或应用处理器，控制所有数据库事务（例如，插入新数据、删除旧数据和修改现有数据的值）和相关的数据库操作（例如，并发控制、事务提交）和回滚和数据复制）。

Basic concepts:
data model: 
database schema: 
Database Engine / server:（例如，Microsoft Jet 数据库引擎和 SQL Server、Oracle 数据库服务器和 IBM DB2 Universal Server）是一组计算机程序，用于处理数据库中包含的数据 

Database作为Database System 的一部分，除了存储了data files之外，还存储数据特征和数据库完整性规则的描述。包括了描述数据库内容的 data dictionary, 一组必须强制执行的数据库完整性规则 intergrity rules, and stored procedures.

数据库系统将数据存储在磁盘阵列中，称为辅助存储设备。当查询需要数据时，它们被读入中央处理单元 (CPU)，它被称为主存储。一些大型数据库系统需要使用具有 TB 级存储容量的三级存储设备。与二级存储设备不同，三级存储设备不能直接被计算机的读取设备访问。当需要三级存储中的数据时，将存储介质（例如，数字视频磁盘[DVD]）检索并加载到数据读取器中，并将数据传输到二级存储设备上。二级存储设备中数据的典型访问时间为 10 到 20 毫秒，而访问三级存储设备上的数据通常需要几秒钟。

与数据库存储和操作密切相关的是数据库安全和完整性约束的概念和方法，这些概念和方法旨在保护数据库中的数据不被破坏、破坏或破坏。 在数据库管理的上下文中，安全性是指为保护数据库免受未经授权的使用和/或数据库内容的修改或破坏而强制执行的所有规则和措施。 现代数据库系统通常提供两种形式的数据安全性：
- 自主安全，也称为权限，控制用户以特定模式（例如只读、读写）访问特定数据文件、记录或字段的能力。
- 强制安全，将用户和数据分为不同的安全级别，然后实施适当的安全措施，允许特定安全级别内的用户访问他们被允许访问的级别的数据。

数据库完整性则是一种保障数据的准确性、正确性和有效性的要求，要达到这个要求，会有共有的约束。这些约束针对了：
- 域约，指定数据值的类型，例如数字、字符或字符串、布尔值、日期和时间以及用户定义。
- 键和关系，它们控制实体作为数据表中的主键、辅助键和外键的使用。
- 语义完整性，这是书面规则，说明数据结构和数据管理中允许和不允许的内容。

软件系统的核心是数据库引擎，它负责存储、检索和操作数据库中的数据，以及管理后台进程，例如数据转换、事务日志和内存管理。Database engine 用户与数据库的物理实现分开，并为他们提供访问数据库内容所需的进程。同时它需要处理数据，会涉及有 data manipulation softwares, 包括了 buffer and file manager. Buffer manager 通过将从辅助存储设备读取的数据分配到主存储器中的特定页面来处理主存储器。如果不再需要现有数据，它通过将页面分配给进入主存储器的新数据来重新使用页面。而 file manager 跟踪数据文件的位置及其与磁盘块的关系。当需要特定的数据文件时，文件管理器在包含该文件的辅助存储设备中定位磁盘块，并将它们发送到缓冲区管理器，然后缓冲区管理器将数据块分配给主存储器页面。

与数据的存储和操作相关联。数据库引擎的功能依赖于主机的操作系统。因此基于 Microsoft Windows 的数据库系统与基于 UNIX 或 Linux 的数据库系统的工作方式不同的原因。早期的数据库系统要求 COBOL 或 PL/1 程序员编写机制来管理与数据库中的文件直接交互的数据存储和检索例程。现代数据库系统使用 SQL 或用 SQL 扩展（例如 Oracle 的 PL/SQL）编写的程序来处理这些任务，这些程序允许用户请求他们需要的数据。

在数据库处理中，查询是用户对数据库提出的问题或任务。查询由称为查询管理器的数据库工具处理。查询管理器的功能是将用户在 SQL 中的高级数据库访问或操作命令（通常发音为 sequel 或拼写为单个字母）转换为对存储数据的一系列操作。常见的语句是 SELECT, PROJECT, JOIN, PRODUCT, UNION, INTERSECT, DIFFERENCE, DIVIDE. SQL是一种non-procedural computer language 非过程计算机语言，因为它没有用于测试条件的 IF 语句，也没有用于程序结构和流程控制的 WHILE、FOR、GOTO 和 CASE 语句。SQL 语句可以通过以下五种方式之一使用：
- 交互式处理，通过命令行用户界面（例如，Oracle 的 sqlplus，DB2 的 db2i，PostgreSQL 的开源 psql 和 MySQL 的 mysql）。
- 嵌入高级计算机语言，如 COBOL、FORTRAN、PL/1、C++ 和 Java，为使用高级语言编写的应用程序查询数据库提供必要的工具。
- 使用调用层接口 (CLI)，它由在操作系统层实现的例程组成（与上述嵌入式 SQL 的情况下的应用程序层相反）。可以调用 CLI 来处理来自编程语言（如 C++ 和 Visual Basic (VB)）的 SQL 语句，在执行时连接到数据库，从数据表中提取数据，获取数据处理状态信息，并呈现结果数据库查询。
- 使用两个标准 Java 应用程序编程接口 (API) 协议，即 Java 数据库连接 (JDBC) 和 Java 嵌入式 SQL (SQLJ)，创建能够从数据库中提取数据的 Java 应用程序和小程序。
- 以存储过程（执行一个或多个数据处理操作的代码块）、函数（在过程中调用参数的代码块）或包（一组存储过程和函数组合在一个模块名称下）。这些程序模块是通过在传统的 SQL 处理环境中添加编程结构、流程控制和子程序来创建的。一个很好的例子是 Oracle 的 SQL 过程语言扩展 (PL/SQL)。

查询并不会更改原始值，当值发生变化时，说明发生了database transaction. 在发生transaction时需要处理并发事务（即当两个或多个用户访问数据库系统并尝试同时更改相同的值时）可能引起的冲突。因此要求数据库能够符合一定原则：
- Atomicity，这意味着一个事务要么全部被执行，要么一个都不执行（也就是说，一个事务永远不能只部分完成）。
- Consistency preservation，这意味着数据库中的数据在事务之前和之后保持在数据库模式以及强加于数据库的其他约束和完整性规则所指定的一致状态。
- Isolation，要求同时交易的结果相互独立。
- Durability or permanency，这意味着在事务完成后，即使系统发生故障或崩溃，也可以并且始终跟踪其结果。

因此要求数据库拥有控制的机制：
- Concurrent control 锁定事务中涉及的数据项，从而将其结果与影响其他事务的结果隔离开来，同时避免它们受到其他事务结果的影响。
- Logging the transactions 在重做日志中跟踪对数据库所做的所有更改，并将日志备份到辅助存储设备上，以便日志数据在可能导致主内存中数据丢失的电源故障时仍然存在.
- Transaction commitment 防止对数据库的任何更改，除非事务已准备好完成，并记录更改。 
 Rollback 允许数据库撤消不完整的事务处理，并在事务完成之前系统发生故障时恢复到其原始一致状态。

日志记录、事务提交和回滚方法旨在处理数据处理的相对较小的中断，这些中断会阻止事务完成。只要事务日志不因电源故障或数据库不当关闭等中断而丢失，这些数据恢复技术就可以很好地工作

但是如果发生更灾难性的故障（例如磁盘崩溃），则需要更复杂的过程来将数据库恢复到故障前的一致状态。在这些情况下，标准的数据库管理程序是使用数据库系统的备份和恢复管理器定期将整个数据库和事务日志复制到外部存储介质上，例如磁带、CD-ROM 和 DVD。在关键数据的情况下，通常会制作备份的第二份副本并将其存储在远离数据库系统所在位置的安全站点中，例如，在另一栋建筑物中。备份频率可以是每天或每周，具体取决于数据库应用程序的性质和数据的重要性。Database Replication / replication servers 是将数据库复制到可能位于不同站点的一台或多台附加计算机上的过程 i.e.  
许多组织需要在分布式数据库系统中使用数据库副本来支持其业务需求：
- 通过允许卫星办公室的用户使用数据库的本地副本而不是直接与中央数据库服务器通信来提高系统性能。
- 通过确保在数据库服务器关闭时数据始终保持可访问性来提高数据库可用性，例如，用于系统维护。



