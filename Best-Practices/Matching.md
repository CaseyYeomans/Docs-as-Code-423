# Matching

# Best Practices for Matching

### Matching / Identity Resolution / Deduplication

1. Use a single matching strategy per entity whenever possible for the cleanest design, predictable behavior, and best performance. Multiple strategies should be used only when absolutely necessary (e.g., householding scenarios) because they introduce more complex stewardship, processing order‑dependency and reduced performance.
2. Determine the attributes that uniquely identify your data.
3. Design attribute sets logically and minimize their count. Use logical groupings of attributes (“control attributes”) to form effective sets.
4. Avoid too many attributes per set. More attributes make for fewer matches and slower processing.
5. Avoid attributes with very high blank percentages (~80%+) because they add no matching value.

#### Person Example

i.    Set 1 = SourceID, SSN, Drivers License, Name (First + Last+Suffix),   
ii.    Set 2 = Address (Address 1 + Zip+ Suite Number),   
iii.    Set 3 = Phone, Email, DOB. Suite Number, Gender etc.

#### Business or Organization Example

i.    Set 1 = Name, Tax ID  
ii.    Set 2 = Duns Number  
iii.    Set 3 = Address, State or Province, Country

#### Product Example

i.    Set 1 = Identifier, Name, Type  
ii.    Set 2 = Description, Type

6. Attribute set order is important – put the set that produces the most matches first.

7. Profile the data to see which attributes are always populated and which have blank values.

8. Which one of these attributes must match exactly for a duplicate record (SourceID, SSN, Drivers License, Phone, Email, Zip) and which ones can be similar but not exactly the same? (Name, Address)

9. Is there a single piece of data that guarantees the record is duplicated or not? (SourceID, SSN, TIN, Drivers License).

10. Are there 2 pieces of data that, when combined, guarantee the record is a duplicate? (Name+Address, Name+Email, Name+Phone)

11. If there are cases when records are matched together but they should be separate (aka overmatching), what attribute can be used to differentiate between them? (Jr/Sr - Suffix/DOB, Twins - First Name Exact/Gender, Business in same building - Suite Number). For those attributes how would you handle blanks? (Blank = Value or Blank <> Value, Value never equals Blank).

12. Start simple, iterate frequently, test comprehensively.

a.    Begin with a simple strategy.  
b.    Use short iterative cycles.  
c.    Re-run all records through the updated strategy after each design change to avoid over‑engineering early and missing unexpected data patterns.  
d.    Avoid assumptions and validate all strategy adjustments through structured testing - even small changes can significantly alter match results and performance degradation is common when testing is skipped.

### Golden Records

13. Decide which attributes should be populated on the golden record. Attributes that only belong on source records should not be promoted. (Source System, Source ID, Source Last Changed Date). Individual status attributes should not be used. (AV status, Active status, etc.).

14. Create Survivorship sets by grouping attributes into logical pieces of data, e.g. Address = Address 1 + Zip+ Suite Number.  Name = First Name + Middle Initial + Last Name + Name Suffix.

15. Filter the attributes where the same criteria will be used to pick the best value from the source system. Do you want to filter out some records to never select values from them?

16. Order the source records that have a higher priority over other source records. You can create one or more attributes to identify priority and must ensure all source records have assigned values.

17. Promotion Criteria allows you to choose between multiple values.

a.    The completeness of the set of values based on the average % of each attributes completeness percentage (Attribute length/Value number of characters = %).  
b.    The set of values that repeats the most times in the cluster.  
c.    The first source record created or the last source record updated.

### Stewardship Options

18. Enable the stewardship features you want visible to the data stewards.

19. The Merge function applies to records from one external system.

20. Merges will only take effect in the system when you publish changes to the external systems via an integration.

### Processing Options

21. Enable the strategy and choose the automated processing options that make sense for your scenario.

a.    Do you want to automatically match new records?   
b.    Do you want to automatically perform survivorship on changed clusters?

22. Identify representative test data populations of between 1% and 10% of the total record volume. Use real data for quality testing. Using smaller data sets will allow you to build strategies and test incrementally. We want to avoid the situation where you start processing all data with no idea of the expected time of completion.

23. Mark your test data with a ‘temporary’ attribute for filtering in the strategy – this helps ensure you are always working with the same input records.

### Clearing Results

24. Use a clearing-only strategy first.

25. Stage deletes in batches of 50K.

26. Rebuild the matching index afterward (critical for performance).

### Performance

27. Keep matching strategies as simple and singular as possible, build them on strong attribute design, enforce continuous validation, and avoid architectural or process decisions that add unnecessary complexity and compute work.

28. Verify the hardware resources meet/exceed recommendations in the system requirements document.

29. Configure the cores on the cluster server. Configure the server’s total minus 2 for matching. For example, if you have 8 CPU cores, you will want to specify 6 for matching.

30. If you have multiple Profisee processing servers (aka a Profisee cluster) you may assign each strategy to a server to minimize the downtime during index rebuilds. You can only run one matching strategy at a time. Check with your Customer Success Manager for information on clusters and licensing.

31. For the best performance, attribute processing order is important inside each set   
a.    Highly distinct, exact attribute first (Email, Phone, SSN, etc.)   
b.    Medium distinct (>1000), exact attribute second (DOB, ZIP, City, etc.)   
c.    High distinct, fuzzy/token attributes third (Name, Address, etc.)   
d.    Low distinct ( 0.8; Address Line 1 > 0.8; First Name > 0.7)

32. For the fastest possible performance, configure Survivorship Options like this:  
a.    Only update clusters that have changed – YES   
b.    Update counts on golden records - YES   
c.    You should consider not creating Masters for Unique records. Leaving this unchecked can save you a lot of extra golden records in relation to your Profisee licensing limits. It will save significantly in terms of processing records for survivorship. However, many customers prefer a Golden Record identifier to be present for every record.

### Synonyms

33. Synonyms apply to matching, not survivorship, and they do not change the record value. Minimize the use of synonym lists to avoid additional processing work for the server.

34. You may have to use them to handle extra characters that do not belong in your data. (.,!?/-). Are there values that appear in records that make them look similar when they should not be? (False positives). Are there substitute/default values entered by the users to overcome missing information? (SSN-111-11-1111, DOB-1/1/1900, Phone - 111-1111-1111).

35. Use synonym lists only on attributes that need it, not on standardized or dirty data.  
d.    For standardized attributes there should be no need.   
e.    Avoid nickname synonym lists as the temptation is to grow the list and solve for typographical and spelling differences (which fuzzy matching will usually overcome).  
f.    Avoid lists with over 50 values.  
g.    Remove the MaestroDefault synonym list from the attributes that don’t need it.

This guide was published on 01/29/2026 and modified on 01/29/2026.