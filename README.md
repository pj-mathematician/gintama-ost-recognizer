# gintama-ost-recognizer
google colab project to identify the original soundtracks used in the anime Gintama (planning to extend to other animes also)
## how it works
Theres a package called [kurby](https://github.com/aberrier/kurby) that downloads an episode in .mp4 format which is then converted into .wav using [ffmpeg](https://github.com/FFmpeg/FFmpeg)

The vocals from the .wav are removed using 2 deep learning vocal-removers : https://github.com/tsurumeso/vocal-remover and https://github.com/Anjok07/ultimatevocalremovergui and i get an mp3 file with all vocals removed with only the bg music and some noise

The vocal removed mp3 is split into chunks based on silence in between to get all the different tracks used in an ep and saved in a folder using [pydub](https://github.com/jiaaro/pydub)

the analysing and matching of the audio is done by fingerprinting based on [audfprint](https://github.com/dpwe/audfprint) i made a ~500mb database of fingerprints of all the osts, and now i iterate through the chunk folder and match every file 

All i have to do now is export the results of each chunk characterized by its time stamp
