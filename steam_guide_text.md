


THIS PART IS LINUX SPECIFIC
0 Introduction Edit
Linux, GameConqueror, And Hollow Knight on PC

Hi!
This is my first guide here on Steam, and after having seen many online asking how to cheat on Hollow Knight, Here is my attempt at it. Note I am using Linux, and it was awhile ago I did this kind of stuff, so hopefully it will be readable!

And I Will only write examples, I used GameConqueror for those who like Gui

Before we dive in, listen to your favo music(my favo is: Crystal Peak), and grab a coffee and lets do this.

If questions, do reply! I might be very slow at answering though but, I will be trying my best!

Good Luck!

Assumptions
* When I say something like "change the values of these addresses" or something on those lines, you should, in Game Conqueror, already have selected all of the addresses (in the window top left) and clicked on them -> "[Add to cheat list/table]") < I will assume this.

* Do know that this might crash, and you might accidentally save when you have done stuff so, first things first, BACKUP the save games! (usually in .config folder's unity3d directory)

* Hearts,HealthPoints,lifes and masks is used interchangebly
* search, and scan, is used interchangebly



Part 1
Variables you choose to change: (the number before the variable denotes the difficulty of changing it's value) (e.g "1: abc" would mean 'abc' has a easy difficulty(1))

- 1 Geo
- 1 Notches
- 1 Health points (masks)
- 3 Soul

through-out this mini-guide I Will be using GameConqueror so, open that up on Linux
And in select process, search "Knight" and take the first one (In my case it is the first one) (ends with something like x86_hollowknight < something like that)
1 Infinite Geo Edit
Geo
1. Start up a save and go over to the game conqueror window, and enter the geo-value you have (say, 15)
2. ingame, gather more geo (1 for example),
3. enter the new geo value, either directly(16) or like this(15+1)
4. continue doing this until you only have 2 or 3 Addresses to choose from
5. try to change each addresses values, from 16 to, say, 1000, and tick that box [x] on each of them
6. you should now not only have 1000 geo, but also *always have 1000 geo* (that's what ticking the box does, it "locks" it.)
7. (optional mathematical analogy) 

Each pattern, kind of follows a similar structure! You could make a exercise: do the above, but this time on hearts, or notches even. It's a nice way to practice without only-guide-following (though, it's nothing wrong with following guides).
2 Infinite Notches Edit
Notches
Now, this is where I thought..It might not work because (maybe?) ingame you really shouldn't be able to have *ALL* charms *AT ONCE*, but..I tried it, and it does (for me) work!

(Note, I am also new to these genre of souls like and 2d games but, its interesting)

1. as usual, open up both game-conqueror and the game, and load a save.
2. now, (you will probably be sitting on a bench already), open inventory, head over to charm selection.
3. equip, say, 1 charm that costs 2 notches. so, (2 bright notches lights up).
4. head over to game conqueror and type "2" and hit scan.
5. equip another charm, that costs, say, 1 notch, (2+1=3) So 3 notches lights up
6. now scan for 3 (or 2+1)
7. repeat this loop until you have a list of notches-addresses (Note: for me I had quite many, 10 maybe, and, of course you could try each one, but it doesn't hurt if you just set all of them to be value:1 and tickbox:[x] )
8. Now, you should* be able to equip every charm ingame.
3 Infinite hearts Edit
Hearts
Hearts (or masks) is probably..as simple as geo. It's basically the same, but with masks instead.
1. if you have 5 hearts, search for 5 in Game Conqueror.
2. get hurt. (once, ideally) (INGAME I should add! not IRL!)
3. re-scan the new value
(if you got hurt and lost 2 hearts, just search for 5-2 or search for 3)
4. repeat until you are left with a short, neat list of addresses.
5. do the usual, "select them" -> "add to table" -> "tick box" -> "change value"
6. You should now be, invincible!

4 Infinite Soul Edit
Soul
Here is where it gets tricky, there is no real number-bar (e.g 0/50) there is just a vague orb that gets filled with some hits on enemies.

So: (Correct me if charm-name below is wrong)
I googled how much Soul per hit with the charm Soul Catcher: it turns out its 14
so 14 soul points per hit with that charm, (can be written 14*1)

How to do infinite
1. empty your soul, completely.(100% empty)
2. and then equip the Soul-Catcher charm
3. hit an enemy ONCE
4. go over to Game-Conqueror,
5. scan for 14 (or 14*1)
6. now, hit an enemy again
7. scan for 28 (or just scan for 14*2)
8. repeat until you have a short list of few addresses
9. as always add those addresses to the cheat-list/table and change each of their values from , (the value you now have) to say, 14*3
10. Now you should have infinite soul.
5 Advanced concepts Edit
Advanced Concepts

Notes:
* I use HK to say Hollow Knight, and GC to say Game Conqueror.
* I Will assume you at least know basic commands,and keywords is (sudo,apt,etc)
* (r&w is read write by the way)
* * But if you don't, feel free to ask! (Really, And I will try my best to explain! ^^)
* ; is a comment, in assembly, as I am coming from that kind of background It kinda stuck with me. so if I say "<code> ; hello" then, <code> is the thing you should type, and ignore the ( ; ...) because ; is a comment.


Advanced

first we want to install scanmem
 sudo apt update 
 sudo apt install scanmem 


Hooking It Up to HK
 sudo scanmem 
this enters scanmem, its interactive, and very simple and easy to use

For those who has followed along above, and maybe even used Cheat Engine, or maybe even done some basic memory manipulation, might know that the first 3 basic things is
1. open the process(hence sudo since we will demand memory r&w access),
2. scan for the value you want to change that you have (e.g 100 geo)
3. manipulate ingame (get more geo or lose geo) and enter the new value (Nothing else is required, no command called "scan <value>" no no, just "value"!


PITFALL: Using
 pidof Hollow 
or
 pidof hollow 
doesnt work if its steam because steam *loves* to hide PID's, instead, you have to
 ps x | grep hollow 
and then see the full path, in my case it looks like this
 /home/grea/.local/share/Steam/steamapps/common/Hollow Knight/hollow_knight.x86_64 

And what you want is the last one, so:
right after the "Hollow Knight/" we have "hollow_knight.x86_64" this is what we want to get pidof from.

 pidof hollow_knight.x86_64 
in my case it's 1883818
this will be used as the first step when we enter "pid (..)" in scanmem.

; Okay! to the code (or script)!
0
 sudo scanmem ; if you havent already 
1
 pid 1883818 
2
 100 ; original geo value 
3
 101 ; added geo value 
4
 list ; when you only have say "3~" results left, type this to list addrs.
5
 set 1337  ; now you can set the geo value to 1337 (leet xD) 


6 Proof Of Concept Media Edit
Proof Of Concept(POC) Media
(screenshots,videos, and so on)

Figure 1.a) Many Charms All At Once

Figure 2.a) Many Geo, More Geo! As the ant bug said, right?

Videos posted via GitHub(GH) Because I can't upload videos to steam guide for some reason
https://github.com/loneicewolf/Steam-Games-Notes/tree/main/GAMES/HollowKnight/Cheats
7 Closing Words from the Author Edit
Closing words & About the Math
It's a wonderful game, I love it. Even more now because one can explore without needing to be scared to lose 850 geo or something, and as this game is full of traps, this is just a way to make it a tad bit more enjoyable *for those who want to use cheats*, if not thats valid too obviously! ^^

Now, Sorry if I was dry in the above steps/structure, I spent 1 hour and 30~ minutes doing this reply in hope to make it clear, and a couple of notes:

when I say "type 14*2" take that literally. Literally input
14*3
into the scan-box, in Game Conqueror. This is what makes it such a nice program, you don't need to be a god at math to do this(I am not, I should add! I suck at math heh)

Thanks For Reading!
Have a nice year! And if you have any questions do reply to me, and I will try my best to answer; Take care!

Warmest wishes from Sweden!
