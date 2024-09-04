# name
Delete Device Helper
# uniquetaskname
base.global.device_inventory_delete.helper.hard
# description
Delete Device Helper
# provider_identifier
providers.core.neops.io/global-device-delete:1
# task_kwargs
## operation_type
HARD
# task_run_input_schema
```json
{
  "$id": "https://neops.io/schema/provider/GlobalDeviceDeleteProviderInput.json",
  "$schema": "http://json-schema.org/draft-07/schema#",
  "title": "Device Delete Parameters",
  "type": "object",
  "required": [],
  "properties": {
    "devices": {
      "type": "array",
      "title": "Device Lists",
      "description": "List of Devices/Device to be Deleted",
      "x-itemTitle": "reference_hostname",
      "items": {
        "type": "object",
        "properties": {
          "id": {
            "type": "integer",
            "title": "ID",
            "description": "ID of the target Object",
            "default": ""
          },
          "hostname": {
            "type": "string",
            "title": "Hostname",
            "description": "Hostname of the target Object",
            "default": ""
          },
          "ip": {
            "type": "string",
            "title": "IP",
            "description": "IP Address of the target Object",
            "default": ""
          },
          "ext_ref": {
            "type": "string",
            "title": "External Reference",
            "description": "External reference of the target Object",
            "default": ""
          }
        }
      }
    }
  }
}
```
# task_run_filter

# pre_run
[]
# post_run
[]
