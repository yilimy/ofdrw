# OFD Reader & Writer

![-](https://img.shields.io/badge/language-java-orange.svg) [![license](https://img.shields.io/badge/license-Apache--2.0-blue)](./LICENSE)


在使用OFDRW前请务必悉知 [***《OFD Reader & Writer免责声明》***](免责声明.md)。


> 如何clone和预览存在困难，请移步 [https://gitee.com/Trisia/ofdrw](https://gitee.com/Trisia/ofdrw)


**Talk is cheap,Show me the code. ——Linus Torvalds**

**像写HTML和Word那样简单的编写OFD。**

根据[《GB/T 33190-2016 电子文件存储与交换格式版式文档》](./GBT_33190-2016_电子文件存储与交换格式版式文档.pdf)标准实现版式文档OFD库（含有书签）。

项目结构：

- [**ofdrw-core**](./ofdrw-core) OFD核心API，参考[《GB/T 33190-2016 电子文件存储与交换格式版式文档》](./GBT_33190-2016_电子文件存储与交换格式版式文档.pdf)实现的基础。
- [**ofdrw-font**](./ofdrw-font) 生成OFD需要的常规字体（OpenType）。
- [**ofdrw-layout**](./ofdrw-layout) OFD布局引擎库，用于文档构建和渲染。
- [**ofdrw-pkg**](./ofdrw-pkg) OFD文件的容器，用于文档的打包。
- [**ofdrw-reader**](./ofdrw-reader) OFD文档解析器，用于OFD的反序列化以及签名签章。
- [**ofdrw-sign**](./ofdrw-sign) OFD文档数字签章。
- [**ofdrw-gm**](./ofdrw-gm) 用于支持签章模块需要的国密电子签章数据结构。
- [**ofdrw-gv**](./ofdrw-gv) OFDRW 所有模块所共用的全局变量。
- [**ofdrw-full**](./ofdrw-full) 上述所有模块整合包，用于简化依赖引入。

## QuickStart

引入依赖
```xml
<dependency>
    <groupId>commons-io</groupId>
    <artifactId>commons-io</artifactId>
    <version>2.6</version>
</dependency>

<dependency>
  <groupId>org.ofdrw</groupId>
  <artifactId>ofdrw-full</artifactId>
  <version>1.5.2</version>
</dependency>
```


如何生成一份OFD文档？

> 如何把大象放入冰箱。

```java
public class HelloWorld {
    public static void main(String[] args) throws IOException {
        Path path = Paths.get("HelloWorld.ofd");
        try (OFDDoc ofdDoc = new OFDDoc(path)) {
            Paragraph p = new Paragraph("你好呀，OFD Reader&Writer！");
            ofdDoc.add(p);
        }
        System.out.println("生成文档位置: " + path.toAbsolutePath());
    }
}
```

效果如下：

![示例](./ofdrw-layout/doc/示例.png)

- [生成示例](https://github.com/Trisia/ofdrw/blob/master/ofdrw-layout/src/test/java/org/ofdrw/layout/OFDDocTest.java)
- [布局示例](https://github.com/Trisia/ofdrw/blob/master/ofdrw-layout/src/test/java/org/ofdrw/layout/LayoutTest.java)
- [Canvas示例](https://github.com/Trisia/ofdrw/blob/master/ofdrw-layout/src/test/java/org/ofdrw/layout/element/canvas/DrawContextTest.java)


相关文档目录：

- [OFD R&W 布局设计](./ofdrw-layout/doc/README.md)
- [OFD R&W Canvas](./ofdrw-layout/doc/canvas/README.md)
- [OFD  R&W 签名签章快速入门](./ofdrw-sign/doc/quickstart/README.md)

> > ***如果您对OFDRW合法签名签章以及验证有意向，我们可以为您提供相关商务咨询服务，请联系QQ: 1009020096 或邮箱 quanguanyu@qq.com。***

推荐的免费OFD阅读器: [福昕OFD版式办公套件 . http://www.htfoxit.com/Download/index/id/712](http://www.htfoxit.com/Download/index/id/712)

## 源码安装

在项目根目录下运行

```bash
mvn install
```

就可以完成项目的构建打包，安装到本地Maven仓库中。

## 交流

***Share and Communicate***

为了方便大家的交流提供QQ群

![QQ群](./img/QQLink.png)


群号： **577682453**

## 参与贡献

参考 [贡献指南](CONTRIBUTING.md)。

## 项目情况

### 进展

[>> 项目进展](releasenotes.md)

如果各位对 OFD R&W 有 **问题** 或是 **建议** 欢迎提交issue和PullRequest，这样的大家的问题都可以很好的得到分享，我也很乐意解答各位问题。

### 项目关注度

> 项目获得 Star曲线

[![Stargazers over time](https://starchart.cc/Trisia/ofdrw.svg)](https://starchart.cc/Trisia/ofdrw)
