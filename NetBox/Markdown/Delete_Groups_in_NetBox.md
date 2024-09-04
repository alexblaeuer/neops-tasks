# name
Delete Groups in NetBox
# uniquetaskname
nb.group.netbox.site.remove
# description
Delete Groups in NetBox (Site)
# provider_identifier
providers.core.neops.io/generic-netbox-jinja-facts:1
# task_kwargs
## mapping
{'add_facts_to': 'GROUP', 'mapping_template': '{% if response.get(group.id, false) %}\n  {# site was deleted #}\n  {% do neops.set_facts({}) %}\n{% else %}\n  {# site was not deleted #}\n  {% do neops.set_facts(group.facts.get("netbox", {})) %}\n{% endif %}'}
## facts_key
netbox
## run_netbox_on
GLOBAL
## execute_template
{#% set device_groups = neops.search_device_groups("*") %#}

{# set some initial variables #}
{% set facts = {} %}
{% set endpoint = "dcim/sites/" %}

{% for group in device_groups %}
  {% if group.facts.get("netbox") %}
  	{# remove group in netbox #}
    -- Delete group: {{ group.name }}    
    {% set response = netbox.delete(endpoint ~ group.facts.netbox.get("id")) %}
    {% do facts.update({group.id: response}) %}
  {% else %}
  	{# no ref to netbox site in facts #}
    -- No NetBox Site mapped to group: {{ group.name }}
  {% endif %}
{% endfor %}

{% do neops.set_facts(facts) %}
## write_on_dry_run
True
# task_run_input_schema
```json
{}
```
# task_run_filter

# pre_run
[]
# post_run
[]
