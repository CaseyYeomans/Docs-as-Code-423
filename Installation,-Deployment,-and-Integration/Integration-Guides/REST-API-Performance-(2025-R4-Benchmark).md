# REST API Performance (2025 R4 Benchmark)

# Profisee REST API Performance Test Results

---

### Approach & Environment

Profisee used a dedicated environment to perform performance testing on the software versions shown below. The Profisee software was isolated from the test harness so that the testing workload did not impact the performance.

|  |  |
| --- | --- |
| Profisee Application Server | 256 Memory, 32 Cores, High Speed Drives |
| Database Server | 256 Memory, 32 Cores, High Speed Drives |
| Test Server | 256 Memory, 32 Cores, High Speed Drives |
| Document Version | 1.0 |
| Prepared For | Performance Validation |
| Environment | Azure IaaS – High Memory / High Core Configuration |

### Data Configuration

|  |  |
| --- | --- |
| Data Shape | 120 Attributes |
| Matching Strategy | Standard party data match |
| Match Passes | 5 |
| Matching Attributes | ID, DOB, Address, Name, etc. |
| Source Records | 15 Million |
| Source Systems | 4 |
| Batch Sizes | 1000 |

## Performance Results

### **Question 1 - Process X Million Records in Under 1 Hour**

If this is purely a data loading question, we do not differentiate between loading matching records and loading any other type of records. If the requirement refers specifically to matching and creating golden records, refer to Question 2 performance results.

| Metric | Value |
| --- | --- |
| Records Per Second | 290 |
| Records Per Hour | 1,044,000 |

Calculation: 290 × 60 × 60 = 1,044,000 records per hour

### **Question 2 - Process X Thousands of Match and Merge Rules**

**Test Execution Summary**

| Metric | Value |
| --- | --- |
| Source Records Processed | 15,000,000 |
| Total Processing Time | 16.1 Hours |
| Match Groups Created | 3,700,000 |
| Total Resulting Records | 18,750,000 |

**Performance Results**

| Metric | Value |
| --- | --- |
| Records Per Second | 323 |
| Records Per Hour | 1,162,800 |

Calculation: 323 × 60 × 60 = 1,162,800 records per hour

### **Question 3 - API / Database Read Performance**

\*(TBD — e.g., Read performance of X Golden Records in under X minutes)\*  
From a read perspective, we do not differentiate between a golden record read and any other data read.

| Metric | Value |
| --- | --- |
| Records Per Second | 1,341 |
| Records Per Hour | 4,827,600 |

Calculation: 1341 × 60 × 60 = 4,827,600 records per hour

### **Question 4 - Message Queue Performance**

\*(TBD — e.g., Publish performance of X Golden Records per second)\*  
If publishing new records → Refer to \*\*Question 1\*\* performance.  
If updating matched records → Standard batch update process.  
If matching-specific publishing → Refer to \*\*Question 2\*\* performance.

| Metric | Value |
| --- | --- |
| Records Per Second | 199 |
| Records Per Hour | 716,400 |

Calculation: 199 × 60 × 60 = 716,400 records per hour

### **Question 5 - MDM Rules Engine**

Process X Thousands of Match and Merge Rules    
Status: TBD - Additional performance metrics will be added here once available.

**Summary**

| Category | Records Per Second | Records Per Hour |
| --- | --- | --- |
| Data Load | 290 | 1,044,000 |
| Match & Merge | 323 | 1,162,800 |
| API / DB Read | 1,341 | 4,827,600 |
| Message Queue | 199 | 716,400 |

### Scenario Performance Graphs

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ic450a58b0994eacc.png)

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i997d02184b7d057.png)

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i26d9a43b399d9590.png)

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-if983bb0ae7982992.png)![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i1441dcab2601d743.png)![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i5971deacf7c036e0.png)![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ie6411b9d200099d6.png)![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ie456555af2ac0404.png)![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i483efa29b35f118a.png)![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ib39ba17fcd47502f.png)![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i604929b7887395bb.png)![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i97da55f662b50976.png)![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-id6e6af068d07f254.png)![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-iddab99517baeb0db.png)![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i295ad2c298dd4cd6.png)![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i8c340a44c17b22ca.png)![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i661c85b0d1716703.png)![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i1baaafb134000caa.png)![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i402fe1b5ceceb9b1.png)![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i3a86b359409a4cbc.png)![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i88c8df402a02d810.png)