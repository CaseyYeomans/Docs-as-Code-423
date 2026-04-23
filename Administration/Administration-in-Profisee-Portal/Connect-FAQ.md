# Connect FAQ

* Can we configure Connect strategies to be event-triggered?

Yes, strategies can be triggered by data changes and scheduled and on-demand data flows.

Connect is easier to configure than Real-Time Event Processing and offers additional options for triggering.  Connect is the recommended approach.

---

* What is the difference between the Webhook Subscriber (Real-Time Event Processing) and the Webhook Service Provider (Connect)?

Connect provides a **streamlined, no-code solution** for connecting to webhooks without setting up Real-Time Event Processing scenarios.

---

* I saw a warning message logged to the *logging.tSystemLog* table by Connect (assemblyname =Profisee.Platform.Services.ConnEx.Api) that said "No records were published." What does this mean?

There are two scenarios that could cause this error to occur:  
  
1) The output attributes on the connect strategy were not configured correctly. An administrator should confirm the strategy works as expected for one record.  
  
2) The strategy ran, but there was nothing to do. As an example, an OpenAI strategy that parses unstructured data might have been triggered, but there was no unstructured data to act against, so no change was published.

* My database service provider is displaying records incorrectly, or failing to load some records. What could be causing this?

Database service providers (such as SQL, Snowflake, Databricks, and others) sort records for paging via a primary key or identity column. If your source database does not contain these, it sorts by the first available column by default. This can create paging issues if this first column is not unique, since each page may have overlapping records.

---

* Can Connect work with metadata like it does with master data?

Connect is currently designed to work with record data only, not solution artifacts or metadata.

* Does Connect work with File Attachments?

Connect can be used with some providers (like ADLS) that use files, but Connect's architecture is designed for working with text or structured data (not files attached to a record in an entity).