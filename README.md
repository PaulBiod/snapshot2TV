# snapshot2TV
## Display your camera snapshot on your android TV (or any android device)

You're watching TV and someone is at your door ? let's show a snapshot  of your camera (or just a message) directly on your TV (or any android device).
There's a lot of ways to achieve this, but I'm gonna show you how to do it programmatically via a script that you can call from any automation/script in Home assistant, just by passing 3 variables to the script : 
```
- the room (so that it will show the snapshop of the camera in that room)
- the title
- the message.
```
So, from any automation, you can send a message or a snapshot directly to your TV just with 4 lines !

First of all, you have to download (from the play store of your tv) an app called "Notification for android TV - it's free) and install it on your tv.
Then, just install in Home assistant an integration called Notification for android ("https://www.home-assistant.io/integrations/nfandroidtv")
Once installed, it will ask for your TV IP, just fill in the IP and give it a name (Room TV for example), and you're good to go.

Once you have the integration installed, there is a new "action" that you can call, something like "notify.room_tv" if the name you gave is "room tv".

Next step, just create a script, you can copy/paste the script of this repository called "send2tv.yaml". Just don't forget to change the rooms and the camera entity associated to each room. In my case, there is 6 cameras, but you just have to adapt it for your needs.
The lines to be changed are commented. The first "IF" is optionnal, but it will prevent the script from running if your TV is switched off.

Once the script is created, you can call it from anywhere in home assistant like this : 

action: script.send2tv (if send2tv is the name of your script, like me)
data:
  room: salon
  title: Motion
  message: Hey Dude, there's someone at your door
  

And that's it ! a nice message with the snapshot will be shown on the TV

Important : 
The camera.snapshot action uses a local path to store the files, so you have to set up the path in your configuration.yaml, something like this : 

homeassistant:
  allowlist_external_dirs:
    - "/config/www/cam"

Hope you enjoy it !
