- 👋 Hi, I’m @jinli995
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
jinli995/jinli995 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
#!/usr/bin/env python
#-*- conding:utf-8 #-*-
#Copyright (C) ***
from datetime import date
import sys
import time
from typing import OrderedDict
import pandas as pd
# from openpyxl import Workbook
import openpyxl
import xlrd
from xlrd import open_workbook, sheet
import xlwt
def pyxl():
    ws = locals() #动态变量
    wp = []
    wb = openpyxl.load_workbook('box.xlsx')
    wb_sheetnames = wb.sheetnames
    print(wb_sheetnames)
    # print(len(wb_sheetnames))
    for j in range(len(wb_sheetnames)):
        ws['ws'+str(j)] = wb[wb_sheetnames[j]]
        # print('共创建的 sheet {}'.format('ws'+str(j)))
    # ws1 = wb[wb_sheetnames[0]]
    # for i in ws1.values:
    #     print(i)

def pds():
    # data1 = pd.read_csv(r"C:\Users\Jinli\Desktop\歌单\box.csv")
    # print(data1.head())
    filename1 = 'box.xlsx'
    date1 = pd.read_excel(filename1,
    sheet_name= None,
    header=None
  )
    date_all = pd.concat([date1['仓库1'],date1['仓库2']],axis=0)
    print(date_all)


    

def xlex():
    filename = 'box.xlsx'
    data1 = xlrd.open_workbook(filename)
    # data1.unload_sheet(0)
    sheetsname = data1.sheet_names()

    # ws1 = data1.sheets()[0]#获取工作sheet列表
    sheet = data1.sheets()
    sheet1 = data1.sheet_by_index(0)

    # data1.sheet_by_name()
    # data1.sheet_by_index()

    # print(data1.nsheets)#获取 sheet 数目


    ws1maxrows = sheet1.nrows
    ws1maxcols = sheet1.ncols
    row1 = sheet1.row_values(0)[1]
    row1len = sheet1.row_len(0)
    # row2 = sheet1.row_values(1)[1]
    # print(row1,row1len)
    # row11 = sheet1.cell_value(0,1)
    # print(row11)

    for i in range(ws1maxrows):
        for j in range(ws1maxcols):
            print(sheet1.cell_value(i,j))

def demo1():
    filename2 = '成绩.xlsx'
    date2 = xlrd.open_workbook(filename2)
    sheet1 = date2.sheet_by_index(0)
    maxrows = sheet1.nrows
    maxcols = sheet1.ncols
    
    for j in range(1,maxrows):
        scor = 0
        for i in range(1,maxcols):
            scor += sheet1.cell_value(j,i)
            if scor>14:
                print(sheet1.cell_value(j,0),sheet1.cell_value(0,i))
                break
def demo2():
    
    filename3 = 'AM335XBD11.xls'
    date2 = xlrd.open_workbook(filename3)
    sheetname = date2.sheet_names()
    sheet1 = date2.sheet_by_index(1)
    # sheet1 = date2.sheet_by_name(sheetname[1])
    maxrows = sheet1.nrows
    maxcols = sheet1.ncols
    list_index = sheet1.row_values(3)
    # print(list_index)
    classnum = list_index.index('类别')
    num = list_index.index('数量')
    pos_num = list_index.index('位号')
    # if sheet1.col_values(classnum) == "smt".upper():
    #     smt_sum += 1
    # print(sheet1.col_values(classnum,start_rowx=5,end_rowx=maxrows-1))
    list_class = sheet1.col_values(classnum,start_rowx=5,end_rowx=maxrows-1)
    list_pos = sheet1.col_values(pos_num,start_rowx=5,end_rowx=maxrows-1)
    list_num = sheet1.col_values(num,start_rowx=5,end_rowx=maxrows-1)

    set_class = set(list_class)
    smt_sum = list_class.count('SMT')
    asm_sum = list_class.count('ASM')
    pth = list_class.count('PTH')
    # print(len(list_pos),len(list_num))
    print(list_pos)
    
    # for j in range(len(list_pos)):
    #     print(len(list(str(list_pos[j]))))



        # if int(list_num[j]) != len(list_pos[j]):
        #     print('wrong')
        # else:print('all')

    for i in range(5,maxrows-1):
        pass

    
        # print(len(sheet1.cell_value(i,pos_num)))
        # print(sheet1.cell_value(i,pos_num))
        # if int(sheet1.cell_value(i,num)) != len(sheet1.cell_value(i,pos_num)):
        #     print('wrong')
        # else:print("全对")


if  __name__ == '__main__':
    demo2()
