# webp-imageio-core
forked from nintha/webp-imageio-core
Java Image I/O reader and writer for the Google WebP image format-  includes the system lib files.

This is based on [webp project of Luciad](https://bitbucket.org/luciad/webp-imageio) 0.4.2) 

### Gradle  (using jitpack)


```
repositories {
    jcenter()
    maven { url 'https://jitpack.io' }
}


dependencies {
    compile 'com.github.wezell:webp-imageio-core:v0.1.2'
}
```

### Usage

```java

      Float q = new Float(1);
      ImageWriter writer = ImageIO.getImageWritersByMIMEType("image/webp").next();
      WebPWriteParam writeParam = new WebPWriteParam(writer.getLocale());
      
      if(q==1) {
        writeParam.setCompressionMode(ImageWriteParam.MODE_EXPLICIT);
        writeParam.setCompressionType("Lossless");

      }else {
        writeParam.setCompressionMode(ImageWriteParam.MODE_EXPLICIT);
        writeParam.setCompressionType("Lossy");
        writeParam.setCompressionQuality(q);
      }


      writer.setOutput(new FileImageOutputStream(new File("test.webp")));
      writer.write(null, new IIOImage(ImageIO.read(file), null, null), writeParam);
      writer.dispose();
```

