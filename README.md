# bdf2-bom
管理 BDF2 项目版本
BDF2 本身Jar包版本管理混乱，所以我使用该项目统一管理 bdf 及 dorado 依赖
在 maven 项目里添加如下代码，跟 dependencies 节点并行，项目可以升级到最新的 BDF2、dorado、Spring 4。

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
