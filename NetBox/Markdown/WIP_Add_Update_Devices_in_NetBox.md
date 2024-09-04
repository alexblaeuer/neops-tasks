# name
WIP Add Update Devices in NetBox
# uniquetaskname
nb.device.netbox.device.add
# description
Add/Update Devices in NetBox
# provider_identifier
providers.core.neops.io/generic-netbox-jinja-facts:1
# task_kwargs
## mapping
{'add_facts_to': 'DEVICE', 'mapping_template': '{% set facts = response.get(device.id, {}) %}\n{% do neops.set_facts(facts) %}'}
## facts_key
netbox
## run_netbox_on
GLOBAL
## execute_template
{#% set devices = neops.search_devices("*") %#}

{# set some initial variables #}
{% set facts = {} %}
{% set device_types = neops.get_common_facts("netbox_device_types") %}
{% set endpoint = "dcim/devices/" %}

{% for device in devices %}
	{% set device_type = device_types | jmespath("[?part_number=='" ~ device.model ~ "']|[0]") %}
  {% set device_type = device_types | jmespath("[?part_number=='" ~ device.model ~ "-L3']|[0]") %}
  {# how to handle the IOSv devices #}
  {# how to handle if device_type not found #}
  {# add device role, serial, platform, site, interfaces, ip, primary_ip4 #}
  
	{% set body = {"name": device.hostname, "status": "active"} %}
  {% if not device.facts.get("netbox") %}
  	{# add device in netbox #}
    -- Add device: {{ device.hostname }}
    {% set response = netbox.post(endpoint, body) %}
    {% do facts.update({device.id: response}) %}
  {% else %}
  	{# update device in netbox #}
    -- Update device: {{ device.hostname }}
    {% set response = netbox.patch(endpoint ~ device.facts.netbox.get("id"), body) %}
    {% do facts.update({device.id: response}) %}
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
