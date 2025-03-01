

大多数应用程序开发人员都使用SQL，可能还有一些NoSQL数据库来构建应用程序。BMDB将这两个数据库中最好的数据库整合到一个统一的平台中，以简化可扩展云服务的开发。
通常情况下，今天的云服务和应用程序一开始只需要少量请求和数据。这些可以由几个节点提供服务。但是，如果该应用程序变得流行，他们将不得不迅速扩展，以处理数百万个请求和数TB的数据，BMDB非常适合这类工作负载。

## **统一SQL和NoSQL**

以下是一些不同的标准，BMDB将SQL和NoSQL的最佳功能整合到一个数据库平台中。

### **数据库特征**

这些可以被松散地定义为选择数据库来构建应用程序或云服务时的高级关注点，例如其数据模型、支持的API、一致性语义等。下表对比了BMDB与SQL和NoSQL数据库提供的一般功能。请注意，有许多不同的NoSQL数据库，每个数据库都有自己的细微行为，并且该表并不适用于所有NoSQL数据库——它只是为了给出一个想法。

| 特征           | SQL                          | NoSQL    | BMDB                   |
| -------------- | ---------------------------- | -------- | ---------------------- |
| 数据模型       | 定义良好的架构（表、行、列） | 无架构   | 都有                   |
| API            | SQL                          | 各式各样 | 关系型SQL +半关系型SQL |
| 一致性         | 强                           | 结果一致 | 强                     |
| 事务           | ACID                         | 无       | ACID                   |
| 高写入吞吐量   | 否                           | 有时     | 是                     |
| 可调整读取延迟 | 否                           | 是       | 是                     |

### **操作特性**

操作特性可以定义为在生产中部署、运行和管理数据库时出现的运行时问题。当在类似云的体系结构中的生产中运行数据库时，许多操作特性变得至关重要。下表比较了BMDB的SQL和NoSQL数据库的功能。与前一节一样，有许多NoSQL数据库在各自方面都有所不同，下表旨在提供一个大致的概念。
下表列出了BMDB支持的一些重要功能，以及用于利用该功能的API。请注意，通常部署多个数据库以实现相同的功能。

| 操作特性            | SQL         | NoSQL                       | BMDB                              |
| ------------------- | ----------- | --------------------------- | --------------------------------- |
| 自动分片            | 否          | 有时                        | 是                                |
| 线性扩展            | 否          | 是                          | 是                                |
| 容错                | 否-手动设置 | 是-智能客户端检测到故障节点 | 是-智能客户端检测到故障节点       |
| 数据恢复            | 否          | 是-但重建会导致高延迟       | 是-自动、高效的数据重建           |
| 地理分布            | 否-手动设置 | 有时                        | 是                                |
| 低延迟读取          | 否          | 是                          | 是                                |
| 可预测的p99读取延迟 | 是          | 否                          | 是                                |
| 高数据密度          | 否          | 有时-当密度增加时会出现延迟 | 是-高数据密度时会出现可预测的延迟 |
| 读取复制副本支持    | 否-手动设置 | 否-没有异步复制             | 是—同步和异步复制选项             |

## **核心功能**

应用程序和云服务依赖于数据库来实现各种内置功能。这些功能可以包括执行多行事务、JSON或文档支持、辅助索引、使用TTL的自动数据过期等等。
下面是一个表，列出了BMDB支持的一些重要功能，以及为了实现这些功能，要使用哪些BMDB的API。请注意，为了实现这些功能，通常会部署多个数据库。 

 

| 数据库功能              | BMDB SQL API | BMDB 云QL API    |
| ----------------------- | ------------ | ---------------- |
| 多行事务                | 是           | 是               |
| 一致的辅助索引          | 是           | 是               |
| JSON/文档支持           | 是           | 是               |
| 二级索引                | 是           | 是               |
| 外键                    | 是           | 否               |
| JOINs                   | 是           | 否               |
| TTL自动数据到期         | 否           | 是-表和列级别TTL |
| 为AI/ML运行Apache Spark | 否           | 是               |

## **线性扩展**

为了测试BMDB 的线性可扩展性，我们运行了一些大型集群基准测试（最多50个节点），并能够将BMDB 扩展到每秒数百万次读写，同时保持低延迟。

 

## **高性能**

BMDB 的构建是为了在不牺牲一致性的情况下在公共云环境中提供性能。BMDB 是用C++编写的，正是因为这个原因。下图显示了BMDB 在运行YCSB基准测试时与ApacheCassandra的比较情况。
下图显示了运行YCSB基准测试时的总操作数/秒：

![](./media/chapter3/16.png)下图显示了YCSB运行的延迟： 
![](./media/chapter3/17.png)