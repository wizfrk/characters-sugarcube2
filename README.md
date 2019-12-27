## Characters using Sugarcube 2
This is a option for handling chracter data when using Sugarcube2 in Twine.

Source code:

    */ Initialize your characters with there default values in Story Init /*
    ::StoryInit
    <<set $characters = {
        "Alice" : {
            name: 'Alice',
            hp: 100
        },
        "John" : {
            name: 'John',
            hp: 100
        }
    }>>
    
    */ You can then use the object as a range for all sorts of interesting stuff /*
    ::Village
    Character Status:
    <<for _character range $characters>>
        <<print "_character.name has _character.hp">>
    <</for>>
    //If you want to use a variable for one character at a time, don't forget that it creates a copy of the Object
    Who is the active character:
    <<listbox "$activeChar" autoselect>>
        <<optionsfrom $characters>>
    <</listbox>>
    [[Forest]]
    
    ::Forest
    $activeChar.name is with you.
    Goldins Attack! $activeChar.name takes 10 damage! <<set $activeChar.hp -= 10>>
    $activeChar.name now has $activeChar.hp!
    // So you have to save your changes back to the main object!
    Saving... <<set $characters[$activeChar.name] to $activeChar>>
    [[Village]]
