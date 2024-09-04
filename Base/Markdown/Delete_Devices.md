# name
Delete Devices
# uniquetaskname
base.device.workflow.devices.remove
# description
Delete Devices in neops Inventory
# provider_identifier
providers.core.neops.io/generic-simple-workflow:1
# task_kwargs
## tasks
### Delete Device Helper
#### run_as
GLOBAL
#### task_id
0
#### allow_all
False
#### titleProp
Delete Device Helper
#### task_enabled
True
#### task_template
```jinja2
{#% set workflow_elements = neops.search_devices("*") %#}

{# set some initial variables #}
{% set params = {"devices": []} %}

{# remove selected devices #}
Delete devices:
{% for device in workflow_elements %}
  -- {{ device.hostname }}
  {% do params.devices.append({"id": device.id}) %}
{% endfor %}

{% do neops.set_params(params) %}
```
#### entity_template
```jinja2
{% do neops.set_entities([]) %}
```
#### task_uniquename
base.global.device_inventory_delete.helper.hard
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
DEVICE
# task_run_input_schema
```json
{}
```
# task_run_filter

# pre_run
[]
# post_run
[]
