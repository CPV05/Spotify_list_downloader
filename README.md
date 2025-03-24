# Spotify Playlist Downloader

A simple Python script to download songs from a Spotify playlist by searching for them on YouTube and extracting the audio.

## Features
- Fetches track names from a Spotify playlist.
- Searches for the tracks on YouTube.
- Downloads the best available audio format.

## Requirements
- Python 3.x
- A Spotify Developer account ([Sign up here](https://developer.spotify.com/dashboard))

## Installation
1. Clone this repository:
   ```sh
   git clone https://github.com/CPV05/Spotify_list_downloader.git
   cd Spotify_list_downloader
   ```
2. Install dependencies:
   ```sh
   pip install spotipy yt-dlp youtube-search-python
   ```

## Configuration
Before running the script, update the following fields in the script:

1. Get your **Spotify Client ID** and **Client Secret** from [Spotify Developer Dashboard](https://developer.spotify.com/dashboard) and set them in the script:
   ```python
   SPOTIFY_CLIENT_ID = 'your_client_id'
   SPOTIFY_CLIENT_SECRET = 'your_client_secret'
   ```
2. Set your preferred download path:
   ```python
   DOWNLOAD_PATH = 'C:\\Users\\User1234\\Music\\%(title)s.%(ext)s'
   ```

## Notes
- The script fetches the track names and searches them on YouTube.
- Downloads the best available audio format.
- The output files will be saved in the specified download directory.

## Disclaimer
This project is for educational purposes only. Make sure you comply with YouTube and Spotify's terms of service.

## Author
By: [CarlesP.](https://github.com/CPV05)

