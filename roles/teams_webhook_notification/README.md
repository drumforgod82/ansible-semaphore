# Role Name teams_webhook_notification

This will format a webhook notification into a card for a team chosen to recieve via webhook api endpoint
card_content.text is received as markdown language
limit of 10 on card_content.sections any larger drops the message from iOS and caps at 10 for desktop/web teams

## Requirements

- community.general

## Role Variables

| Variable              | Required? | Description                                       | Type       | Example                                      | Notes                                       |
| --------------------- | --------- | ------------------------------------------------- | ---------- | -------------------------------------------- | ------------------------------------------- |
| card_content.title    | Yes       | Top line in Teams notification                    | String     | this is the title of the card                |                                             |
| card_content.text     | Yes       | Section of text under title in Teams notification | String     | this is the text under the title of the card |                                             |
| color_choice          | No        | color choice of the notification                  | String     | 'red'                                        | Case insensitive, defaults to blue          |
| team_to_notify        | No        | team to notify                                    | String     | 'green_hornets'                              | Case insensitive, defaults to green_hornets |
| card_content.sections | No        | sections of the card below initial text           | dictionary |                                              |

## Dependencies

Collections:

- community.general

## Example Playbook

```yaml
- name: post to teams channel
  hosts: localhost
  gather_facts: false
  roles:
    - role: teams_webhook_notification
      vars:
        card_content:
          title: "Title Content passed from play into test role"
          text: "this is the **text** passed into the role from the play with {{ color_choice }} as color"
          # This portion can be safely commented out or added in as needed
          sections:
            - title: This section is passed in from the play and otherwise not enumerated
              facts:
                - name: account_name_example_1@domain.com
                  value: invalid
                - name: account_name_example_2@domain.com
                  value: success
                - name: account_name_example_3@domain.com
                  value: failed
        color_choice: "blue"
        team_to_notify: "green_hornets"
```

## License

BSD

## Author Information

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
