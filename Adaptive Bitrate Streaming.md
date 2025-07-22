technique used in video streaming that allows the quality of a video stream to adjust dynamically based on the user’s network conditions.
## Principles
• Maximise the downloaded video quality.
• Minimise the rebuffering.
• Minimise the startup delay.
• Maximise the stream stability.
• Minimize the bandwidth wastage/power drain of the device.

## High-level idea 
break down the whole video into chunks of a few seconds. Each chunk may have a different resolution and thus has a different size. The size is then indirectly adjusted by changing the resolution of each chunk. How and when the size is changed is up to the decision of the algorithm. We covered two main types:

- Buffer-based algorithm : The resolution is decided upon considering the status of the buffer.
- Latency-based algorithm : The resolution is decided upon considering the latency of chunks.

## DASH (Dynamic Adaptive Streaming over HTTP)
> a **specific implementation of ABR** that is an open standard developed by the Moving Picture Experts Group (MPEG). It allows streaming of media content over HTTP. The DASH client (video player) uses an MPD file (Media Presentation Description; an XML file describing the structure of the media) to determine which segment to download next, based on the current network conditions, and can switch between different bitrates as needed. DASH is widely supported.