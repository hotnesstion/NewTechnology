##### 1依赖

```xml
<dependency>
  <groupId>org.apache.pdfbox</groupId>
  <artifactId>pdfbox</artifactId>
  <version>2.0.17</version>
</dependency>
```

转化过程中可能会遇到转换缺失等问题，请加上以下依赖：

(1) jpegerror的异常

```xml
<dependency>
    <groupId>com.twelvemonkeys.imageio</groupId>
    <artifactId>imageio-jpeg</artifactId>
    <version>3.4.2</version>
</dependency>
```

(2) ERROR: Cannot read JBIG2 image: jbig2-imageio is not installed

```xml
<dependency>
    <groupId>org.apache.pdfbox</groupId>
    <artifactId>jbig2-imageio</artifactId>
    <version>3.0.2</version>
</dependency>
```

(3) Cannot read JPEG2000 image: Java Advanced Imaging (JAI) Image I/O Tools are not installed

```xml
<dependency>
    <groupId>com.github.jai-imageio</groupId>
    <artifactId>jai-imageio-core</artifactId>
    <version>1.4.0</version>
</dependency>

<dependency>
    <groupId>com.github.jai-imageio</groupId>
    <artifactId>jai-imageio-jpeg2000</artifactId>
    <version>1.3.0</version>
</dependency>
```

生产环境一般用Linux主机，当然Linux主机也有自己的字体，我们一般开发环境用的是Windows自带的字体文件。

我们的做法是，直接把Windows下的字体（C:\Windows\Fonts）文件移动到Linux下（可行）。

```bash
#cd /usr/share/fonts/   // 进入系统自带的字体目录
#mkdir myfonts  // myfonts 是你自己随便取得文件夹名字
#将字体文件拷贝到这个文件夹下，在cd /usr/share/fonts/目录下执行以下命令
#mkfontscale   
#mkfontdir
#fc-cache -fv           //更新字体缓存
#source /etc/profile    // 执行以下命令让字体生效
#fc-list    // 查看系统中所有得字体，可用于测试是否安装字体成功
```























