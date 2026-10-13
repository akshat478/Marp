# Marp
An interactive map app that indexes 4,000 real OpenStreetMap nodes of New Delhi in an R-tree, then compares it live against brute-force search on every pan and zoom. It includes a from-scratch Guttman R-tree, tested with 1,831 checks, that ran 500 queries on 100k items about 280x faster.
