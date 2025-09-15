# computer lab nineteen eighty and six

## a cool pp shader!
this is a shader and it is a post processing shader and its for pretending your game was released a long time ago before sonic was invented. it is _not_ a crt shader, it is _not_ period-piece-drama-accurate and it is not meant to be any kind of emulated or recreated thing. it is just an artistic expression of what it felt like to look at a terminal when i was a young boy and perhaps the damned wall was still up.

## how to work it
well basically you import the package and just call `computer_lab_nineteen_eighty_and_six()` in the post draw event, and then draw the application surface. you will need to do all the regular things for a pp effect such as disabling blending and making sure the the thing is drawn stretched or scaled or whatever you need.

```gml
/* CREATE EVENT */
application_surface_draw_enable(false);

/* POST DRAW EVENT */

computer_lab_nineteen_eighty_and_six();

gpu_set_blendenable(false);
draw_surface(application_surface, 0, 0, width, height);
gpu_set_blendenable(true);
```

## how it works
it does several passes that include some color bleeding, which is a chromatic abberation that gets blurred, as well as a regular chromatic abberation which just does a regular non blurred thing. then some noise and a horizontal scanline are thrown in the mix. its all very uncomplex.

however!

this shader makes an assumption that your application surface is scaled higher than your view. so if your view is 640x360 then your application surface should have a size of 1920x1080. if your game is 1920x1080 then probably just leave it that will be fine.

## tips und tricks
- this thing works best for low resolution jraphics. it is meant to give you the old timey feels so if you apply it to something new timey it will probably look like not good
- there is actually a debug function in there, if you call `computer_lab_nineteen_eighty_and_six_debug(true)`, that will bring up a debug window where you can play with the parameters of things and fine tune it to do whatever you want. however you will need to write those things down and change them in the `computer_lab_nineteen_eighty_and_six()` function cause they are all static variables.
- this shader makes and reuses two surfaces to do cool shit, keep that in mind when you are looking for batch break and texture swap boogiemen
- this is the end of this project! i made it for a game that is no longer in production. the reason the uniform values are baked at a specific value and the reason everything seems really static is because it was never meant to be public. yet here we are! you will have to adjust and tune and fix this on your own tho

## before & after
![shows a cool picture before the filter](https://github.com/attic-stuff/computer-lab-nineteen-eighty-and-six/blob/master/without.png)
  
  ![shows a cool picture after the filter](https://github.com/attic-stuff/computer-lab-nineteen-eighty-and-six/blob/master/with.png)

  ## license
  this package is provided as is and without any kind of warranty. you are free to use it in your projects but please leave me out of it. i am not responsible for anything you do with it, i do not want credit for it, and i have zero liability for whatever you do with it. if you are using any element of this repository then you agree to that.
