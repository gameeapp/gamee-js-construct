# Introduction

GAMEE is a social platform full of HTML5 games. Our goal is to make the games playable everywhere. You can play in the mobile apps (Android, iOS), bots (Telegram, Kik, Facebook Messenger) or directly on web.

[GAMEE JS](https://github.com/gameeapp/gamee-js) is our Javascript framework for connecting HTML5 game to GAMEE platform.

## Construct Plugins

We developped 2 plugins for C3 and C2 to allow Construct users to integrate our javascript framework without any need to learn any code more than that we have developed an Emulator that helps game designers to create and test games within the Gamee's Construct Plugins. The Emulator is not connected to any backend. It should work as replica of the web platform.

The Emulator Tool is only published on our website, you can use it from [here](https://emulator.gameeapp.com)

# Download

You can download the C3 and C2 plugins from here :

- [C2](./plugins/gamee.c2addon)
- [C3](./plugins/gamee.c3addon)

# Setup

## Add plugins to the editors

### C3

1. Menu -> View -> Addon Manager
2. Install new Addon
3. Select the gamee.c3addon and Click Open
4. Restart the Editor

### C2

1. Drag drop the gamee.c2addon to the Construct 2 Application
2. Click install
3. Restart the Editor

## Use Gamee Emulator

### C3

1. Menu -> Project -> Remote Preview
2. Copy/Paste the generate link to the Emulator
3. Click on **Upload Game**

### C2

1. **Press F5** or Click on **Run Layout**
2. Copy/Paste the opened url to the Emulator
3. Click on **Upload Game**

**!IMPORTANT, if you are going to use a non-secure url, for example in C2 the generated url looks like this http://localhost:50000, this must be loaded inside the non-secure (http) version of the emulator**

# Usage

## Properties

| Name         | Description                                                             |
| ------------ | ----------------------------------------------------------------------- |
| Coins        | Enable in-game-purchase using Gamee Coins                               |
| Ghost mode   | Enable the Ghost mode were you see other players movement when you play |
| Log events   | Enable events logging                                                   |
| Player data  | Enable loading a player data from Gamee's servers                       |
| Replay       | Enable the Replay mode for your games                                   |
| Rewarded ads | Enable ads in the game                                                  |
| Save state   | Enable getting and setting states                                       |
| Share        | Enable sharing your score without other players                         |
| Social data  | Enable getting other players data                                       |

## Conditions

### General

| Name           | Description                                                                         |
| -------------- | ----------------------------------------------------------------------------------- |
| On Initialized | Will be triggered when the Handshake is done                                        |
| On Start       | Will be triggered when the user will start game or restart it                       |
| On Stop        | Will be triggered when the user pauses the game                                     |
| On Resume      | Will be triggered when the user resumes the game after pause or GameeApp suspension |

### Ads

| Name                              | Description                                                     |
| --------------------------------- | --------------------------------------------------------------- |
| On Loaded Rewarded Video          | Will be triggered when a rewarded video is available and loaded |
| On Rewarded Video Watched         | Will be triggered when a player watched the rewarded video      |
| On Rewarded Video Skipped/Ignored | Will be triggered when a player skip or ignore the reward video |
| On No Rewarded Video available    | Will be triggered when a no rewarded video is available         |

### Audio

| Name      | Description                                                                                     |
| --------- | ----------------------------------------------------------------------------------------------- |
| On Mute   | Will be triggered when user clicks the mute button and the game must mute all game sounds       |
| On Unmute | Will be triggered when user clicks the unmute button and the game should unmute all game sounds |

### Erros

| Name     | Description                              |
| -------- | ---------------------------------------- |
| On Error | Will be triggered when an error occurred |

### Ghost

| Name          | Description                                |
| ------------- | ------------------------------------------ |
| Is Ghost Mode | Will be triggered if ghost mode is active  |
| On Ghost Show | Will be triggered when the ghost is shown  |
| On Ghost Hide | Will be triggered when the ghost is hidden |

### Player

| Name                     | Description                                             |
| ------------------------ | ------------------------------------------------------- |
| On Request Player Data   | Will be triggered when a player data is requested       |
| On Request Player Replay | Will be triggered when a player replay is requested     |
| On Request Save State    | Will be triggered when a player save state is requested |

### Purchase

| Name                   | Description                                       |
| ---------------------- | ------------------------------------------------- |
| On Purchased Item      | Will be triggered when an Item has been purchased |
| On Purchased Item Fail | Will be triggered when an Item purchase fail      |

### Replay

| Name           | Description                                |
| -------------- | ------------------------------------------ |
| Is Replay Mode | Will be triggered if Replay mode is active |

### Social

| Name                | Description                                     |
| ------------------- | ----------------------------------------------- |
| On Post Shared      | Will be triggered when a post is shared         |
| On Post Shared fail | Will be triggered when a post sharing fail      |
| On Request Social   | Will be triggered when a social request is made |

## Actions

### General

| Name                | Description                                                                                  |
| ------------------- | -------------------------------------------------------------------------------------------- |
| Game Initialization | Initial handshake action, game notifies Gamee platform about its existence                   |
| Game Ready          | Should be called when game is ready to start. It signals game is able to recevie start event |
| Game Over           | Notifies platform player ended the game                                                      |
| Game Save           | Save data from the game, Requires the property **Save State** to be Enabled                  |
| Update Score        | Updates the score making it visible for player                                               |

- Game Over

  - Optional
    - **Replay Data** Data to use on replay mode or ghost mode
    - **Save State** Data you want to store from the game

- Game Save

  - Mandatory
    - **Json to store** The json you want to store in gamee servers, it must be a string
  - Optional
    - **Share Score** When you save the Game State, you can set the Share Score option to True, It will trigger a screen asking player to share the progress with his actual score. The game must be paused during this process. The game continues when it receives a resume message

- Update Score
  - Mandatory
    - **Score** The Player score
  - Optional
    - **Ghost Sign** if this is set to true, it will update the Ghost Score, if the game is in Ghost mode

### Ads

You must Enable the property **Rewarded Ads**

| Name                | Description                       |
| ------------------- | --------------------------------- |
| Load Rewarded Video | Load rewarded ads inside the game |
| Show Rewarded Video | Show rewarded ads inside the game |

### Log

You must Enable the property **Log events**

| Name      | Description                                                                           |
| --------- | ------------------------------------------------------------------------------------- |
| Log Event | Events that the developer can store so he would be able to see statistics of the game |

- Log Event
  - Mandatory
    - **Event Name** The name of the event, shouldn´t be longer than 24 characters
    - **Event Value** The value of the event

### Player

| Name                      | Description                                                                                                  |
| ------------------------- | ------------------------------------------------------------------------------------------------------------ |
| Request Player Data       | Will get information about the current logged in player. Requires the property **Player Data** to be Enabled |
| Request Player Replay     | Will get information for Replay Mode. Requires the property **Replay** to be Enabled                         |
| Request Player Save State | Will get save state of specific user. Requires the property **Save State** to be Enabled                     |

- Request Player Replay
  - Mandatory
    - **User ID** The unique ID of the player you want to get the Replay Data

* Request Player Save State
  - Mandatory
    - **User ID** The unique ID of the player you want to get the Save State

### Purchase

| Name          | Description                                                                                     |
| ------------- | ----------------------------------------------------------------------------------------------- |
| Purchase Item | Purchase items inside the game using GAMEE Coins. Requires the property **Coins** to be Enabled |

- Purchase Item
  - Mandatory
    - **Coin Cost** The cost of the item
    - **Item Name** The name of the item
    - **Item Image** The Image of the item (base64Image)
  - Optional
    - **Developer Payload** Data to store about the purchase

### Social

| Name           | Description                                                                                        |
| -------------- | -------------------------------------------------------------------------------------------------- |
| Share          | Share a post on feed or battles. Requires the property **Share** to be Enabled                     |
| Request Social | Will get more social data about Gamee players. Requires the property **Social Data** to be Enabled |

- Share
  - Mandatory
    - **Text** The message of the post
    - **Destination** It will indicate where the post is going to be published, in Feed or Battle
    - **Picture** Image for the post. The image should be in format 4:3 (640x480px), 1:1 (640x640), or 3:4 (640x852). Maximum size is 150 kB. (base64Image)
  - Optional
    - **Score** The score of the Player
    - **Init Data** Data saved it to use it on the post for other players

## Expressions

| Name               | Description                                                                                                           |
| ------------------ | --------------------------------------------------------------------------------------------------------------------- |
| gameeSaveState     | Contains data you previously saved                                                                                    |
| gameeReplayData    | Contains data to use on replay mode or ghost mode                                                                     |
| gameeReplayVariant | Contains variante to use on replay mode or ghost mode                                                                 |
| gameeSocialData    | Contains friends and player data (score, avatar, highScore, etc...)                                                   |
| gameePlatform      | Contains the platform the player is using it could be **android**,**ios**,**web**,**mobile_web**                      |
| gameeLocale        | Contains the country and the language of the player for example **\"**en_US**\"**,**\"**es_MX**\"**,**\"**pt_BZ**\"** |
| gameeGameContext   | contains the context of the game it could **normal** or **battle**                                                    |
| gameePlayerData    | Json received if a player access the game through a post made with the **Share** action                               |
