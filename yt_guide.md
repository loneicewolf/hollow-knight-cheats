The cheating playlist
https://youtube.com/playlist?list=PLzPjNm14Efb1iDqQgvqkocHpbHj_CfYib&si=9inwO1QPORcroUfe

> **This DOUBLE JUMP video was very long, AND VERY detailed, so I paste the notes I show the viewers here: so You can read them, at your own pace!**



Hii janna here again!
LONG STORY turned VERY SHORT - 
I tried to achieve Infinite Double Jump in HK.
Why? because I got many, DMS in chat apps asking me to explain and stuff, so I figured let's do that! as people seem to like that!

NOTE BEFORE YOU CONTINUE, I will just quickly scroll down, so you can read the text if you want, but it's details, mostly, for people who just want "show me how to cheat without long explanation" just skip trough.
(It's quite long, and detailed, I wrote this yesterday night, so I don't need to write it while recording)



and so I thought, how I would do it,
Most games uses 2 "things":
thing 1) either they use "set var=0" 
thing 2) or they use bitwise 'tricks' like    "xor var,var"; 

Basically xors var with itself, to become zero, and this is like a drop-in replacement for "set <somevariable> to 0" because it operates faster, (bitwise ops is generally, faster than just setting a value)

Now why I bring this up is cuz we will be doing some 
bitwise operations BUT - Don't worry - the audience of this video isn't Math or Programming experts (I'm not one anyway) I will only give you as much info, without details on unnec. stuff, so that you just 'know' what happens and so on, otherwise, this would turn into a assembly + bitwise op video which, frankly put - isn't the goal of my videos xD my goal, is the technical challenge!


So, but Before I dive in, I will first paste a number and a code-snippet which, will look very obvious to everyone:
```
for i in {0..10}; do echo "$i = $(( $i << 24 )); in some games"; done
16777216
```

It's obvious what it is right? 
Jokes aside,
No, No Of Course it's not, what is 16777216? 
and what's that big line of commanmds?
Let me explain!
```
$i << 24

is a "left bitwise shift" 24 times, of number "$i" so if you set "$i" to be 2 for example, we have 
2 << 24 = 33554432
```
Why is this important? What is this?
Well, as I previously mentioned,
BUT let me re-state it into more obvious terms:
```
2   <<   24    =      33554432
<  this     equals   this >
```
Now, a common misconception is,
okay so instead of
	var=2
we do
	var=33554432

But that's wrong, because that's setting the value *anyway*,
what is "correct" (if you using bitwise ops that is)
```
is
	var << 24
```
# Now Finally I will explain #
```
Why use 
	1 << 24 (which is 16777216 to be scanned for)
instead of
	var = 1
?
```
Because, game devs sometimes use 
BitWise Operations as a FASTER drop-in replacement for explicit variable-setting.

So we can use this knowledge to make a loop to predict new "1,2,3" values to scan for:
```
# for i in {0..10}; do echo "$i = $(( $i << 24 )); in some games"; done
0 = 0; in some games
1 = 16777216; in some games
2 = 33554432; in some games
3 = 50331648; in some games
4 = 67108864; in some games
5 = 83886080; in some games
6 = 100663296; in some games
7 = 117440512; in some games
8 = 134217728; in some games
9 = 150994944; in some games
10 = 167772160; in some games
```
So, in essence what this gives us is a very neat table with new "1"'s and "2"'s (..)'s To scan for

imagine a game which don't use 
it uses this bitwise operation instead
this means it's predictable, because
# REAL ANALOGY: I think many of you who has used cheat engine or any "mem scan" tool in a game, has noticed, sometimes those cliche numbers, 0, 1, 2, is so "many" like, it's 2,000,000 results or something, it's huge, it takes a lot of time to narrow it down, to "cheat" on such a variable, 

Now, 
you can just use (assuming the game uses bitwise in your specific case), bitwise ops,
now, the difference is just you scanning for another value, BUT Pretending it is another val.
For example,

Let's take a example of my own godot game(you can find demos of it on my yt)
I will later on use BitWise operations instead of assigning a value cuz it's faster,
so my game use bitwise operation `1 << 24` for saying "player has not used a key yet" 
```
so,
instead of you scanning for:
	"1" and then "0"
you scan for
	"16777216" and then "0"
```
## Now, what does this give us?
It gives us the results quicker! cuz quite more "few" results would have 16777216 as a "1",
Now, it might still be 1,000~ but, that's at least in the realm of "possibilites"

so, what I did was I thought,
since scanmem cant freeze values 
I could make a pipe. A drip. < analogy
in linux you can make a pipe, and a script that 'drips' "set 0" commands, each second, 
I will do that later on, as this text (that you read now) is wayy too long anyway

SO LET'S JUST DIVE IN NOW


> (Don't worry these notes will be avail. in either the description or in my github repo, Which I will link in the comments, so people can read, and take their time, and maybe even ask questions and/or improve it!)
> ^^
> 
