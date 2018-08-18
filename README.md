# bdf2-bom
管理 BDF2 项目版本
BDF2 本身Jar包版本管理混乱，所以我使用该项目统一管理 bdf 及 dorado 依赖
在 maven 项目里添加如下代码，跟 dependencies 节点并行，然后删除掉dependencies节点里dependency/version 被标识为Duplicating managed version的 version 节点。
项目可以升级到最新的 BDF2、dorado、Spring 4。


```XML
<dependencyManagement>
	<dependencies>
		<dependency>
			<groupId>org.xobo.dorado</groupId>
			<artifactId>bdf2-bom</artifactId>
			<version>0.0.1</version>
			<type>pom</type>
			<scope>import</scope>
		</dependency>
	</dependencies>		
</dependencyManagement>
```

示例 pom.xml

```XML
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
	<modelVersion>4.0.0</modelVersion>
	<groupId>com.bstek.bdf2</groupId>
	<version>1.0.0</version>
	<artifactId>bdf2-project</artifactId>
	<packaging>war</packaging>
	<dependencies>
		<dependency>
			<groupId>com.bstek.bdf2</groupId>
			<artifactId>bdf2-core</artifactId>
			<!-- 应该删除的 version 节点 -->
			<!--  <version>2.0.9</version> -->
		</dependency>
		<dependency>
			<groupId>org.hsqldb</groupId>
			<artifactId>hsqldb</artifactId>
			<version>2.0.0</version>
		</dependency>
	</dependencies>
	<dependencyManagement>
		<dependencies>
			<!-- bdf2 版本管理 -->
			<dependency>
				<groupId>org.xobo.dorado</groupId>
				<artifactId>bdf2-bom</artifactId>
				<version>0.0.1</version>
				<type>pom</type>
				<scope>import</scope>
			</dependency>
		</dependencies>
	</dependencyManagement>
	<repositories>
		<repository>
			<id>bsdn-maven-repository</id>
			<url>http://nexus.bsdn.org/content/groups/public/</url>
		</repository>
	</repositories>
</project>
```
