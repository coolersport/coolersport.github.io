---
layout: post
category : misc
tagline: "Bookmarklet to show lyrics for Google Music"
tags : [google music, lyrics, bookmarklet]
---
{% include JB/setup %}

This [bookmarklet](http://en.wikipedia.org/wiki/Bookmarklet) adds support for lyrics in Google Music.
 
When you play a song and like to sing along, this can help fetching corresponding lyrics from [LyricWikia](http://lyrics.wikia.com) and display on the screen.
It is just a harmless [bookmarklet](http://en.wikipedia.org/wiki/Bookmarklet) which requires you to install nothing (see source code).
All you need to do is dragging the link below to your browser bookmark bar.

<iframe src="//code.coolersport.info/html/google-music-lyrics-bookmarklet.html" width="300" height="50" style="display:block;margin:0 auto;border:none">&nbsp;</iframe>

The [bookmarklet](http://en.wikipedia.org/wiki/Bookmarklet) must be used in the Google Music tab and a song is being played.
Clicking on it the first time will show a panel with lyrics of the current song.
Clicking while the song is still playing will hide the lyrics panel. When a new song is played, click again to load new lyrics.

If a song's lyrics is unavailable, you will be prompted to search and create new entry on [LyricWikia](http://lyrics.wikia.com).
The new lyrics will be available soon after being published.

If there is any issue, please leave a comment at the bottom of the page.

Verbose version:

    javascript:(function(){
        var artist = document.getElementById('player-artist') || false;
        artist = artist ? artist.innerText + ':' : '';
        var url = 'https://lyrics-coolersport.rhcloud.com/index.php/'+encodeURI(artist+document.getElementById('playerSongTitle').innerText);
        var frame = document.getElementById('lyricsframe');
        if (frame || false) {
            var removing = frame.src == url;
            frame.parentNode.parentNode.removeChild(frame.parentNode);
            if (removing) return false;
        }
        var div = document.createElement('div');
        document.getElementsByTagName('body')[0].appendChild(div);
        div.style.position = 'fixed';
        div.style.top=0;
        div.style.left=0;
        div.style.right=0;
        div.style.bottom=0;
        div.style.zIndex=999999;
        div.style.pointerEvents='none';
        frame = document.createElement('iframe');
        div.appendChild(frame);
        frame.id = 'lyricsframe';
        frame.style.border = '2px groove #fff';
        frame.style.width='50%';
        frame.style.height='70%';
        frame.style.margin='5% auto';
        frame.style.display='block';
        frame.style.pointerEvents='all';
        frame.src = url;
        return false;
    })();


