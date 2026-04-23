# REST Performance

The following data comes from internal testing and displays the average performance metrics for REST GET requests. Note that these testes were performed in Profisee version 2023.R1, but should be comparable for all current releases.

### GET

This data shows that increasing the time interval helps when adding more users. For the tested environment size, the most efficient interval was ~10-18 seconds between calls and prevented calls from failing. Calls began to fail below 10 second intervals. When more users are added to an environment, more ramp-up time should be allocated.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i46ea40fa8df72154.png)

### POST

Testing shows that lowering request size helps with throughput when processing single or few calls. When processing loads of 1 million or greater, it is faster to use a larger request size.

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i40d42e57fef49169.png)

![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-i554be99d37245feb.png)