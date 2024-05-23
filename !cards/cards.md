# HA Configuration 
### _This is a basic instruction on how to get these cards working in your HA Setup._
Shoot me a comment if you need help, and I'll do my best to get you up and going.

- #### Multi-room Player Card
  In order for this to work in my setup, I have installed vlc on an endpoint client, and have it running in the background with the following command:
> ```sh
> cvlc -I telnet --telnet-password=<mysecret> &
> ``` 
  ***By default, the vlc telnet plugin runs on port tcp/4212. \
  
  To use this card, configure the system like this:
  - Add your endpoint(s) via the VLC Telnet integration from **Settings -> Devices & Services -> + Add Integration**. Specify the IP/Host, secret, and port (4213).
  - Open the VLC Integration, click your added endpoint, and click the 'entity' link under the added integration.
  - Click on the entity that was created in the next window, and then the cog (settings) button on the top right of the popup.
  - Give your endpoint a Logical Name, such as "[Multiroom Player] Livingroom", and prepend the Entity ID of the device with `mrp_`. ex: 'mrp_livingroom'. Repeat for all VLC endpoints.

  > *** FOREWORD: While I assume it is possible to add other media_player entities to the below group, I have not tested that. I would guess you could add Amazone Echos or Google Nest Minis, but I dont have those devices in the house to test this theory. If someone would let me know if this is possible I can remove this note and modify this instruction.
  - Add a Media Player Group Helper object from **Settings -> Devices & Services -> Helpers -> + Create Helper** Give it a Logical name, ex. '[Multi Room Player] Endpoints' and add your entit(ies) to it.
  - *** !KEY! Click on the entity that was created in the next window, and then the cog (settings) button on the top right of the popup. Change the Entity ID to `mrp_helper` The Accompanying package **will not work** if not.
  - Done!

  Add the card to your dashboard, and edit/add the configuration of it with the notes from the card yaml.