# Global Bulletin Board, version 4.0.6
created by Myrddin@Witchcraft/Dreaming/Elysium (http://www.firstmagic.com/~merlin/)

Anyone may use this code. I only ask that those that do send me a quick email 'registering' their copy with me and that the CREDITS attribute be kept on the board, unchanged.

Any questions/problems/suggestions regarding this code should be emailed to me. You may also contact me at Witchcraft if necessary.

## CHANGES
### 4.0.6:

 * BugFix: Patched a security hole (thanks to Alierak for pointing it out)
 * PennFix: Minor tweak to +bbremove that will keep Penn's cleaner and prevent odd behavior
 * Feature: Message headers internal to the bbs now store dbref of the owner of the poster. 

### 4.0.5:

 * Improved +bbscan (Amberyl)
 * Improved number range error handling (Kareila@ChaoticMUX)
 * BugFix: +bbmove - better error handling, and replaced missing '}'
 * BugFix: FN_SETR behaves better for those that need it. 

### 4.0.4:

 * BugFix: +bbsearch now checks permissions properly
 * BugFix: base 36 to base 10 conversion tweaked to be friendlier to Penn (added a base case of '0' to fold()).
 * BugFix: Posting to an anonymous board no longer appends your BB_SIG.
 * BugFix: BBS is now aware of the 8k MUX buffer limit. This affects the 'percentage' full meter.
 * PennFix: +bbmove tweaked to be friendlier to PennMUSH.
 * PennFix: Various other PennMUSH fixes, most involving flags. Should help the BBS run correctly on PennMUSH's.
 * Feature: Post notification now includes [board]/[#]
 * Help: Help files have been expanded in the areas of message timeouts and locking groups. 

### 4.0.3:

 * BugFix: +bbcleargroup now checks permissions properly
 * BugFix: +bbcleargroup will no longer re-order remaining groups
 * BugFix: Automatic post notification for anonymous boards now uses the anonymous 'title' instead of the poster's name. 

### 4.0.2:

 * BugFix: +bbsearch will now work properly on all servers
 * Some attribute cleanup 

### 4.0.1:

 * BugFix: Message ID's no longer improperly sorted by certain commands
 * BugFix: Update-Installer should no longer scramble message ID's 

### 4.0.0:

 * Misc. security enhancements. (including the MUX set() hole)
 * Up to 25% increase in storage capacity.
 * Support for message timeouts. Fully configurable.
 * Support for anonymous boards. Configurable 'From' field title. Obviously, MUSH staff can determine original poster.
 * Post notification: online players are notified of new posts.
 * New Command: +bbsearch. Allows user to search a group for posts by a specific author.
 * New Command: +bbnotify. Allows user to toggle post notification for boards.
 * New Staff Command: +bbconfig. For setting global/group timeout values, anonymous boards, built-in timeout monitor. 

## FEATURES:

 * Multi-subject/group bulletin board system, coded specifically to be used globally.
 * Lockable groups. Locks can be as simple or as complex as needed. Groups can have seperate locks for reading and writing, allowing you to set up groups that are read-only for the general populace of the MUSH (good for IC newspapers, staff-to-player announcements, etc). Also included is a wizard command that will automatically lock groups based on flags (wizard, admin, staff, etc) or attributes (race:were, race:mortal, etc)
 * Unread status. Board keeps track of which messages a player has read. Unread messages will be marked as such. The +bbread command allows for a player to automatically read all unread messages in any group. Likewise, a +bbcatchup command allows users to mark all messages in a group as read.
 * +bbscan command. This command will give you a brief list of how many unread messages are in each group. This command was designed to be placed in a player's @aconnect attribute. Combined with the ability to read all unread messages in a group, this allows for players to quickly and easily stay current with the bulletin board.
 * Split posting. Users can either post a message with a single command, or 'split' the posting as they're writing it (similar to the way you would compose mail using the Brandy Mailer).
 * Leave/Join groups. Players can remove themselves from groups, making the list of groups they see shorter, and allowing them to omit groups they have no interest in. Obviously, they can rejoin whenever they wish. 

## Instructions for Installation:
**INTRODUCING THE NEW SUPER-EASY INSTALLER!**
Now, you don't even need to pre-create objects then edit the code file with the correct dbref's (if that didn't make sense, don't worry :) ).

To install the BB, this is all you need to do:

 * Quote the code file to the MUSH via your preferred method. The /quote option under tinyfugue works wonderfully.
 * If you are quoting this file to the MUSH with anyone other than #1 (god), there are a couple of extra steps you need to take after quoting this file:
 * @attribute/access bb_read=hidden wizard
 * @attribute/access bb_omit=hidden wizard
 * @attribute/access bb_silent=hidden wizard
 * Place the Global BB in the Master Room of the MUSH. The bbpocket will have already been placed inside the BB object for convenience. Don't worry, objects inside objects in the Master Room are not searched for global commands -- having the bbpocket inside the BB won't add to your lag one bit. :-) 

And that's it! The installer will create the objects for you, set the code, and do the rest of the work. It even detects differences between MUSH and MUX and makes the necessary changes (so far this only involves a difference of a couple flags and the lnum() function)

Miscellaneous Notes:

 * The +bblock command only allows for simple locks. For more complex/custom locks, all you need to do is modify the CANREAD and/or CANWRITE attributes on the groups in question. :-)
 * The 3.0 and above versions were written to be used on TinyMUSH 2.2 (or later) or TinyMUX. If you have an older version of TinyMUSH, the changes are minimal (namely, replacing hasattr() wtih some equivalent soft code - there might be some other minor changes)
 * Don't use the bb as god (#1). The reason for this is that the bb stores an attribute on each character that contains the message-id's of the messages you've read. TinyMUSH doesn't allow anything to modify or set attributes on god (#1), therefore, the bb won't be able to keep track of messages you've read, or groups you've omitted yourself from. Besides, it's a bad habit to use god (#1) for day-to-day administrative stuff anyhoo. ;-) 

*(Note from Mike: I reformatted this README from HTML to Markdown for inclusion in the repository, but no changes were made to the content, just the formatting.)*
