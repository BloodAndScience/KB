# Media files convertation

## Cutting video into equal chunks

```powershell
$if="NeetCode-PythonForInterview.mp4"
$d =$(gl)
$total_size=$(ffprobe -v error -show_entries format=size -of default=noprint_wrappers=1:nokey=1 $if)
$chunk = $(10*1024*1024)
```

```powershell

$input_file = "NeetCode-PythonForInterview.mp4"
$output_dir = $(gl)

New-Item -ItemType Directory -Path $output_dir -Force | Out-Null

$total_size = (Get-ChildItem $input_file).Length
$chunk_size = 10MB
$num_chunks = [Math]::Ceiling($total_size / $chunk_size)

for ($i=0; $i -lt $num_chunks; $i++) {
    $start = $i * $chunk_size
    $output_file = Join-Path $output_dir "chunk$(`"{0:D3}`" -f $i).mp4"
    ffmpeg -i $input_file -c copy -fs $chunk_size -ss $start $output_file
}

```


## Links

[FFMPEG cheatsheet](https://gist.github.com/nickkraakman/e351f3c917ab1991b7c9339e10578049)

## Subs

Generate and burn YouTube like subs

```bash
yt-dlp --write-auto-subs --sub-langs ru https://www.youtube.com/watch?v=0mJ4W2R_MMo


ffmpeg -i 'HaosIn.webm' -vf "subtitles=HaosIn.vtt:force_style='Fontsize=36,Fontname=Roboto,OutlineColour=&H40000000,BorderStyle=3'" -s 1280x720 Haos.mp4
```

## Gifsi Gif to Webp

`ffmpeg -i video.mp4 frame%04d.png`
`gifski -o file.gif frame*.png`
`gif2webp [options] input_file.gif -o output_file.webp`

!Imporatant the output and input file may be normal but something like -vf subtitiles=./tmp/video. shout use `/` instead of Windows standard `\`


## Burn Subtitiles

`ffmpeg -i input.mp4 -vf "subtitles=subtitle.srt:force_style='Fontname=Roboto,OutlineColour=&H40000000,BorderStyle=3'" output.mp4`


! `subtitles =./file/address` not `subtitle=.\file\address`
`ffmpeg -i video.mkv -vf subtitles=./local/video.mkv .\res\out.avi`

## List

- ScreenToGif
- Youtube-dl
- ffmbeg
- giftowebp
- imgtowebp

## FFMPEG

### Cahange default language

#### Hide output

`-loglevel quiet`

#### Limit CPU usage

`-threads 12 `

### Get info

`ffprobe input.mp4`

### 360 Videos

[360 Video cheatsheet](https://gist.github.com/nickkraakman/e351f3c917ab1991b7c9339e10578049)

My 360 compression. 
*!Important:* has `-ss` and `-fs` 
```bash
ffmpeg -i .\mistok-src.mp4 -c:v libx264 -b:v 23M -pix_fmt yuv420p -c:a aac -b:a 192K -ss 03 -fs 90M mistok-5.mp4
```


### Limit file size
`ffmpeg -i input -fs 10M -c copy output`

###  Segment video and reset timesstamp
```bash
ffmpeg -i .\Adventure.Time.Distant.Lands.s01e01.WEB-DL.720p.NewStation.mkv -f segment -strttime 1 -segment_time 15:00 -c copy -reset_timestamps 1 E01-%03d.mp4
```

```bash
ffmpeg -i .\Adventure.Time.Distant.Lands.s01e02.WEB-DL.720p.NewStation.mkv -vf subtitles=Adventure.Time.Distant.Lands.s01e02.WEB-DL.720p.NewStation.mkv -ss 37:47 -d 01:00   SubTest.mp4
```


### Crop TikTokVideo 

ffmpeg -i input.mp4 -filter:v "crop=576:850" output.mp4

### Split Audio

Split audio into the equal 30 min parts

```powershell
ffmpeg -i .\ADHD-Relief.mp3 -f segment -segment_time 3000 -c copy ADHDRelief%03d.mp3
```
### FLAC to mp3

`ffmpeg -i input.flac -ab 320k -map_metadata 0 -id3v2_version 3 output.mp3
egment -strftime 1`

### 


### Cut part of video 
`-ss` - start teime
`-t` - Duration 

```powershell
ffmpeg --s 00:05:00 -i '.\input.mkv' -s 1280x720 -t 300 'out.mp4'
```
```powershell
ffmpeg -ss 00:07:34  -i input.mp4 -t 00:00:15 -s 1280x720 -vcodec copy -acodec copy output.mp4
```

### Speed up 

20x times `0.05=1/20`

```powershell
ffmpeg -i 'input.mkv' -filter:v "setpts=0.05*PTS" SpeedUp.mp4
```

### Gif
`-f gif` 
Format we wan't output into

```bash
ffmpeg -i animated.gif -movflags faststart -pix_fmt yuv420p -vf "scale=trunc(iw/2)*2:trunc(ih/2)*2" video.mp4
```
### Main

`-i StickAround.mp4`
Input file is StickAround.mp4


`-ss 61.0` 
We want to start reading  from 61 second.

`-t 2.5`
We wan't to read only 2.5 seconds

### Mp4ToGif

Command:

```powershell 
ffmpeg -ss 61.0 -t 2.5 -i StickAround.mp4 -f gif StickAround.gif 
```

### Crop the video
```bash
ffmpeg -i ForEugene.mp4 -filter:v 'crop=iw-840' 'EugeneCrop.mp4'
```

#### Resize

`ffmpeg -i some.mkv -s 1280x720 output.mp4`

## Scripts

### MrLoopGif

This script generate

```PowerShell
$style = "'Fontsize=36,Fontname=Hack,OutlineColour=&H40000000,BorderStyle=3'"

function MakeSubs {
	ffmpeg -i $($in) -map "0:2" $subs
}

function MakeFrames {

	rm $frames
	ffmpeg -i $($in) -s $scale -ss $($ss) -t $t -vf "subtitles=$($subs):force_style=$($style), fps=12" 'frame%04d.png'

}
function MakeGifFromFrames {

	rm $gout
	#gifski -o $gout frame*.png
	gifski -o $gout --quality 80 --fps=12 "frame*.png" 
	ii $gout
}
```
