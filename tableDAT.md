# tableDAT
#### 在第0行后增加
op.appendRow( [ list], 0)
#### 删除
op.clear(keepFirstRow = True)
#### 改
#### 查看
op[ rowname, colname] / op[ rowidx, colidx] 
op.par.rows

#### 判断值
1. 某单元格不为空
op[ rowname, colname].val is None
2. 某行state值对应的ty
![3ff83b812e4aa1db2675f2be085dd6e](https://user-images.githubusercontent.com/56717775/179653446-68f3717a-57f4-426c-9f0a-33611ede150e.png)
op('in1')[me.inputRow, 'ty'+ op('in1')[me.inputRow, 'state']]


## datexec
def onRowChange(dat, rows):
idx = row[0]
type = dat[ idx, 'type'].val
