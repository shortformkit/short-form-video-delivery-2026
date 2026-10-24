# Short-form video delivery 2026: what Reels, TikTok and Shorts actually serve

Resolution, codec, bitrate and loudness (LUFS, true peak) of **135 public short videos** as delivered by Instagram, TikTok and YouTube on 12 October 2026. One row per video, measured from the delivered files, not from upload guidelines.

Full write-up with charts: [What Reels, TikTok and Shorts really deliver (study 2026)](https://shortformkit.com/short-form-video-quality-study-2026/)

## Key findings

| | Instagram Reels | TikTok | YouTube Shorts |
|---|---|---|---|
| Videos | 51 | 42 | 42 |
| Median loudness | -14.1 LUFS | -21.2 LUFS | -19.6 LUFS |
| 80 % range | -15.0 to -14.1 | -27.5 to -15.0 | -24.4 to -10.8 |
| Within ±1 LU of -14 LUFS | 92 % | 10 % | 7 % |
| True peak above -1 dBTP | 82 % | 24 % | 34 % |
| Codec of the best stream | VP9 100 % | H.265 88 %, H.264 12 % | VP9 81 %, H.264 19 % |
| Median video bitrate (best stream) | 2.1 Mbit/s | 1.1 Mbit/s | 5.7 Mbit/s |
| Highest resolution offered | 1440p (4 %) | 1080p | 2160p (19 %) |

- **Instagram normalises audio to about -14 LUFS.** No Reel was louder than -14.0 LUFS, so mixing louder for Reels buys nothing.
- **TikTok does not level the delivered files.** A quiet upload stays quiet.
- **YouTube Shorts keep the uploaded level** and are the loudest and most varied.
- **Instagram's best stream is always VP9**, H.264 was never offered at that resolution. Relevant for editors: some NLEs and older Macs decode VP9 slowly.

## Files

- `data/videos.csv`: one row per video
- `data/summary.json`: the aggregated figures above, per platform

| Column | Meaning |
|---|---|
| platform | instagram, tiktok or youtube |
| url | public post URL |
| uploader | account name |
| duration | seconds, when the platform reports it |
| max_w, max_h, short_side | largest resolution offered (pixels) |
| best_vcodec | codec of the highest-quality video stream (vp09, h265, avc1/h264) |
| has_h264_at_best | an H.264 stream exists at that top resolution |
| best_tbr_kbps | total bitrate of the best stream (kbit/s) |
| fps | frame rate, when reported |
| max_audio_kbps | bitrate of the best audio stream (kbit/s) |
| lufs, lra, true_peak | integrated loudness (LUFS), loudness range (LU), true peak (dBTP), measured with ffmpeg ebur128 |
| measured_at | UTC timestamp of the measurement |

## Method

135 public videos (51 Instagram Reels, 42 TikToks, 42 YouTube Shorts) from 20 large public accounts in media, sports, science and entertainment: recent posts as shown on each profile on 2026-10-12, pinned posts included. Each video was requested logged out from a residential connection in Switzerland. The list of offered streams was read with yt-dlp, and the audio of the delivered file measured with ffmpeg's `ebur128` filter (integrated loudness and true peak, 4x oversampled). Silent videos (below -60 LUFS) are excluded from loudness figures (2 in total).

Limits: apps may receive different streams than the web, and big accounts are not every creator. Read this as a snapshot, not a census.

## License and citation

Data: [CC BY 4.0](LICENSE). Please credit and link:

> Shortform Kit, "Short-form video delivery 2026", measured 12 October 2026. https://shortformkit.com/short-form-video-quality-study-2026/

Check your own file before upload with the free [LUFS meter](https://shortformkit.com/lufs-meter/) or the [lufs-meter-js](https://github.com/shortformkit/lufs-meter-js) library.
