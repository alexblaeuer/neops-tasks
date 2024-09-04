# name
Restart Device Helper
# uniquetaskname
base.device.restart_device.helper
# description
Restart Device Helper
# provider_identifier
providers.core.neops.io/device-restart:1
# task_kwargs
# task_run_input_schema
```json
{
  "$id": "https://neops.io/schema/provider/DeviceRestart.json",
  "$schema": "http://json-schema.org/draft-07/schema#",
  "title": "Device Restart",
  "type": "object",
  "required": [
    "restart",
    "timeout"
  ],
  "properties": {
    "timeout": {
      "title": "timout till failed",
      "type": "integer",
      "description": "wait till restart timeout exception is thrown",
      "default": 1200
    },
    "restart": {
      "title": "Are you sure",
      "type": "boolean",
      "description": "Are you sure to restart the device",
      "default": false
    },
    "activate": {
      "title": "Activate new software?",
      "type": "boolean",
      "description": "Activate new software as well?",
      "default": false
    },
    "reload_in_one": {
      "title": "Delayed reload (1m)",
      "type": "boolean",
      "description": "Delay reload for 1 minute",
      "default": false
    },
    "save_config_if_required": {
      "title": "Save Config if Required",
      "type": "boolean",
      "description": "Save config before restart if asked so",
      "default": true
    },
    "wait_on_reconnect": {
      "title": "Wait till device is reloaded",
      "type": "boolean",
      "description": "",
      "default": true
    }
  }
}
```
# task_run_filter

# pre_run
[]
# post_run
[]
