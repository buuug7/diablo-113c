Udie Too

Ultimate Diablo Item Editor 2
    Version 1.10.011b release 2004/10/31

New Stuff ...

General
Character animation in town! Shows what you will look like as you change items.
Skill key page added. You can set any skill to key and/or Left/Right click.
Text file viewer. Lets you view skill.txt, itemstatcost.txt, monstat.txt and states.txt in the mpq.

Item pages
Quick fill/remove gems.
Copy/paste items.
Drop on ground / off page deletes item. Be Careful ;-)

Item Editor
Added ...
  normal selection keys. Shift lets you select bits using any movement keys.
  Ctrl + keys to move to next/prev field & next/prev list.
  C - copies selection
  P - paste (insert) selection
  Rare Prefix/suffix support

Fixed ...
  drop Runeword for jewels. Makes usable 'iths' now.
  More Skill stats fixed. (aura,state, non_classSkill)
  mouse selection improved.

Other fixes

Nox support fixed in item store.
Ladder characters recognized. Added toggle to change them to normal.


Still broken ...
   Some set items and uniques are not created correctly.
   Some item stats may need fixing. Too many stats, too little time ;-)
   Too much memory used with lots of savefiles on load screen.
   Modified/added itemstatcost entries are not used.

You can download the latest version from http://home.stx.rr.com/svr


**NOTE TO MOD USERS**
    To use Udie with a mod you must make a shortcut to udietoo.exe and set the 
    "working path" / "Start In:" to the Diablo II directory or your mod folder.
    AND you need to put C:\UdieToo\UdieToo.exe -direct as the command line.
    This works for TXT type mods. DLL mods probably won't work right.


Features...

    UdieToo allows you to load your characters and change whatever you want. It
    works just like the game except you can edit the values you see and change
    the items anyway you want (within the bounds of the game). The editor uses
    the actual files Diablo II uses so if the game changes so does the editor.

Mod Maker Friendly ...

    For you mod makers out there, I added the "-direct" command line switch.
    Just like the game, it tells the editor to use files extracted to a local 
    directory structure in the working directory. This is an excellent way to
    test mods with new items,sets,uniques etc.

Using the item editor ...

    After loading a character you can edit any item by right clicking it and 
    picking 'edit' from the popup menu. The item editor opens with your item
    showing.

    Binary Editor:
	There is a binary editor control to edit the actual data of the
    item. The bits show in reverse order from normal notation to allow 
    continuous flow from field to field. It takes a little getting used to,
    but it's worth it when deciphering unknown data. Each field is an alternate
    color and each section (basic,item specific,property lists) has a different
    set of colors.

    Status Display:
	As you move the cursor along the status display below shows current 
    position etc. The field name/description is shown above along with the
    value of the field. Left-clicking the value will popup a dialog box that 
    allows you to change it in human readable form ;-).

    Keys:
	Arrows	- move cursor around.
	Space	- toggle bit under cursor
	0/1	- set bit to 0/1
	INS	- switch between insert and over-write

	Shift	- Select (hilight) bits for copying/pasting
	Drag mouse - same

	C	- copies selection
	P	- pastes (inserts) previously copied bits into current location

	Ctrl+Left - previous field
	Ctrl+right - next field
	Ctrl+up - previous list
        Ctrl+dn - next list

	* Delete only works in insert mode. Be very careful inserting and
	deleting bits. You can trash an item if you dont know what you are
	doing.

    Property List Boxes:
	There are several property lists that let you modify the item easily.
	You select the list you want using the button menu up right. Scroll
	through the list using the mouse (no kb control, sorry). Left click
	a property to 'grab' it. The cursor changes to show you have it. Left
	click your item to 'Apply' the property to it. What happens depends on
	the type of property.
	
	'Properties': 
	    This will insert the selection into the first property section of
	    your item. All items except for Simple items (potions etc.) will 
	    have this property section, although it may be empty. The parameters
	    are all set max (1111 ...).

	'Rune Words':
	    Will wipe the item down to a 'normal' except for the first property
	    section. Then it will socket the item,insert the appropriate runes,
	    and apply the correct attributes for the selected runeword. BUT ...
	    If the item is not the correct type, Diablo will reset the runeword
	    to 0xFFFF "ITH". But the properties will remain.

	'Magic Prefix/Suffix':
	    Wipes the item if it isn't Magic. Makes it magic, then add the 
	    correct attributes for the selection.

	'Rare Prefix/Sufix'
	    Will make item rare if not already. Set the name selected. No
	    attributes are added.

	'Unique'
	    Drag a unique title onto your item.
	    Will make the item a Unique item and add the properties.


Examples ...
    
    To make a socketed item: Move cursor until "Socketed" appears. The value
    should say 'False'. Make sure Insert Mode is off (cursor is wide).Press
    space bar to set bit to '1'. Display says 'True'. Move the cursor down to
    find "number of sockets". Be sure insert mode is on (the cursor is thin).
    Type '0100' (this will set 2 sockets, remember bits are in reverse).
    Press INS to turn insert mode back off.
  

    To remove sockets, reverse the process...
        Find 'Number of sockets'. With INS on, delete 4 bits. Find 'Socketed'.
    With INS off, Press SPACE to set bit to '0'.

    Whenever you turn on a flag, you MUST insert bits to align the fields again
    Whenever you turn off a flag you MUST delete  "" "" "" ..

    To change an existing value. Just overwrite it.(With INS off)

    !!! CAUTION !!!
    If you Unsocket an item you must remove the gems first !


Other things ...

    Dead Body:
	You can view your dead body (Even if you dont have one ;-). If you
	put an item on it , your dead body will appear the next time you
	start Diablo.

    Spell Tree:
	Clicking an spell icon will increase it's level. Shift-clicking will
	decrease it.

    Quest Page:
	Each tab has a set of numbers. Each number is the state of a quest on
	the page. Selecting an icon will turn the corresponding number green.
	The gray numbers are the Act start/end status. Act V is messed up
	because Blizzard had used those numbers for other data, So they had to
	move Act V down a few bytes reletive to the others. I haven't adjusted
	the tab yet. Keys work the same as the Item editor but there is no
	insert mode.

    Palette Page:
	This doesnt do anything. I used it when deciphering item coloring. I
	thought modders might like it so I left it.

    Player Page:
	Lets you set the Difficulty/Act and Title of your character. The Title
	is set by selecting the highest difficulty completed. When you select
	a different Act, the map switches the that town. It loads really slow.
	I should put the 'Loading...' screen up but it's embeded in the 
	character loading code. I'll add that sometime.

File Formats ...

    'Variable Structure Definition':
    I wanted to come up with a way to adjust the structure for items as
    needed (without rewriting any code). So I created this format to 
    describe item data. I should use the extension '.vsd' but its a tabbed
    text file so I used .txt for easy editing.
    Here are the columns ...

    'type' : resulting type for the field.
	    BYTE - 8 bit unsigned value. Displays as decimal(hex)
	    WORD - 16 bit value. Displays as Hex
	    DWRD - 32 bit value. Displays as Hex
	    BOOL - 16 bit value. Displays as "True/False"
	    ASC7 - 7 bit per character null terminated string. The bits field 
		    is max number of characters. Displays as text.
	    ASC8 - 8 bit per character null terminated string. The bits field
		    is max number of characters. Displays as text.
	    FILE - Used to load other definition files. The 'name' column is
		    the filename to load in. Bits should be 0.
	    PROP - A built in type used for property lists. The data is decoded
		    using the 'properties.txt' file.
	    LOOK - Look up field in a list ... not implemented

        'name' : name of field to use in conditions.

        'bits' : actual size of field data in bits (unless noted above). Must
    	    be smaller than the selected type.

        'desc' : description. Shows in editor.

        'cond1': condition result to include this field. If the comparison of
	    'condvar1' with 'condval1' results in this number, include this
	        field. Can be  -1 , 0, 1 . In other words (less than),(equal to),
    	    (greater than).

        'condvar1' : the field name to use in compare.

        'condval1' : a value to compared it to.

        'condX ...' : more conditions

Files ...

    'fields.txt' : VSD file describing basic item format
    'extend.txt' : VSD file describing extended item format. Included by 
        fields.txt if 'bSimple' == 0.

    'controls.txt' : A quicky I used to tell where to put stuff on pages.
	    Could be better.

    'properties.txt' : A great list of properties. Many thanks to 'Fuzzier' ,
	    the creator of 'Item Creator'. I added modcodeX columns to tell which
        parameters to use with modcodes. Also fixed a few properties.

    'fake.txt' : a list of 'Fake' properties Diablo uses. Used to expand out
	    the correct properties for the item.

    'quests.txt' : Quest list with offsets for the binary editor and string.tbl
	    keys to lookup the right text.
    
    'filenames.txt': List of all MPQ files used by the editor. If Blizzard
	    changes something, this needs to be changed.

NOTE ...
    Only the item editor uses the VSD files at the moment. The rest of the
    code uses a fixed format so Diablo II vers 1.10 probably wont work. I'm
    working on converting everything over. Maybe by the beta release.




Thanks To ...

    trevin, Fuzzier, TeLAMoN,shadowmaster, Stoned2000, ericjwin, Paul Siramy,
    Tom Amigo, AK74 and many more.

    Thanks to all out there who have worked on character/item formats, dt1/ds1
    files, MPQ viewers etc. I found most of the tech I needed from you guys so
    I spent most of my time coding. (Most of it ... I did find a few pearls on
    my own ;-)

    Special Thanks to Jamella for making an almost great editor and leaving us
    hangin. Every time I trashed a character I got one step closer to starting
    this ;-) (sorry Jamella, couldn't resist ;-)

    svr@intcomm.net


DISCLAIMER ====================================================================

    The author is not responsible for anything. Use at your own risk.


END DISCLAIMER ================================================================


