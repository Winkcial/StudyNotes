
每一个 Maven 项目都是一个文件夹

```shell
# 创建一个 Hello 目录
.
├── pom.xml# Maven 的核心配置文件。 
└── src
    ├── main # 放置主程序 Java 代码和配置文件。
    │   ├── java # 你的程序包和包中的 Java 文件。
    │   └── resources # 你的程序使用的配置文件
    └── test
        ├── java # 测试程序的代码
        └── resource # 测试程序需要使用的配置文件
```

命令

```shell
$ mvn complie 编译 src/main 目录下的所有 Java 文件
```

- 第一次编译会下载很多东西（插件 即 jar 包）

- 下载目录你的文件（默认 .m2 可以修改成你自己的）

- 编译成功会出现 target 目录

```
org.apache.maven.plugins:maven-compiler-plugin:compile 
```

