# name
Import Module Types from NetBox
# uniquetaskname
nb.gobal.netbox.module_types.import
# description
Import Module Types from NetBox
# provider_identifier
providers.core.neops.io/generic-netbox-jinja-facts:1
# task_kwargs
## mapping
{'add_facts_to': 'GLOBAL', 'mapping_template': '{% do neops.set_facts(response) %}'}
## facts_key
netbox_module_types
## run_netbox_on
GLOBAL
## execute_template
{% set endpoint = "dcim/module-types/" %}
{% set response = netbox.get(endpoint) %}
{% do neops.set_facts(response) %}
## write_on_dry_run
False
# task_run_input_schema
```json
{}
```
# task_run_filter

# pre_run
[]
# post_run
[]
