---
layout: post
category : misc
tagline: "Bookmarklet to show lyrics for Google Music"
tags : [google music, lyrics, bookmarklet]
---
{% include JB/setup %}

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
    var div = document.createElement("div");
    document.getElementsByTagName("body")[0].appendChild(div);
    div.style.position = 'fixed';
    div.style.top=0;
    div.style.left=0;
    div.style.right=0;
    div.style.bottom=0;
    div.style.zIndex=999999;
    div.style.pointerEvents='none';
    frame = document.createElement("iframe");
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