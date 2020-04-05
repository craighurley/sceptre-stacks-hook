# Overview

The purpose of this hook is to set the stack termination protection status.

## Install

```sh
pip install git+https://git@github.com/craighurley/sceptre-terminationprotection-hook.git@1.0.0#egg=sceptre-terminationprotection-hook
```

## Available Hooks

### set_stack_termination_protection

Fetches the callers current public IP.

Syntax:

```yaml
hooks:
  <HOOK_POINT>:
    - !set_stack_termination_protection <STATE>
```

#### Example

Configure sceptre to set the stack termination protection status.

```yaml
hooks:
  after_create:
  - !set_stack_termination_protection enabled
  after_update:
    - !set_stack_termination_protection enabled
{% if environment != 'prod' %}
  before_delete:
    - !set_stack_termination_protection disabled
{% endif %}
```

Run sceptre to create/launch/delete a stack and sceptre will enable/disable the stack termination protection status accordingly.
