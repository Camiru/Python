# Python
## 爬蟲練習

利用pandas抓到匯率後,<br />
可以建立簡單的UI產生當天美金匯率視窗<br />
import pandas #用pandas抓表格<br />
import tkinter<br />
import tkinter as tk<br />
from tkinter import *<br />
from tkinter.ttk import *<br /><br /><br />

win=tk.Tk()#產生視窗<br /><br />

win.title('匯率換算')#視窗標題<br />
win.geometry('250x100')#視窗大小<br />
win.configure(background='white')#視窗背景<br /><br />

header_label = tk.Label(win, text='美元台幣當日匯率換算')<br />
header_label.pack()<br /><br />

def ClickOK():<br />
    label.config(text="換算結果 " +'\n' + str(uscurrency)+ " 台幣")<br />
button=Button(win, text="OK", command=ClickOK)<br /><br />

label=Label(win, text="幣值")<br />
dfs = pandas.read_html('http://rate.bot.com.tw/xrt?Lang=zh-TW')<br />
currency = dfs[0]<br />
currency[u'幣別'] = currency[u'幣別'].str.extract('\((\w+)\)' , expand=True)<br />
uscurrency = currency.ix[0:0,0:2] #取美金<br /><br /><br />


label.pack()<br />
button.pack()<br />
win.mainloop()<br />
