# Streams

## Get the specified channel's stream

`GET /streams/:channel/`

### Response

#### If the specified channel is offline

`200 OK` with an empty stream object.

    {
      "stream": null,
      "_links": {
        "self": "https://api.twitch.tv/kraken/streams/hebo"
      }
    }

#### If the specified channel is online

`200 OK` with the stream object.

    {
      "stream": {
        "game": "StarCraft II: Wings of Liberty",
        "name": "live_user_incontroltv",
        "created_at": "Tue Jul 24 13:22:26 2012",
        "viewers": 3505,
        "updated_at": "Tue Jul 24 15:33:39 2012",
        "channel_id": 20248706,
        "_links": {
          "self": "https://api.twitch.tv/kraken/streams/live_user_incontroltv"
        },
        "_id": 138658440,
        "delay_length": 0,
        "broadcaster": "fme",
        "geo": "US",
        "channel": {
          "name": "incontroltv",
          "game": "StarCraft II: Wings of Liberty",
          "created_at": "2011-02-07T06:24:25Z",
          "teams": [
            {
              "name": "eg",
              "created_at": "2011-10-11T23:59:43Z",
              "background": "http://static-cdn.jtvnw.net/jtv_user_pictures/team-eg-background_image-089a407eb59fe3b2.png",
              "updated_at": "2012-01-15T19:43:40Z",
              "banner": "http://static-cdn.jtvnw.net/jtv_user_pictures/team-eg-banner_image-8089b058e6ffe4cd-640x125.png",
              "logo": "http://static-cdn.jtvnw.net/jtv_user_pictures/team-eg-team_logo_image-53eaf029dad7d5c9-300x300.png",
              "_links": {
                "self": "https://api.twitch.tv/kraken/teams/eg"
              },
              "_id": 2,
              "info": "Team Info\n",
              "display_name": "Evil Geniuses"
            }
          ],
          "banner": "http://static-cdn.jtvnw.net/jtv_user_pictures/incontroltv-channel_header_image-612847bc6f091b50-640x125.jpeg",
          "updated_at": "2012-07-24T20:22:26Z",
          "_id": 20248706,
          "_links": {
            "stream_key": "https://api.twitch.tv/kraken/channels/incontroltv/stream_key",
            "self": "https://api.twitch.tv/kraken/channels/incontroltv",
            "chat": "https://api.twitch.tv/kraken/chat/incontroltv",
            "commercial": "https://api.twitch.tv/kraken/channels/incontroltv/commercial",
            "features": "https://api.twitch.tv/kraken/channels/incontroltv/features"
          },
          "logo": "http://static-cdn.jtvnw.net/jtv_user_pictures/incontroltv-profile_image--300x300.",
          "mature": null,
          "display_name": "iNcontroLTV",
          "status": "EGiNcontroL: music, commentary and all the stuff that makes rainbows and children possible"
        },
        "status": "EGiNcontroL: music, commentary and all the stuff that makes rainbows and children possible",
        "partner": true
      },
      "_links": {
        "self": "https://api.twitch.tv/kraken/streams/live_user_incontroltv"
      }
    }

## Get a list of streams

`GET /streams`

This is a flexible method that allows you to query for multiple streams based on a number of parameters.

### Parameters

- `game` (optional): The game to query.
- `channel` (optional): A list of channel names to query, seperated by commas.
- `limit` (optional): The maximum number of streams to return, up to 100.
- `offset` (optional): The offset to begin listing streams, defaults to 0.

#### Get list of Diablo III streams

`GET /streams?game=Diablo+III`

#### Get multiple channels

`GET /streams?channel=incredibleorb,incontroltv`

## Get a list of featured (promoted) streams

`GET /streams/featured`

### Parameters

- `limit` (optional): The maximum number of streams to return, up to 100. Defaults to 25.
- `offset` (optional): The offset to begin listing games, defaults to 0.

### Response
    
Response an array of featured streams. Each element in the featured array has promotional text, a promotional image, and a nested stream object (see above).

    {
      "_links": {
         self: "https://api.twitch.tv/kraken/streams/featured?limit=25&offset=0",
         next: "https://api.twitch.tv/kraken/streams/featured?limit=25&offset=25"
      },
      "featured": [
        {
          "image": "http://s.jtvnw.net/jtv_user_pictures/hosted_images/therun.jpg",
          "text": "This is the run! Watch as multi-time world record Super Mario 64 gamer, Siglemic, pushes the N64 classic to its absolute limits."
          "stream": {
            ...
          }
        },
        [...]
      ]
    }