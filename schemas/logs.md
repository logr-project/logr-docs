**Table Name:** logs

| Column Name  | Type                     | Primary Key | Not Null | Default | References   | On Update | On Delete | Unique | Constraint             | Check                                                               |
| ------------ | ------------------------ | ----------- | -------- | ------- | ------------ | --------- | --------- | ------ | ---------------------- | ------------------------------------------------------------------- |
| id           | UUID                     | Primary Key |          |         |              |           |           |        |                        |                                                                     |
| title        | varchar(50)              |             | Not Null |         |              |           |           |        |                        |                                                                     |
| slug         | varchar(50)              |             | Not Null |         |              |           |           |        | slug_contains          | OCTET_LENGTH(slug) >= 1                                             |
| quick_view   | text                     |             | Not Null |         |              |           |           |        | quick_view_min_and_max | OCTET_LENGTH(quick_view) >= 3 AND OCTET_LENGTH(quick_view) <= 4096  |
| content      | text                     |             | Not Null |         |              |           |           |        | content_min_and_max    | OCTET_LENGTH(content) >= 3 AND OCTET_LENGTH(content) <= 61440       |
| logged_at    | timestamp with time zone |             |          |         |              |           |           |        |                        |                                                                     |
| discoverable | boolean                  |             | Not Null | false   |              |           |           |        |                        |                                                                     |
| space_id     | UUID                     |             | Not Null |         | spaces(id)   | Cascade   | Cascade   |        |                        |                                                                     |
| *Timestamps with Timezone*                                                                                                                                                                                                |

+ Composite Unique Constraint: `UNIQUE (space_id, slug)`