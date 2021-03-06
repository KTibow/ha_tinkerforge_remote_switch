# Tinkerforge remote switch
This component has been created to be used with Home Assistant

The `Tinkerforge remote switch` integration lets you integrate the tinkerforge [HAT Brick](https://www.tinkerforge.com/en/doc/Hardware/Bricks/HAT_Brick.html) or [HAT Zero Brick](https://www.tinkerforge.com/en/doc/Hardware/Bricks/HAT_Zero_Brick.html) with a [Remote Switch Bricklet 2.0](https://www.tinkerforge.com/en/doc/Hardware/Bricklets/Remote_Switch_V2.html) into home assistant.
You can switch 433 Mhz plug sockets with home assistant and you can also react on the remote control keys.

You have to install the [Tinkerforge Brick Daemon](https://www.tinkerforge.com/en/doc/Software/Brickd.html).
Use the [Brick Viewer](https://www.tinkerforge.com/en/doc/Software/Brickv.html) to detect the uid, remote type and so on.

## Configuration

To enable this component, add the following lines to your `configuration.yaml` file:

```yaml
# Example main configuration.yaml entry
tinkerforge_switch:
  host: localhost
  port: 4223
  uid: EC2
  remote_type: A
```

| Field | Type | Required | Default | Description |
|:----- |:---- |:-------- |:------- |:----------- |
| host  | string | false | localhost | IP address or hostname of the [brick daemon](https://www.tinkerforge.com/en/doc/Software/Brickd.html). |
| port  | integer | false | 4233    | The port number of the [brick daemon](https://www.tinkerforge.com/en/doc/Software/Brickd.html). |
| uid   | string | true   |         | The uid of the [Remote Switch Bricklet 2.0](https://www.tinkerforge.com/en/doc/Hardware/Bricklets/Remote_Switch_V2.html). You can see the uid in the [Brick Viewer](https://www.tinkerforge.com/en/doc/Software/Brickv.html). |
| remote_type | string | true |     | A, B or C. The remote type of the plug socket or remote control. Have a lock in the [Brick Viewer](https://www.tinkerforge.com/en/doc/Software/Brickv.html) while pressing the remote control buttons. |

```yaml
# Example switches configuration.yaml entry
switch:
  - platform: tinkerforge_switch
    switches:
      - id: brennstuhl_fb_a
        friendly_name: Brennstuhl FB A
        house_code: 31
        receiver_code: 1
      - id: brennstuhl_fb_B
        friendly_name: Brennstuhl FB B
        house_code: 31
        receiver_code: 2
```

| Field | Type | Required | Default | Description |
|:----- |:---- |:-------- |:------- |:----------- |
| id  | string | true |   | The internal id of the switch |
| friendly_name | string | false |  | Sets a meaningful name for the switch, if not provided the switch will be named after the id. |
| house_code | integer | true   |   | The house_code of the plug socket. Have a lock in the brick viewer while pressing the remote control buttons. |
| receiver_code | string | true |   | The receiver_code of the lug socket. Have a lock in the brick viewer while pressing the remote control buttons. |
| icon | string | false |   | Set an icon for the switch. |
