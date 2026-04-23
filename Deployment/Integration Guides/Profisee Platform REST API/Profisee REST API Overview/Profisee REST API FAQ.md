# Profisee REST API FAQ

The following are answers to frequently asked questions about the Profisee REST API:

- How should I format datetime (DTM) values in my REST request?

Without a qualifier, datetimes are assumed to be in UTC. The following represents how they are stored in the database before the DTMs are converted to local time (based on your timezone):

| | |
| --- | --- |
| **JSON Body Value** | **Database DateTime Value** |
| "2001-05-16T13:12:00" | 21-05-16 13:12:00.0000000 |
| "2001-05-16T13:12:00Z" | 21-05-16 13:12:00.0000000 |
| "2001-05-16T13:12:00+04" | 21-05-16 09:12:00.0000000 |
| "2001-05-16T13:12:00-04" | 21-05-16 17:12:00.0000000 |