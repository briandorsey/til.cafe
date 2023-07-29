+++
title="Convert GIFs to black and white using gifsicle"
date=2023-07-29
[taxonomies] 
post_type=["TIL"]
[extra] 
summary="Command line recipe for converting GIFs to just black and white." 
+++

If you need to convert a GIF image from color or grey scale into just black and white, here is a recipe using a command line tool called [gifsicle](https://www.lcdf.org/gifsicle/)

Here is my original image (captured from the [Playdate Simulator](play.date/dev)).

![alt text][rain]

And after running this command:
``` sh
$ gifsicle --gamma=1 --use-colormap=bw < rain.gif > rain_bw.gif
```

We get a black and white image. I needed to use the gamma flag for this image, since it's so low contrast, the default result was a solid black image. 

![alt text][rain_bw]

And... that's pretty much it. For more details on various options for `gifsicle`, see the [gifsicle docs](https://www.lcdf.org/gifsicle/man.html)

[rain]: rain.gif "A two color, low contrast animated GIF file, showing trees with a rain animation."
[rain_bw]: rain_bw.gif "A two color, black and white animated GIF file, showing trees with a rain animation."

