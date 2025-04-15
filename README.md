# Turbo Data Availability Tools

This repository contains two shell scripts for interacting with the Turbo Data Availability (TurboDA) service:

## turbo

A command-line tool for submitting data to and querying the TurboDA service.

### Features
- Submit raw data chunks
- Query submission status
- Configurable network selection (turing/mainnet)
- API key management
- Verbose output mode for debugging

### Usage
```bash
./turbo [GLOBAL OPTIONS] <ACTION> [ACTION OPTIONS]

GLOBAL OPTIONS:
  -n, --network <network>  Network, turing or mainnet (default: turing)
  -k, --api-key <file>    API key file (default: ~/.turbo/key-<network>)
  -v, --verbose           Enable verbose output
  -h, --help             Show help message

ACTIONS:
  submit <data>          Submit string data
  submit-raw <file>      Submit raw binary data
  query <submission_id>  Query submission status
  query-data <submission_id> Query submitted data
```

## turbobench

A benchmarking tool for testing TurboDA submissions with support for parallel processing.

### Features
- Submit multiple data chunks in parallel
- Configurable number of submission copies
- Detailed logging of submission results
- Performance statistics (throughput, success rate)
- Support for both GNU Parallel and xargs for parallel processing
- macOS-compatible file locking for concurrent log writes

### Usage
```bash
./turbobench [OPTIONS]

OPTIONS:
  -n, --num-copies <n>  Number of times to submit each chunk (default: 1)
  -k, --api-key <file>  API key file
  -v, --verbose         Enable verbose output
  -p, --parallel <n>    Number of chunks to submit in parallel (default: 1)
  -h, --help           Show help message
```

### Example Output
```
Will submit 7 files 2 time(s) with 4 jobs in parallel...
Benchmark complete. Results written to turbobench.log

Summary:
--------
Total time: 5.23 seconds
Total size: 7.00 MB
Throughput: 1.34 MB/s
Successful submissions: 14
Failed submissions: 0
```

## Installation

1. Clone this repository
2. Ensure you have required dependencies:
   - `curl` for HTTP requests
   - `jq` for JSON parsing
   - Optional: `parallel` for GNU Parallel support (falls back to xargs if not available)
3. Set up your API key:
   ```bash
   mkdir -p ~/.turbo
   echo "your-api-key" > ~/.turbo/key-turing  # for turing network
   echo "your-api-key" > ~/.turbo/key-mainnet # for mainnet
   ```

## Contributing

Feel free to open issues or submit pull requests for improvements!

## License

MIT License