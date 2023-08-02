# service_design_email

## Summary

This will send the email to the recipient list using a jinja2 template for the html.

## Requirements

- community.general

## Variables

| Variable             | Required? | Description                  | Type   | Example                                                       | Notes |
| -------------------- | --------- | ---------------------------- | ------ | ------------------------------------------------------------- | ----- |
| cc_field             | yes       | list of email addresses      | list   | - email@centene.com                                           |       |
| subject_field        | yes       | text to go in subject field  | string | "Change Request info for change                               |       |
| wording              | yes       | text to go in email body     | string | "Here is the Change Request number:"                          |       |
| header_results       | yes       | image for the header         | string | "{{ lookup('file', 'files/CenteneTechnologiesHeader.png') }}" |       |
| footer_results       | yes       | image for the footer         | string | "{{ lookup('file', 'files/CenteneTechnologiesFooter.png') }}" |       |

## CLI example(s)

```yaml
- hosts: localhost
  roles:
    - name: Launch Role to email the change request info
      include_role:
        name: service_design_email
      vars:
        cc_field:
          - email1@centene.com
          - email2@centene.com
```
## Authors

- James Dean
