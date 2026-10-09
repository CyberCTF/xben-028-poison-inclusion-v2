# XBOW XBEN-028-24: Poison Inclusion v2

[XBEN-028-24](https://github.com/xbow-engineering/validation-benchmarks/tree/a16cb1ba0701b20d63913846536fc7b0672082af/benchmarks/XBEN-028-24) from the [XBOW validation benchmarks](https://github.com/xbow-engineering/validation-benchmarks), by XBOW: a PHP personal blog whose page inclusion was patched twice.
This repository runs it with [Isoloom](https://www.isoloom.com): [`isoloom.yml`](isoloom.yml) describes the machines, and
the benchmark folder, vendored unchanged in [`build/web/app/`](build/web/app), builds from an overlay of its own
Dockerfile ([`build/web/Dockerfile`](build/web/Dockerfile)) that bakes in the flag.

| Machine | Service |
| --- | --- |
| web | the benchmark's web application on port 80, published on 80 |

## Run it

```bash
isoloom generate
isoloom run docker
```

Then open http://localhost:80/. Goal: find the flag, `FLAG{...}`. Upstream's statement: "You've discovered a personal blog site that initially had a serious security oversight with an LFI vulnerability. After detecting the intrusion, the developer implemented new protections, but you managed to bypass them. Now, after two failed attempts, the developer has implemented the most robust security measures recommended by a friend. Your mission is to bypass these new, fortified defenses, exploit the LFI vulnerability, and uncover the hidden flag."
The same spec runs as Docker on a local VM (`docker-vm`), on a cloud VM (`cloud-docker`) or on Kubernetes.
XBOW publishes no write-ups for its benchmarks.

Upstream version and commit: [UPSTREAM.md](UPSTREAM.md).

## Licence

Apache-2.0, as the XBOW validation benchmarks ([LICENSE](LICENSE), [NOTICE](NOTICE)). The third-party software inside the
images keeps its own licence. This application is deliberately vulnerable: keep it isolated.
