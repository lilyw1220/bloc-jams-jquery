    1) This file declares a class, Player, instantiates it, and assigns it to a global player variable.
    2) The Player class contains six methods:
        constructor()
        getDuration()
        getTime()
        playPause()
        skipTo()
        setVolume()
    3) The constructor() method sets initial values for the currentlyPlaying, playState, volume, and soundObject properties.
        currentlyPlaying is set to the first item in album.songs.
        The initial playState is "stopped".
        volume is set to the number 80.
        The soundObject instantiates a new buzz.sound object using the soundFileUrl property of this.currentlyPlaying. The buzz variable doesn't appear to be initialized here, so presumably it's a dependency loaded elsewhere.
    4) The getDuration() method returns this.soundObject.getDuration(). It appears to be a wrapper for a method available on this.soundObject.
    5) The getTime() method returns this.soundObject.getTime(). It also appears to be a wrapper for a method available on this.soundObject.
    6) The playPause() method accepts one parameter, song. It sets it to this.currentlyPlaying by default. It checks to see if this.currentlyPlaying is different from song, and if so, it:
        Stops the soundObject property.
        Removes the "playing" and "paused" classes from the element property of this.currentlyPlaying.
        Sets this.currentlyPlaying to the function's parameter, song.
        Changes the playState property to "stopped".
        Instantiates a new sound object using this.currentlyPlaying, which was just updated to song.
        It also checks that if the playState is paused or the playState is stopped
        -the soundObject volume is set to setVolume with a parameter of this.volume.
        -plays the soundObject property
        -changes the playState property to "playing"
        -removes "paused" class from the element property of this.currentlyPlaying and adds "playing"
        If not, then
        -pause the soundObject property
        -changes the playState to "paused"
        -removes "playing" class from the element property of this.currentlyPlaying and adds "paused".
    7) The skipTo() method accepts one parameter, "percent." If the player is playing, it will return:   this.soundObject.setTime( (percent / 100) * this.soundObject.getDuration() );
    8) The setVolume() method accepts one parameter, "percent." The soundObject is set to the value of the percent of "volume."
