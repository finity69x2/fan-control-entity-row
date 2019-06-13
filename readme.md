This is an element to add a fan control row to Home Assistant.

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
| customIsOffColor | String | No | '#f44c09' | Sets the color of the 'Off' button if fan is off |
| customIsOnLowColor | String | No | '#43A047' | Sets the color of the 'Low' button if fan is on low |
| customIsOnMedColor | String | No | '#43A047' | Sets the color of the 'Med' button if fan is on Medium |
| customIsOnHiColor | String | No | '#43A047' | Sets the color of the 'Hi' button if fan is on high |
| customIsOffSpdColor | String | No | '#759aaa' | Sets the color of the the buttons if that selection is off |


The values for the colors can be any valid color string in "HEX", "RGB" or by color name.

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
            customTheme: true
            customIsOnLowColor: 'rgb(255, 0, 0)'
            customIsOnMedColor: '#888888'
            customIsOnHiColor: '#222222'
            customIsOffSpdColor: '#aaaaaa'
            customIsOffColor: 'purple'
  ```

This is with the default Lovelace frontend theme set:

![Default](default_fan_ex.gif)


This is with the "Slate" frontend theme set:

![Slate](slate_fan_ex.gif)

