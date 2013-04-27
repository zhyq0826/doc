# SUNION *key1 key2 ... keyN*

**TIME COMPLEXITY**:
O(N) where N is the total number of elements in all the provided sets

**DESCRIPTION**:
Return the members of a set resulting from the union of all the sets hold at
the specified keys. Like in LRANGE the result is sent to the client as a
multi-bulk reply (see the protocol specification for more information). If just
a single key is specified, then this command produces the same result as
SMEMBERS.

Non existing keys are considered like empty sets.

**RETURN VALUE**:
Multi bulk reply, specifically the list of common elements.
