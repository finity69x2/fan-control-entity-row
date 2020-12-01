Changes:

- v2.0 - added the ability to hide the medium speed button for use with a two speed fan.

- v1.8 & v1.9 - BREAKING CHANGES! - I modified the options to be consistent with my other control rows and changed the default button order. I also added the option to reverse the button order. See the readme.md for updated coinfiguration options.

- v1.6 - added the ability to customize the text for the buttons. defaults to "OFF, LOW, MED, HIGH"

This is an element to add a fan control row to Home Assistant for 3-speed fans.

It uses the code that can be found in my fan control package @ https://github.com/finity69x2/Home-Assistant/blob/master/packages/fan_package.yaml

Installation:

Copy the fan-control-entity-row.js file to the appropriate folder in your Home Assistant Configuration directory (/config/www/).

Place the following in your "resources" section in your lovelace configuration (updating the localation to where you placed the above file):

  ```
    - url: /local/fan-control-entity-row.js
      type: js
  ```
    
Then to use this in a card place the following in your entity card:


<b>Options:</b>

| Name | Type | Required | Default | Description |
| --- | --- | --- | --- | --- |
| entity | String | Yes | none | a fan entity_id |
| type | String | Yes | none | custom:fan-control-entity-row |
| name | String | No | none | A custom name for the entity in the row |
| customTheme | Boolean | No | false | set to true to use a custom theme |
| reverseButtons | Boolean | No | false | Set to true to reverse the button order |
| isTwoSpeedFan | Boolean | No | false | Set to true to hide the Medium Speed button |
| sensStateWithSpeed | Boolean | No | false | Used only for certain firmware that requires the Statre command be sent with the speed command  |
| isOffColor | String | No | '#f44c09' | Sets the color of the 'Off' button if fan is off |
| isOnLowColor | String | No | '#43A047' | Sets the color of the 'Low' button if fan is on low |
| isOnMedColor | String | No | '#43A047' | Sets the color of the 'Med' button if fan is on Medium |
| isOnHiColor | String | No | '#43A047' | Sets the color of the 'High' button if fan is on high |
| buttonInactiveColor | String | No | '#759aaa' | Sets the color of the buttons if that selection is off |
| customOffText | String | No | 'OFF' | Sets the text of the "off" button |
| customLowText | String | No | 'LOW' | Sets the text of the "low" speed button |
| customMedText | String | No | 'MED' | Sets the text of the "medium" speed button |
| customHiText | String | No | 'HIGH' | Sets the text of the "High" speed button |


The values for the colors can be any valid color string in "HEX", "RGB" or by color name.

The optional "sendStateWithSpeed" config entry is only needed to be set to true if for some reason your fan needs the state command of "on" to be sent along with the desired speed command. As far as I know this is only needed for use with fans flashed with the ESPHome Firmware.

<b>Comfguration Examples:</b>
    
  ```
    cards:
      - type: entities
        title: Fans
        show_header_toggle: false
        entities:
        ## USE THIS CONFIG TO HAVE IT MATCH YOUR THEME ##
          - entity: fan.master_bedroom_fan
            type: custom:fan-control-entity-row
            name: MBR Fan Not Custom
            customTheme: false
        ## USE THIS CONFIG TO USE A DEFAULT CUSTOM THEME
          - entity: fan.sunroom_fan
            type: custom:fan-control-entity-row
            name: Sunroom Fan Default Custom
            customTheme: true
        ## USE THIS CONFIG TO USE A 'CUSTOMZED' CUSTOM THEME
          - entity: fan.sunroom_fan
            type: custom:fan-control-entity-row
            name: Sunroom Fan Custom Custom
            reverseButtons: true
            customTheme: true
            isOnLowColor: 'rgb(255, 0, 0)'
            isOnMedColor: '#888888'
            isOnHiColor: '#222222'
            buttonInactiveColor: '#aaaaaa'
            isOffColor: 'purple'
        ## USE THIS CONFIG FOR USE WITH THE ESPHOME FIRMWARE (ALONG WITHE THE THEME SETTING ABOVE IF DESIRED)
          - entity: fan.master_bedroom_fan
            type: custom:fan-control-entity-row
            name: MBR Fan Not Custom
            sendStateWithSpeed: true
        ## USE THIS CONFIG TO SET CUSTOM BUTTON TEXT (NOT REQUIRED TO SET "customTheme: true" TO USE THESE )
          - entity: fan.sunroom_fan
            type: custom:fan-control-entity-row
            name: Sunroom Fan Custom Custom
            customHiText: me
            customLowText: do
            customMedText: re
            customOffText: not
  ```

This is with the default Lovelace frontend theme set:

![Default](default_fan_ex.gif)


This is with the "Slate" frontend theme set:

![Slate](slate_fan_ex.gif)

This is how this plugin looks with the Light Brightness Preset & Binary Button Rows:

![Slate-Compare](button-row-example-compare.gif)
