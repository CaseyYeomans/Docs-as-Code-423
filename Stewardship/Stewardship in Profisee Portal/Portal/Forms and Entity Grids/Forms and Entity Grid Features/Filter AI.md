# Filter Using AI

A Profisee instance that has been [configured for OpenAI integration](https://support.profisee.com/wikis/profiseeplatform/open_AI) can use OpenAI to help filter attributes in the portal. These settings can be configured though Profisee FastApp Studio, or in the portal via **Settings** > **OpenAI Admin**(must be a Super Administrator to configure).

With OpenAI filtering, users can use plain language to fetch attributes that meet their desired criteria. Though there are recommended best practices for this feature, any creative plain language application will yield results.

To access the OpenAI filter, navigate to an entity grid and enter the [Custom Filter](https://support.profisee.com/wikis/profiseeplatform/filter_and_sort) view. The OpenAI Beta control appears if configured by a FastApp Studio admin.
![](https://Profisee.magentrixcloud.com/sys/staticasset/read/file-ie6c2c1efe990bf15.png)Here, you can type within the **Filter with natural language**field to automatically build expressions using the OpenAI copilot. To get the best results for straightforward uses, we recommend formatting your query like a regular filter expression. For example, writing the prompt: "Color is red, blue, or yellow and cost is more than $300" would automatically build the expression *Color Equals Red OR Color Equals Blue OR Color Equals Yellow AND Cost Is Greater Than 300*.

However, for complex use cases, you can implement more creative language to get results using terms that are not expressly used in the attribute. For example the prompt, "Expensive bikes that are a primary color" might also return the expression: *Color Equals Red OR Color Equals Blue OR Color Equals Yellow AND Cost Is Greater Than 300*.

The regular Filter/Sort dialogue, as well as the Quick Filter, can still be used as normal while the OpenAI filter is configured.