**Table Name:** profiles

| Column Name | Type        | Primary Key | Not Null | References | On Update | On Delete | Unique | Constraint | Check                       |
| ----------- | ----------- | ----------- | -------- | ---------- | --------- | --------- | ------ | ---------- | --------------------------- |
| id          | UUID        | Primary Key |          |            |           |           |        |            |                             |
| handle      | varchar(15) |             | Not Null |            |           |           | Unique | handle_min | OCTET_LENGTH(handle) >= 4   |
| name        | varchar(25) |             | Not Null |            |           |           |        | name_min   | CHAR_LENGTH(name) >= 4      |
| story       | text        |             | Not Null |            |           |           |        | story_max  | OCTET_LENGTH(story) <= 4096 |
| user_id     | UUID        |             | Not Null | users(id)  | Cascade   | Cascade   | Unique |            |                             |
| *Timestamps with Timezone*                                                                                                                  |