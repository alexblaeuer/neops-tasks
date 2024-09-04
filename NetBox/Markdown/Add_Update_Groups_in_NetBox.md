# name
Add Update Groups in NetBox
# uniquetaskname
nb.group.netbox.site.add
# description
Add/Update Groups in NetBox as Site
# provider_identifier
providers.core.neops.io/generic-netbox-jinja-facts:1
# task_kwargs
## mapping
{'add_facts_to': 'GROUP', 'mapping_template': '{% set facts = response.get(group.id, {}) %}\n{% do neops.set_facts(facts) %}'}
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
	{% set body = {"name": group.name, "slug": group.name | lower, "status": "active", "description": group.description} %}
	{% if group.get("location") %}
  	{# set address if group is a location #}
  	{% set location = group.get("location") %}
  	{% do body.update({"physical_address": location.address ~ ", " ~ location.zip_code ~ " " ~ location.city ~ ", " ~ location.country, "latitude": location.lat, "longitude": location.lon}) %}
  {% endif %}
  {% if not group.facts.get("netbox") %}
  	{# add group in netbox #}
    -- Add group: {{ group.name }}
    {% set response = netbox.post(endpoint, body) %}
    {% do facts.update({group.id: response}) %}
  {% else %}
  	{# update group in netbox #}
    -- Update group: {{ group.name }}
    {% set response = netbox.patch(endpoint ~ group.facts.netbox.get("id"), body) %}
    {% do facts.update({group.id: response}) %}
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
