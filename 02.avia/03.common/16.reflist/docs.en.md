---
title: RefList
taxonomy:
    category:
        - docs
    author:
        - KFimchenko
---

### The list of Identifiers

This type is the array of Ref fields, used to send a list of identifiers of other objects.

#### Format description

-   **Ref** - pointer to the ID of the object specified in the parent field

#### Sample

The **Ref** field indicates the object from the parent field, in this example it is the passenger.

```xml
<TravellerRef>
  <Ref>1</Ref>
  <Ref>2</Ref>
</TravellerRef>
```