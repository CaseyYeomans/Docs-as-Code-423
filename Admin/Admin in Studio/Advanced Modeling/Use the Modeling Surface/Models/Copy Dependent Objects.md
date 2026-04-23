# Copy Dependent Objects

Create additional objects to handle dependencies in an object copied or moved from one model to another model, or even from one area of a model to another. For example, if you copy an entity containing two domain-based attributes to a different model, Advanced Modeling copies the entities referenced by those domain-based attributes to the new model as well.

Profisee copies dependent objects as follows:

| When you perform this copy procedure: | The application does this if there are dependent objects: |
| --- | --- |
| **Entity from Model A to Model B** | Prompts the user to copy any dependent objects. Any entities referenced by domain-based attributes are automatically included. Referenced entities are included by minimal reference only, rather than copied in their entirety. |
| **Attribute to an entity in a different model** | Copies any attributes and any referenced entities for domain-based attributes (no prompt) |