

- remove all replace() hacks in query.ts
- test "is true" vs "is not false" (the latter selects nulls) / same for "is false" vs "is not false"
- test that "a is true is false" returns nulls like "is not true"
      => is also equivalent to "a is true is not true"

- UT: "select * from tbl where id=null"  => MUST RETURN NOTHING ! ... with or without indexes.
- UT: "select * from tbl where id is null"  => MUST RETURN NULL VALUES ! ... with or without indexes
- UT: check that throws ambiguous column: "select x.a from (select val1 as a, val2 as a from tbl) x;"