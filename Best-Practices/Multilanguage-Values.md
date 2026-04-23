# Multilanguage Values

# Best Practices for Multilanguage Values

Organizations operating across regions and markets often need to manage master data values in multiple languages - for example, product names, descriptions, or classifications that must be presented correctly to users, customers, and systems in different locales.  
Common challenges include:

* Storing multilingual text without losing characters or corrupting data
* Avoiding schema changes every time a new language is introduced
* Governing translations independently from core master data
* Ensuring downstream systems receive the correct language values with appropriate fallback behavior

While Profisee natively supports multilingual text storage through Unicode character sets, successfully managing multilingual values at scale requires a deliberate design pattern. This article describes the recommended Profisee design pattern for multilingual values, which addresses these challenges using standard Profisee modeling and governance capabilities.

This article explains how Profisee attributes can be used to store, manage, and govern attribute values in multiple languages, what is possible with the Profisee data model, and common implementation patterns to achieve multilingual support in Master Data Management (MDM) solutions. It is intended for data architects, MDM administrators, and implementation teams designing global or multi regional solutions.

### Background: Unicode and Multilingual Data in Profisee

Profisee stores attribute values using Unicode character sets, which means the platform natively supports:

* Non Latin alphabets (for example, Chinese, Japanese, Korean)
* Right to left languages (such as Arabic and Hebrew)
* Accented and extended characters used across European languages
* Mixed language content within the same data model

Because Profisee uses Unicode at the storage level, any string attribute can technically contain values from any language without schema changes or special configuration.  
However, while Unicode enables storage of multilingual text, governing, organizing, and consuming multilingual values effectively requires intentional data modeling. The remainder of this article focuses on how to design Profisee models to manage multilingual data in a scalable and governed way.

### What Is Possible with Profisee Attributes

Because Profisee uses Unicode character encoding, attributes are not limited to a single language or alphabet. This allows Profisee models to:

* Store multiple language representations of the same business concept
* Use the same attribute type across regions and markets
* Ingest multilingual data from upstream systems without transformation
* Publish multilingual values to downstream systems

Profisee does not treat language as a special attribute type. Instead, multilingual support is achieved through standard modeling patterns using entities, attributes, and relationships, with language treated as business data rather than metadata.  
Using Profisee, you can store multiple language versions of an attribute value, govern translations independently (approval workflows, stewardship), track which language is authoritative vs. translated, serve different language values to consuming systems and add additional languages over time without redesigning the core domain model.

## Design Options for Multilingual Attributes

### Option 1: Language-Specific Attributes (Not Recommended at Scale)

Example:

* Product Name\_EN
* Product Name\_FR
* Product Name\_DE

Pros

* Simple to understand
* Easy for small, fixed language sets

Cons

* Poor scalability
* Schema changes required for each new language
* Difficult to govern consistently
* Results in sparse and difficult to maintain models

When to use

* Very small implementations
* One or two fixed languages only

Although Unicode allows these attributes to store multilingual text, this pattern does not scale well in multi-locale solutions.

### Option 2: Translation (Child) Entity Pattern (Recommended)

This is the recommended pattern for managing multilingual values in Profisee.  
Unicode enables each translated value to be stored correctly, while the data model controls how those values are organized and governed.  
Conceptual Model is a Base Entity and a Translation Entity that represents the language neutral or default record (often in a primary or global language). Stores translated attribute values, each associated with a specific language. Example:  
Entity: Product

* Product ID
* Default Product Name
* Brand
* Category

Entity: Product Translation

* A domain-based attribute (DBA) to the Product entity which is the foreign key to the base entity
* Language Code as a DBA (for example, en-US, fr-FR)
* Product Name
* Product Description

This pattern ensures each Product can have multiple translation records, one per language.

### How This Design Pattern Works in Profisee

1. Create a Translation Entity  
Create a separate entity to store language specific values.  
Typical characteristics:

* A foreign key to the base entity
* A language identifier
* One or more translatable attributes (stored as Unicode strings)

2. Model the Relationship  
Create a one to many relationship from the base entity to the translation entity. Example:

* Product → Product Translation

3. Use a Language Reference Entity (Optional but Recommended)  
Rather than storing raw text language codes:

* Create a Language reference entity
* Store standardized ISO language codes and display names
* Enforce referential integrity across translations

This improves consistency, reporting, and governance.

### Governance and Stewardship Considerations

Because translated values are stored as first class attribute data (not metadata), you can:

* Apply separate workflows for translated values
* Assign regional stewards or translators
* Validate the presence of required languages
* Track translation completeness by market or region
* Distinguish authoritative values from translated values

Unicode storage ensures all languages are handled correctly, while Profisee governance ensures they are managed correctly.

### Consumption Patterns

Downstream System Access - consuming systems can:

* Request a specific language
* Fall back to a default language when needed
* Receive all available translations

Many implementations create:

* Language filtered integration views
* APIs that request translations dynamically by language code
* Flattened language outputs for systems that expect pivoted structures

## Best Practices Summary

* Rely on Unicode support for multilingual text storage
* Use a translation entity instead of language specific attributes
* Treat language as reference data, not schema structure
* Govern translations independently from core master data
* Design consumption patterns with fallback logic

## Conclusion

Profisee’s use of Unicode character sets enables native storage of multilingual attribute values across all supported entities. By applying this Profisee design pattern for multilingual values - centered on translation entities and language reference data - organizations can build scalable, governed, and future proof multilingual MDM solutions without relying on language specific attributes or schema changes.