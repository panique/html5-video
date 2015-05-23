# html5-video

A simple copy&paste solution for crossbrowser-safe HTML5 video with a flash fallback. Open-source and 100% free for
private and commercial projects. Works on all browsers (unless the user is completely retarded and surfs with an
extremely outdated browser and doesn't have flash installed at the same time).

### Supported browsers

This code block is made to be crossbrowser-safe. It will run on Chrome, Firefox, Safari, Internet Explorer 6 - 11 and
most mobile browsers. Please note that old or bad browsers (Ie6, IE7, IE8 and Opera) are not able to playback .mp4 and
therefore need Flash installed to show a video. If they don't have flash: No video.

### How to use

This demo includes a demo.html that shows a full implementation inside a naked HTML document. The video player itself
looks like this: To work with it, simply exchange demo.mp4 with your .mp4 file and demo.jpg with your .jpg!
Due to Flash security restrictions this will only work on a real server (that has an IP or a domain) or in a local
environment, like localhost / 127.0.0.1! DON'T simply open a .html file (that lays on your desktop) containing the
above code with a double-click. This will not work (due to flash's security restrictions).

```html
<!-- HTML5 video tag -->
<video controls="controls" poster="img/demo.jpg" width="640" height="360">
    <!-- .mp4 file for native playback in IE9+, Firefox, Chrome, Safari and most mobile browsers -->
    <source src="vid/demo.mp4" type="video/mp4" />
    <!-- flash fallback for IE6, IE7, IE8 and Opera -->
    <object type="application/x-shockwave-flash"
            data="swf/flowplayer-3.2.18.swf" width="640" height="360">
        <param name="movie" value="swf/flowplayer-3.2.18.swf" />
        <param name="allowFullScreen" value="true" />
        <param name="wmode" value="transparent" />
        <!-- note the encoded path to the image and video files, relative to the .swf! -->
        <!-- more on that here: http://en.wikipedia.org/wiki/Percent-encoding -->
        <param name="flashVars"
               value="config={'playlist':['..%2Fimg%2Fdemo.jpg',{'url':'..%2Fvid%2Fdemo.mp4','autoPlay':false}]}" />
        <!-- fallback image if flash fails -->
        <img src="img/demo.jpg" width="640" height="360" title="No Flash found" />
    </object>
</video>
```

Note the encoded URL in `<param name="flashVars" ...`. More on how to encode
[here on Wikipedia](http://en.wikipedia.org/wiki/Percent-encoding).

I've also written an article on this script here:
[DEV METAL - Crossbrowser-safe HTML5 video (IE6+) with a few lines of code and just one .mp4 video file]
(http://www.dev-metal.com/crossbrowser-safe-html5-video-ie6-lines-code)

### Why only .mp4 and no .ogv or .webm ?

Good question! These days every HTML5 browser (IE9+, Chrome, Firefox, Safari, most mobile browsers) is able to play
.mp4 nativly. The only browser who totally fails is Opera (desktop version). Opera still needs .ogv or .webm, but as
there's a fine flash fallback also Opera users can see the video. Unless they also don't have flash. And seriously,
do people who surf with Opera AND reject to install flash deserve to see a video ? Those bloody idiots!
If you are forced to still give native support for Opera, then add an .ogv file right after the first source tag:

```html
<!-- note the .ogv format but the ogg mime type -->
<source src="vid/demo.ogv" type="video/ogg" />
```

### Used third-party flash player

This repository uses the free version of the Flowplayer (currently 3.2.18).
The free version of the Flowplayer is licensed under GNU GENERAL PUBLIC LICENSE Version 3 (GPL).
You can download the latest version on [Flowplayer's download page](https://flowplayer.org/pricing/#downloads).
You'll find the .swf files (one is the player itself, one is for the autoloaded UI controls) in the *swf* folder.
Don't touch, don't move, unless you know exactly what you do. The company behind Flowplayer offers commercial,
unbranded solutions too. I'm not affiliated in any way with Flowplayer or Flowplayer Ltd.

### Used demo video and image files

The used image and video are parts of the Peach Open Movie project and licensed under Creative Commons Attribution 3.0.

### Troubleshooting

1. "It does not work in IE6/7/8" or "I only see a blank white page in Internet Explorer 6/7/8":
   You don't have Flash installed! These extremely outdated browsers cannot display videos without Flash.

2. Safari browsers might need proper MIME-type handling for video files, so add `AddType video/mp4 .mp4` to your
   Apache config (or into a .htaccess in the video folder). More [here](http://stackoverflow.com/q/2643447/1114320).

3. "Flash cannot find the video files": As explained above, due to Flash security restrictions this will not work
   locally on your computer unless you upload everything to a real server or work within localhost / 127.0.0.1!
   Also make sure you have set the paths to the file correctly.

### Further read

- [DiveIntoHTML5 - Video on the web](http://diveintohtml5.info/video.html)
- This project was inspired by the [Video For Everybody Generator](http://v4e.thewikies.com/)
  (that still works quite well but has some legal issues and hotlinks player files).

### Support & Donate

If this saves you a lot of time, stress and money, then consider getting a new cheap server at [Host1Plus](https://affiliates.host1plus.com/ref/devmetal/36f4d828.html) or [DigitalOcean](https://www.digitalocean.com/?refcode=40d978532a20). Thanks!
