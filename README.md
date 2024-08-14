# **arma3mercenaries Jukebox Script**



                     __..-----')
         ,.--._ .-'_..--...-'
        '-"'. _/_ /  ..--''""'-.
        _.--""...:._:(_ ..:"::. \
     .-' ..::--""_(##)#)"':. \ \)    
    /_:-:'/  :__(##)##)    ): )   
    "  / |  :' :/""\///)  /:.'  
      / :( :( :(   (#//)  "       
     / :/|\ :\_:\   \#//\   
     |:/ | ""--':\   (#//)              
     \/  \ :|  \ :\  (#//)
          \:\   '.':. \#//\      
           ':|    "--'(#///)
                      (#///)
                      (#///)
                       \#///\
                       (##///)
                       (BV///)
                       (+#///)
                       (JL///)
                        \=#///\
                        (ANV///)
                        (IRV///)
                        (MWV////)__...-----....__
                        (#/::'''                 ""--.._
                   __..-'''                             "-._
           __..--""           By BrianV1981            	   "-..____
  ___..--""                                                    "-..____
    (_ ""---....___                                     __...--"" _)
      """--...  ___"""""-----......._______......----"""     --"""
                    """"       ---.....   ___....----
## Multiplayer and Dedicated Server Jukebox Script
<details>
  <summary>Overview</summary>


  The Arma3Mercenaries Jukebox Script is a simple, lightweight, and easy-to-incorporate system designed to bring customizable music playback to your Arma 3 missions. It allows players to interact with a custom radio interface, pick songs, or listen to randomly selected tracks from a playlist.

  **Fully multiplayer and dedicated server compatible**: This script works seamlessly in both multiplayer environments and on dedicated servers, ensuring all players experience synchronized music playback.

</details>

<details>
  <summary>Features</summary>

  - **Custom Radio Interface**: Players can select specific tracks to play using a straightforward and accessible interface.
  - **Mute Functionality**: The mute button plays a silent track as a workaround due to the use of event handlers that play a random track if a song ends.
  - **Event-Driven Music Playback**: Automatically plays a new random track when the current one ends, providing continuous music during gameplay.
  - **Optional Random Looping**: The script includes an optional feature for looping random tracks, which can be enabled or disabled based on player preference.
  - **Multiplayer Compatibility**: The script is fully compatible with multiplayer and dedicated servers, ensuring synchronized music for all players.

</details>

<details>
  <summary>Script Descriptions</summary>

  #### 1. `arma3mercenaries_jukebox_customInterface.hpp`

  **Description:**
  This file defines the custom interface for the jukebox. It includes buttons for different tracks, a mute button, and a title display.

  #### 2. `arma3mercenaries_jukeboxGUIDefinitions.hpp`

  **Description:**
  Provides the necessary GUI elements such as `RscText`, `RscButton`, and `RscSlider`. These elements are used in constructing the jukebox interface.

  #### 3. `arma3mercenaries_playRandomTracks.sqf`

  **Description:**
  Handles the logic for playing random tracks from the playlist. It includes the functionality to automatically select and play a new track when the current one ends.

</details>

<details>
  <summary>How to Use</summary>

  1. **Add Jukebox to Objects:**
     - To add the jukebox to any object in the game, use the following code in the object's init field:
       ```cpp
       // Add arma3mercenaries Radio action
       _this addAction ["arma3mercenaries Radio", {
           createDialog "CustomInterface";
       }, "", 0, false, false, "", "player distance _target < 5"];
       ```

  2. **Include in `description.ext`:**
     - Add the following to your `description.ext` file:
       ```cpp
       #include "arma3mercenaries/jukebox/arma3mercenaries_jukebox_customInterface.hpp"
       class CfgMusic {
           #include "arma3mercenaries/jukebox/arma3mercenaries_jukeboxMusic.hpp"
       };
       ```

  3. **Initialize in `init.sqf`:**
     - Include the following in your `init.sqf` file to start the jukebox:
       ```sqf
       execVM "arma3mercenaries/jukebox/arma3mercenaries_playRandomTracks.sqf";
       ```

  4. **Optional Looping:**
     - The script **arma3mercenaries_playRandomTracks.sqf** that loops the music is optional. Removing this step will allow players to just use the radio interface to pick the songs they want to listen to.

     - skip this step of include the following in your `init.sqf` file if you want an even lighter weight version.
       ```sqf
       execVM "arma3mercenaries/jukebox/arma3mercenaries_playRandomTracks.sqf";
       ```

</details>

<details>
  <summary>Important Notes</summary>

  - **Mute Button**: The mute button currently plays a silent track as a workaround until event handlers can be managed more effectively.
  - **Event Handler**: The event handler plays a random track when it detects that a song has ended. This ensures continuous music playback.
  - **Modularity**: The script is designed to be simple, lightweight, and easy to incorporate into any mission.
  - **Multiplayer Compatibility**: Fully compatible with multiplayer and dedicated servers, ensuring all players experience synchronized music playback.

</details>

<details>
  <summary>Future Plans</summary>

  - **3D Sound Integration**: Incorporate songs with 3D sound to enhance the immersive experience.
  - **Interface Improvement**: Enhance the visual and functional aspects of the jukebox interface.
  - **Better Documentation**: Develop more detailed and user-friendly documentation to help mission creators integrate the jukebox.

</details>
