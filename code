import twstock
import pandas as pd
import matplotlib
import mplfinance as mpf

stock = input("請輸入股票代碼 : ")
s_year = int(input('請輸入起始年分(西元):'))
s_month = int(input('請輸入起始月份:'))
target_stock = stock  #股票代號變數
stock = twstock.Stock(target_stock)  
target_price = stock.fetch_from(s_year, s_month)  #至今每天的data

name_attribute = [
    'Date', 'Capacity', 'Turnover', 'Open', 'High', 'Low', 'Close', 'Change',
    'Transcation'
]  #幫收集到的資料設定title

df = pd.DataFrame(columns=name_attribute, data=target_price)


filename = f'C:\python training\sideproject -stocktw\\{target_stock}.csv'
#指定Data Frame轉存csv檔案的檔名與路徑

df.to_csv(filename)

df = pd.read_csv(f'C:\python training\sideproject -stocktw\\{target_stock}.csv', parse_dates=True, index_col=1) #讀取目標股票csv檔的位置

df.rename(columns={'Turnover':'Volume'}, inplace = True) 


mc = mpf.make_marketcolors(up='r',down='g',inherit=True)
s  = mpf.make_mpf_style(base_mpf_style='yahoo',marketcolors=mc)


kwargs = dict(type='candle', mav=(5,20,60), volume=True, figratio=(10,8), figscale=0.75, title=target_stock, style=s) 


mpf.plot(df, **kwargs)
