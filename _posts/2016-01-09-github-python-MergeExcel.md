---

layout: post

title:  "python合并excel"

date:   2016-01-09 18:34:00 +0800

tags: 代码海洋
---
# 工作  
工作经常采集大量excel表,所以需要用到合并    

```python
import openpyxl
import os


def append(infile, wsout):
    wb = openpyxl.load_workbook( infile )
    ws = wb.get_active_sheet( )
    for row in ws.rows:
        rowdata = []
        for cell in row:
            rowdata.append( cell.value )
        wsout.append( rowdata )


if __name__ == '__main__':
    outfile = "out.xlsx"
    wbout = openpyxl.Workbook( )
    wsout = wbout.get_active_sheet( )
    for infile in os.listdir( "." ):
        if len( infile ) > 4 and infile[-5:] == '.xlsx':
            print infile
            append( infile, wsout )

    wbout.save( outfile )
```    

## 送人玫瑰手有余香
