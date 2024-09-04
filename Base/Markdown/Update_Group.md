# name
Update Group
# uniquetaskname
base.group.workflow.group.update
# description
Update a Group in neops Inventory
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
{#% set workflow_elements = neops.search_device_groups("*") %#}

{# set some initial variables #}
{% set params = {"groups": []} %}

{# check only one group selectet #}
{% if workflow_elements | count == 1 %}
	{% set group = {"reference_id": workflow_elements[0].id} %}
  Update group:
  -- {{ workflow_elements[0].name }}
  
  {% if input.get("name") %}
    {% do group.update({"name": input.get("name")}) %}
  {% endif %}
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
  
  {% do params.groups.append(group) %}
{% else %}
	More than one group selected:
	{{ workflow_elements | jmespath("[*].name") }}
{% endif %}

{% do neops.set_params(params) %}
```
#### entity_template
```jinja2
{% do neops.set_entities([]) %}
```
#### task_uniquename
base.global.group_inventory_delete.helper.both
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
GROUP
# task_run_input_schema
```json
{
  "$id": "https://neops.io/schema/UpdateGroup.json",
  "$schema": "http://json-schema.org/draft-07/schema#",
  "title": "Update Group",
  "type": "object",
  "required": [],
  "properties": {
    "name": {
      "type": "string",
      "title": "Name",
      "description": "Name of the Group",
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
