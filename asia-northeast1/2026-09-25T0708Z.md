# asia-northeast1 · 2026-09-25T0708Z

## service
    state:    active
    restarts: 0
    since:    Fri 2026-09-25 07:06:09 UTC

## clock
    Reference ID    : D8177B55 (216.23.123.85)
    System time     : 0.000028170 seconds slow of NTP time
    Last offset     : -0.000002676 seconds

## disk
    /dev/sda1        20G  2.9G   16G  16% /
    ledger: 4.3M

## 24h report

  PHASE 0 · INGEST LAG
  ──────────────────────────────────────────────────────────────────────────

  Transport floor        control:binance  (millisecond-precision push feed)
    p50 5 ms · p95 10 ms · n=95
    This is the fastest this box can see anything. Nothing below is beatable.

  SOURCE                        N      p50      p95      p99      max   NOTE
  ──────────────────────────────────────────────────────────────────────────
  control:binance              95        5       10       12       12   reference
  control:coinbase            194       98      113      199      225   reference
  chain:launchlab              22      321      494      552      567   
  chain:pumpfun                61      336      616      663      666   

  VERDICT
  ──────────────────────────────────────────────────────────────────────────
  Bar (written down before collecting): p50 < 800 ms, p95 < 2000 ms


  Chain sources — raw, and less the ~500 ms block-time truncation:
    chain:launchlab          raw p50     321 · p95     494
                             adj p50       0 · p95       0   (would pass, n=22)
    chain:pumpfun            raw p50     336 · p95     616
                             adj p50       0 · p95     116   (would pass, n=61)

    Not counted as a pass or a fail. The adjustment is an assumption
    about a known artefact, not a measurement — a source that clears the
    bar only after subtracting 500 ms has not been shown to clear it.
    Time these against slot arrival to settle it properly.

  Nothing clears the bar on a real sample yet.
  Before concluding the strategy is dead, check in this order:
    1. Is the transport floor high? → the VM is in the wrong region.
    2. Is the poll interval most of the lag? → poll faster or find a push feed.
    3. Is the source stamp ±1s and the lag under ~1.5s? → the measurement is
       at its resolution limit; you need a millisecond-stamped feed to go finer.
  If none of those explain it, that IS the answer, and it cost you a weekend.

## deploy
    commit:  no autopull clone
    state:   never deployed

## outcome labels
    labelled 60   traded 58 (96.7%)   graduated 0
    standard 30-SOL curve: 26 of 60 (43.3%)   non-standard: 34
    REAL sol deposited | STANDARD curves, traded (n=26, funded>=1 SOL: 14):
      <0.1                   6   23.1%
      0.1-1                  6   23.1%
      1-10                   9   34.6%
      10-85 SOL              5   19.2%
      >=85 (graduation)      0    0.0%
    SOL still in curve at 1h | STANDARD, >=1 SOL in (n=0):
      kept <20% (dumped)     0    0.0%
      20-50%                 0    0.0%
      50-90%                 0    0.0%
      held >=90%             0    0.0%
    S2FLABELS	labelled=60	traded=58	grad=0	std=26	dumped=0	funded=0

## feed health
    2026-09-25T07:06:08.837Z INFO    s2f.chain:pumpfun      chain:pumpfun: ref 31 ms-precise / 0 fell back to blocktime (0.0%), blocktime 0 ok / 0 cached / 0 lost (0.00%) [http 0, rpc 0, net 0], 514 slots cached, 0 inflight
    2026-09-25T07:06:08.840Z INFO    s2f.chain:launchlab    chain:launchlab: ref 13 ms-precise / 0 fell back to blocktime (0.0%), blocktime 0 ok / 0 cached / 0 lost (0.00%) [http 0, rpc 0, net 0], 514 slots cached, 0 inflight

## last log lines
    2026-09-25T07:06:10.343Z INFO    s2f.chain:launchlab    subscribed (id 5614829)
    2026-09-25T07:06:10.343Z INFO    s2f.chain:launchlab    subscribed (id 3188426)
    2026-09-25T07:06:10.365Z INFO    s2f.rss:sec-press      primed with 25 existing items
    2026-09-25T07:06:10.528Z INFO    s2f.rss:federalregister primed with 1 existing items
    /etc/systemd/system/signal-to-fill.service:23: Unknown key 'StartLimitIntervalSec' in section [Service], ignoring.
    /etc/systemd/system/signal-to-fill.service:23: Unknown key 'StartLimitIntervalSec' in section [Service], ignoring.
