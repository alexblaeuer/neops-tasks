# name
Add Update Device Helper
# uniquetaskname
base.global.device_inventory_update.helper.both
# description
Add or Update Device Helper
# provider_identifier
providers.core.neops.io/global-device-update:1
# task_kwargs
## operation_type
BOTH
## platform_detection
False
# task_run_input_schema
```json
{
  "$id": "https://neops.io/schema/provider/GlobalDeviceUpdateProviderInput.json",
  "$schema": "http://json-schema.org/draft-07/schema#",
  "title": "Host Update Parameters",
  "type": "object",
  "required": [],
  "properties": {
    "devices": {
      "type": "array",
      "title": "Device Lists",
      "description": "List of Devices/Device Values to be Updated",
      "x-itemTitle": "reference_hostname",
      "items": {
        "type": "object",
        "properties": {
          "reference_id": {
            "type": "integer",
            "title": "Reference ID",
            "description": "ID of the existing Object",
            "default": 0
          },
          "reference_hostname": {
            "type": "string",
            "title": "Reference Hostname",
            "description": "Hostname of the existing Object",
            "default": ""
          },
          "reference_ip": {
            "type": "string",
            "title": "Reference IP",
            "description": "IP Address of the existing Object",
            "default": ""
          },
          "reference_ext_ref": {
            "type": "string",
            "title": "Reference External Reference",
            "description": "Match on external reference of existing Object",
            "default": ""
          },
          "hostname": {
            "type": "string",
            "title": "Hostname",
            "description": "Hostname of the new/updated Object",
            "default": ""
          },
          "ip": {
            "type": "string",
            "title": "IP",
            "description": "IP Address of the new/updated Object",
            "default": ""
          },
          "ext_ref": {
            "type": "string",
            "title": "External Reference",
            "description": "External reference of the new/updated Object",
            "default": ""
          },
          "username": {
            "type": "string",
            "title": "Username",
            "description": "Username of the updated Objects",
            "default": ""
          },
          "password": {
            "type": "string",
            "title": "Password",
            "description": "Password of the updated Objects",
            "default": ""
          },
          "groups_add": {
            "type": "array",
            "title": "Groups to add the device",
            "description": "Groups to add the device",
            "items": {
              "type": "integer"
            }
          },
          "groups_remove": {
            "type": "array",
            "title": "Groups to remove the device",
            "description": "Groups to Remove from Group",
            "items": {
              "type": "integer"
            }
          },
          "platform": {
            "type": "string",
            "title": "Platform",
            "description": "Platform of the new/updated Object",
            "default": ""
          }
        }
      }
    },
    "global_username": {
      "type": "string",
      "title": "Global Username",
      "description": "Global Username of the updated Objects",
      "default": ""
    },
    "global_password": {
      "type": "string",
      "title": "Global Password",
      "description": "Global Password of the updated Objects",
      "default": ""
    },
    "global_platform": {
      "type": "string",
      "title": "Platform",
      "description": "Platform of the new/updated Object",
      "default": ""
    }
  }
}
```
# task_run_filter

# pre_run
[]
# post_run
[]
