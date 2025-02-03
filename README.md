Sylvo -Wolf’s answer to "Sylvan" combat in Achaea

** note: needs AK aff tracker by Austere and Svof (temporarily until I’m able to improve some gmcp stuff)


Install the latest release through the Package Manager:


Sylvo is a sylvan offense system to handle your affliction selection.

While I’ve enjoyed learning to code several times over the many years, this is an "old man’s" attempt to give back to the community. I would like to deeply thank Hikagejuunin and his band of misfits for all their hard work. For if it were not for finding the Loki system, I do not feel my attempts would be as progressed as they are. This slimmed down, basic sylvan offensive system, hopefully gives those that are typically more non-combatant but wish to try, as another functional framework to expand upon. It was my intention to build it in a way that could hopefully be "easily" converted to other classes.

I'd also like to thank the third party code I made use of for this release, primarily Hikas Loki serpent system, Svof and Austere's AK tracker

**Sylvo scripts and some of the sylvo aliases have extra commentation and/or tips

GETTING STARTED:

First off make sure you add, ak should have one in the alias section, if you use this one, may not need: 

ak.feedback = false
ak.scoreup(target)

to your target alias, - -  for some reason I kept running into issue where ak wouldn’t see that I lost feedback on target, and this is my temporary fix.

** add vinefn() to "missed hit" trigger in Ak - - will vinewreath 

**recommended to add/create this to a script with the, sysLoadEvent (like Lokisettings if you have that), otherwise you’ll end up receiving double limb echo’s

-- to disable svo limb
function Limboff()
  disableTrigger("svo (limbcounter)")
  disableScript("svo (limbcounter)")
end
-- now disable svo limb:
Limboff()

** code in limbfn() in thorn is new and not fully tested

** You will also want to add a custom prompt if ya got svof, otherwise see how Austere's AK handles that for other curing systems:

**Both of the automatic scripts are intended to deliver any needed affliction, by using the proper “skill”, if the intended skill, can not deliver 

from AK tracker's Osettings!:
----------------------------------------------------------------------------------------------------------------------

--*

--Svo Prompt--

--add ^y@ml_oprompt to your custom prompt

--*


--WYS Prompt--

--type wshow display

--add @owysprompt into your prompt

-----------------------------------------------------------------------------------------------------------------------

EXAMPLE CUSTOM PROMPTS:

--Hika original
vconfig customprompt ^1@health^pinkhp^r@(diffhealth)^gray(^2@%health^g%^gray)^c|^2@mana^bmp^2^gray^b@diffmana^gray(^2@%mana^g%^gray)^c|^gray(@%endurance%^g^yellowen^gray)^c|^gray(@%willpower%^g^magentawp^gray)^c|^2^gold^DarkOrange@eqbal@affs^W-^c| ^r@target @promptstring @gametargethp ^y@ml_oprompt

--Hika new
vconfig customprompt ^SlateGrayH:^1@health^r@(diffhealth)^SlateGray(^azure@%health%^SlateGray) ^SlateGrayM:^2@mana^b@(diffmana)^SlateGray(^azure@%mana%^SlateGray) ^DarkSlateGray(^G@%endurance^SlateGrayE ^G@%willpower^SlateGrayW^DarkSlateGray) ^2^gold^DarkOrange@eqbal @affs^W -^SlateGray ^red@target ^SlateGray(^w@gametargethp^SlateGray) ^y@ml_oprompt

--Hika new with \n
vconfig customprompt \n^SlateGrayH:^1@health^r@(diffhealth)^SlateGray(^azure@%health%^SlateGray) ^SlateGrayM:^2@mana^b@(diffmana)^SlateGray(^azure@%mana%^SlateGray) ^DarkSlateGray(^G@%endurance^SlateGrayE ^G@%willpower^SlateGrayW^DarkSlateGray) ^2^gold^DarkOrange@eqbal @affs^W -^SlateGray ^red@target ^SlateGray(^w@gametargethp^SlateGray) ^y@ml_oprompt


CORE COMMANDS:

** Currently is no error checking or little backups  in manual modes, so be careful of the way and which, afflictions you apply.

thr<xx> <xx> - thornrend alias             
  example: thr<dd> <rl> = thornrend kola/delphinium right leg

** 'thr<rl>' will automatically select afflictions while attacking limb of choice, in this case it being right leg

** 'thr' with no afflictions specified will automatically select afflictions from thornstack

** Currently is no error checking or backups  in manual modes, so be careful of the way and which, afflictions you apply.

manual thorn aflliction selections:

Propagations:

k = "kelp",
v = "valerian",
b = "bellwort",
e = "elm",
d = "kola",
h = "hawthorn",
l = "Lobelia",
g = "Goldenseal",
p = "bloodroot", 
a = "skullcap",
s = "sileris ",

Venoms:

a = "aconite",
b = "oculus",
c = "curare",
d = "delphinium",
e = "eurypteria",
f = "epteth",
g = "gecko",
i = "digitalis",
k = "kalmia",
l = "larkspur",
m = "monkshood",
n = "selarnia",
o = "voyria",
p = "prefarar",
q = "epseth",
r = "darkshade",
s = "slike",
u = "euphorbia",
v = "vernalius",
x = "xentio",
z = "vardrax",

wt<xx> - weatherweaving alias
** wt with no venoms specified will automatically select venoms from stacking
  

manual weave afflictions:

**feel free to change these in the alias
a = "Static", --paralysis 
b = "Thunderclap",--cure deaf/sensitivity
c = "Flash",--cure blind/transfix (req 18 arcane power) 
d = "Cyclone",--dizzy/impatience 
e = "Hailstone",--clumsy/epilepsy/impatience
f = "Waterspout",--confusion/dizzy/vertigo/better dam with flooded room
g = "Razorwind",--health leech 
k = "Windwhip",--causes damage —3.90
l = "Bolt",--dam/<75 health cause blackout (req 16 arcane power) –2.80
m = "Shear",--removes shields


other aliases:
  

tr = target reset

el <direction> = evoke lightning (to hit target in adjacent rooms direction)

pc = to set when in a party **to start overcharging afflictions in weaving faster

af = toggles autoshear (shield handeling)

cb = calls bees if you’ve already summoned, otherwise calls new swarm ** relies on Svof, haven’t been able to test fully yet

atr = toggles when to try and transfix

TO USE:

Set your target **ak has a deactivated one, if you dont have your own.

cb  **currently use svof’s "swarm defense"
thr or wt **2 main attacks, the choice is yours

Any and all suggestions are welcome and appreciated. 
