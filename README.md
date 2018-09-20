**Note:** This repository was forked from [minimaxir/video-to-gif-osx](https://github.com/minimaxir/video-to-gif-osx).
* Added support for spaces in paths and filenames
* Added support for Finder Quick Action in MacOS Mojave (10.14)

# Convert Video to GIF on OSX

This repository contains a set of utilities that allow the user to easily convert video files to high-quality, low file size GIFs on OS X. This post is a complement to my blog post [Making a Video-to-GIF Right-Click Menu Item in OS X](http://minimaxir.com/2015/08/gif-to-video-osx/)

![](https://user-images.githubusercontent.com/1969831/45839619-2a832200-bd15-11e8-9a19-8a8a5778cad5.gif)

The primary intent for this tool is used with Quicktime Movie files obtained from using the Screen Recording feature on OS X or iOS input.

The tool comes in three forms, depending on user needs:

* **[Convert Video to GIF](https://github.com/mrbruins/video-to-gif-osx/raw/master/Convert%20Video%20to%20GIF%20App%20Custom.zip)** - An OS X (< 10.14) Service which adds a "Convert Video to GIF" right-click menu item to all video files, which outputs a GIF of the video in the same folder of the source(s). (file must be unzipped on desktop). On MacOS Mojave and higher (10.14+), this file installs as a quick action for Finder.
* **[video_to_gif_osx.sh](https://raw.githubusercontent.com/mrbruins/video-to-gif-osx/master/video_to_gif_osx.sh)** - A Shell script which accepts video(s) as parameter(s) and outputs a GIF of the video in the same folder of the source(s).
* **[Convert Video to GIF App](https://github.com/mrbruins/video-to-gif-osx/raw/master/Convert%20Video%20to%20GIF%20App.zip)** - An Application which prompts the user for video(s) and outputs a GIF of the video in the same folder of the source(s). (file must be unzipped on desktop; when prompted for security warning go to "Security and Privacy" in System Preference and allow Convert Video to GIF App to run)

There is also a special fourth tool, [Convert Video to GIF App Custom](https://github.com/mrbruins/video-to-gif-osx/raw/master/Convert%20Video%20to%20GIF%20App%20Custom.zip) app, which is less streamlined but also allows you to specify a custom start time, end time, maximum width, frame rate, and # of colors. For example, here's a GIF of [Freedom Planet](https://en.wikipedia.org/wiki/Freedom_Planet) from a test video of 2:00 to 2:05, a max width of 640px, and 4 colors:

![](http://i.imgur.com/ZSY6RM7.gif)

## Installation

*Note: Installation may have issues depending on system config, particularly step #2. If you run into issues, let me know.*

1. Open up Terminal and install [Homebrew](http://brew.sh) by running this command and following the instructions:

		ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

2. Install the three GIF-making applications using this Homebrew command:

		brew install ImageMagick mplayer gifsicle

3. Download the tool of choice. To install the Convert Video to GIF Service, download and double-click.

## Tests

When running into the script, you may run into an issue where the .GIF is generated, but the file size is zero bytes. That means the script errored out at some point except the "create a GIF" line.

The `tests` folder contains a basic test case to debug the script. To activate the test, `cd` into the folder and run:

	sh test.sh test_video.mov

This outputs a `test_results.txt` in addition to the test GIF. If `test_results.txt` matches `expected_results.txt`, you should be good to go. If there is a discrepency, send me the output of `test_results.txt`.

## Notes

All forms have a max GIF width of 480px; this is a value chosen to both manage file size and compatability with all applications. If you wish to create larger GIFs, open up the tool and change the value of `GIF_MAX_SIZE` at the beginning of the file.

## Known Issues

* If the video has unusual dimensions (e.g. 7.00 aspect ratio), the GIF output will not be resized correctly. (in fairness, you probably do not want a GIF with an unusual aspect ratio)
* ~~If the video file or the parent directory has spaces, the tool may throw errors.~~ Fixed!
* Convert Video to GIF Custom has no sanity check for input validation yet. (e.g. don't increase the frame rate beyond 60fps or bad things happen). If you encounter any issues *specific to the Custom app*, let me know.

## Maintainer
* Forked from Max Woolf [(@minimaxir)](http://minimaxir.com)
