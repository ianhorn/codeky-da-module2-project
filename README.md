# Analyzing Monthly AWS S3 Logs for KyFromAbove Explorer Use

The [KyFromAbove Explorer](https://explore.kyfromabove.ky.gov) is a web app map viewer for Kentucky's Oblique Imagery.  Although the viewer is available for public consumption, one of the primary intended users is the Property Valuation Administrator, or  the PVA.  This product allows PVAs to view recently collected imagery that assists them view properties from several angles along with some other tools.  As you can imagine, acquiring oblique imagery in a statewide campaign is unprecedented.  By tackling this project at a statewide scale, discount pricing was acheived that save local governments money.

Kentucky is able to extends this savings as part of the [AWS Registry of Open Data](https://registry.opendata.aws/kyfromabove/), which covers the cost of imagery storage.  By extracting a dataset from the logs files for the month of November, I plan to analyze some data as it pertains to the source imagery for the KyFromAbove Explorer.

My primary questions:
 - How many requests does the bucket receive from the KyFromAbove Explorer?
 - How much data is consumed (in bytes)?
 - What are the most popular images?
 - Who is using the data?

___

### Procedures

Export data from AWS using Athena.
Run some pandas dataframe manipulations to answer my questions.
Create a map of users

### Setup

To get started clone this repo:

```bash
git clone https://github.com/ianhorn/codeky-da-module2-project.git

cd codeky-da-module2-project

python3 -m venv venv

source venv/bin/activate

pip install -r requirements.txt

```
---
### Download the data

There are two ways to download the data.  One is from the large csv file or downloading a compressed file and using gzip to decompress it.

```bash
# the compressed file
curl -LO https://ky.box.com/shared/static/i51gwqpefsgwyooodjtuy0ima6w8u6xg.gz

gzip -dc i51gwqpefsgwyooodjtuy0ima6w8u6xg.gz  > athena_output.csv

# uncompressed file
curl -LO https://ky.box.com/shared/static/h55nx1ca7ztcuzqvf8tu4g5q48t6lmqk.csv > athena.csv
```
You could also just use these links and then rename your file to *athena_output.csv*.

Download the [CSV]( 'https://ky.box.com/shared/static/h55nx1ca7ztcuzqvf8tu4g5q48t6lmqk.csv') (4.18 GB) data file<br>
Download the [GZIP](https://ky.box.com/shared/static/i51gwqpefsgwyooodjtuy0ima6w8u6xg.gz) (667 MB) compressed csv data file.

# Notebook

Go to the [data-project notebook](data-project.ipynb) to see work flow.

___

# Summary

