## 发布

### setting.xml

在`servers`节点下添加：

```xml
<server>
  <id>github</id>
  <username>yourgithubusername</username>
  <password>yourgithubpasswd</password>
</server>
```

### pom文件

#### properties节点

```xml
<properties>
    <github.global.server>github</github.global.server>
    <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
</properties>
```

#### build节点

```xml
<build>
  <plugins>
    <plugin>
      <groupId>org.codehaus.mojo</groupId>
      <artifactId>versions-maven-plugin</artifactId>
      <version>2.3</version>
      <configuration>
        <generateBackupPoms>false</generateBackupPoms>
      </configuration>
    </plugin>
    <plugin>
      <artifactId>maven-deploy-plugin</artifactId>
      <version>2.8.2</version>
      <configuration>
        <altDeploymentRepository>
          internal.repo::default::file://${project.build.directory}/maven-repo
        </altDeploymentRepository>
      </configuration>
    </plugin>
    <plugin>
      <groupId>com.github.github</groupId>
      <artifactId>site-maven-plugin</artifactId>
      <version>0.12</version>
      <configuration>
        <message>Maven artifacts for ${project.artifactId}, version: ${project.version}</message>
        <noJekyll>true</noJekyll>
        <outputDirectory>${project.build.directory}/maven-repo</outputDirectory><!--本地jar地址-->
        <branch>refs/heads/master</branch><!--分支的名称, refs/heads是固定的-->
        <merge>true</merge>
        <includes>
          <include>**/*</include>
        </includes>
        <repositoryName>maven-repo</repositoryName><!--对应github上创建的仓库名称 name-->
        <repositoryOwner>cayzlh</repositoryOwner><!--github 仓库所有者即登录用户名-->
      </configuration>
      <executions>
        <execution>
          <goals>
            <goal>site</goal>
          </goals>
          <phase>deploy</phase>
        </execution>
      </executions>
    </plugin>
  </plugins>
</build>
```

## 使用

pom文件中加入以下配置：

```xml
<repositories>
  <repository>
    <id>maven-repo</id>
    <url>https://raw.githubusercontent.com/cayzlh/maven-repo/master/</url>
    <releases>
      <enabled>true</enabled>
    </releases>
    <snapshots>
      <enabled>false</enabled>
    </snapshots>
</repository>
```

## 目录

```
.
├── 123.md
├── README.md
└── com
    └── cayzlh
        ├── base-spring-boot-autoconfig
        │   ├── 0.1.2
        │   ├── maven-metadata.xml
        │   ├── maven-metadata.xml.md5
        │   └── maven-metadata.xml.sha1
        ├── base-spring-boot-sample
        │   ├── 0.1.2
        │   ├── maven-metadata.xml
        │   ├── maven-metadata.xml.md5
        │   └── maven-metadata.xml.sha1
        ├── base-spring-boot-starter
        │   ├── 0.1.2
        │   ├── maven-metadata.xml
        │   ├── maven-metadata.xml.md5
        │   └── maven-metadata.xml.sha1
        ├── base-spring-boot-starter-parent
        │   ├── 0.1.2
        │   ├── maven-metadata.xml
        │   ├── maven-metadata.xml.md5
        │   └── maven-metadata.xml.sha1
        ├── cayzlh-starters
        │   ├── 0.1.2
        │   ├── maven-metadata.xml
        │   ├── maven-metadata.xml.md5
        │   └── maven-metadata.xml.sha1
        ├── commons
        │   ├── 0.1.2
        │   ├── maven-metadata.xml
        │   ├── maven-metadata.xml.md5
        │   └── maven-metadata.xml.sha1
        ├── jwt-spring-boot-autoconfig
        │   ├── 0.1.2
        │   ├── maven-metadata.xml
        │   ├── maven-metadata.xml.md5
        │   └── maven-metadata.xml.sha1
        ├── jwt-spring-boot-sample
        │   ├── 0.1.2
        │   ├── maven-metadata.xml
        │   ├── maven-metadata.xml.md5
        │   └── maven-metadata.xml.sha1
        ├── jwt-spring-boot-starter
        │   ├── 0.1.2
        │   ├── maven-metadata.xml
        │   ├── maven-metadata.xml.md5
        │   └── maven-metadata.xml.sha1
        ├── jwt-spring-boot-starter-parent
        │   ├── 0.1.2
        │   ├── maven-metadata.xml
        │   ├── maven-metadata.xml.md5
        │   └── maven-metadata.xml.sha1
        ├── redis-distributedlock-spring-boot-autoconfig
        │   ├── 0.1.2
        │   ├── maven-metadata.xml
        │   ├── maven-metadata.xml.md5
        │   └── maven-metadata.xml.sha1
        ├── redis-distributedlock-spring-boot-sample
        │   ├── 0.1.2
        │   ├── maven-metadata.xml
        │   ├── maven-metadata.xml.md5
        │   └── maven-metadata.xml.sha1
        ├── redis-distributedlock-spring-boot-starter
        │   ├── 0.1.2
        │   ├── maven-metadata.xml
        │   ├── maven-metadata.xml.md5
        │   └── maven-metadata.xml.sha1
        ├── redis-distributedlock-spring-boot-starter-parent
        │   ├── 0.1.2
        │   ├── maven-metadata.xml
        │   ├── maven-metadata.xml.md5
        │   └── maven-metadata.xml.sha1
        ├── redisson-distributedlock-spring-boot-autoconfig
        │   ├── 0.1.2
        │   ├── maven-metadata.xml
        │   ├── maven-metadata.xml.md5
        │   └── maven-metadata.xml.sha1
        ├── redisson-distributedlock-spring-boot-sample
        │   ├── 0.1.2
        │   ├── maven-metadata.xml
        │   ├── maven-metadata.xml.md5
        │   └── maven-metadata.xml.sha1
        ├── redisson-distributedlock-spring-boot-starter
        │   ├── 0.1.2
        │   ├── maven-metadata.xml
        │   ├── maven-metadata.xml.md5
        │   └── maven-metadata.xml.sha1
        ├── redisson-distributedlock-spring-boot-starter-parent
        │   ├── 0.1.2
        │   ├── maven-metadata.xml
        │   ├── maven-metadata.xml.md5
        │   └── maven-metadata.xml.sha1
        ├── zk-distributedlock-spring-boot-autoconfig
        │   ├── 0.1.2
        │   ├── maven-metadata.xml
        │   ├── maven-metadata.xml.md5
        │   └── maven-metadata.xml.sha1
        ├── zk-distributedlock-spring-boot-sample
        │   ├── 0.1.2
        │   ├── maven-metadata.xml
        │   ├── maven-metadata.xml.md5
        │   └── maven-metadata.xml.sha1
        ├── zk-distributedlock-spring-boot-starter
        │   ├── 0.1.2
        │   ├── maven-metadata.xml
        │   ├── maven-metadata.xml.md5
        │   └── maven-metadata.xml.sha1
        └── zk-distributedlock-spring-boot-starter-parent
            ├── 0.1.2
            ├── maven-metadata.xml
            ├── maven-metadata.xml.md5
            └── maven-metadata.xml.sha1
```