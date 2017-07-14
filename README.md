Introduction
============

Fast DNS query tool. It can run multiple threads to query a single DNS server
very quickly.

Installation
============

Requires Python 3.5 or higher. Requires the `dnspython` library.

    $ /opt/lcogt-python35/bin/pvenv env
    $ source env/bin/activate
    $ pip install --upgrade pip && pip install -r requirements.txt
    $ ./dnsfast --help

Runtime Options
===============

Please see `dnsfast --help`:

    usage: dnsfast [-h] [-w WORKERS] [-q QUERY] [-c COUNT] [-d DELAY] [-s SERVER]
                   [-p PRINTEVERY]
    
    optional arguments:
      -h, --help            show this help message and exit
      -w WORKERS, --workers WORKERS
                            Number of workers to run in parallel
      -q QUERY, --query QUERY
                            Hostname to query
      -c COUNT, --count COUNT
                            Number of queries to run
      -d DELAY, --delay DELAY
                            Delay between each query (ms)
      -s SERVER, --server SERVER
                            Nameserver to query
      -p PRINTEVERY, --printevery PRINTEVERY
                            Print status updates every N queries


Example Output
==============

    $ ./dnsfast -q configdb.lco.gtn -c 10000 -p 1000 -s 172.16.5.7
    Starting testing...
    Query Servers: 172.16.5.7
    Query Hostname: configdb.lco.gtn
    Number of Queries: 10000
    Delay after each query: 0 ms
    Number of concurrent workers: 5
    
    Processed 1000/10000 results (0.88 s elapsed, 1137.49 QPS) -> NOERROR=1000
    Processed 2000/10000 results (1.65 s elapsed, 1209.89 QPS) -> NOERROR=2000
    Processed 3000/10000 results (2.43 s elapsed, 1234.42 QPS) -> NOERROR=3000
    Processed 4000/10000 results (3.21 s elapsed, 1244.62 QPS) -> NOERROR=4000
    Processed 5000/10000 results (3.99 s elapsed, 1254.62 QPS) -> NOERROR=5000
    Processed 6000/10000 results (4.77 s elapsed, 1258.36 QPS) -> NOERROR=6000
    Processed 7000/10000 results (5.54 s elapsed, 1264.04 QPS) -> NOERROR=7000
    Processed 8000/10000 results (6.33 s elapsed, 1264.60 QPS) -> NOERROR=8000
    Processed 9000/10000 results (7.10 s elapsed, 1267.70 QPS) -> NOERROR=9000
    Processed 10000/10000 results (7.88 s elapsed, 1269.56 QPS) -> NOERROR=10000
    
    Elapsed time: 7.89 s Queries: 10000 QPS: 1267.64
    NOERROR=10000
