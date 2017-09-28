---
title: RefList
taxonomy:
    category:
        - docs
    author:
        - KFimchenko
---

### The list of Identifiers

This type is an array of fields Ref, used to send a list of identifiers of other objects.

#### Format description

-   **Ref** - the pointer to the identifier of the object specified in the parent field

#### Example

The Ref field indicates the object from the parent field, in this example it is the passenger.

```xml
<TravellerRef>
  <Ref>1</Ref>
  <Ref>2</Ref>
</TravellerRef>
```