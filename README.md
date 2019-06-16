# Introduction

GAMEE is a social platform full of HTML5 games. Our main goal is to make the games playable everywhere. You can play on mobile apps (Android, iOS), bots (Telegram, Kik, Facebook Messenger) or directly on the web.

[GAMEE JS](https://github.com/gameeapp/gamee-js) is our Javascript framework for connecting HTML5 game to GAMEE platform.

## Construct Plugins

We developed 2 plugins for C3 and C2 to allow Construct users to integrate our javascript framework without any need to learn any code. More than that, we developed an Emulator that helps game designers create and test games within the Gamee's Construct Plugins. The Emulator is not connected to any backend. It should work as a replica of the web platform.

The Emulator Tool is only published in our website, you can use it from [here](https://emulator.gameeapp.com)

# Table of contents

- [Change Log](#change-log)
  - [2.3](#2.3)
- [Download](#download)
- [Setup](#setup)
  - [Add plugins to the editors](#add-plugins-to-the-editors)
    - [C2](#c2)
    - [C3](#c3)
  - [Use Gamee Emulator](#use-gamee-emulator)
    - [C2](#c2-1)
    - [C3](#c3-2)
- [Usage](#usage)
- [Properties](#properties)
- [Conditions](#conditions)
  - [General](#general)
  - [Ads](#ads)
  - [Audio](#audio)
  - [Erros](#erros)
  - [Ghost](#ghost)
  - [Player](#player)
  - [Purchase](#purchase)
  - [Replay](#replay)
  - [Social](#social)
- [Actions](#actions)
  - [General](#general-1)
    - Game Over
    - Game Save
    - Update Score
  - [Ads](#ads-1)
  - [Log](#log)
    - Log Event
  - [Player](#player-1)
    - Request Player Replay
    - Request Player Save State
  - [Purchase](#purchase-1)
    - Purchase Item
  - [Social](#social-1)
    - Share
    - Request Battle Data **(2.3)**

# Change Log

## 2.3

- Added Action "Request Battle Data"
- Added Condition "On Request Battle Data"
- Added Expression "gameeCountry"
- Added Expression "gameePlayerMembershipType"
- Added Expression "gameeGameContextId"
- Added Expression "gameeBattleData"

# Download

You can download the C3 and C2 plugins from here :

- [C2](./plugins/gamee.c2addon)
- [C3](./plugins/gamee.c3addon)

# Setup

## Add plugins to the editors

### C2

1. Drag drop the gamee.c2addon to the Construct 2 Application
2. Click install
3. Restart the Editor

### C3

1. Menu -> View -> Addon Manager
2. Install new Addon
3. Select the gamee.c3addon and Click Open
4. Restart the Editor

## Use Gamee Emulator

### C2

1. **Press F5** or Click on **Run Layout**
2. Copy/Paste the opened url to the Emulator
3. Click on **Upload Game**

### C3

1. Menu -> Project -> Remote Preview
2. Copy/Paste the generate link to the Emulator
3. Click on **Upload Game**

**!IMPORTANT : if you are going to use a non-secure url you must load the game in the non-secure url of the emulator as well**

# Usage

## Properties

| Name         | Description                                                                |
| ------------ | -------------------------------------------------------------------------- |
| Coins        | Enable in-game-purchase using Gamee Coins                                  |
| Ghost mode   | Enable the Ghost mode where you see other players' movements when you play |
| Log events   | Enable events logging                                                      |
| Player data  | Enable loading a player data from Gamees' servers                          |
| Replay       | Enable the Replay mode for your games                                      |
| Rewarded ads | Enable ads in the game                                                     |
| Save state   | Enable getting and setting states                                          |
| Share        | Enable sharing your score with other players                               |
| Social data  | Enable getting other players data                                          |

## Conditions

### General

| Name           | Description                                                                         |
| -------------- | ----------------------------------------------------------------------------------- |
| On Initialized | Will be triggered when the Handshake is done                                        |
| On Start       | Will be triggered when the user starts or restarts a game                           |
| On Stop        | Will be triggered when the user pauses the game                                     |
| On Resume      | Will be triggered when the user resumes the game after pause or GameeApp suspension |

### Ads

| Name                              | Description                                                          |
| --------------------------------- | -------------------------------------------------------------------- |
| On Loaded Rewarded Video          | Will be triggered when a rewarded video is available and loaded      |
| On Rewarded Video Watched         | Will be triggered when a player finishes watching the rewarded video |
| On Rewarded Video Skipped/Ignored | Will be triggered when a player skip or ignore the rewarded video    |
| On No Rewarded Video available    | Will be triggered when no rewarded videos are available              |

### Audio

| Name      | Description                                                                                     |
| --------- | ----------------------------------------------------------------------------------------------- |
| On Mute   | Will be triggered when user clicks the mute button and the game must mute all game sounds       |
| On Unmute | Will be triggered when user clicks the unmute button and the game should unmute all game sounds |

### Erros

| Name     | Description                            |
| -------- | -------------------------------------- |
| On Error | Will be triggered when an error occurs |

### Ghost

| Name          | Description                                     |
| ------------- | ----------------------------------------------- |
| Is Ghost Mode | Will be triggered when the ghost mode is active |
| On Ghost Show | Will be triggered when the ghost is shown       |
| On Ghost Hide | Will be triggered when the ghost is hidden      |

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
| On Purchased Item Fail | Will be triggered when an Item purchase fails     |

### Replay

| Name           | Description                                  |
| -------------- | -------------------------------------------- |
| Is Replay Mode | Will be triggered when Replay mode is active |

### Social

| Name                             | Description                                          |
| -------------------------------- | ---------------------------------------------------- |
| On Post Shared                   | Will be triggered when a post is shared              |
| On Post Shared fail              | Will be triggered when a post sharing fails          |
| On Request Social                | Will be triggered when a social request is made      |
| On Request Battle Data **(2.3)** | Will be triggered when a battle data request is made |

## Actions

### General

| Name                | Description                                                                                                                 |
| ------------------- | --------------------------------------------------------------------------------------------------------------------------- |
| Game Initialization | Initial handshake action, game notifies Gamee platform about its existence                                                  |
| Game Ready          | Should be called when the game is ready to start. It signals the Gamee plateform that it is able to recevie the start event |
| Game Over           | Notifies the platform that the player ended the game                                                                        |
| Game Save           | Saves data from the game. Requires the property **Save State** to be Enabled                                                |
| Update Score        | Updates the score making it visible to the player                                                                           |

- Game Over

  - Optional
    - **Replay Data** Data to use on replay mode or ghost mode
    - **Save State** Data you want to store from the game

- Game Save

  - Mandatory
    - **Json to store** The json you want to store in Gamee servers, it must be a string.
  - Optional
    - **Share Score** When you save the Game State, you can set the Share Score option to True. It will trigger a screen asking the player to share the progress with his actual score. The game must be paused during this process. The game continues when it receives a resume message

- Update Score
  - Mandatory
    - **Score** The Player score
  - Optional
    - **Ghost Sign** if it is set to true, it will update the Ghost Score, if the game is in Ghost mode

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
    - **User ID** The unique ID of the player that you want to get their Replay Data

- Request Player Save State
  - Mandatory
    - **User ID** The unique ID of the player that you want to get their Save State

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
    - **Developer Payload** Purchase data to be stored

### Social

| Name                          | Description                                                                                                |
| ----------------------------- | ---------------------------------------------------------------------------------------------------------- |
| Share                         | Shares a post on Feed or Battles. Requires the property **Share** to be Enabled                            |
| Request Social                | Will get more social data about Gamee players. Requires the property **Social Data** to be Enabled         |
| Request Battle Data **(2.3)** | Will get data about a battle when the context is "battle". If the context is different, returns empty data |

- Share
  - Mandatory
    - **Text** The message of the post
    - **Destination** It will indicate where the post is going to be published, on Feed or Battle
    - **Picture** Image for the post. The image should be in format 4:3 (640x480px), 1:1 (640x640), or 3:4 (640x852). Maximum size is 150 kB. (base64Image)
  - Optional
    - **Score** The score of the Player
    - **Init Data** Data that will be shared with other players when they use the post.

## Expressions

| Name                                | Description                                                                                                            |
| ----------------------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| gameeSaveState                      | Contains data you previously saved                                                                                     |
| gameeReplayData                     | Contains data to use on replay mode or ghost mode                                                                      |
| gameeReplayVariant                  | Contains variante to use on replay mode or ghost mode                                                                  |
| gameeSocialData                     | Contains friends and player data (score, avatar, highScore, etc...)                                                    |
| gameePlatform                       | Contains the platform the player is using, it could be **android**,**ios**,**web**,**mobile_web**                      |
| gameeLocale                         | Contains the country and the language of the player, for example **\"**en_US**\"**,**\"**es_MX**\"**,**\"**pt_BZ**\"** |
| gameeGameContext                    | Contains the context of the game, it could be **normal** or **battle**                                                 |
| gameePlayerData                     | Received Json when a player accesses the game through a post made with the **Share** action                            |
| gameeCountry **(2.3)**              | Contains player country in ISO 3166-1 alpha-2                                                                          |
| gameePlayerMembershipType **(2.3)** | Contains the membership type of the player, it could be "basic" or "vip"                                               |
| gameeGameContextId **(2.3)**        | Contains the game context ID                                                                                           |
| gameeBattleData **(2.3)**           | Contains the game battle data                                                                                          |
