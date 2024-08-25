# ffmpeg7.0.2_rtmp_h265

FFmpeg 6.1以后的版本已经默认支持enhanced rtmp

该patch用来让FFmpeg 7.0.2兼容过去国内常用的codecid=12的方案

编译ffmpeg前
```sh
cd ffmpeg
git checkout n7.0.2
git apply /path/to/ffmpeg7.0.2-flv-hevc.patch
```

使用
* mux/推流：需要设置: -f flv -flvflags ext_codec
```markup
ffmpeg -re -i source.flv -c:v libx265 -c:a copy -f flv -flvflags ext_codec rtmp://192.168.0.1/live/1000
```

* demux/拉流: 无需客户外操作，自动识别
