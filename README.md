動画変換用Docker
================


# 実行

## 例: movie.mp4

```
INFILE=movie
docker run -v $(pwd):/work ubuntu/ffmpeg cd /work; ffmpeg -i ${INFILE}.mp4 -vcodec libx264 -b:v 256k -acodec aac -strict experimental -ab 64k -ar 44100 -flags +loop-global_header -map 0 -bsf h264_mp4toannexb -f segment -segment_format mpegts -segment_time 10 -segment_list ${INFILE}.m3u8 ${INFILE}%04d.ts
```

# build

```
docker build -t ubuntu/ffmpeg .
```

