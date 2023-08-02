# service_design_change

## Summary

Creates the Change Request for the Service Design process.  It will also get the ServiceNow Developer on-call for the week and add them to the change.

## Requirements

- servicenow.servicenow

## Variables

| Variable             | Required? | Description                  | Type   | Example                              | Notes                                   |
| -------------------- | --------- | ---------------------------- | ------ | ------------------------------------ | --------------------------------------- |
| sn_username          | yes       | sn username                  | string | '{{ lookup("env", "SN_USERNAME") }}' |                                         |
| sn_password          | yes       | sn password                  | string | '{{ lookup("env", "SN_PASSWORD") }}' |                                         |
| sn_instance          | yes       | sn instance                  | string | cncdev                               |                                         |
| vtb_board            | yes       | vtb board specific sys_id    | string | bf60757cdbd549108ec3aa1d139619c8     | This is for the Infra Request vtb board |
| vtb_lane             | yes       | vtb lane on the board sys_id | string | 548075bcdbd549108ec3aa1d139619af     | This is for the land on vtb board       |
| service_offring      | yes       | specific SO name             | string | "IT Service Design"                  |                                         |
| source_justification | yes       | specific source justificatio | string | "Application - Enhancement"          |                                         |
| cmdb_ci              | yes       | needs a CI attached          | string | "ServiceNow Service Design"          |                                         |
| assignment_group     | yes       | group assigned to            | string | "IT-Server Windows DevOps"           |                                         |
| assigned_to          | yes       | whom to assign to            | string | jamdean                              |                                         |

## CLI example(s)

```yaml
- hosts: localhost
  roles:
    - name: Launch Role to create change request
      include_role:
        name: service_design_change
      vars:
        sn_instance: "cncdev"
```
## Authors

- James Dean
