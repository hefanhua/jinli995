- ð Hi, Iâm @jinli995
- ð Iâm interested in ...
- ð± Iâm currently learning ...
- ðï¸ Iâm looking to collaborate on ...
- ð« How to reach me ...

<!---
jinli995/jinli995 is a â¨ special â¨ repository because its `README.md` (this file) appears on your GitHub profile.
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
    ws = locals() #å¨æåé
    wp = []
    wb = openpyxl.load_workbook('box.xlsx')
    wb_sheetnames = wb.sheetnames
    print(wb_sheetnames)
    # print(len(wb_sheetnames))
    for j in range(len(wb_sheetnames)):
        ws['ws'+str(j)] = wb[wb_sheetnames[j]]
        # print('å±åå»ºç sheet {}'.format('ws'+str(j)))
    # ws1 = wb[wb_sheetnames[0]]
    # for i in ws1.values:
    #     print(i)

def pds():
    # data1 = pd.read_csv(r"C:\Users\Jinli\Desktop\æ­å\box.csv")
    # print(data1.head())
    filename1 = 'box.xlsx'
    date1 = pd.read_excel(filename1,
    sheet_name= None,
    header=None
  )
    date_all = pd.concat([date1['ä»åº1'],date1['ä»åº2']],axis=0)
    print(date_all)
#æåµå¥åè¡¨åç´ ä¸ªæ°ååº
def num_list(list1):
    num = []
    for i in list1:
        if isinstance(i,list):
            num.append(len(i))
        else:num.append(1)
    return num
    

def xlex():
    filename = 'box.xlsx'
    data1 = xlrd.open_workbook(filename)
    # data1.unload_sheet(0)
    sheetsname = data1.sheet_names()

    # ws1 = data1.sheets()[0]#è·åå·¥ä½sheetåè¡¨
    sheet = data1.sheets()
    sheet1 = data1.sheet_by_index(0)

    # data1.sheet_by_name()
    # data1.sheet_by_index()

    # print(data1.nsheets)#è·å sheet æ°ç®


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
    filename2 = 'æç»©.xlsx'
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
    wrong = 0
    filename3 = 'AM335XBD11.xls'
    date2 = xlrd.open_workbook(filename3)
    sheetname = date2.sheet_names()
    sheet1 = date2.sheet_by_index(1)
    # sheet1 = date2.sheet_by_name(sheetname[1])
    maxrows = sheet1.nrows
    maxcols = sheet1.ncols
    list_index = sheet1.row_values(3)
    # print(list_index)
    classnum = list_index.index('ç±»å«')
    num = list_index.index('æ°é')
    pos_num = list_index.index('ä½å·')
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
    # print(list_pos)
    # print(list(list_pos[4]))
    a = (list_pos[2].replace(' ','')).split(',')#ååæ ¼,ä¸ªæ°
 

    # print(num_list(list_pos))
    for j in range(len(list_pos)):
        
        # print(len(list_pos[j].replace(' ','').split(',')))
        # print(int(list_num[j]))
        if int(list_num[j]) == len(list_pos[j].replace(' ','').split(',')):
            continue
            # print('1')
        else:
            print('ç¬¬{}è¡æ°ééè¯¯ å®éæ°éåºä¸º {}'.format(j+1,len(list_pos[j].replace(' ','').split(','))))
            wrong += 1

    if wrong == 0:
        print("å®å¨æ­£ç¡®") 
    else:print(wrong)

    for i in range(5,maxrows-1):
        pass
        # print(len(sheet1.cell_value(i,pos_num)))
        # print(sheet1.cell_value(i,pos_num))
        # if int(sheet1.cell_value(i,num)) != len(sheet1.cell_value(i,pos_num)):
        #     print('wrong')
        # else:print("å¨å¯¹")
    
   


if  __name__ == '__main__':
    demo2()
