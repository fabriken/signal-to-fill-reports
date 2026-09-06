# europe-west3 · 2026-09-06T2024Z

## service
    state:    active
    restarts: 0
    since:    Sun 2026-09-06 06:34:11 UTC

## clock
    Reference ID    : 74CBDA6D (nur1.aup.dk)
    System time     : 0.000039792 seconds slow of NTP time
    Last offset     : -0.000032093 seconds

## disk
    /dev/sda1        20G  3.1G   16G  17% /
    ledger: 111M

## 24h report

  PHASE 0 · INGEST LAG
  ──────────────────────────────────────────────────────────────────────────

  Transport floor        control:coinbase  (millisecond-precision push feed)
    p50 51 ms · p95 68 ms · n=63,634
    This is the fastest this box can see anything. Nothing below is beatable.

  SOURCE                        N      p50      p95      p99      max   NOTE
  ──────────────────────────────────────────────────────────────────────────
  control:coinbase         63,634       51       68      156      367   reference
  chain:pumpfun             9,762    1,239    1,816    2,274   18,142   ±1s source stamp
  chain:launchlab          73,841    1,456   22,907   29,313   50,016   ±1s source stamp

  VERDICT
  ──────────────────────────────────────────────────────────────────────────
  Bar (written down before collecting): p50 < 800 ms, p95 < 2000 ms

    FAIL  chain:pumpfun            p50   1,239 ms · p95   1,816 ms
    FAIL  chain:launchlab          p50   1,456 ms · p95  22,907 ms

  Nothing clears the bar on a real sample yet.
  Before concluding the strategy is dead, check in this order:
    1. Is the transport floor high? → the VM is in the wrong region.
    2. Is the poll interval most of the lag? → poll faster or find a push feed.
    3. Is the source stamp ±1s and the lag under ~1.5s? → the measurement is
       at its resolution limit; you need a millisecond-stamped feed to go finer.
  If none of those explain it, that IS the answer, and it cost you a weekend.

## last log lines
    2026-09-06T20:24:40.369Z INFO    httpx                  HTTP Request: POST https://api.mainnet-beta.solana.com "HTTP/1.1 429 Too Many Requests"
    2026-09-06T20:24:40.390Z INFO    httpx                  HTTP Request: POST https://api.mainnet-beta.solana.com "HTTP/1.1 429 Too Many Requests"
    2026-09-06T20:24:40.419Z INFO    httpx                  HTTP Request: POST https://api.mainnet-beta.solana.com "HTTP/1.1 429 Too Many Requests"
    2026-09-06T20:24:40.446Z INFO    httpx                  HTTP Request: POST https://api.mainnet-beta.solana.com "HTTP/1.1 429 Too Many Requests"
    2026-09-06T20:24:40.966Z INFO    httpx                  HTTP Request: POST https://api.mainnet-beta.solana.com "HTTP/1.1 429 Too Many Requests"
    2026-09-06T20:24:40.981Z INFO    httpx                  HTTP Request: POST https://api.mainnet-beta.solana.com "HTTP/1.1 429 Too Many Requests"
