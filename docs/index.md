[Ajuro.Net.Types](https://otb-expert.github.io/Ajuro.Net.Types/)

# Ajuro.IEX.Downloader
	

[NuGet](https://www.nuget.org/packages/Ajuro.IEX.Downloader) | [GitHub](https://github.com/OTB-Expert/Ajuro.IEX.Downloader) | [Docs](https://profimedica.github.io/Ajuro.IEX.Downloader)

-------


## Quick Start

![Overview diagram](https://otb.expert/projects/ajuro.iex.downloader/overview.png)


**Download Intraday Data**

Historical data can be downloaded day-by-day using this endpoint: 
https://iexcloud.io/docs/api/#intraday-prices



**Downloader controller**

OTB Expert downloads page:

http://otb.expert/Ajuro.Web.JS/src/#page-downloads

Endpoint:

https://otb.expert/api/downloader/file/downloads

Daily downloads completness:

![Overview diagram](https://otb.expert/projects/ajuro.iex.downloader/page-downloads.png)

## Types

##### DownloadIntradayReport

- SymbolId - local symbolId associated with the IEX symbol.
- Code - symbol code used by all brockers.
- From - the date of the oldest record (hour is omitted).
- To - the date of the most recent record (hour is omitted).
- Count - number of days collected.
- Details - see IntradayDetail.

code:

    public class DownloadIntradayReport
    {
        public int SymbolId { get; set; }
        public string Code { get; set; }
        public DateTime From { get; set; }
        public DateTime To { get; set; }
        public int Count { get; set; }
        public List<IntradayDetail> Details { get; set; }
    }


##### IntradayDetails

- Count - Number of valid ticks in the intraday array (null or zero values are not valide)
- Total - Number ticks including the invalid ones. -1 for file reading exception.
- Seconds - Unix timestamp. See https://www.unixtimestamp.com/index.php
- Samples - not used for reports.

code:

    public class IntradayDetail
    {
        public object Samples { get; set; }
        public int Count { get; set; }
        public int Total { get; set; }
        public long Seconds { get; set; }
    }

**Release Notes:**
v 0.0.1: Prerelease version


## To do list:

- Alert on missing intra-day files
- Show last status per symbol (Code, LastIntraday DB/Files, LastProcessed DB/Files)
- UnitTesting - DateTime intervals, Incremental download, incremental processing
- UnitTesting - Email alert on missing intraday

------------