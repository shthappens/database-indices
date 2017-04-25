```
SELECT name FROM ingredients WHERE name ILIKE '%brussels sprout%';
```
```
SELECT count(*) FROM ingredients WHERE name ILIKE '%brussels sprout%';
```
```
SELECT count(*) FROM ingredients WHERE unit ILIKE '%gallon%' AND name ILIKE '%brussels sprout%';
```
```
SELECT count(*) FROM ingredients WHERE unit ILIKE '%gallon%' AND name ILIKE '%brussels sprout%' OR name ILIKE '%j%';
```
```
QUERY PLAN
-------------------------------------------------------------------------------------------------------------------
 Aggregate  (cost=2152.32..2152.33 rows=1 width=8) (actual time=192.585..192.585 rows=1 loops=1)
   ->  Seq Scan on ingredients  (cost=0.00..2152.00 rows=129 width=0) (actual time=3.408..192.382 rows=88 loops=1)
         Filter: (((unit)::text ~~* '%gallon%'::text) AND ((name)::text ~~* '%brussels sprout%'::text))
         Rows Removed by Filter: 99912
 Planning time: 0.352 ms
 Execution time: 192.636 ms
(6 rows)
```
```
QUERY PLAN
-------------------------------------------------------------------------------------------------------------------
Aggregate  (cost=2152.32..2152.33 rows=1 width=8) (actual time=190.672..190.672 rows=1 loops=1)
->  Seq Scan on ingredients  (cost=0.00..2152.00 rows=129 width=0) (actual time=2.427..190.470 rows=88 loops=1)
Filter: (((unit)::text ~~* '%gallon%'::text) AND ((name)::text ~~* '%brussels sprout%'::text))
Rows Removed by Filter: 99912
Planning time: 0.255 ms
Execution time: 190.720 ms
(6 rows)
```
