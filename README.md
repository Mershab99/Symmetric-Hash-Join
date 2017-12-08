# Symmetric-Hash-Join
CSI3130 Final project. change hash join to Symmetric hash join with in PostgreSQL 8.1.7

## TODO
- [ ] Make a (more) proper readme
- [x] Change optimizer so that both the inner and the outer relations are first processed by hash nodes before being processed by the hash join operator.
    - Relevant Files:
        - [createplan.c](./createplan.c)
- [x] Modify the hashing algorithm to support pipeline execution instead of the multi-tuple execution mode that is currently implemented (*ExecHash* Function)
    - Relevant Files:
        - [nodeHash.c](./nodeHash.c)
- [x]  Disable the use of multiple batches. In other words assume that the whole hash table consists of one batch that is resident in the memory for the duration of the join processing.
    - Relevant Files:
        - [nodeHashjoin.c](./nodeHashjoin.c)
- [x] Modify the structure of *HashJoinState* to support the symmetric hash join algorithm. Replicate the existing structures to support bi-directional probing.
    - Relevant Files:
        - [execnodes.h](./execnodes.h)
- [ ] Replace the hash join algorithm with the symmetric hash join algorithm. After completing the join operation, print the number of resulting tuples that were found by probing the inner hash table and outer has tables repsectively.
     - Relevant Files:
        - [nodeHashjoin.c](./nodeHashjoin.c)
- [ ] Disable other join operatiors to force the symmetric hash join operator.
    - Relevant Files
        - [postgresql.conf](./postgresql.conf)
          Usually found in the data directory. See [link](https://www.postgresql.org/docs/9.3/static/config-setting.html).
