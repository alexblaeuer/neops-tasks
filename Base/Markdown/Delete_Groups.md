# name
Delete Groups
# uniquetaskname
base.group.workflow.groups.remove
# description
Delete Groups in neops Inventory
# provider_identifier
providers.core.neops.io/generic-simple-workflow:1
# task_kwargs
## tasks
### Delete Group Helper
#### run_as
GLOBAL
#### task_id
0
#### allow_all
False
#### titleProp
Delete Group Helper
#### task_enabled
True
#### task_template
```jinja2
{#% set workflow_elements = neops.search_device_groups("*") %#}

{# set some initial variables #}
{% set params = {"groups": []} %}

{# remove selected groups #}
Delete groups:
{% for group in workflow_elements %}
  -- {{ group.name }}
  {% do params.groups.append({"id": group.id}) %}
{% endfor %}

{% do neops.set_params(params) %}
```
#### entity_template
```jinja2
{% do neops.set_entities([]) %}
```
#### task_uniquename
base.global.group_inventory_delete.helper.hard
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
{}
```
# task_run_filter

# pre_run
[]
# post_run
[]
