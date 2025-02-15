import spotipy
from spotipy.oauth2 import SpotifyClientCredentials
from yt_dlp import YoutubeDL
from youtube_search import YoutubeSearch

#####################################################
# Spotify_list_downloader:
# 
# You need to sign up for https://developer.spotify.com/dashboard, go to your profile, and fill in these fields:
SPOTIFY_CLIENT_ID = ''
SPOTIFY_CLIENT_SECRET = ''
#
# Here, enter the desired download path:
DOWNLOAD_PATH = 'C:\\Users\\User1234\\Music\\%(title)s.%(ext)s'
#
# By: CarlesP.
#####################################################


def get_spotify_playlist_tracks(playlist_url):
    auth = SpotifyClientCredentials(client_id=SPOTIFY_CLIENT_ID, client_secret=SPOTIFY_CLIENT_SECRET)
    sp = spotipy.Spotify(client_credentials_manager=auth)
    
    playlist_id = playlist_url.split("/")[-1].split("?")[0]
    results = sp.playlist_tracks(playlist_id)
    tracks = []
    
    for item in results['items']:
        track = item['track']
        tracks.append(f"{track['name']} {track['artists'][0]['name']}")
    
    return tracks

def download_youtube_audio(track_name):
    ydl_opts = {
        'format': 'bestaudio/best',  # Descarga el mejor formato de audio disponible
        'outtmpl': DOWNLOAD_PATH ,  # Ruta personalizada
        'noplaylist': True,  # Descarga solo el video, no la playlist
        'cachedir': False,  # Desactiva la caché para evitar errores
    }
    
    try:
        # Buscar en YouTube
        results = YoutubeSearch(track_name, max_results=1).to_dict()
        if results:
            url = f"https://youtube.com{results[0]['url_suffix']}"
            with YoutubeDL(ydl_opts) as ydl:
                info = ydl.extract_info(url, download=True)
                filename = ydl.prepare_filename(info)
                print(f"Descargado: {filename}")
        else:
            print(f"No encontrado: {track_name}")
    except Exception as e:
        print(f"Error en {track_name}: {str(e)}")

if __name__ == "__main__":
    playlist_url = input("Ingresa la URL de la playlist de Spotify: ")
    tracks = get_spotify_playlist_tracks(playlist_url)
    
    for track in tracks:
        download_youtube_audio(track)
