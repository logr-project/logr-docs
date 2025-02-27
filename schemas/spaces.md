**Table Name:** spaces

| Column Name  | Type        | Primary Key | Not Null | Default | References   | On Update | On Delete | Unique | Constraint      | Check                             |
| ------------ | ----------- | ----------- | -------- | ------- | ------------ | --------- | --------- | ------ | --------------- | --------------------------------- |
| id           | UUID        | Primary Key |          |         |              |           |           |        |                 |                                   |
| handle       | varchar(15) |             | Not Null |         |              |           |           | Unique | handle_min      | OCTET_LENGTH(handle) >= 4         |
| name         | varchar(25) |             | Not Null |         |              |           |           |        | name_min        | CHAR_LENGTH(name) >= 4            |
| description  | text        |             | Not Null |         |              |           |           |        | description_max | OCTET_LENGTH(description) <= 4096 |
| discoverable | boolean     |             | Not Null | false   |              |           |           |        |                 |                                   |
| profile_id   | UUID        |             | Not Null |         | profiles(id) | Cascade   | Cascade   |        |                 |                                   |
| *Timestamps with Timezone*                                                                                                                                          |