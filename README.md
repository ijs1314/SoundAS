[license]: https://github.com/treefortress/SoundAS/raw/master/license.txt

SoundAS
=======

A modern lightweight sound manager for AS3. 

The goal of SoundAS is to simplifying playback of your audio files, with a focus on easily transitioning from one to another, and differentiating between SoundFX and Music Loops.

#Features
* Clean modern API
* Built-in Tweening system, no dependancies
* Easy memory management

#API Overview

##SoundAS
This Static Class is the main interface for the library. It's responsible for loading and controlling all sounds globally.

Loading / Unloading: 

*    addSound(type:String, sound:Sound):void
*    loadSound(url:String, type:String, buffer:int = 100):void
*    removeSound(type:String):void
*    removeAll():void

Playback:

*    getSound(type:String, forceNew:Boolean = false):SoundInstance
*    play(type:String, volume:Number = 1, startTime:Number = -1, loops:int = 0, 
     allowMultiple:Boolean = false, allowInterrupt:Boolean = true):SoundInstance
*    playFx(type:String, volume:Number = 1, startTime:Number = -1, loops:int = 0):SoundInstance
*    playLoop(type:String, volume:Number = 1, startTime:Number = -1):SoundInstance
*    resume(type:String, volume:Number = 1, startTime:Number = -1, loops:int = 0):SoundInstance


##SoundInstance
Controls playback of individual sounds, allowing you to easily stop, start, resume and set volume or position.

#Code Examples

###Loading

    //Load sound from an external file
    SoundAS.loadSound("assets/Click.mp3", "click");

    //Inject an already loaded Sound instance
    SoundAS.addSound(clickSound, "click");

###Basic Playback

    //Play sound.
        //allowMultiple: Allow multiple overlapping sound instances.
        //allowInterrupt: If this sound is currently playing, start it over.
    SoundAS.play("click", volume, startTime, loops, allowMultiple, allowInterrupt);

    //Shortcut for typical game fx (no looping, allows for multiple instances)
    SoundAS.playFx("click");

    //Shortcut for typical game music (loops forever, no multiple instances)
    SoundAS.playLoop("click");

    //Toggle Mute 
    SoundAS.mute = !SoundAS.mute;

    //Fade Out
    SoundAS.getSound("click").fadeTo(0);

###Advanced 

    //Mute one sound
    SoundsAS.getSound("click").mute = true;

    //Fade from .3 to .7 over 3 seconds
    SoundAS.getSound("click").fadeFrom(.3, .7, 3000);

	//Manage a SoundInstance directly
    var sound:SoundInstance = SoundAS.getSound("click");
    sound.play(volume);
    sound.position = 500; //Set position of sound in milliseconds
    sound.volume = .5; 
	sound.fadeTo(0);

---
### License
[WTFPL][license]

