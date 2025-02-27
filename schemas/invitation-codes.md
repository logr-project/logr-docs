**Table Name:** invitation_codes

| Column Name | Type            | Primary Key  | Unique | Not Null | References    | On Update | On Delete | Constraint  | Check                    |
| ----------- | --------------- | ------------ | ------ | -------- | ------------- | --------- | --------- | ----------- | ------------------------ |
| id          | UUID            | Primary Key  |        |          |               |           |           |             |                          |
| code        | varchar(16)[^1] |              | Unique | Not Null |               |           |           | code_length | OCTET_LENGTH(code) = 16  |
| profile_id  | UUID            |              |        | Not Null | profiles(id)  | Cascade   | No Action |             |                          |
| used_by_id  | UUID            |              | Unique |          | profiles(id)  | Cascade   | No Action |             |                          |
| *Timestamps With Timezone*                                                                                                                        |

[^1]: Postgres checks for *character length* or *graphemes* but for `code` we also mean this limit as *bytes* or *OCTET_LENGTH*: `"OCTET_LENGTH(code) = 16"`
