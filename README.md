# Cheat Sheet

Random stuff I find myself needing now and again, but not frequently enough to know them from the top of my head.

## 2-pass AV1 VBR encoding

```
ffmpeg -i input.mkv -an -pix_fmt yuv420p10le -f yuv4mpegpipe -strict -1  - | SvtAv1EncApp -i - -w 1920 -h 1080 --rc 1 --tbr 1300 --keyint 300 --stats stat_file.stat --pass 1

ffmpeg -i input.mkv -an -pix_fmt yuv420p10le -f yuv4mpegpipe -strict -1  - | SvtAv1EncApp -i - -w 1920 -h 1080 --rc 1 --tbr 1300 --keyint 300 --stats stat_file.stat --pass 2 -b output.ivf

ffmped -i output.ivf -i audio.opus -map 0:v:0 -map 1:a:0 -c:v copy -c:a copy merged.mkv
```

Note: `--keyint` FPS times 10 in that keys. Totally optional. 
