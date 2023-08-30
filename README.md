# ha-tesla-lovelace-floorplan

#### Disclaimer: I have made this for my self. You are more than welcome to use it in any way you like, but do so with guaraantees of anything, nor expectations of updates/upgrades/fixes. I'm not saying I won't, but don't use this with the expectation, as I can give no promises.

I should also say that this is a work in progress, some things don't work yet. I'll try to update as I fix. I am also testing, and I might add/remove features too fit my use case. I'll try to remember to make a "release" for any major changes, so each version is still around.

This is a card for controlling and viewing a Tesla car. I have made this for a black Model Y, since this i what I have. However, I have provided a tetmplate and guide if anyone wants tto replace the images with their own model/color.

All doors closed, car offline | Trunk open, car online
:-------------------------:|:-------------------------:
<img src="https://github.com/Aephir/ha-tesla-lovelace-floorplan/blob/main/images/all-closed-offline.png?raw=true" width="400" /> | <img src="https://github.com/Aephir/ha-tesla-lovelace-floorplan/blob/main/images/trunk-open-online.png?raw=true" width="400" />

## Requirements
- The [Tesla custom component](https://github.com/alandtse/tesla)
- The [ha-floorplan component](https://github.com/ExperienceLovelace/ha-floorplan)

## Installation
No addiional installation required. Simply:
- Add the `tesla-floorplan.svg` to your preferred location (if not under `/config/www/floorplan/tesla`, then modify line 4 in the `tesla-florplan.yaml` accordingly)
- Add the tesla-floorplan.css to the same location as the `tesla-floorplan.svg` (if not under `/config/www/floorplan/tesla`, then modify line 7 in the `tesla-florplan.yaml` accordingly)
- Add or copy the content of `packages/tesla_floorplan_package.yaml` to your preferred locaiton (`/config/packages` is used for my examples)
- Add the following to your `configuraion.yaml` (replacing the last `packages` with the folder you used).

```
homeassistant:
  packages: !include_dir_named packages
```

- Replace all intances of `.tesla_model_y_` in the `tesla-floorplan.yaml` with `.$YOUR_TESLA_NAME_`, where `$YOUR_TESLA_NAME` is whatever you named your Tesla (the prefix to all the entity names created when you set up the Tesla custom inntegration)
- Then go to your Lovelace dashboard to add a new card, select `manual`, and copy the content of `tesla-florplan.yaml` and press save.


## Features

### Information
- Each door, trunk, frunk, and charging port will show as open/closed on the central image.
- Battery state (%) and range left is displayed in the top left.
  - It is colored according to charge, with 50 % to 80 % shown in the grey you see above.
- Whether the car is plugged in, and whether it i charging is diplayed in the top.
- The temperature inside, outide, and what the AC is set for is displayed in the left of the top row of icons at the botttom.
  - It is colored according to temparature, with 18 °C to 23.1 °C shown in the grey you see above.
- Location, Destination, and last update is shown in the center of the top row of icons at the botttom.
- The connectivity status is shown in the second from the right of the top row of icons at the botttom.
  - Grey if connected, red if not.
- The tire pressure warning is shown in the right-most of the top row of icons at the botttom.
  - Grey if normal (thresshold set to lesss than 0.3 bar different from the recommended 2.9 bar)


### Control
The icons in the lower row are colored with the "standard" grey for what I have deemed the "stanard" state, and a dark red for the "attention" state. They are, from left to right::
- AC
  - Tapping will turn on to "auto" if off, and turn off if "on"
- Defrost <-- Not working yet (need to add script to handle toggling)
- Steering wheel heating
  - Toggles heated steering wheel
- Window vent
  - Toggle the "vent". If "off" (toggling to "on"), all windows will move to a "slightly open" state (both if they are closed, and if they are open).
- Lock
  - Toggles the lock state of the car
- Charing port __OBS! USE WITH CARE__ Home Assistan does not always have the latest data, and you might inadvertedly close it while a plug is actually in, which could damage your charge port (and perhaps charger).
  - Tapping will do the following in the following situation:
    - If the charger is locked (plugged in), it will unlock so you can remove the charger
    - If the port is closed, it will open
    - If the port is open, it will close it if it detects that (1) the charger is unplugged, (2) the car is not charging
- Frunk
  - Open the frunk
- Trunk
  - Toggle the open/close state of the trunk
- Force Update
  - Update the data so sensors have the current state (hint: you can see when it was last updated oon tthe card)





