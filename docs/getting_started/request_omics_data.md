### How to download the omics data files?

- Download a metadata table from multi-omics data page.(such as genomics data in <a href="https://www.chinese-quartet.org/#/data/download/quartet-genomics" target="_blank">Multiomics Data -> Genomics Data</a>
- Get the md5sum of files which you want to download from the metadata table.
- Follow the following docs to download your expected files.

#### Download `file transfer tool - biominer-aget`
Download biominer-aget binary from [BioMiner Aget for Linux](https://www.indexd.org/biominer-aget/biominer-aget_x86-64_linux) or [BioMiner Aget for Mac](https://www.indexd.org/biominer-aget/biominer-aget_x86-64_macosx)

Copy the biominer-aget binary into /usr/bin/biominer-aget or any other directory which in PATH variable.

#### Download a data file with biominer-aget
e.g. you want to download the file with UUID `00006134-c655-4bbe-9144-0ee86da83902` or Hash (such as md5sum, sha128...) `b02ced3319ba35746e2436d67b04a42c` from the repository biominer.fudan-pgx, you can run the following command:

```bash
biominer-aget --guid biominer.fudan-pgx/00006134-c655-4bbe-9144-0ee86da83902 --output-dir ~/Downloads/ --repo gsa --chunk_size 1m --concurrency 1000

## or

biominer-aget --hash b02ced3319ba35746e2436d67b04a42c --output-dir ~/Downloads/ --repo gsa --chunk_size 1m --concurrency 1000

## NODE repo doesn't support http range, so the --chunk_size and --concurrency arguments don't work for it.

biominer-aget --hash b02ced3319ba35746e2436d67b04a42c --output-dir ~/Downloads/ --repo node
```

!!!note Please note that
    1. The `chunk_size` and `concurrency` parameters are related with the download speed. **There may be tens or hundreds of times the difference, so it's worth taking some time to find the best one.**
    
    2. The biominer-aget binary is not available for Windows.
    
    3. Not each file can be found in all these repos, so you need to specify a repo name when you downloading expected file.

```bash
$ biominer-aget --help
Biominer Aget 0.3.7
Jingcheng Yang <yjcyxky@163.com>
An Index Engine for Omics Data Files

USAGE:
    biominer-aget [FLAGS] [OPTIONS]

FLAGS:
    -D, --debug      Activate debug mode
    -h, --help       Prints help information
    -V, --version    Prints version information

OPTIONS:
    -a, --api-server <api-server>      The api server address
    -k, --chunk_size <chunk_size>      The number ofinterval length of each concurrent request [default: '50m']
    -c, --concurrency <concurrency>    The number of concurrency request [default: 10]
        --dns-timeout <dns-timeout>    DNS Timeout(seconds) of request [default: 10]
    -g, --guid <guid>                  The guid of the file you want to download, e.g. biominer.fudan-pgx/00006134-c655-
                                       4bbe-9144-0ee86da83902
    -H, --hash <hash>                  The hash of the file you want to download, e.g. b47ee06cdf62847f6d4c11bb12ac1ae0
    -o, --output-dir <output-dir>      Output directory [default: ./]
    -p, --password <password>          Password for the biominer api server [default: anonymous]
    -r, --repo <repo>                  Which data repository you want to download from [default: node]  [possible
                                       values: node, gsa, s3, oss, minio]
        --retries <retries>            The maximum times of retring [default: 0]
        --retry-wait <retry-wait>      The seconds between retries [default: 0]
    -t, --timeout <timeout>            Timeout(seconds) of request [default: 60]
    -u, --username <username>          Username for the biominer-indexd api server [default: anonymous]
```

### How do you know a file is stored at which repo?

Please access [the BioMiner Indexd service](http://www.indexd.org/index) and query file by md5sum, filename, or other metadata.

When you find the record of a file, you can see more information as the following picture.

In the picture, you can see the URLs field, it can tell you the file is stored at which repos.

![biominer-indexd](../assets/images/indexd.png)

### Why BioMiner Indexd?

We will release our data to multiple repos (such as [NODE](https://www.biosino.org/node/), [GSA](https://ngdc.cncb.ac.cn/gsa/), [SRA](https://www.ncbi.nlm.nih.gov/sra), [ENA](https://www.ebi.ac.uk/ena/browser/) etc.), for your convenience, we provide the BioMiner Indexd service for aggregating all these repos.

BioMiner Indexd is a hash-based data indexing and tracking service providing globally unique identifiers.
