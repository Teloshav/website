---
title: "Navidrome Smart Playlists (Work in progress!)"
linkTitle: "Smart Playlists"
weight: 100
description: >-
     How to set up, use and create your own smart playlists for Navidrome!
---
# Contents (Work in progress!!):
- [Setup](#Setup)
- [Example Smart Playlists](#Example Smart Playlists)

# Setup
Smart playlists are a JSON object put into a file with a `.nsp` extension, 
Navidrome will create a dynamic/query based playlist and keep it updated. 
The `.nsp` files should be put in the music folder that's been specified 
in the [configuration file](https://www.navidrome.org/docs/usage/configuration-options/#basic-configuration) (Environment variable ND_MUSICFOLDER).

---
# Example Smart Playlists

- 100 Most recently played songs
```{
  "all": [
    {"inTheLast": {"lastPlayed": 30}}
  ],
  "sort": "lastPlayed",
  "order": "desc",
  "limit": 100
}
```
- 80's top songs
```{
  "all": [
    { "any": [
      {"is": {"loved": true}},
      {"gt": {"rating": 3}}
    ]},
    {"inTheRange": {"year": [1981, 1990]}}
  ],
  "sort": "year",
  "order": "desc",
  "limit": 25
}
```
- Favourites (limited up to 500 songs)
```{
  "all": [
    {"is": {"loved": true}}
  ],
  "sort": "dateLoved",
  "order": "desc",
  "limit": 500
}
```
- All songs in random order (not recommended for large libraries)
```{
  "all": [
    {"gt": {"playCount":-1}}
  ],
  "sort": "random"
}

