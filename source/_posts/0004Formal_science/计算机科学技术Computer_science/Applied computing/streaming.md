# live streaming settings

## live streaming  video setting

### Televisions are of the following resolutions

- Standard-definition television (SDTV):
  - 480i (NTSC-compatible digital standard employing two interlaced fields of 243 lines each)
  - 576i (PAL-compatible digital standard employing two interlaced fields of 288 lines each)
- Enhanced-definition television (EDTV):
  - 480p (720 × 480 progressive scan)
  - 576p (720 × 576 progressive scan)
- High-definition television (HDTV):
  - 720p (1280 × 720 progressive scan)
  - 1080i (1920 × 1080 split into two interlaced fields of 540 lines)
  - 1080p (1920 × 1080 progressive scan)
- Ultra-high-definition television (UHDTV):
  - 4K UHD (3840 × 2160 progressive scan)
  - 8K UHD (7680 × 4320 progressive scan)

#### interlaced and progressive

the “i” in this example indicates an “interlaced” image scan. Besides interlaced there is also another method, known as “progressive” scan.

Interlaced: In the first frame, only the odd numbers of vertical lines are displayed, the even lines stay blank. In the following frame, the even numbers of vertical lines will be displayed, while the odd lines stay blank. This method effectively halves the required bandwidth and reduces flicker. Also it allows for better adaption of different frame rates, as overlapping frames can be merged into each other.
Progressive: Each frame carries the full amount of vertical lines and the full image information is displayed on every single frame. Whilst requiring more video bandwidth, it will allow for better image quality compared to the interlaced method.

### Luminance/chrominance systems in general

The primary advantage of luma/chroma systems such as Y′UV, and its relatives Y′IQ and YDbDr, is that they remain compatible with black and white analog television (largely due to the work of Georges Valensi). The Y′ channel saves all the data recorded by black and white cameras, so it produces a signal suitable for reception on old monochrome displays. In this case, the U and V are simply discarded. If displaying color, all three channels are used, and the original RGB information can be decoded.

Another advantage of Y′UV is that some of the information can be discarded in order to reduce bandwidth. The human eye has fairly little spatial sensitivity to color: the accuracy of the brightness information of the luminance channel has far more impact on the image detail discerned than that of the other two. Understanding this human shortcoming, standards such as NTSC and PAL reduce the bandwidth of the chrominance channels considerably. (Bandwidth is in the temporal domain, but this translates into the spatial domain as the image is scanned out.)

#### Y'CbCr Color Model

In the Y'CbCr color model, the three colors Red, Green, and Blue are not expressed as an individual value like it is done in RGB. Instead, the information will be encoded into a luminance value (Y) and two chrominance components (Cb, Cr)

#### chroma

Chrominance (chroma or C for short) is the signal used in video systems to convey the color information of the picture (see YUV color model), separately from the accompanying luma signal (or Y' for short). Chrominance is usually represented as two color-difference components: U = B′ − Y′ (blue − luma) and V = R′ − Y′ (red − luma).

#### Chroma Subsampling

Chroma Subsampling is a method to reduce the amount of data information of a Y'CrCb video signal. The perception of the human visual system (HVS) is less sensitive to color information than it is to changes in luminance, or brightness. So even if the human vision is capable of resolving differences in luminance in fine detail, it may not recognize if chroma information is greatly reduced in the resulting picture. Basically, a video signal that takes advantage of Chroma Subsampling will use less bandwidth because the color information in the signal has a lower resolution than the brightness information.

### Frame Rate

The frame rate of a video signal defines how many consecutive images will be displayed in a finite amount of time, to result in a motion picture perception at the viewer. Usually the frame rate is expressed in frames per second (FPS).

Good examples are the two major television standards NTSC and PAL, which are referring to a frame rate of 30 FPS (**NTSC**) and 25 FPS (**PAL**). Those frame rates originated from the frequency of the mains power supply in the counties in which each standard has been established. Modern theatrical film runs at 24 FPS. This is the case for both physical film and digital cinema systems.

### Video over Ethernet

In a single digital video signal, there are 5 relevant factors to determine how much data is required:

- Video Resolution - Which is the size of the digital video image - (examples: 4k, 1080p, 720p, etc... )
- Frame Rate - The speed at which the digital image is refreshed - (examples: 60hz, 30hz, etc... )
- Color space - The gamut of possible colors that can be represented by the color encoding of a signal. (examples: RGB, YUV, Y'CrCb)
- Chroma Sub-sampling - The reduction of color information by using fewer bits per pixel at a cost of color space. (examples: 4:4:4, 4:2:2, 4:2:0)
- Color bit-depth - This is the binary number which represents the total number of possible values for each color component. In much like digital audio, the more bits we have the greater depth possible for the signal. (examples: 10-bit, 12-bit).

#### example

Let's take one example of an uncompressed video signal that is a common signal format:

1080p, 60 Hz, YUV 4:2:2, 10-bit = 2.49 Gbps

We can read this line as a combination of all of the parameters we have shown above. If we were to break this statement out into a series of sentences, we read this as a digital video signal that has a resolution of 1080p with a frame rate of 60Hz. It utilizes the YUV color space and 4:2:2 chroma sub-sampling for each YUV component. There are 10-bits used for each of the three color components listed.

To calculate the bandwidth we start with the resolution of the image:

1920 * 1080 (for 1080p) = 2,073,600 pixels in an image of this size.

Then multiply by the refresh rate:

2,073,600 * 60Hz = 124,416,000 total pixels (per second)

You can think of this number 124,416,000 as the number of pixels a display will have shown in one second of video.

Now we need to remember that each pixel is made up of three components, each of them are of a certain bit depth. Furthermore we might be "sub sampling" a set of pixels to help reduce the data footprint with a small trade off in image detail.

We start with the Chroma subsampling ratio of 4:2:2. This ratio is applied over a 2 x 4 block of pixels or a total of 8 pixels as we previously learned. Thus we first need to take our total number of pixels and divide them by 8:

124,416,000 pixels / 8 pixels in our 2x4 row = 15,552,000 blocks of 8 pixels.

Now we calculate what we know regarding our Chroma subsampling ratio and apply that to the number of blocks making sure to include our 10-bit color bit-depth per component:

Y' =  8 pixels * 10-bits = 80 total bits for Y' for each 8 pixel block

U = 4 pixels * 10-bits = 40 total bits for U for each 8 pixel block

V = 4 pixels * 10-bits = 40 total bits for V for each 8 pixel block

Now we add those all together and multiply that against the number of blocks to finally arrive at the total amount of data required for this video signal:

160 bits for each 8 pixel block * 15,552,000 blocks = 2,488,320,000 total bits required for one second of video.

Or more nicely expressed: 2.49 Gbps

### Compression

![Alt text](/assets/images/streaming/image.png)


| --- | Intra-Frame: M-JPEG, JPEG 2000 | Interframe: MPEG-4 part 10 / H.264 (AVC), H.265 (HVEC) |
| --- | --- | --- |
| Latency | As low as 33 msec | 200 msec or higher |
| Bandwidth | High | Low |
| Compression | < 25:1 | > 25:1 |
| Processing | Symmetric| Asymmetric |
| Error Tolerance | High|  Low (Reference Frames) |

### broadband speed

A broadband speed of 2 Mbit/s or more is recommended for streaming standard-definition video, for example to a Roku, Apple TV, Google TV or a Sony TV Blu-ray Disc Player.

5 Mbit/s is recommended for high-definition content

and 9 Mbit/s for ultra-high-definition content.

Streaming media storage size is calculated from the streaming bandwidth and length of the media using the following formula (for a single user and file):
storage size in megabytes is equal to length (in seconds) × bit rate (in bit/s) / (8 × 1024 × 1024).

For example, one hour of digital video encoded at 300 kbit/s (this was a typical broadband video in 2005 and it was usually encoded in 320 × 240 resolution) will be: (3,600 s × 300,000 bit/s) / (8 × 1024 × 1024) requires around 128 MB of storage.

Using a multicast protocol the server sends out only a single stream that is common to all users. Therefore, such a stream would only use 300 kbit/s of server bandwidth.

#### youtube

Recommended bitrate setting ranges are based on video ingestion resolution and frame rate. These recommendations are the same for AV1 and HEVC.  

![Alt text](/assets/images/streaming/image-1.png)


#### an estimation on the usage in different resolutions

240p: 225MB per hour
360p: 315MB per hour
480p: 562.5MB per hour
720p at 30FPS: 1237.5MB (1.24GB) per hour
720p at 60FPS: 1856.25MB (1.86GB) per hour
1080p at 30FPS: 2.03GB per hour
1080p at 60FPS: 3.04GB per hour
1440p (2K) at 30FPS: 4.28GB per hour
1440p (2K) at 60FPS: 6.08GB per hour
2160p (4K) at 30FPS: 10.58GB per hour
2160p (4K) at 60FPS: 15.98GB per hour

These calculations are based on YouTubes data and has been calculated according to this.

For 480p video (standard quality), YouTube recommends a bitrate between 500 and 2,000Kbps. Let’s average these two extremes and use 1,250Kbps.

1,250Kbps (kilobits per second) divided by 1,000 gives us 1.25Mbps (megabits per second). Since there are eight bits in one byte, 1.25Mbps divided by eight equals roughly 0.156 megabytes per second of video. Multiplying this by 60 seconds means that 480p video uses around 9.375MB of data per minute on YouTube.

"9.375MB per minute times 60 minutes in an hour results in roughly 562.5MB of data per hour of YouTube streaming at 480p."
