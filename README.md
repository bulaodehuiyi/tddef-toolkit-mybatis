# tddef-toolkit-mybatis
mybatis-generator插件，生成基础dao和常见crud方法，支持mysql和oracle分页，实体类带注释

generatorConfig.xml配置如下：
<?xml version="1.0" encoding="UTF-8"?>  
<!DOCTYPE generatorConfiguration  
  PUBLIC "-//mybatis.org//DTD MyBatis Generator Configuration 1.0//EN"  
  "mybatis-generator-config_1_0.dtd">
<generatorConfiguration>
	<!-- 配置参数 -->
	<properties resource="conf/config4Generator.properties" />
	<context id="context" targetRuntime="MyBatis3">
		<property name="javaFileEncoding" value="UTF-8"/>
		<property name="mapperTargetPackage" value="${packeageName}.dao" />
		<plugin type="org.mybatis.generator.plugins.SerializablePlugin"></plugin>
		<plugin type="com.tangdi.def.toolkit.mybatis.generator.TdPaginationPlugin" />
		<plugin type="com.tangdi.def.toolkit.mybatis.generator.TdMapperPlugin" />
		<commentGenerator type="com.tangdi.def.toolkit.mybatis.generator.TdCommentGenerator">
		</commentGenerator>

		<!--数据库链接URL，用户名、密码 -->
		<jdbcConnection driverClass="${jdbc_driverClassName}"
			connectionURL="${jdbc_url}" userId="${jdbc_username}" password="${jdbc_password}">
		</jdbcConnection>
		<javaTypeResolver>
			<property name="forceBigDecimals" value="false" />
		</javaTypeResolver>

		<!-- 生成模型的包名和位置 -->
		<javaModelGenerator targetPackage="${packeageName}.entity"
			targetProject="${projectName}/src/main/java">
			<property name="enableSubPackages" value="true" />
			<property name="trimStrings" value="true" />
		</javaModelGenerator>
		<!-- 生成映射文件的包名和位置 -->
		<sqlMapGenerator targetPackage="conf.mapper"
			targetProject="${projectName}/src/main/java">
			<property name="enableSubPackages" value="true" />
		</sqlMapGenerator>
		<!-- 生成DAO的包名和位置 -->
		<!-- <javaClientGenerator type="XMLMAPPER"
			targetPackage="${packeageName}.dao" targetProject="${projectName}/src/main/java">
			<property name="enableSubPackages" value="true" />
			<property name="rootInterface" value="com.tangdi.tbc.dao.BaseMapper"/>
		</javaClientGenerator> -->

		<!-- 要生成的表 -->
		<table tableName="auth_org" domainObjectName="AuthOrg" enableCountByExample="false" enableUpdateByExample="false" enableDeleteByExample="false" enableSelectByExample="false" selectByExampleQueryId="false"></table>
		</context>
</generatorConfiguration>
