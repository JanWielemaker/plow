  - tnot/1: can never be called on a tabled goal with answer subsumption
    because its argument must be ground and a call to a tabled goal
    with answer subsumption cannot be ground!

## Possible problem:

Looks like negation_suspend/3 calls

  - shift(call_info(Skeleton, tnot(Worklist)))
  - caught in moded_delim/5
  - creates suspension as used for moded tabling
  - dummy answer from negative_worklist() as pushed by
    tbl_put_moded_args() pushes ATOM_trienode
  - This causes completion_step/1 to restart the continuation
    using delim/4 instead of moded_delim/5
