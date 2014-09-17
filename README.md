cordova-media-generator
=======================

CLI Utility that generates Cordova / Phonegap image assets required for app store submission, icons, and splash screens.
It requires your logo to have a solid background colour but does not distort or lose any image content so everything is at the maximum size without loss.

Usage:

with NodeJS installed:

```bash
$ npm install -g cordova-media-generator
```

Then:
```bash
$ npm init
```

Once installed, cd to the root of your Cordova application and run:
```bash
$ mediagen <logofilename.jpg> <backgroundcolourinhex-egFFF>
```

EXAMPLE:
```bash
$ mediagen logo.jpg fff
```

If you have created a `mediagen-config.json` file (see below), you can just run:
```bash
$ mediagen
```

This will overwrite all logos and splash screen images in the `<projectdir>/platforms` directory with the correct sizes and in the correct location for Cordova (As at 3.5)
> The recommended image or logo size is 2000px x 2000px. Its not a problem if the logo isn't square.

It also creates a `<projectdir>/Media` directory that has images for the Apple and Android stores such as an app icon.

## Custom Assets
You can create additional custom images if you need to submit to alternative app stores or have other needs that we haven't thought of yet.

Simply go to your project directory and run
```bash
$ mediagen init
```

It will create an example file called `mediagen-config.json` which you can now edit. Add as many or few files as you need to the array.

> Note: The default path for files is the `<projectdir>/platforms` directory, you might need to use `../` as in the example below

###Example `mediagen-config.json`
```javascript
{
    "image": "logo.png",
    "background": "fff",
    "customImages": [
        {"width": 120, "height": 120, "path": "../Media/custom", "filename":"filename.png"}
    ]
}
```

The config variables are below:

image: the large source image
background: the solid background colour in hex values
custom images: an array of custom image objects for additional media if desired
    - width: the width of the image in pixels
    - height: the height of the image in pixels
    - path: the directory to save the output
    - filename: the output file name with extension
