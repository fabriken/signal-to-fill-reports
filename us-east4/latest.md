# us-east4 · 2026-09-06T0631Z

## service
    state:    active
    restarts: 0
    since:    Sun 2026-09-06 06:19:31 UTC

## clock
    Reference ID    : D890E4B3 (216-144-228-179-host.colocrossing.com)
    System time     : 0.000004069 seconds fast of NTP time
    Last offset     : +0.000000185 seconds

## disk
    /dev/sda1        20G  2.9G   16G  16% /
    ledger: 66M

## 24h report

  PHASE 0 · INGEST LAG
  ──────────────────────────────────────────────────────────────────────────

  Transport floor        control:coinbase  (millisecond-precision push feed)
    p50 6 ms · p95 20 ms · n=62,312
    This is the fastest this box can see anything. Nothing below is beatable.

  SOURCE                        N      p50      p95      p99      max   NOTE
  ──────────────────────────────────────────────────────────────────────────
  control:coinbase         62,312        6       20       86      635   reference
  chain:pumpfun            12,411    1,203    1,656    1,834    5,150   ±1s source stamp
  chain:launchlab          25,794    1,388   17,239   27,344   42,638   ±1s source stamp

  VERDICT
  ──────────────────────────────────────────────────────────────────────────
  Bar (written down before collecting): p50 < 800 ms, p95 < 2000 ms

    FAIL  chain:pumpfun            p50   1,203 ms · p95   1,656 ms
    FAIL  chain:launchlab          p50   1,388 ms · p95  17,239 ms

  Nothing clears the bar on a real sample yet.
  Before concluding the strategy is dead, check in this order:
    1. Is the transport floor high? → the VM is in the wrong region.
    2. Is the poll interval most of the lag? → poll faster or find a push feed.
    3. Is the source stamp ±1s and the lag under ~1.5s? → the measurement is
       at its resolution limit; you need a millisecond-stamped feed to go finer.
  If none of those explain it, that IS the answer, and it cost you a weekend.

## last log lines
    2026-09-06T06:31:16.371Z WARNING s2f.truth:accounts     HTTP 403 — this instance needs an access token
    /etc/systemd/system/signal-to-fill.service:23: Unknown key 'StartLimitIntervalSec' in section [Service], ignoring.
    2026-09-06T06:31:17.311Z INFO    httpx                  HTTP Request: POST https://api.mainnet-beta.solana.com "HTTP/1.1 429 Too Many Requests"
    /etc/systemd/system/signal-to-fill.service:23: Unknown key 'StartLimitIntervalSec' in section [Service], ignoring.
