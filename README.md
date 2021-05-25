# Kivy-Live-Ui

Kivy-Live-UI helps you code on your Computer system and see result instantly on your android phone without recompiling, It makes use of `kaki` and `watchdog` project to detect a file modification and then transmits the changes through python `socket` to the **server** and then the server broadcast it to all Ui devices connected to it and all client code updaters too.

**Client Updaters(*Kivy-Live-Client*)** is the package in charge of transmitting update to the server

**Kivy-Live-Server** is the package in charge of broadcating the update transmitted by *Kivy-Live-Client* to all connected devices

**Kivy-Live** is the Android apk or package that displays the UI

Note
: During the compilation of Kivy-Live to apk I used buildozer and after the first build, I change line 791 of `.buildozer/android/platform/build-armeabi-v7a/dists/kivylive__armeabi-v7a/build.py` 
from 
```python
ap.add_argument('--no-compile-pyo', dest='no_compile_pyo', action='store_true', help='Do not optimise .py files to .pyo.')
```

to

```python
ap.add_argument('--no-compile-pyo', dest='no_compile_pyo', action='store_false', help='Do not optimise .py files to .pyo.')
```

(the change there is in `action='store_*****'`)

this makes the python codes not to be compiled because the **KivyLive** app needs to be writing to those file so a to trigger the update event


# How to Use

Download and install the apk, start the server(**KivyLiveServer**)(make sure watchdog is installed), connect the android phone the server by providing the `server ip` in the text field provided(in case you want to compile yours and add extra requirements, do not add `kaki` because I mad a few changes and bundled it with the app), finally start the **KivyLiveClient** and point it to the directory that you want to listen update from e.g `python3 main.py /home/test/my_project/`.

During the 1st connection of the **Client Updater(*KivyLiveClient*)** the server will send it the latest update of the code and those codes will be stored in the same directory with the **Client Updater**

![kivylive](https://user-images.githubusercontent.com/42192162/119441673-6b316580-bd1e-11eb-9958-2848b405e1ed.gif)
![kivy live ui](https://user-images.githubusercontent.com/42192162/119441925-da0ebe80-bd1e-11eb-806f-1ffd9032fb2d.gif)

