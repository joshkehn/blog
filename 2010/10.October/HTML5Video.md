{"title": "HTML5 Video and Kinetic Typography","date": 1287544232000}
++++++++++
I have been hankering to post some video in HTML5's *extremely* easy to use format. The issue was I couldn't find anything decent to post. Ends up I really like well done [Kinetic Typography](http://en.wikipedia.org/wiki/Kinetic_typography). Two very well done and popular videos are V's speech to Eve from V for Vendetta and the Chemical Burn scene from Fight Club. These videos were done by [Chris Silich](http://www.chrissilich.com/) and [Sebastian Jaramillo](http://www.sebastianjt.com) respectively. *My deepest thanks go out to them for providing me with the raw files to re-encode and permission to use them.* 

Flash is great for some things but not for others. HTML5 specs include a `<video>` tag that allows easy platform based decoding. Disadvantages are lack of control (cannot splice ads in) and source availability (unless you want to code some rather nasty stuff, people can download the video). Flash solves both these problems but it doesn't solve the mobile device issue, mainly it's not a lightweight player when decoding. Some devices have hardware based [H.264](http://en.wikipedia.org/wiki/H.264/MPEG-4_AVC) decoding available. 

You can put video up in whatever format you wish, however the issue remains with codecs. Different browsers prefer different codecs. Mobile Safari only recognizes the H.264 codec, while Firefox only recognizes Theora (Ogg container, Vorbis audio). Theora / Vorbis is free while H.264 is licensed. Chrome supports H.264 and VP8, which is another codec. For more reading on this lovely subject I refer you to [Dive Into HTML5: Video](http://diveintohtml5.com/video.html) which has excellent breakdowns and technical details about codecs.

The markup for this is very easy and I'll try to explain it in pieces.

    <video id="vidv" controls="true" preload="none" width="480" height="272" poster="src" draggable="true">

The `<video>` tag starts off with some pretty intuitive options. Controls implements the browsers native control bar, `preload="none"` stops it from preloading (doesn't work in Chrome), width, height, `poster=` allows you to specify an external image to display initially instead of the first few frames of the video. `Draggable` will supposedly let you "drag to save" but this doesn't work in all browsers.

In order to overcome the aforementioned codec issue I include two differently encoded sources. One in H.264 (Chrome, Safari), and one in Ogg Theora / Vorbis. These are specified as different source elements.

    <source type='video/mp4; codecs="avc1.42E01E, mp4a.40.2"'....
    <source type='video/ogg; codecs="theora, vorbis"'....

Something to understand is this does not work in any version of IE. **IE users have my sympathies.** You shouldn't be using that browser anyways. There are open source Flash player workarounds, but I wanted to keep this pure HTML5. In a true usability setting you would implement various JavaScript code to determine feature capabilities and render the appropriate video setting.

### Without further ado, the videos.

<video id="vidv" controls="true" preload="none" width="480" height="272" poster="http://c0027442.cdn1.cloudfiles.rackspacecloud.com/v.png" draggable="true">
<source src="http://c0027442.cdn1.cloudfiles.rackspacecloud.com/v.mp4" type='video/mp4; codecs="avc1.42E01E, mp4a.40.2"' />
<source src="http://c0027442.cdn1.cloudfiles.rackspacecloud.com/v.ogv" type='video/ogg; codecs="theora, vorbis"' />
</video>
<br />
<video id="vidfc" controls="true" preload="none" width="480" height="320" poster="http://c0027442.cdn1.cloudfiles.rackspacecloud.com/fightclub.png" draggable="true">
<source src="http://c0027442.cdn1.cloudfiles.rackspacecloud.com/fightclub.mp4" type='video/mp4; codecs="avc1.42E01E, mp4a.40.2"' />
<source src="http://c0027442.cdn1.cloudfiles.rackspacecloud.com/fightclub.ogv?v=1" type='video/ogg; codecs="theora, vorbis"' />
</video>

***

For those wondering about V's speech, I have it below as well as title anchor tags that help clarify the words.

> [Voilà](# "Used to call attention, to express satisfaction or approval, or to suggest an appearance as if by magic")! In view, a humble [vaudevillian](http://en.wikipedia.org/wiki/Vaudeville "A theatrical genra of variet entertainment, here used to describe a veteran of this style") [veteran](# "A person who has long service or experience in a particular occupation or field"), cast [vicariously](# "Experienced or realized through imaginative or sympathetic participation in the experience of another") as both [victim](# "An unfortunate person who suffers from a disaster or other adverse circumstance.") and [villain](# "The bad person in a work of fiction; often the main antagonist of the hero.") by the [vicissitudes](# "Regular change or succession from one thing to another, or one part of a cycle to the next; alternation; mutual succession; interchange.") of [Fate](# "A personification of fate (the cause that predetermines events)."). This [visage](# "Image or illusion, what is presented instead of the truth"), no mere [veneer](# "An attractive appearance that covers or disguises true nature or feelings") of [vanity](# "Excessive pride in or admiration of one's own appearance or achievements"), is a [vestige](# "A faint mark or visible sign left by something which is lost, or has perished, or is no longer present; remains") of the [vox populi](# "Voice of the people"), now [vacant](# "Empty"), [vanished](# "Unnoticed or invisible"). However, this [valorous](# "Has the qualities of valor; strength of mind in regard to danger; a brave man.") [visitation](# "An encounter") of a by-gone [vexation](# "An irritation or annoyance"), stands [vivified](# "Brought to life") and has [vowed](# "Solemnly promised") to [vanquish](# "Defeat or overcome") these [venal](# "Corrupt, or crooked; able to bribe") and [virulent](# "Infectious, malignant, deadly") [vermin](# "Plague creatures, fleas, lice mice, rats") [vanguarding](# "Protecting") [vice](# "Succession") and [vouchsafing](# "To graciously give") the [violently](# "Involving extreme force or motion") [vicious](# "Pertaining to vice; characterized by immorality or depravity") and [voracious](# "Having a great appetite for anything") [violation](# "The act or an instance of violating or the condition of being violated") of [volition](# "The mental power or ability of choosing; the will"). The only [verdict](# "Judgement") is [vengeance](# "Revenge"); a [vendetta](# "Bitter, destructive feud"), held as a [votive](# "Dedicated or given in fulfillment of a vow or pledge"), not in [vain](# "Pointless, futile"), for the [value](# "Worth") and [veracity](# "Truthfulness") of such shall one day [vindicate](# "To clear from an accusation, suspicion or criticism") the [vigilant](# "Watchful, alert, wary") and the [virtuous](# "Full of virtue, having excellent moral character"). [Verily](# "Without doubt"), this [vichyssoise](# "Thick soup") of [verbiage](# "Words") [veers](# "Leans, is moving towards") most [verbose](# "Containing more then necessary"), so let me simply add that it is my very good honor to meet you and you may call me V.

<cite>Original text from [V for Vendetta](http://www.whysanity.net/monos/vendetta.html), corrected and marked up by Joshua Kehn</cite>