# name
Add Update Group Helper
# uniquetaskname
base.global.group_inventory_update.helper.both
# description
Add/Update Group Helper
# provider_identifier
providers.core.neops.io/global-device-group-update:1
# task_kwargs
## operation_type
BOTH
# task_run_input_schema
```json
{
  "$id": "https://neops.io/schema/provider/GlobalDeviceGroupUpdateProviderInput.json",
  "$schema": "http://json-schema.org/draft-07/schema#",
  "title": "Device Group Parameters",
  "type": "object",
  "required": [],
  "properties": {
    "groups": {
      "type": "array",
      "title": "Groups List",
      "description": "List of Device Group Values to be Updated",
      "x-itemTitle": "reference_group_name",
      "items": {
        "type": "object",
        "properties": {
          "reference_id": {
            "type": "integer",
            "title": "Reference ID",
            "description": "ID of the existing Object",
            "default": 0
          },
          "reference_name": {
            "type": "string",
            "title": "Reference Name",
            "description": "Name of the existing Device Group Object",
            "default": ""
          },
          "name": {
            "type": "string",
            "title": "Name",
            "description": "Name of the existing Device Group Object",
            "default": ""
          },
          "devices_add": {
            "type": "array",
            "title": "Devices to add",
            "description": "Devices to add to Group",
            "items": {
              "type": "integer"
            }
          },
          "devices_remove": {
            "type": "array",
            "title": "Devices to remove",
            "description": "Devices to Remove from Group",
            "items": {
              "type": "integer"
            }
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
