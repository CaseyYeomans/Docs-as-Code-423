# Batching Guidance for Large Volume REST API Calls

When inserting records into an entity, users may often encounter timeout issues when updating a large number of records. This issue can be resolved by inserting records in batches, otherwise known as **Batching** records. There is no one-size-fits-all solution to batching records; however, the following findings and recommendations may assist in determining the ideal batch sizes for your data.

### Findings

The following tests were performed on the same entity with about 200 attributes per record. The tests were performed in a 32GB RAM, 4 cores, 8 logical processors CPU, with both Profisee Service Host and SQL server Service running in the same environment.

| | | | | |
| --- | --- | --- | --- | --- |
| **Test Number** | **Request Size (Records sent in request)** | **Total Records Sent** | **Total Run Time** | **Average Response Time (in seconds)** |
| **Test 1** | 50,000 | 1,000,000 | 1h 41min 31sec | 304.5894 |
| **Test 2** | 50,000 | 12,000,000 | 22h 46min 49sec | 341.66 |
| **Test 3** | 10 | 1,000,000 | 17h 43min 41sec | 0.668 |

Comparing Test 1 to Test 3, the total amount of records sent per request in the larger batch of 50k records per request would be the recommended batch size to send since it took only 20 POST calls to send 1M total records, compared to the 10 records request that needed 10k POST calls to send the same amount 1M total records.

It also took less time for the 50k records request (1h 41min) than the 10 records requests (17h 43min). The time on the Test 3, the smallest batch size sending only 1M total records, compares more to the time it took Test 2 to send 12M records.

Comparing Average Response Time, the request size of 10 was faster on average because the request itself has fewer records to send, but this is offset by the amount of total request needed to send 1M total records. Also, keeping the request size at 50k records per request shows that average response time was around the 5min timeout times, meaning most users would not need to increase the default 5min timeout variable in the config file.

### General Recommendations

We recommend that users make a body request of about 50k records--making larger request sizes rather than smaller request sizes--since the smaller request size takes more calls and time to achieve the same total records to send. Entity wideness (or number of attributes) will also impact the performance and size recommendation.