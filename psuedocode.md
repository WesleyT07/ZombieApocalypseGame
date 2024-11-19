# START Game

DISPLAY "Title Screen"
DISPLAY "Start Button"
IF Start Button is CLICKED THEN
    SWITCH TO "Playing Screen"
    DISPLAY Score, Instructions, and Menu Button
END IF

# In-game logic

WHILE Game is Running DO
    SPAWN Enemies on Screen

    ALLOW Player to MOVE using Keyboard
    ALLOW Player to SHOOT using Mouse

    FOR EACH Enemy DESTROYED DO
        INCREASE Player's Score
        CHECK IF Level Completed
    END FOR

    RANDOMLY DROP Power-Ups from Top of Screen
    IF Player SHOOTS Power-Up WITHIN 5 Seconds THEN
        ACTIVATE Power-Up Effect
    ELSE IF Power-Up REACHES Bottom of Screen THEN
        REMOVE Power-Up
    END IF

    IF Level Completed THEN
        MOVE TO Next Level
        INCREASE Difficulty
    END IF

    IF Player DIES THEN
        RESTART Level
    END IF
END WHILE

# Character selection menu

DISPLAY "Character Selection Button" on Startup Menu
IF Character Selection Button is CLICKED THEN
    DISPLAY Character Options
    ALLOW Player to SELECT Character
    CHECK IF Character is UNLOCKED
    IF UNLOCKED THEN
        ASSIGN Character to Player
    ELSE
        DISPLAY "Character Locked"
    END IF
END IF

# Pause game

DISPLAY "Menu Button" at Top Left Corner
IF Menu Button is CLICKED THEN
    PAUSE Game
    DISPLAY Settings Menu
    IF "Adjust Volume/Music/SFX" is SELECTED THEN
        ALLOW Adjustments
    END IF
    IF "Return to Main Menu" is SELECTED THEN
        SWITCH TO "Main Menu"
    END IF
END IF

END Game
