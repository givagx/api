# EduFocal API
A REST api for EduFocal data; includes:
- Questions
- Tests
- Courseworks
- Users
- Schools
- Answers



## Questions
* Create
* List by (teacher, subject, topic, id, list of ids, parent_id)



/questions
/questions/id/answers

/teachers
/teachers/id/questions

/subjects
/subjects/id/questions

/topics
/topics/id/questions
/topics/id,id,id/questions


/messages
/users/id/messages
/messages/id,id,id


Want to use GUIDs for all resources. Will have to plan and implement a migration from the existing integer-based
IDs to guids.

A suggestion?
1. Add uid column to all tables
2. Run migrations to set all these new uids
3. Add foreign key columns for these new uids in corresponding tables, such as (topic_uid)
4. Update all topic_uids to match the primary keys by cross-referencing with the integer-based ids
5. Set uid keys as primary and foreign keys and remove contraints from integer-based keys
6. Drop the integer-based ids and rename all uid columns to be id (and topic_id, respectively)
7. Implement Eloquent-based models that support uid keys naturally

Steps 1 to 6 should be automated and repeatable as a migration step.

Build the new API based on these guid keys.
