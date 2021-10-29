# oracle-query-rows-to-columns
Oracle query rows to columns

1. create table
```
create table sklh_tgh(sekolah varchar2(20), tahun_pbyr number(4), jml_tgh number);
```

2. insert data
```
insert into sklh_tgh values ('SD',2018, 5000000);
insert into sklh_tgh values ('SD',2019, 6000000); 
insert into sklh_tgh values ('SD',2020, 8000000);
insert into sklh_tgh values ('SD',2021, 10000000);
insert into sklh_tgh values ('SMP',2019,7000000);
insert into sklh_tgh values ('SMP',2020,7500000);
insert into sklh_tgh values ('SMP',2021,5500000);
insert into sklh_tgh values ('SMA',2021,20000000);
```

3. query rows
```
select * from sklh_tgh;

output:
SEKOLAH 	     TAHUN_PBYR    JML_TGH
-------------------- ---------- ----------
SD			   2018    5000000
SD			   2019    6000000
SD			   2020    8000000
SD			   2021   10000000
SMP			   2019    7000000
SMP			   2020    7500000
SMP			   2021    5500000
SMA			   2021   20000000

8 rows selected.
```

4. query rows to columns
```
select * from sklh_tgh
    pivot (
    min(jml_tgh)
    for tahun_pbyr in ('2018','2019','2020','2021');
    
output:
SEKOLAH 		 '2018'     '2019'     '2020'	  '2021'
-------------------- ---------- ---------- ---------- ----------
SD			5000000    6000000    8000000	10000000
SMP				   7000000    7500000	 5500000
SMA							20000000

SQL>
```
