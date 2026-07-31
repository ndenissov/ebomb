# Email Behavioral Overload & Monitoring Benchmark (E.B.O.M.B.)

[![PyPI version](https://img.shields.io/pypi/v/ebomb.svg)](https://pypi.org/project/ebomb/)
[![Downloads](https://static.pepy.tech/badge/ebomb)](https://pepy.tech/project/ebomb)
[![Python versions](https://img.shields.io/pypi/pyversions/ebomb.svg)](https://pypi.org/project/ebomb/)
[![License](https://img.shields.io/pypi/l/ebomb.svg)](https://github.com/ndenissov/ebomb/blob/main/LICENSE)
[![GitHub stars](https://img.shields.io/github/stars/ndenissov/ebomb)](https://github.com/ndenissov/ebomb/stargazers)

**EBOMB** (**e**mail **B**ehavioral **O**verload and **M**onitoring **B**enchmark) is an open-source benchmarking tool
designed to evaluate email server resilience, inbox rate-limiting, and spam filtering behaviors under synthetic
high-volume load.

The tool automates incoming subscription request flows to help system administrators, QA engineers, and security
auditors measure how mail infrastructure behaves under traffic spikes and concurrent delivery stress.

⚠️ **Disclaimer:** This software is intended strictly for authorized security auditing, benchmarking, and load testing
of infrastructure you own or have explicit written permission to test. Unauthorized automated traffic generation against
third-party services is strictly prohibited.

## Core Capabilities

* **Inbound Load Benchmarking:** Simulates concurrent subscription requests across configurable endpoints to test queue
  handling and buffer limits.
* **Filter Behavior Analysis:** Evaluates spam filter classification accuracy (e.g., SpamAssassin, Rspamd) when subject
  to automated request flows.
* **Multi-threaded Execution:** Utilizes configurable thread pools (`multiprocessing.dummy.ThreadPool`) for scalable
  concurrency testing.
* **Network & Proxy Support:** Includes optional SOCKS5 proxy rotation (including Tor support) to simulate distributed
  client traffic patterns.

## Installation

```bash
pip install -U ebomb
```

## Quick Start (CLI)

```bash
# Display CLI parameters and benchmark options
python -m ebomb --help

# Run a benchmark test against authorized target mailboxes
python -m ebomb benchmark-user1@example.com benchmark-user2@example.com -tc 4 --proxy --verbose
```

```bash
python -m ebomb --help
usage: ebomb [-h] [--threads-count THREADS_COUNT] [--proxy | --no-proxy] [--forever | --no-forever] [--verbose | --no-verbose] targets [targets ...]

Email Behavioral Overload & Monitoring Benchmark (E.B.O.M.B.)

positional arguments:
  targets               Email addresses separated by spaces.

options:
  -h, --help            show this help message and exit
  --threads-count, -tc THREADS_COUNT
  --proxy, --no-proxy   Use proxy.
  --forever, --no-forever
                        Run forever, otherwise only one circle.
  --verbose, --no-verbose
                        Display something on the screen.
```