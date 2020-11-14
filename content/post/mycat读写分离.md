+++
date="2020-11-14T23:17:34+08:00"
title="mycat读写分离"
tags=["mycat"]
categories=["mycat"]

+++
## mycat 下载

1. 下载地址 

   http://www.mycat.org.cn/

2. 安装

   ```shell
   cd /usr/local/src
   
   wget http://dl.mycat.org.cn/1.6-RELEASE/Mycat-server-1.6-RELEASE-20161028204710-linux.tar.gz
   
   tar -zxvf Mycat-server-1.6-RELEASE-20161028204710-linux.tar.gz
   
   mv mycat /usr/local/
   
   cd /usr/local/mycat/
   
   ```

   

3. 目录

   bin:命令文件
   catlet:空的,扩展
   conf:配置文件(server.xml,schema.xml,rule.xml等)
   lib:依赖的jar包

4. 启动

   cd bin

   ./mycat console 

5. 注意

   要关闭防火墙 不然连接不上 

6. 配置

   schema.xml

   ```shell
   <?xml version="1.0"?>
   <!DOCTYPE mycat:schema SYSTEM "schema.dtd">
   <mycat:schema
       xmlns:mycat="http://io.mycat/">
       <!--配置数据表-->
       <schema name="itcast" checkSQLschema="false" sqlMaxLimit="100">
           <table name="tb_ad" dataNode="dn1" rule="mod-long" />
       </schema>
       <!--配置分片关系-->
       <dataNode name="dn1" dataHost="cluster1" database="itcast" />
       <!--配置连接信息-->
       <dataHost name="cluster1" maxCon="1000" minCon="10" balance="3"
                   writeType="1" dbType="mysql" dbDriver="native" switchType="1"
                   slaveThreshold="100">
           <heartbeat>select user()</heartbeat>
           <writeHost host="W1" url="192.168.1.99:3306" user="root"
                        password="root">
               <readHost host="W1R1" url="192.168.1.99:3307" user="root" password="root" />
           </writeHost>
       </dataHost>
   </mycat:schema>
   ```

   server.xml

   ```
   <?xml version="1.0"?>
   ● firewalld.service - firewalld - dynamic firewall daemon
   <mycat:server
       xmlns:mycat="http://io.mycat/">
       <system>
           <property name="nonePasswordLogin">0</property>
           <property name="useHandshakeV10">1</property>
           <property name="useSqlStat">0</property>
           <property name="useGlobleTableCheck">0</property>
           <property name="sequnceHandlerType">2</property>
           <property name="subqueryRelationshipCheck">false</property>
           <property name="processorBufferPoolType">0</property>
           <property name="handleDistributedTransactions">0</property>
           <property name="useOffHeapForMerge">1</property>
           <property name="memoryPageSize">64k</property>
           <property name="spillsFileBufferSize">1k</property>
           <property name="useStreamOutput">0</property>
           <property name="systemReserveMemorySize">384m</property>
           <property name="useZKSwitch">false</property>
       </system>
       <!--这里是设置的itcast用户和虚拟逻辑库-->
       <user name="itcast">
           <property name="password">root</property>
           <property name="schemas">itcast</property>
       </user>
   </mycat:server>
   ```

   



## 文档资料 

[[Mycat学习笔记 第一篇. MySql 读写分离与日志分析——主从单结点](https://www.cnblogs.com/kaye0110/p/5134588.html)](https://www.cnblogs.com/kaye0110/p/5134588.html)

