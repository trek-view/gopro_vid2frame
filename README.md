# GoPro 360 mp4 video to frames

Converts GoPro mp4s with equirectangular projections into single frames with correct metadata.

## Installation

TODO 

## Usage

### Camera support

This video only accepts mp4 videos shot on a GoPro cameras.

It supports both 360 and non-360 videos. In the case of 360 videos, these must be processed by GoPro Software to final mp4 versions.

This script has currently been tested with the following GoPro cameras:

* GoPro HERO
	* HERO 8
	* HERO 9
	* HERO 10
* GoPro MAX
* GoPro Fusion

### Video requirements

* Must be shot on GoPro camera
* Must have telemetry (GPS enabled when shooting)

### Validation

To ensure the video can be processed, the following checks are applied.

For .mp4 videos we can determine video is spherical (equirectangular) if it contains the following metatag `<XMP-GSpherical:ProjectionType>equirectangular</XMP-GSpherical:ProjectionType>`.

Once type (360/non-360) has been determined, we next check it contains telemetry from GoPro by identifying the following metatag `<TrackN:MetaFormat>gpmd</TrackN:MetaFormat>`. _Note: TrackN where N = track number, which varies between GoPro cameras._ 

If the script fails any of these checks, you will see an error returned.

### Options

```
$  gopro-frame-maker.py [options] VIDEO_NAME.mp4
```

Options:

* -r n sets the frame rate (frames per second) for extraction, default: `5`. Options available:
	* `1`
	* `2` 
	* `5`
* -q n sets the extracted quality between 2-6. 1 being the highest quality (but slower processing), default: 1. This is value used for ffmpeg `-q:v` flag. Options available:
	* `1`
	* `2` 
	* `3`
	* `4`
	* `5`
* -d enable debug mode, default: off.  Options available:
	* `true`
	* `false` 

#### Examples (MacOS)

##### TODO


## Support

Join our Discord community and get in direct contact with the Trek View team, and the wider Trek View community.

[Join the Trek View Discord server](https://discord.gg/ZVk7h9hCfw).

## License

The code of this site is licensed under an [MIT License](/LICENSE).