# name
WIP Add Device
# uniquetaskname
base.global.workflow.device.add
# description
Add new Device to neops Inventory
# provider_identifier
providers.core.neops.io/generic-simple-workflow:1
# task_kwargs
## tasks
### Add/Update Group Helper
#### run_as
GLOBAL
#### task_id
0
#### allow_all
False
#### titleProp
Add/Update Group Helper
#### task_enabled
True
#### task_template
```jinja2
{# set some initial variables #}
{% set group = {"name": input.get("name")} %}
{% if input.get("address") %}
  {% do group.update({"address": input.get("address"), "as_location": true}) %}
{% endif %}
{% if input.get("zip_code") %}
  {% do group.update({"zip_code": input.get("zip_code"), "as_location": true}) %}
{% endif %}
{% if input.get("city") %}
  {% do group.update({"city": input.get("city"), "as_location": true}) %}
{% endif %}
{% if input.get("country") %}
  {% do group.update({"country": input.get("country"), "as_location": true}) %}
{% endif %}
{% if input.get("lon") %}
  {% do group.update({"lon": input.get("lon"), "as_location": true}) %}
{% endif %}
{% if input.get("lat") %}
  {% do group.update({"lat": input.get("lat"), "as_location": true}) %}
{% endif %}

{% set params = {"groups": [group]} %}
{% do neops.set_params(params) %}
```
#### entity_template
```jinja2
{% do neops.set_entities([]) %}
```
#### task_uniquename
base.global.group_inventory_update.helper.both
#### task_cache_update
False
#### task_copy_results
False
#### task_include_pre_post
True
#### task_stop_workflow_on_failed
False
#### task_request_to_write_results
True
#### task_request_to_write_pre_post_run_results
False
### run_as
GLOBAL
# task_run_input_schema
```json
{
  "$id": "https://neops.io/schema/AddGroup.json",
  "$schema": "http://json-schema.org/draft-07/schema#",
  "title": "Add Group",
  "type": "object",
  "required": [
    "name"
  ],
  "properties": {
    "name": {
      "type": "string",
      "title": "Name",
      "description": "Name of the new Group",
      "default": ""
    },
    "address": {
      "type": "string",
      "title": "Street with Number",
      "description": "Street with Number",
      "default": ""
    },
    "zip_code": {
      "type": "string",
      "title": "ZIP",
      "description": "ZIP Code",
      "default": ""
    },
    "city": {
      "type": "string",
      "title": "City",
      "description": "City",
      "default": ""
    },
    "country": {
      "type": "string",
      "title": "Country",
      "description": "Country",
      "default": ""
    },
    "lat": {
      "type": "number",
      "title": "Latitude",
      "description": "Country",
      "default": ""
    },
    "lon": {
      "type": "number",
      "title": "Longitude",
      "description": "Longitude",
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
