
# Building a Recommendation Model
**Internship Assignment- Think Analytics**
**Submitted By- Shivam Panchal(shivam.panchal@mail.com)**


**Setting the work directory**


```python
import os
os.chdir('C://users/Shivam Panchal/Desktop/Analytics Assignment')
print os.getcwd()
```

    C:\users\Shivam Panchal\Desktop\Analytics Assignment
    

**Importing Graphlab**


```python
import graphlab
```

**Importing the necessary files**


```python
offer_df = graphlab.SFrame('OfferMaster (22).csv')
bank_df = graphlab.SFrame('BankMaster (1).csv')
merchant_df = graphlab.SFrame('MerchantMaster (21).csv')
offer_loc_df = graphlab.SFrame('OfferLocation (1).csv')
offer_Cate_df = graphlab.SFrame('OfferCategorization (1).csv')
payment_df = graphlab.SFrame('Payment (1).csv')
seller_df = graphlab.SFrame('Seller (3).csv')
customer_df = graphlab.SFrame('CustomerMaster (3).csv')
category_df = graphlab.SFrame('CategoryMaster (4).csv')
shop_df = graphlab.SFrame('Shop (5).csv')
```

    This non-commercial license of GraphLab Create for academic use is assigned to shivamvaish09@gmail.com and will expire on October 16, 2017.
    

    [INFO] graphlab.cython.cy_server: GraphLab Create v2.1 started. Logging: C:\Users\SHIVAM~1\AppData\Local\Temp\graphlab_server_1482258081.log.0
    


<pre>Unable to parse line "41628,NULL,Android Calling Tablet just for Rs.2999/-,NULL,"Get best prices and heavy discounts on your purchase."</pre>



<pre>Unable to parse line "Order Now : 08010058888 / 01244592323"</pre>



<pre>Unable to parse line "",Online,3,31-05-2016,09-06-2016,,Discount,N,02-06-2016,NULL"</pre>



<pre>Unable to parse line "41629,NULL,Intex Multimedia Speakers just for Rs.999/-,NULL,"Get best prices and heavy discounts on Multimedia Speakers + Free Aluma Wallet Worth Rs.499/-"</pre>



<pre>Unable to parse line "Order Now : 08010058888 / 01244592323"</pre>



<pre>Unable to parse line "",Online,3,31-05-2016,09-06-2016,,Discount,N,02-06-2016,NULL"</pre>



<pre>Unable to parse line "41630,NULL,Save 60% on Golden Embroidered Suit,NULL,"Get Golden Embroidered Suit just for Rs.799 instead of Rs.1999/-"</pre>



<pre>Unable to parse line "Order Now : 08010058888 / 01244592323",Online,5,31-05-2016,09-06-2016,,Discount,N,02-06-2016,NULL"</pre>



<pre>Unable to parse line "41631,NULL,International Packages Starting at just Rs. 40990/-,NULL,"Tour Package - Flight + Cab + Accommodation + Tourist Trains."</pre>



<pre>Unable to parse line "Duration : 4N/5D"</pre>



<pre>810 lines failed to parse correctly</pre>



<pre>Finished parsing file C:\users\Shivam Panchal\Desktop\Analytics Assignment\OfferMaster (22).csv</pre>



<pre>Parsing completed. Parsed 100 lines in 0.597029 secs.</pre>


    ------------------------------------------------------
    Inferred types from first 100 line(s) of file as 
    column_type_hints=[long,long,str,str,str,str,str,str,str,str,str,str,str,str]
    If parsing fails due to incorrect types, you can correct
    the inferred type list above and pass it to read_csv in
    the column_type_hints argument
    ------------------------------------------------------
    


<pre>Unable to parse line "41622,NULL,Sale Upto 30% OFF,NULL,Get best prices and heavy discounts on School Products.,Offline,3,01-06-2016,15-06-2016,,Discount,N,01-06-2016,NULL"</pre>



<pre>Unable to parse line "41628,NULL,Android Calling Tablet just for Rs.2999/-,NULL,"Get best prices and heavy discounts on your purchase."</pre>



<pre>Unable to parse line "Order Now : 08010058888 / 01244592323"</pre>



<pre>Unable to parse line "",Online,3,31-05-2016,09-06-2016,,Discount,N,02-06-2016,NULL"</pre>



<pre>Unable to parse line "41629,NULL,Intex Multimedia Speakers just for Rs.999/-,NULL,"Get best prices and heavy discounts on Multimedia Speakers + Free Aluma Wallet Worth Rs.499/-"</pre>



<pre>Unable to parse line "Order Now : 08010058888 / 01244592323"</pre>



<pre>Unable to parse line "",Online,3,31-05-2016,09-06-2016,,Discount,N,02-06-2016,NULL"</pre>



<pre>Unable to parse line "41630,NULL,Save 60% on Golden Embroidered Suit,NULL,"Get Golden Embroidered Suit just for Rs.799 instead of Rs.1999/-"</pre>



<pre>Unable to parse line "Order Now : 08010058888 / 01244592323",Online,5,31-05-2016,09-06-2016,,Discount,N,02-06-2016,NULL"</pre>



<pre>Unable to parse line "41631,NULL,International Packages Starting at just Rs. 40990/-,NULL,"Tour Package - Flight + Cab + Accommodation + Tourist Trains."</pre>



<pre>2621 lines failed to parse correctly</pre>



<pre>Finished parsing file C:\users\Shivam Panchal\Desktop\Analytics Assignment\OfferMaster (22).csv</pre>



<pre>Parsing completed. Parsed 40183 lines in 0.387775 secs.</pre>



<pre>Finished parsing file C:\users\Shivam Panchal\Desktop\Analytics Assignment\BankMaster (1).csv</pre>



<pre>Parsing completed. Parsed 24 lines in 0.024518 secs.</pre>


    ------------------------------------------------------
    Inferred types from first 100 line(s) of file as 
    column_type_hints=[long,str]
    If parsing fails due to incorrect types, you can correct
    the inferred type list above and pass it to read_csv in
    the column_type_hints argument
    ------------------------------------------------------
    


<pre>Finished parsing file C:\users\Shivam Panchal\Desktop\Analytics Assignment\BankMaster (1).csv</pre>



<pre>Parsing completed. Parsed 24 lines in 0.031522 secs.</pre>



<pre>Finished parsing file C:\users\Shivam Panchal\Desktop\Analytics Assignment\MerchantMaster (21).csv</pre>



<pre>Parsing completed. Parsed 100 lines in 0.04203 secs.</pre>


    ------------------------------------------------------
    Inferred types from first 100 line(s) of file as 
    column_type_hints=[long,str,long,str]
    If parsing fails due to incorrect types, you can correct
    the inferred type list above and pass it to read_csv in
    the column_type_hints argument
    ------------------------------------------------------
    


<pre>Unable to parse line "2784,Charles & Keith,NULL,Offline"</pre>



<pre>Unable to parse line "2785,French Connection,NULL,Offline"</pre>



<pre>Unable to parse line "2786,Diesel,NULL,Offline"</pre>



<pre>Unable to parse line "4484,Eye World Opticians,NULL,Offline"</pre>



<pre>Unable to parse line "2787,Superdry,NULL,Offline"</pre>



<pre>Unable to parse line "4485,Aman Sports,NULL,Offline"</pre>



<pre>Unable to parse line "2788,Aldo,NULL,Offline"</pre>



<pre>Unable to parse line "4486,Socute Ladies & KIds Wear,NULL,Offline"</pre>



<pre>Unable to parse line "2789,Kenneth Cole,NULL,Offline"</pre>



<pre>Unable to parse line "4487,Dream Choice Mens Wear,NULL,Offline"</pre>



<pre>Unable to parse line "2790,Only,NULL,Offline"</pre>



<pre>1657 lines failed to parse correctly</pre>



<pre>Finished parsing file C:\users\Shivam Panchal\Desktop\Analytics Assignment\MerchantMaster (21).csv</pre>



<pre>Parsing completed. Parsed 2989 lines in 0.035025 secs.</pre>



<pre>Finished parsing file C:\users\Shivam Panchal\Desktop\Analytics Assignment\OfferLocation (1).csv</pre>



<pre>Parsing completed. Parsed 100 lines in 0.037025 secs.</pre>


    ------------------------------------------------------
    Inferred types from first 100 line(s) of file as 
    column_type_hints=[long,long]
    If parsing fails due to incorrect types, you can correct
    the inferred type list above and pass it to read_csv in
    the column_type_hints argument
    ------------------------------------------------------
    


<pre>Finished parsing file C:\users\Shivam Panchal\Desktop\Analytics Assignment\OfferLocation (1).csv</pre>



<pre>Parsing completed. Parsed 4842 lines in 0.037028 secs.</pre>



<pre>Finished parsing file C:\users\Shivam Panchal\Desktop\Analytics Assignment\OfferCategorization (1).csv</pre>



<pre>Parsing completed. Parsed 100 lines in 0.118623 secs.</pre>


    ------------------------------------------------------
    Inferred types from first 100 line(s) of file as 
    column_type_hints=[long,long]
    If parsing fails due to incorrect types, you can correct
    the inferred type list above and pass it to read_csv in
    the column_type_hints argument
    ------------------------------------------------------
    


<pre>Finished parsing file C:\users\Shivam Panchal\Desktop\Analytics Assignment\OfferCategorization (1).csv</pre>



<pre>Parsing completed. Parsed 132252 lines in 0.109578 secs.</pre>



<pre>Finished parsing file C:\users\Shivam Panchal\Desktop\Analytics Assignment\Payment (1).csv</pre>



<pre>Parsing completed. Parsed 100 lines in 0.051537 secs.</pre>


    ------------------------------------------------------
    Inferred types from first 100 line(s) of file as 
    column_type_hints=[long,long,long,str]
    If parsing fails due to incorrect types, you can correct
    the inferred type list above and pass it to read_csv in
    the column_type_hints argument
    ------------------------------------------------------
    


<pre>Finished parsing file C:\users\Shivam Panchal\Desktop\Analytics Assignment\Payment (1).csv</pre>



<pre>Parsing completed. Parsed 5019 lines in 0.042028 secs.</pre>



<pre>Finished parsing file C:\users\Shivam Panchal\Desktop\Analytics Assignment\Seller (3).csv</pre>



<pre>Parsing completed. Parsed 100 lines in 0.144971 secs.</pre>


    ------------------------------------------------------
    Inferred types from first 100 line(s) of file as 
    column_type_hints=[long,long,long]
    If parsing fails due to incorrect types, you can correct
    the inferred type list above and pass it to read_csv in
    the column_type_hints argument
    ------------------------------------------------------
    


<pre>Finished parsing file C:\users\Shivam Panchal\Desktop\Analytics Assignment\Seller (3).csv</pre>



<pre>Parsing completed. Parsed 42340 lines in 0.079556 secs.</pre>



<pre>Finished parsing file C:\users\Shivam Panchal\Desktop\Analytics Assignment\CustomerMaster (3).csv</pre>



<pre>Parsing completed. Parsed 100 lines in 0.045973 secs.</pre>


    ------------------------------------------------------
    Inferred types from first 100 line(s) of file as 
    column_type_hints=[long,str,str,str,str]
    If parsing fails due to incorrect types, you can correct
    the inferred type list above and pass it to read_csv in
    the column_type_hints argument
    ------------------------------------------------------
    


<pre>Finished parsing file C:\users\Shivam Panchal\Desktop\Analytics Assignment\CustomerMaster (3).csv</pre>



<pre>Parsing completed. Parsed 4246 lines in 0.04053 secs.</pre>



<pre>Finished parsing file C:\users\Shivam Panchal\Desktop\Analytics Assignment\CategoryMaster (4).csv</pre>



<pre>Parsing completed. Parsed 84 lines in 0.03002 secs.</pre>


    ------------------------------------------------------
    Inferred types from first 100 line(s) of file as 
    column_type_hints=[long,str,long]
    If parsing fails due to incorrect types, you can correct
    the inferred type list above and pass it to read_csv in
    the column_type_hints argument
    ------------------------------------------------------
    


<pre>Finished parsing file C:\users\Shivam Panchal\Desktop\Analytics Assignment\CategoryMaster (4).csv</pre>



<pre>Parsing completed. Parsed 84 lines in 0.032023 secs.</pre>



<pre>Unable to parse line ""4501","Cafe Coffee Day","No. 1691, Dr. Rajkumar Road, Prakash Nagar, Near Bank Of Baroda, "</pre>



<pre>Unable to parse line "Rajaji Nagar, Bengalur - 560010",,,"Bengaluru",,"12.9849815","77.553344","Karnataka",,,"1","1","1","1","1","1","1","1",,"9343003288","3000","2016-01-20",,"Y","Data Upload","HSBC","Monish","Monish","2016-02-09 00:00:00""</pre>



<pre>Unable to parse line ""4525","Cafe Coffee Day","No. 15, Sigma Mall,  Cunningham Road, "</pre>



<pre>Unable to parse line "Bangalore - 560052",,,"Bengaluru",,"12.9879542","77.5923133","Karnataka",,,"1","1","1","1","1","1","1","1",,"7483258046","3000","2016-01-20",,"Y","Data Upload","HSBC","Monish","Monish","2016-02-09 00:00:00""</pre>



<pre>Unable to parse line ""4526","Cafe Coffee Day","No.6, Palace Cross Road, Opp. Mount Carmal College, Vasanth Nagar, "</pre>



<pre>Unable to parse line "Bangalore - 560052",,,"Bengaluru",,"12.9879802","77.5857472","Karnataka",,,"1","1","1","1","1","1","1","1",,"9342434024","3000","2016-01-20",,"Y","Data Upload","HSBC","Monish","Monish","2016-02-09 00:00:00""</pre>



<pre>Unable to parse line ""4531","Cafe Coffee Day","Cafe Coffee Day, opp. ITC Banaswadi, Banaswadi Main Road, "</pre>



<pre>Unable to parse line "Maruti Sevanagar,  Bangalore ? 560005",,,"Bengaluru",,"12.9996212","77.6230773","Karnataka",,,"1","1","1","1","1","1","1","1",,"9243601924","3000","2016-01-20",,"Y","Data Upload","HSBC","Monish","Monish","2016-02-09 00:00:00""</pre>



<pre>Unable to parse line ""4551","Cafe Coffee Day","No 11, Ground Floor, Forum Mall, Hosur Road, Koramangala, "</pre>



<pre>Unable to parse line "Bangalore - 560095",,,"Bengaluru",,"12.9287659","77.615515","Karnataka",,,"1","1","1","1","1","1","1","1",,"9343712764","3000","2016-01-20",,"Y","Data Upload","HSBC","Monish","Monish","2016-02-09 00:00:00""</pre>



<pre>160 lines failed to parse correctly</pre>



<pre>Finished parsing file C:\users\Shivam Panchal\Desktop\Analytics Assignment\Shop (5).csv</pre>



<pre>Parsing completed. Parsed 100 lines in 0.247365 secs.</pre>


    ------------------------------------------------------
    Inferred types from first 100 line(s) of file as 
    column_type_hints=[long,str,str,str,str,str,long,float,float,str,str,str,long,long,long,long,long,long,long,str,str,long,long,str,str,str,str,str,str,str,str]
    If parsing fails due to incorrect types, you can correct
    the inferred type list above and pass it to read_csv in
    the column_type_hints argument
    ------------------------------------------------------
    


<pre>Unable to parse line ""4484","Oh Calcutta","Hotel Rosewood, Tulsiwadi Lane, Opp. Mahindra Heights, Tardeo, Mumbai - 400 034.",,,"Mumbai",,"18.9725328","72.7454453","Maharashtra",,,"1","1","1","1","1","1","1","1",,"(022)23539114","3069","2016-01-20",,"Y","Data Upload","HSBC","Mo..."</pre>



<pre>Unable to parse line ""4501","Cafe Coffee Day","No. 1691, Dr. Rajkumar Road, Prakash Nagar, Near Bank Of Baroda, "</pre>



<pre>Unable to parse line "Rajaji Nagar, Bengalur - 560010",,,"Bengaluru",,"12.9849815","77.553344","Karnataka",,,"1","1","1","1","1","1","1","1",,"9343003288","3000","2016-01-20",,"Y","Data Upload","HSBC","Monish","Monish","2016-02-09 00:00:00""</pre>



<pre>Unable to parse line ""4525","Cafe Coffee Day","No. 15, Sigma Mall,  Cunningham Road, "</pre>



<pre>Unable to parse line "Bangalore - 560052",,,"Bengaluru",,"12.9879542","77.5923133","Karnataka",,,"1","1","1","1","1","1","1","1",,"7483258046","3000","2016-01-20",,"Y","Data Upload","HSBC","Monish","Monish","2016-02-09 00:00:00""</pre>



<pre>Unable to parse line ""4526","Cafe Coffee Day","No.6, Palace Cross Road, Opp. Mount Carmal College, Vasanth Nagar, "</pre>



<pre>Unable to parse line "Bangalore - 560052",,,"Bengaluru",,"12.9879802","77.5857472","Karnataka",,,"1","1","1","1","1","1","1","1",,"9342434024","3000","2016-01-20",,"Y","Data Upload","HSBC","Monish","Monish","2016-02-09 00:00:00""</pre>



<pre>Unable to parse line ""4531","Cafe Coffee Day","Cafe Coffee Day, opp. ITC Banaswadi, Banaswadi Main Road, "</pre>



<pre>Unable to parse line "Maruti Sevanagar,  Bangalore ? 560005",,,"Bengaluru",,"12.9996212","77.6230773","Karnataka",,,"1","1","1","1","1","1","1","1",,"9243601924","3000","2016-01-20",,"Y","Data Upload","HSBC","Monish","Monish","2016-02-09 00:00:00""</pre>



<pre>Unable to parse line ""4551","Cafe Coffee Day","No 11, Ground Floor, Forum Mall, Hosur Road, Koramangala, "</pre>



<pre>211 lines failed to parse correctly</pre>



<pre>Finished parsing file C:\users\Shivam Panchal\Desktop\Analytics Assignment\Shop (5).csv</pre>



<pre>Parsing completed. Parsed 5858 lines in 0.138599 secs.</pre>



```python
graphlab.canvas.set_target('ipynb')
```

**Extracting the most frequent items or offers**


```python
offer_df['OfferTitle'].show()
```




```python
# Reading the json file containing the User History

user_hist = graphlab.SFrame.read_json('events_data.json', orient='lines')
```


<pre>Finished parsing file C:\users\Shivam Panchal\Desktop\Analytics Assignment\events_data.json</pre>



<pre>Parsing completed. Parsed 100 lines in 3.15424 secs.</pre>


    ------------------------------------------------------
    Inferred types from first 100 line(s) of file as 
    column_type_hints=[dict]
    If parsing fails due to incorrect types, you can correct
    the inferred type list above and pass it to read_csv in
    the column_type_hints argument
    ------------------------------------------------------
    


<pre>Read 56225 lines. Lines per second: 7667.57</pre>



<pre>Finished parsing file C:\users\Shivam Panchal\Desktop\Analytics Assignment\events_data.json</pre>



<pre>Parsing completed. Parsed 155073 lines in 11.2856 secs.</pre>



```python
user_cont = user_hist['attributes']
```


```python
customer_id = [object['CustomerID'] for object in user_cont if object.has_key('OfferID') & object.has_key('CustomerID')] 
offer_id = [object['OfferID'] for object in user_cont if object.has_key('OfferID') & object.has_key('CustomerID')] 
```


```python
user_hist
```




<div style="max-height:1000px;max-width:1500px;overflow:auto;"><table frame="box" rules="cols">
    <tr>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">_id</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">application</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">arrival_timestamp</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">attributes</th>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'$oid': '57a30ce268fd080<br>9ec4d194f'} ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'package_name':<br>'com.think.vito', ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'$numberLong':<br>'1470183523054'} ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'Category': '120000',<br>'CustomerID': '4078', ...</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'$oid': '57a30ce268fd080<br>9ec4d1950'} ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'package_name':<br>'com.think.vito', ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'$numberLong':<br>'1470183523054'} ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'MenuItem': 'OfferList',<br>'CustomerID': '4078'} ...</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'$oid': '57a30ce268fd080<br>9ec4d1951'} ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'package_name':<br>'com.think.vito', ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'$numberLong':<br>'1470183523054'} ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'Category': 'Recharge',<br>'CustomerID': '4078'} ...</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'$oid': '57a30ce268fd080<br>9ec4d1952'} ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'package_name':<br>'com.think.vito', ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'$numberLong':<br>'1470183523054'} ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'CustomerID': '4078'}</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'$oid': '57a30ce268fd080<br>9ec4d1953'} ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'package_name':<br>'com.think.vito', ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'$numberLong':<br>'1470183523054'} ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{}</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'$oid': '57a30ce268fd080<br>9ec4d1954'} ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'package_name':<br>'com.think.vito', ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'$numberLong':<br>'1470193295093'} ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{}</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'$oid': '57a30ce268fd080<br>9ec4d1955'} ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'package_name':<br>'com.think.vito', ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'$numberLong':<br>'1470193404776'} ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{}</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'$oid': '57a30ce268fd080<br>9ec4d1956'} ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'package_name':<br>'com.think.vito', ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'$numberLong':<br>'1470193404776'} ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{}</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'$oid': '57a30ce268fd080<br>9ec4d1957'} ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'package_name':<br>'com.think.vito', ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'$numberLong':<br>'1470193404776'} ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{}</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'$oid': '57a30ce268fd080<br>9ec4d1958'} ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'package_name':<br>'com.think.vito', ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'$numberLong':<br>'1470193404776'} ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{}</td>
    </tr>
</table>
<table frame="box" rules="cols">
    <tr>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">client</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">device</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">event_timestamp</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">event_type</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">event_version</th>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'cognito_id': 'us-east-1<br>:2e26918b-f7b1-471e- ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'locale': {'country':<br>'US', 'code': 'en_US', ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'$numberLong':<br>'1470183505399'} ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">OfferViewed</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3.0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'cognito_id': 'us-east-1<br>:2e26918b-f7b1-471e- ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'locale': {'country':<br>'US', 'code': 'en_US', ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'$numberLong':<br>'1470183500206'} ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">ContextMenuItemSelected</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3.0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'cognito_id': 'us-east-1<br>:2e26918b-f7b1-471e- ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'locale': {'country':<br>'US', 'code': 'en_US', ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'$numberLong':<br>'1470183499171'} ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">CategoryPageCategorySelec<br>tion ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3.0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'cognito_id': 'us-east-1<br>:2e26918b-f7b1-471e- ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'locale': {'country':<br>'US', 'code': 'en_US', ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'$numberLong':<br>'1470183490481'} ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">_session.start</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3.0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'cognito_id': 'us-east-1<br>:2e26918b-f7b1-471e- ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'locale': {'country':<br>'US', 'code': 'en_US', ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'$numberLong':<br>'1470183490480'} ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">_session.stop</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3.0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'cognito_id': 'us-<br>east-1:e96515c9-5824- ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'locale': {'country':<br>'GB', 'code': 'en_GB', ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'$numberLong':<br>'1470193238844'} ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">_session.start</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3.0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'cognito_id': 'us-<br>east-1:e96515c9-5824- ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'locale': {'country':<br>'GB', 'code': 'en_GB', ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'$numberLong':<br>'1470193278227'} ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">_session.stop</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3.0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'cognito_id': 'us-<br>east-1:e96515c9-5824- ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'locale': {'country':<br>'GB', 'code': 'en_GB', ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'$numberLong':<br>'1470193253960'} ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">_session.start</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3.0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'cognito_id': 'us-<br>east-1:e96515c9-5824- ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'locale': {'country':<br>'GB', 'code': 'en_GB', ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'$numberLong':<br>'1470193253959'} ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">_session.stop</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3.0</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'cognito_id': 'us-<br>east-1:e96515c9-5824- ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'locale': {'country':<br>'GB', 'code': 'en_GB', ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'$numberLong':<br>'1470193331291'} ...</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">_session.start</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3.0</td>
    </tr>
</table>
<table frame="box" rules="cols">
    <tr>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">metrics</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">session</th>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{}</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'start_timestamp':<br>{'$numberLong': ...</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{}</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'start_timestamp':<br>{'$numberLong': ...</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{}</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'start_timestamp':<br>{'$numberLong': ...</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{}</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'start_timestamp':<br>{'$numberLong': ...</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{}</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'start_timestamp':<br>{'$numberLong': ...</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{}</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'start_timestamp':<br>{'$numberLong': ...</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{}</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'start_timestamp':<br>{'$numberLong': ...</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{}</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'start_timestamp':<br>{'$numberLong': ...</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{}</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'start_timestamp':<br>{'$numberLong': ...</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{}</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">{'start_timestamp':<br>{'$numberLong': ...</td>
    </tr>
</table>
[155073 rows x 11 columns]<br/>Note: Only the head of the SFrame is printed.<br/>You can use print_rows(num_rows=m, num_columns=n) to print more rows and columns.
</div>




```python
user_cont
```




    dtype: dict
    Rows: 155073
    [{'Category': '120000', 'CustomerID': '4078', 'OfferID': '45436'}, {'MenuItem': 'OfferList', 'CustomerID': '4078'}, {'Category': 'Recharge', 'CustomerID': '4078'}, {'CustomerID': '4078'}, {}, {}, {}, {}, {}, {}, {}, {'MenuItem': 'DashBoard', 'CustomerID': '4079'}, {'CustomerID': '4079'}, {'CustomerID': '4079', 'HomePageSelection': 'Offline'}, {}, {}, {}, {'CustomerID': '4055'}, {}, {'CustomerID': '4055', 'OfferID': '26000'}, {'Category': '50000', 'CustomerID': '4055', 'OfferID': '26000'}, {}, {}, {}, {'Category': '50000', 'CustomerID': '4055', 'OfferID': '26000'}, {}, {'MenuItem': 'DashBoard', 'CustomerID': '4055'}, {}, {'Category': '50000', 'CustomerID': '4055', 'OfferID': '26000'}, {'CustomerID': '4055'}, {'MallID': '181', 'CustomerID': '4055'}, {'CustomerID': '4055', 'OfferID': '26000'}, {'MenuItem': 'OfferList', 'CustomerID': '4055'}, {'MenuItem': 'DashBoard', 'CustomerID': '4055'}, {'MenuItem': 'OfferList', 'CustomerID': '4055'}, {}, {}, {'MallID': '181', 'CustomerID': '4055'}, {'CustomerID': '4055', 'OfferID': '26000'}, {'MenuItem': 'DashBoard', 'CustomerID': '4055'}, {'CustomerID': '4055', 'OfferID': '26000'}, {'CustomerID': '4055', 'OfferID': '26000'}, {'CustomerID': '4055'}, {'CustomerID': '4055', 'OfferID': '26000'}, {}, {'CustomerID': '4055'}, {'MenuItem': 'OfferList', 'CustomerID': '4055'}, {}, {'CustomerID': '4055', 'OfferID': '26000'}, {'MallID': '181', 'CustomerID': '4055'}, {'Category': '50000', 'CustomerID': '4055', 'OfferID': '26000'}, {'Category': '50000', 'CustomerID': '4055', 'OfferID': '26000'}, {'CustomerID': '4081'}, {}, {'CustomerID': ' '}, {}, {'MenuItem': 'Search', 'CustomerID': '4081'}, {'CustomerID': '4081', 'HomePageSelection': 'All'}, {'MenuItem': 'DashBoard', 'CustomerID': '4081'}, {}, {'CustomerID': '4081'}, {}, {'CustomerID': '4081'}, {'MenuItem': 'OfferList', 'CustomerID': '4060'}, {'MenuItem': 'OfferList', 'CustomerID': '4060'}, {}, {'MenuItem': 'OfferList', 'CustomerID': '4060'}, {}, {'Category': '10000', 'CustomerID': '4060', 'OfferID': '49124'}, {'City': 'Mumbai', 'Area': ' Andheri East', 'PinCode': '400047', 'Road': '4,Andheri East', 'CustomerID': '4060'}, {'Category': 'Fashion', 'CustomerID': '4060'}, {'Category': 'Grocery', 'CustomerID': '4060'}, {'Category': '10000', 'CustomerID': '4060', 'OfferID': '49124'}, {'Category': '10000', 'CustomerID': '4060', 'OfferID': '46287'}, {'Category': '10000', 'CustomerID': '4060', 'OfferID': '49124'}, {'Category': 'Gifts', 'CustomerID': '4060'}, {'Category': '70000', 'CustomerID': '4060', 'OfferID': '44862'}, {'MallID': '193', 'CustomerID': '4060'}, {'MallID': '181', 'CustomerID': '4060'}, {'MenuItem': 'Category', 'CustomerID': '4060'}, {'Category': '70000', 'CustomerID': '4060', 'OfferID': '44862'}, {'MenuItem': 'DashBoard', 'CustomerID': '4060'}, {'Category': 'Recharge', 'CustomerID': '4060'}, {'MenuItem': 'OfferList', 'CustomerID': '4060'}, {'MenuItem': 'OfferList', 'CustomerID': '4060'}, {'CustomerID': '4060', 'HomePageSelection': 'Online'}, {'Category': '10000', 'CustomerID': '4060', 'OfferID': '46287'}, {'MenuItem': 'OfferList', 'CustomerID': '4060'}, {}, {'CustomerID': '4082'}, {}, {'City': 'Mumbai', 'Area': ' Powai', 'PinCode': '400072', 'Longitude': '72.8935654', 'Latitude': '19.1145723', 'CustomerID': '3908', 'Road': '54, Chandivali Farm Road,Chandivali'}, {}, {'CustomerID': ' '}, {'CustomerID': '71', 'ModeID': '105502940559970717177', 'Result': 'Success', 'Mode': 'Google'}, {'MenuItem': 'DashBoard', 'CustomerID': '71'}, {}, {}, {'MenuItem': 'DashBoard', 'CustomerID': '3908'}, {'CustomerID': ' '}, ... ]




```python
customer_id
```




    ['4078',
     '4055',
     '4055',
     '4055',
     '4055',
     '4055',
     '4055',
     '4055',
     '4055',
     '4055',
     '4055',
     '4055',
     '4055',
     '4060',
     '4060',
     '4060',
     '4060',
     '4060',
     '4060',
     '4060',
     '3908',
     '2270',
     '2270',
     '2270',
     '2270',
     '2270',
     '2270',
     '2270',
     '2270',
     '2270',
     '2270',
     '2270',
     '2270',
     '2270',
     '2270',
     '2270',
     '2270',
     '2270',
     '2270',
     '2270',
     '2270',
     '2270',
     '2270',
     '2270',
     '2270',
     '2270',
     '2270',
     '2270',
     '2270',
     '2270',
     '2270',
     '2270',
     '2270',
     '2270',
     '2270',
     '2270',
     '2270',
     '2270',
     '4062',
     '4062',
     '4062',
     '4062',
     '4062',
     '4062',
     '4062',
     '4062',
     '4062',
     '2251',
     '2251',
     '2251',
     '4000',
     '4000',
     '4000',
     '4000',
     '4000',
     '4000',
     '4000',
     '4000',
     '4000',
     '4000',
     '4000',
     '4000',
     '4000',
     '4000',
     '4075',
     '4000',
     '4075',
     '4075',
     '4076',
     '4076',
     '4076',
     '4074',
     '4074',
     '4074',
     '4074',
     '4074',
     '4077',
     '4077',
     '4062',
     '4062',
     '4062',
     '4062',
     '4062',
     '4062',
     '4062',
     '4062',
     '4062',
     '4062',
     '4062',
     '4062',
     '4062',
     '4062',
     '4062',
     '4062',
     '3908',
     '3908',
     '3908',
     '3908',
     '3908',
     '3908',
     '3908',
     '3908',
     '3908',
     '4078',
     '4078',
     '4078',
     '4062',
     '4062',
     '4064',
     '4064',
     '4064',
     '4066',
     '4066',
     '4066',
     '4066',
     '4066',
     '4066',
     '4066',
     '4066',
     '4066',
     '4066',
     '4066',
     '4066',
     '4066',
     '4066',
     '3943',
     '4068',
     '4068',
     '4068',
     '4068',
     '4056',
     '4069',
     '4069',
     '4069',
     '4069',
     '4069',
     '4069',
     '4069',
     '4069',
     '4069',
     '4069',
     '4069',
     '4069',
     '4069',
     '4069',
     '4069',
     '4069',
     '4069',
     '4069',
     '4069',
     '4069',
     '4069',
     '4069',
     '4069',
     '4069',
     '4069',
     '4069',
     '4069',
     '4069',
     '4069',
     '4069',
     '4069',
     '4069',
     '4069',
     '4071',
     '4071',
     '4071',
     '4071',
     '4071',
     '4071',
     '4071',
     '4071',
     '4068',
     '4068',
     '4068',
     '4068',
     '4068',
     '4073',
     '4073',
     '4073',
     '4073',
     '4073',
     '4073',
     '4073',
     '4045',
     '4045',
     '4045',
     '4045',
     '4045',
     '4045',
     '4045',
     '4045',
     '196',
     '196',
     '4047',
     '4048',
     '4048',
     '4048',
     '4049',
     '4049',
     '4049',
     '4049',
     '4049',
     '4049',
     '4049',
     '4049',
     '4049',
     '4049',
     '4049',
     '4049',
     '4050',
     '4050',
     '4050',
     '4052',
     '4052',
     '4052',
     '4016',
     '4016',
     '4055',
     '4055',
     '4055',
     '4055',
     '4055',
     '4055',
     '4055',
     '4056',
     '4058',
     '4058',
     '4058',
     '4058',
     '4058',
     '4061',
     '4061',
     '4061',
     '4061',
     '4061',
     '4061',
     '4061',
     '4061',
     '4061',
     '4061',
     '4061',
     '4061',
     '4061',
     '4061',
     '4061',
     '4061',
     '4061',
     '4061',
     '4061',
     '4061',
     '4034',
     '4035',
     '4035',
     '4035',
     '4035',
     '4035',
     '4035',
     '4035',
     '4035',
     '4035',
     '4035',
     '4035',
     '4035',
     '4035',
     '4035',
     '4035',
     '4035',
     '4035',
     '4035',
     '4035',
     '4035',
     '4036',
     '4036',
     '4036',
     '4037',
     '4037',
     '4038',
     '4038',
     '4038',
     '4038',
     '4038',
     '4040',
     '4040',
     '4040',
     '4040',
     '4040',
     '4040',
     '4040',
     '4040',
     '4040',
     '4040',
     '4040',
     '4040',
     '4040',
     '4040',
     '4040',
     '4040',
     '4040',
     '4040',
     '4042',
     '4020',
     '4020',
     '4020',
     '4020',
     '4020',
     '4043',
     '4043',
     '4043',
     '4043',
     '4043',
     '4043',
     '4043',
     '4043',
     '4043',
     '4043',
     '4039',
     '4039',
     '4039',
     '4016',
     '4016',
     '4016',
     '4016',
     '4016',
     '4000',
     '4000',
     '4017',
     '4017',
     '4017',
     '4017',
     '4017',
     '4017',
     '4017',
     '4017',
     '4018',
     '4018',
     '4019',
     '4019',
     '4019',
     '4019',
     '4021',
     '4021',
     '4021',
     '4021',
     '4021',
     '4021',
     '4021',
     '4021',
     '4021',
     '4021',
     '4021',
     '4021',
     '4021',
     '4021',
     '4021',
     '4021',
     '4021',
     '4021',
     '4021',
     '4024',
     '4019',
     '4019',
     '4019',
     '4019',
     '4019',
     '4019',
     '3968',
     '3968',
     '3968',
     '3968',
     '3968',
     '3968',
     '3968',
     '3968',
     '3968',
     '4027',
     '4027',
     '4027',
     '4027',
     '4027',
     '4027',
     '4027',
     '4027',
     '4027',
     '4027',
     '4027',
     '4027',
     '4027',
     '4027',
     '4027',
     '4027',
     '4019',
     '4019',
     '4019',
     '4019',
     '4019',
     '4019',
     '4019',
     '4019',
     '4029',
     '4029',
     '4029',
     '4029',
     '4025',
     '4010',
     '4010',
     '4010',
     '4010',
     '4010',
     '4010',
     '4010',
     '4010',
     '4010',
     '4010',
     '4010',
     '4010',
     '4010',
     '4010',
     '4010',
     '4010',
     '4010',
     '4010',
     '3995',
     '3995',
     '3995',
     '4011',
     '4011',
     '4011',
     '4011',
     '4011',
     '4011',
     '4011',
     '4011',
     '4011',
     '3995',
     '4012',
     '4012',
     '4012',
     '4012',
     '4012',
     '4012',
     '4012',
     '4012',
     '4014',
     '4014',
     '4014',
     '4014',
     '4014',
     '4014',
     '4014',
     '4014',
     '4014',
     '4014',
     '4014',
     '4014',
     '4014',
     '4014',
     '4014',
     '4014',
     '4014',
     '4014',
     '4014',
     '4014',
     '4014',
     '4014',
     '4014',
     '4014',
     '4014',
     '4014',
     '4014',
     '4014',
     '4014',
     '4014',
     '4014',
     '4014',
     '4014',
     '4014',
     '4014',
     '4014',
     '4014',
     '4014',
     '4014',
     '4014',
     '4014',
     '4014',
     '4014',
     '4014',
     '4014',
     '4014',
     '4014',
     '4014',
     '4014',
     '4014',
     '4014',
     '4014',
     '4014',
     '4014',
     '4014',
     '4014',
     '3996',
     '3996',
     '3996',
     '4000',
     '4000',
     '4000',
     '4000',
     '4000',
     '4000',
     '4000',
     '4000',
     '4000',
     '4000',
     '4000',
     '4000',
     '4000',
     '4000',
     '4000',
     '4000',
     '4000',
     '4000',
     '4001',
     '4001',
     '4001',
     '4001',
     '4001',
     '4001',
     '4001',
     '4001',
     '4002',
     '4005',
     '4005',
     '4005',
     '4006',
     '4006',
     '4006',
     '4006',
     '4007',
     '4007',
     '3995',
     '3995',
     '3995',
     '3995',
     '3995',
     '4008',
     '4008',
     '4008',
     '4008',
     '4008',
     '4008',
     '4008',
     '4008',
     '4008',
     '4008',
     '2251',
     '2251',
     '2251',
     '2251',
     '2251',
     '2251',
     '2251',
     '3989',
     '3989',
     '3989',
     '3989',
     '3989',
     '3989',
     '3989',
     '3963',
     '3963',
     '3963',
     '3963',
     '3963',
     '3995',
     '3995',
     '3995',
     '3995',
     '3995',
     '3995',
     '3995',
     '3995',
     '3995',
     '3995',
     '3995',
     '3995',
     '3995',
     '3985',
     '3996',
     '3996',
     '3996',
     '3996',
     '3996',
     '3996',
     '3996',
     '3996',
     '3996',
     '3996',
     '3996',
     '3998',
     '3998',
     '3998',
     '3998',
     '3998',
     '3998',
     '3998',
     '3998',
     '3998',
     '3998',
     '3998',
     '3998',
     '3998',
     '3998',
     '3998',
     '3998',
     '3998',
     '3998',
     '3998',
     '3998',
     '3998',
     '3998',
     '3998',
     '3998',
     '3998',
     '3998',
     '3998',
     '3998',
     '3987',
     '3987',
     '3987',
     '3987',
     '3987',
     '2251',
     '2251',
     '2251',
     '2251',
     '2251',
     '2251',
     '3987',
     '3987',
     '3987',
     '3987',
     '3987',
     '3988',
     '3988',
     '3988',
     '3989',
     '3989',
     '3989',
     '3989',
     '3989',
     '3989',
     '3989',
     '3989',
     '3989',
     '3989',
     '3989',
     '3989',
     '3989',
     '3989',
     '3989',
     '3963',
     '3963',
     '3963',
     '3991',
     '3991',
     '3991',
     '3991',
     '3985',
     '3985',
     '3985',
     '3985',
     '3985',
     '3985',
     '3985',
     '3985',
     '3985',
     '3985',
     '3985',
     '3944',
     '3944',
     '3944',
     '3976',
     '3976',
     '3981',
     '3981',
     '3981',
     '3981',
     '3981',
     '3981',
     '3981',
     '3981',
     '3981',
     '3981',
     '3981',
     '3981',
     '3981',
     '3981',
     '3981',
     '3981',
     '3981',
     '3981',
     '3981',
     '3981',
     '3981',
     '3981',
     '3981',
     '3981',
     '3981',
     '3981',
     '3981',
     '3981',
     '3981',
     '3981',
     '3981',
     '3981',
     '3981',
     '3981',
     '3984',
     '3985',
     '3985',
     '3985',
     '3985',
     '3985',
     '3985',
     '3985',
     '3985',
     '3985',
     '3985',
     '3985',
     '3985',
     '3985',
     '3985',
     '3985',
     '3985',
     '3985',
     '3981',
     '3981',
     '3981',
     '3981',
     '3981',
     '3981',
     '3981',
     '3981',
     '3981',
     '3981',
     '3981',
     '3981',
     '3981',
     '3981',
     '3981',
     '3981',
     '3981',
     '3981',
     '3981',
     '3981',
     '3981',
     '3981',
     '3981',
     '3981',
     '3981',
     '3981',
     '3981',
     '3981',
     '3981',
     '3981',
     '3981',
     '3981',
     '3981',
     '3981',
     '3981',
     '3981',
     '3981',
     '3981',
     '3981',
     '3981',
     '3981',
     '3981',
     '3986',
     '3986',
     '3986',
     '3986',
     '3986',
     '3986',
     '3986',
     '3986',
     '3986',
     '3986',
     '3986',
     '3986',
     '3986',
     '3986',
     '3986',
     '3986',
     '3986',
     '3986',
     '3986',
     '3986',
     '3951',
     '3951',
     '3964',
     '3964',
     '3964',
     '3964',
     '3964',
     '3964',
     '3964',
     '3964',
     '3964',
     '3964',
     '3964',
     '3964',
     '3964',
     '3964',
     '3964',
     '3964',
     '3964',
     '3964',
     '3964',
     '3964',
     '3964',
     '3964',
     '3964',
     '3964',
     '3964',
     '3964',
     '3968',
     '3970',
     '3970',
     '3970',
     '3971',
     '3972',
     '3972',
     '3972',
     '3971',
     '3971',
     '3972',
     '3972',
     '3972',
     '3973',
     '3973',
     '3973',
     '3973',
     '3973',
     '3973',
     '3973',
     '3973',
     '3972',
     '3972',
     '3972',
     '3973',
     '3973',
     '3973',
     '3973',
     '3973',
     '3973',
     '3973',
     '3973',
     '3973',
     '3973',
     '3973',
     '3973',
     '3973',
     '3973',
     '3973',
     '3973',
     '3973',
     '3973',
     '3973',
     '3973',
     '3973',
     '3975',
     '3976',
     '3976',
     '3976',
     '3976',
     '3976',
     '3976',
     '3976',
     '3978',
     '3978',
     '3978',
     '3978',
     '3978',
     '3978',
     '3978',
     '3978',
     '3978',
     '3978',
     '3978',
     '3980',
     '3980',
     '3821',
     '3821',
     '3964',
     '3964',
     '3964',
     '3964',
     '3964',
     '3964',
     '3964',
     '3964',
     '3964',
     '3964',
     '3964',
     '3964',
     '3964',
     '3964',
     '3964',
     '3964',
     '3964',
     '3964',
     '3964',
     '3964',
     '3965',
     '3965',
     '3965',
     '3965',
     '3965',
     '3965',
     '3965',
     '3965',
     '3967',
     '3967',
     '3967',
     '3967',
     '3967',
     '3967',
     '3967',
     '3967',
     '3957',
     '3957',
     '3957',
     '3957',
     '3957',
     '3957',
     '3957',
     '3957',
     '3957',
     '3957',
     '3907',
     '3907',
     '3907',
     '3907',
     '3907',
     '3944',
     '3944',
     '3944',
     '3944',
     '3944',
     '3944',
     '22',
     '22',
     '3949',
     '3950',
     '3950',
     '3950',
     '3950',
     '3950',
     '3950',
     '3952',
     '3952',
     '3952',
     '3952',
     '3952',
     '3952',
     '3952',
     '3952',
     '3952',
     '3949',
     '3954',
     '3777',
     '3777',
     '3777',
     '3777',
     '3777',
     '3777',
     '3777',
     '3777',
     '3777',
     '3777',
     '3777',
     ...]




```python
len(customer_id)
```




    26312




```python
offer_id
```




    ['45436',
     '26000',
     '26000',
     '26000',
     '26000',
     '26000',
     '26000',
     '26000',
     '26000',
     '26000',
     '26000',
     '26000',
     '26000',
     '49124',
     '49124',
     '46287',
     '49124',
     '44862',
     '44862',
     '46287',
     '16067',
     '49340',
     '49329',
     '37819',
     '42609',
     '49327',
     '47607',
     '48725',
     '49322',
     '49330',
     '37819',
     '49331',
     '47607',
     '49339',
     '49331',
     '42609',
     '49325',
     '49340',
     '49197',
     '48725',
     '49330',
     '49338',
     '43621',
     '49338',
     '43621',
     '49337',
     '49325',
     '49326',
     '49322',
     '49197',
     '49339',
     '49336',
     '49336',
     '49329',
     '49327',
     '49329',
     '49326',
     '49337',
     '45227',
     '49349',
     '47303',
     '47303',
     '47303',
     '47303',
     '29759',
     '49349',
     '29759',
     '39319',
     '39315',
     '39319',
     '26198',
     '26199',
     '31719',
     '26203',
     '26193',
     '26199',
     '26203',
     '26198',
     '26204',
     '26193',
     '26205',
     '26206',
     '31719',
     '31719',
     '30687',
     '42593',
     '30687',
     '49070',
     '47303',
     '47303',
     '47303',
     '20459',
     '32321',
     '32321',
     '20459',
     '20459',
     '11846',
     '11846',
     '47303',
     '47303',
     '49069',
     '49069',
     '49070',
     '49070',
     '38665',
     '38665',
     '49349',
     '47303',
     '49348',
     '47303',
     '49348',
     '47303',
     '49349',
     '45227',
     '28943,29067,28939,29071,28754,28938,26000,28940,29070,29066,26260,32837,32778,32830,32998,29065,26280,33001,29069,32592,29073,29072,29068,26258,26259,',
     '37818,37819,44371,33292,49127,39831,39763,42696,39933,45532,45533,45303,45304,46849,46850,46851,47607,23080,47734,46558,45531,47681,30976,48139,44748,',
     '26098,28644,',
     '33292,48169,47559,40498,42607,',
     '17379,26000,26024,28644,',
     '48840,49069,47303,46250,45436,',
     '44393,46849,46591,41028,41031,36349,32269,32927,29827,29821,46012,29515,46593,33049,33996,46011,',
     '42593',
     '46850,45304,29477,29499,46851,29516,39933,29500,29511,39831,45533,37819,45303,33292,29510,28644,29513,37818,45532,29514,39763,44371,46849,42696,',
     '49336',
     '49336',
     '49336',
     '46257',
     '46257',
     '24977',
     '24977',
     '21024',
     '29515',
     '26580',
     '26578',
     '26573',
     '26574',
     '26575',
     '26576',
     '26579',
     '26000',
     '26594',
     '26594',
     '26579',
     '26000',
     '29515',
     '20097',
     '32773',
     '32773',
     '32773',
     '32773',
     '42593',
     '37819',
     '43887',
     '43887',
     '46558',
     '43887',
     '43887',
     '48139',
     '48139',
     '37819',
     '33292',
     '46558',
     '48139',
     '40827',
     '40827',
     '40827',
     '46011',
     '42593',
     '46011',
     '30619',
     '33996',
     '33996',
     '33996',
     '33996',
     '30619',
     '26146',
     '39319',
     '26298',
     '26626',
     '26465',
     '41331',
     '41331',
     '41331',
     '39319',
     '42593',
     '40498',
     '29658',
     '29658',
     '42607',
     '47559',
     '29658',
     '33292',
     '28644',
     '28644',
     '28644',
     '28644',
     '26098',
     '47303',
     '45931',
     '45932',
     '45930',
     '45931',
     '45930',
     '45930',
     '43887',
     '26298',
     '26626',
     '43887',
     '26146',
     '26211',
     '26465',
     '26211',
     '16148',
     '16148',
     '46243',
     '45969',
     '45969',
     '42825',
     '45950',
     '47303',
     '45340',
     '45950',
     '47303',
     '45950',
     '45950',
     '45335',
     '45340',
     '45335',
     '45340',
     '45340',
     '47303',
     '47303',
     '47303',
     '46260',
     '46260',
     '46260',
     '37274',
     '37274',
     '26146',
     '26298',
     '26626',
     '26000',
     '26465',
     '26000',
     '26000',
     '49069',
     '45957',
     '43887',
     '42593',
     '45957',
     '42593',
     '23080',
     '23080',
     '26465',
     '26298',
     '23080',
     '23080',
     '26626',
     '26146',
     '46259',
     '33292',
     '33292',
     '32528',
     '32528',
     '49069',
     '48840',
     '49069',
     '49069',
     '48840',
     '46259',
     '49069',
     '33885',
     '26626',
     '26298',
     '26146',
     '45620',
     '26465',
     '45620',
     '26465',
     '26626',
     '47978',
     '47981',
     '26298',
     '26626',
     '42593',
     '26146',
     '47981',
     '26298',
     '26146',
     '30617',
     '47978',
     '26465',
     '45953',
     '45227',
     '45953',
     '26000',
     '26000',
     '28041',
     '42593',
     '28041',
     '28270',
     '28062',
     '49068',
     '49068',
     '49067',
     '49067',
     '49067',
     '49067',
     '45949',
     '49067',
     '49070',
     '48172',
     '48172',
     '49070',
     '49067',
     '49069',
     '49069',
     '45949',
     '45949',
     '45949',
     '42593',
     '48858',
     '48855',
     '48858',
     '48858',
     '48858',
     '39316',
     '39316',
     '39316',
     '42438',
     '30617',
     '26146',
     '26298',
     '42593',
     '26465',
     '26626',
     '42593',
     '28913',
     '28913',
     '37274',
     '45626',
     '45626',
     '46885',
     '46885',
     '17379',
     '17379',
     '11844',
     '49133',
     '29739',
     '29739',
     '11844',
     '11844',
     '11844',
     '11844',
     '26016',
     '26016',
     '20855',
     '20855',
     '24391',
     '24391',
     '39319',
     '39319',
     '39319',
     '39319',
     '39319',
     '47622',
     '39319',
     '39319',
     '48281',
     '48281',
     '48281',
     '48281',
     '48281',
     '48281',
     '48645',
     '48645',
     '48645',
     '39319',
     '39319',
     '45950',
     '34461',
     '34461',
     '44237',
     '44237',
     '44237',
     '44237',
     '26360',
     '26631',
     '26360',
     '26631',
     '26370',
     '26000',
     '29515',
     '26000',
     '26370',
     '11845',
     '11845',
     '45337',
     '48426',
     '48426',
     '45337',
     '11844',
     '11850',
     '43621',
     '11846',
     '11850',
     '11846',
     '11844',
     '11850',
     '43621',
     '43621',
     '20087',
     '20087',
     '42593',
     '32831',
     '32831',
     '32833',
     '32833',
     '42593',
     '17379',
     '17379',
     '26000',
     '26000',
     '42593',
     '20089',
     '20089',
     '42593',
     '30617',
     '26626',
     '26465',
     '26146',
     '42593',
     '26298',
     '22674',
     '26298',
     '26146',
     '26465',
     '30617',
     '26626',
     '42593',
     '42593',
     '22674',
     '26844',
     '42593',
     '26844',
     '45961',
     '45961',
     '45953',
     '45953',
     '45961',
     '45961',
     '40322',
     '40322',
     '40322',
     '42593',
     '30617',
     '29442',
     '28644',
     '28644',
     '28644',
     '28644',
     '42593',
     '29442',
     '45949',
     '40322',
     '45227',
     '45227',
     '45229',
     '40322',
     '40322',
     '40322',
     '40322',
     '45955',
     '46258',
     '46256',
     '45953',
     '46260',
     '46260',
     '45952',
     '46260',
     '45961',
     '46260',
     '45957',
     '46259',
     '46257',
     '45951',
     '45958',
     '45957',
     '48420',
     '47565',
     '40322',
     '45229',
     '38665',
     '46260',
     '46261',
     '46260',
     '47303',
     '46256',
     '45953',
     '46258',
     '45951',
     '45949',
     '48886',
     '45955',
     '45227',
     '45953',
     '46257',
     '45950',
     '45961',
     '46882',
     '45953',
     '45953',
     '45952',
     '46259',
     '46570',
     '40322',
     '45229',
     '40322',
     '40322',
     '30364',
     '30364',
     '45970',
     '20616',
     '42593',
     '20459',
     '20459',
     '20459',
     '20616',
     '31642',
     '31642',
     '31642',
     '26724',
     '20242',
     '12599',
     '31642',
     '31642',
     '26724',
     '20242',
     '31642',
     '12599',
     '47981',
     '47981',
     '47981',
     '43887',
     '43887',
     '43887',
     '43887',
     '43887',
     '29067',
     '47873',
     '47873',
     '47873',
     '26465',
     '26298',
     '26146',
     '26626',
     '45958',
     '45958',
     '26849',
     '24376',
     '26846',
     '24376',
     '26846',
     '45917',
     '45918',
     '46250',
     '46250',
     '45917',
     '45953',
     '45953',
     '45918',
     '45951',
     '45951',
     '39315',
     '26465',
     '26146',
     '30944',
     '30944',
     '26298',
     '26626',
     '46540',
     '46541',
     '46536',
     '46540',
     '46541',
     '46541',
     '46541',
     '26000',
     '42593',
     '29442',
     '29442',
     '30547',
     '26198',
     '26198',
     '28094',
     '26000',
     '28094',
     '26000',
     '26849',
     '26183',
     '20459',
     '20459',
     '26183',
     '20459',
     '20459',
     '47113',
     '45970',
     '42593',
     '26465',
     '26626',
     '26146',
     '26298',
     '30617',
     '26465',
     '26626',
     '26298',
     '26146',
     '46260',
     '46260',
     '46257',
     '46260',
     '46260',
     '46260',
     '46260',
     '46260',
     '46260',
     '46257',
     '46260',
     '46260',
     '46260',
     '46257',
     '46257',
     '46260',
     '46260',
     '46260',
     '46260',
     '46260',
     '46260',
     '46260',
     '46260',
     '46260',
     '46260',
     '46260',
     '46260',
     '46260',
     '46253',
     '46253',
     '46253',
     '48169',
     '48169',
     '29065',
     '29065',
     '29065',
     '29065',
     '29065',
     '29065',
     '33292',
     '20459',
     '33292',
     '20459',
     '33292',
     '42593',
     '30364',
     '30364',
     '47367',
     '47274',
     '47367',
     '45874',
     '45874',
     '45909',
     '45914',
     '47274',
     '41951',
     '41951',
     '45909',
     '45914',
     '45914',
     '45914',
     '46536',
     '26000',
     '47556',
     '47556',
     '26318',
     '26318',
     '26280',
     '26280',
     '48203',
     '48203',
     '45931',
     '45932',
     '45932',
     '48203',
     '48203',
     '47113',
     '45917',
     '45917',
     '39319',
     '45932',
     '45932',
     '45932',
     '46260',
     '46260',
     '37818',
     '44371',
     '37818',
     '11927',
     '11927',
     '11927',
     '37819',
     '11927',
     '37818',
     '37819',
     '11927',
     '37818',
     '44371',
     '12496',
     '12496',
     '12575',
     '12575',
     '12671',
     '12575',
     '38689',
     '12575',
     '32528',
     '32528',
     '32528',
     '12678',
     '12678',
     '38689',
     '38689',
     '47886',
     '48540',
     '47886',
     '48540',
     '48540',
     '45337',
     '47873',
     '40507',
     '39553',
     '39553',
     '40507',
     '48203',
     '48203',
     '45958',
     '45958',
     '45917',
     '45961',
     '45961',
     '45917',
     '47113',
     '48203',
     '45918',
     '47113',
     '45918',
     '45744',
     '45337',
     '45744',
     '45742',
     '45742',
     '20113',
     '20113',
     '12496',
     '45747',
     '38617',
     '12496',
     '38617',
     '47558',
     '47558',
     '45747',
     '45748',
     '45748',
     '37818',
     '44371',
     '44371',
     '37819',
     '37819',
     '37818',
     '44371',
     '44371',
     '37818',
     '37818',
     '46035',
     '46849',
     '45741',
     '46858',
     '46849',
     '46035',
     '45744',
     '45744',
     '42982',
     '42982',
     '45741',
     '45337',
     '47886',
     '46858',
     '47886',
     '45955',
     '26146',
     '26626',
     '26298',
     '30617',
     '26465',
     '42593',
     '27113',
     '27113',
     '46258',
     '40322',
     '45961',
     '45961',
     '45950',
     '45950',
     '46260',
     '46258',
     '46260',
     '40322',
     '45955',
     '26132',
     '26132',
     '42607',
     '26465',
     '26626',
     '42607',
     '42609',
     '42593',
     '45576',
     '29740',
     '45576',
     '29740',
     '26379',
     '26146',
     '30617',
     '26298',
     '28049',
     '26375',
     '28002',
     '26375',
     '28002',
     '26379',
     '26356',
     '26356',
     '28049',
     '24495',
     '42609',
     '42593',
     '42593',
     '33747',
     '33308',
     '33747',
     '29477',
     '11834',
     '11834',
     '11834',
     '29477',
     '29477',
     '11850',
     '11850',
     '11850',
     '42593',
     '42593',
     '26146',
     '26626',
     '26298',
     '30617',
     '42593',
     '26465',
     '46759',
     '46759',
     '46759',
     '40415',
     '40415',
     '20737',
     '19871',
     '19871',
     '19372',
     '19372',
     '42593',
     '20742',
     '15937',
     '35170',
     '35170',
     '15937',
     '20742',
     '28644',
     '20288',
     '20288',
     '20737',
     '28644',
     '20742',
     '20742',
     '11836',
     '38665',
     '45961',
     '45961',
     '45958',
     '38665',
     '38665',
     '45958',
     '48420',
     '48420',
     '46260',
     '46260',
     '48420',
     '46257',
     '48203',
     '48203',
     '40685',
     '46257',
     '40685',
     '30617',
     '45335',
     '28943',
     '26258',
     '42593',
     '44371',
     '44371',
     '46929',
     '46929',
     '46929',
     '44371',
     '46929',
     '37819',
     '44371',
     '40824',
     '37819',
     '12768',
     '44409',
     '44409',
     '26849',
     '26849',
     '44409',
     '42593',
     '12768',
     '26221',
     '26221',
     '39114',
     '39114',
     '26221',
     '48027',
     '39114',
     '48027',
     '48477',
     '46424',
     '48477',
     '47942',
     '48477',
     '43887',
     '47942',
     '43887',
     '34974',
     '34974',
     '26238',
     '26000',
     '26238',
     '26000',
     '26069',
     '26069',
     '28017',
     '28017',
     '26146',
     '26298',
     '26465',
     '26626',
     '42593',
     '45932',
     '45932',
     '45932',
     '45932',
     '45932',
     '45932',
     '26425',
     '26425',
     '42593',
     '35176',
     '30458',
     '20850',
     '20850',
     '30458',
     '35176',
     '47565',
     '47565',
     '46257',
     '47303',
     '40322',
     '40322',
     '40322',
     '46257',
     '47303',
     '42593',
     '42593',
     '42044',
     '42044',
     '42044',
     '42044',
     '45918',
     '40322',
     '47251',
     '40322',
     '45918',
     '45918',
     '47251',
     ...]




```python
len(offer_id)
```




    26312



** Now, for predicting the offers, we have to consider two features- offer_id and customer_id**


```python
features = {
    "CustomerID": customer_id, "OfferID": offer_id
}
```


```python
features
```




    {'CustomerID': ['4078',
      '4055',
      '4055',
      '4055',
      '4055',
      '4055',
      '4055',
      '4055',
      '4055',
      '4055',
      '4055',
      '4055',
      '4055',
      '4060',
      '4060',
      '4060',
      '4060',
      '4060',
      '4060',
      '4060',
      '3908',
      '2270',
      '2270',
      '2270',
      '2270',
      '2270',
      '2270',
      '2270',
      '2270',
      '2270',
      '2270',
      '2270',
      '2270',
      '2270',
      '2270',
      '2270',
      '2270',
      '2270',
      '2270',
      '2270',
      '2270',
      '2270',
      '2270',
      '2270',
      '2270',
      '2270',
      '2270',
      '2270',
      '2270',
      '2270',
      '2270',
      '2270',
      '2270',
      '2270',
      '2270',
      '2270',
      '2270',
      '2270',
      '4062',
      '4062',
      '4062',
      '4062',
      '4062',
      '4062',
      '4062',
      '4062',
      '4062',
      '2251',
      '2251',
      '2251',
      '4000',
      '4000',
      '4000',
      '4000',
      '4000',
      '4000',
      '4000',
      '4000',
      '4000',
      '4000',
      '4000',
      '4000',
      '4000',
      '4000',
      '4075',
      '4000',
      '4075',
      '4075',
      '4076',
      '4076',
      '4076',
      '4074',
      '4074',
      '4074',
      '4074',
      '4074',
      '4077',
      '4077',
      '4062',
      '4062',
      '4062',
      '4062',
      '4062',
      '4062',
      '4062',
      '4062',
      '4062',
      '4062',
      '4062',
      '4062',
      '4062',
      '4062',
      '4062',
      '4062',
      '3908',
      '3908',
      '3908',
      '3908',
      '3908',
      '3908',
      '3908',
      '3908',
      '3908',
      '4078',
      '4078',
      '4078',
      '4062',
      '4062',
      '4064',
      '4064',
      '4064',
      '4066',
      '4066',
      '4066',
      '4066',
      '4066',
      '4066',
      '4066',
      '4066',
      '4066',
      '4066',
      '4066',
      '4066',
      '4066',
      '4066',
      '3943',
      '4068',
      '4068',
      '4068',
      '4068',
      '4056',
      '4069',
      '4069',
      '4069',
      '4069',
      '4069',
      '4069',
      '4069',
      '4069',
      '4069',
      '4069',
      '4069',
      '4069',
      '4069',
      '4069',
      '4069',
      '4069',
      '4069',
      '4069',
      '4069',
      '4069',
      '4069',
      '4069',
      '4069',
      '4069',
      '4069',
      '4069',
      '4069',
      '4069',
      '4069',
      '4069',
      '4069',
      '4069',
      '4069',
      '4071',
      '4071',
      '4071',
      '4071',
      '4071',
      '4071',
      '4071',
      '4071',
      '4068',
      '4068',
      '4068',
      '4068',
      '4068',
      '4073',
      '4073',
      '4073',
      '4073',
      '4073',
      '4073',
      '4073',
      '4045',
      '4045',
      '4045',
      '4045',
      '4045',
      '4045',
      '4045',
      '4045',
      '196',
      '196',
      '4047',
      '4048',
      '4048',
      '4048',
      '4049',
      '4049',
      '4049',
      '4049',
      '4049',
      '4049',
      '4049',
      '4049',
      '4049',
      '4049',
      '4049',
      '4049',
      '4050',
      '4050',
      '4050',
      '4052',
      '4052',
      '4052',
      '4016',
      '4016',
      '4055',
      '4055',
      '4055',
      '4055',
      '4055',
      '4055',
      '4055',
      '4056',
      '4058',
      '4058',
      '4058',
      '4058',
      '4058',
      '4061',
      '4061',
      '4061',
      '4061',
      '4061',
      '4061',
      '4061',
      '4061',
      '4061',
      '4061',
      '4061',
      '4061',
      '4061',
      '4061',
      '4061',
      '4061',
      '4061',
      '4061',
      '4061',
      '4061',
      '4034',
      '4035',
      '4035',
      '4035',
      '4035',
      '4035',
      '4035',
      '4035',
      '4035',
      '4035',
      '4035',
      '4035',
      '4035',
      '4035',
      '4035',
      '4035',
      '4035',
      '4035',
      '4035',
      '4035',
      '4035',
      '4036',
      '4036',
      '4036',
      '4037',
      '4037',
      '4038',
      '4038',
      '4038',
      '4038',
      '4038',
      '4040',
      '4040',
      '4040',
      '4040',
      '4040',
      '4040',
      '4040',
      '4040',
      '4040',
      '4040',
      '4040',
      '4040',
      '4040',
      '4040',
      '4040',
      '4040',
      '4040',
      '4040',
      '4042',
      '4020',
      '4020',
      '4020',
      '4020',
      '4020',
      '4043',
      '4043',
      '4043',
      '4043',
      '4043',
      '4043',
      '4043',
      '4043',
      '4043',
      '4043',
      '4039',
      '4039',
      '4039',
      '4016',
      '4016',
      '4016',
      '4016',
      '4016',
      '4000',
      '4000',
      '4017',
      '4017',
      '4017',
      '4017',
      '4017',
      '4017',
      '4017',
      '4017',
      '4018',
      '4018',
      '4019',
      '4019',
      '4019',
      '4019',
      '4021',
      '4021',
      '4021',
      '4021',
      '4021',
      '4021',
      '4021',
      '4021',
      '4021',
      '4021',
      '4021',
      '4021',
      '4021',
      '4021',
      '4021',
      '4021',
      '4021',
      '4021',
      '4021',
      '4024',
      '4019',
      '4019',
      '4019',
      '4019',
      '4019',
      '4019',
      '3968',
      '3968',
      '3968',
      '3968',
      '3968',
      '3968',
      '3968',
      '3968',
      '3968',
      '4027',
      '4027',
      '4027',
      '4027',
      '4027',
      '4027',
      '4027',
      '4027',
      '4027',
      '4027',
      '4027',
      '4027',
      '4027',
      '4027',
      '4027',
      '4027',
      '4019',
      '4019',
      '4019',
      '4019',
      '4019',
      '4019',
      '4019',
      '4019',
      '4029',
      '4029',
      '4029',
      '4029',
      '4025',
      '4010',
      '4010',
      '4010',
      '4010',
      '4010',
      '4010',
      '4010',
      '4010',
      '4010',
      '4010',
      '4010',
      '4010',
      '4010',
      '4010',
      '4010',
      '4010',
      '4010',
      '4010',
      '3995',
      '3995',
      '3995',
      '4011',
      '4011',
      '4011',
      '4011',
      '4011',
      '4011',
      '4011',
      '4011',
      '4011',
      '3995',
      '4012',
      '4012',
      '4012',
      '4012',
      '4012',
      '4012',
      '4012',
      '4012',
      '4014',
      '4014',
      '4014',
      '4014',
      '4014',
      '4014',
      '4014',
      '4014',
      '4014',
      '4014',
      '4014',
      '4014',
      '4014',
      '4014',
      '4014',
      '4014',
      '4014',
      '4014',
      '4014',
      '4014',
      '4014',
      '4014',
      '4014',
      '4014',
      '4014',
      '4014',
      '4014',
      '4014',
      '4014',
      '4014',
      '4014',
      '4014',
      '4014',
      '4014',
      '4014',
      '4014',
      '4014',
      '4014',
      '4014',
      '4014',
      '4014',
      '4014',
      '4014',
      '4014',
      '4014',
      '4014',
      '4014',
      '4014',
      '4014',
      '4014',
      '4014',
      '4014',
      '4014',
      '4014',
      '4014',
      '4014',
      '3996',
      '3996',
      '3996',
      '4000',
      '4000',
      '4000',
      '4000',
      '4000',
      '4000',
      '4000',
      '4000',
      '4000',
      '4000',
      '4000',
      '4000',
      '4000',
      '4000',
      '4000',
      '4000',
      '4000',
      '4000',
      '4001',
      '4001',
      '4001',
      '4001',
      '4001',
      '4001',
      '4001',
      '4001',
      '4002',
      '4005',
      '4005',
      '4005',
      '4006',
      '4006',
      '4006',
      '4006',
      '4007',
      '4007',
      '3995',
      '3995',
      '3995',
      '3995',
      '3995',
      '4008',
      '4008',
      '4008',
      '4008',
      '4008',
      '4008',
      '4008',
      '4008',
      '4008',
      '4008',
      '2251',
      '2251',
      '2251',
      '2251',
      '2251',
      '2251',
      '2251',
      '3989',
      '3989',
      '3989',
      '3989',
      '3989',
      '3989',
      '3989',
      '3963',
      '3963',
      '3963',
      '3963',
      '3963',
      '3995',
      '3995',
      '3995',
      '3995',
      '3995',
      '3995',
      '3995',
      '3995',
      '3995',
      '3995',
      '3995',
      '3995',
      '3995',
      '3985',
      '3996',
      '3996',
      '3996',
      '3996',
      '3996',
      '3996',
      '3996',
      '3996',
      '3996',
      '3996',
      '3996',
      '3998',
      '3998',
      '3998',
      '3998',
      '3998',
      '3998',
      '3998',
      '3998',
      '3998',
      '3998',
      '3998',
      '3998',
      '3998',
      '3998',
      '3998',
      '3998',
      '3998',
      '3998',
      '3998',
      '3998',
      '3998',
      '3998',
      '3998',
      '3998',
      '3998',
      '3998',
      '3998',
      '3998',
      '3987',
      '3987',
      '3987',
      '3987',
      '3987',
      '2251',
      '2251',
      '2251',
      '2251',
      '2251',
      '2251',
      '3987',
      '3987',
      '3987',
      '3987',
      '3987',
      '3988',
      '3988',
      '3988',
      '3989',
      '3989',
      '3989',
      '3989',
      '3989',
      '3989',
      '3989',
      '3989',
      '3989',
      '3989',
      '3989',
      '3989',
      '3989',
      '3989',
      '3989',
      '3963',
      '3963',
      '3963',
      '3991',
      '3991',
      '3991',
      '3991',
      '3985',
      '3985',
      '3985',
      '3985',
      '3985',
      '3985',
      '3985',
      '3985',
      '3985',
      '3985',
      '3985',
      '3944',
      '3944',
      '3944',
      '3976',
      '3976',
      '3981',
      '3981',
      '3981',
      '3981',
      '3981',
      '3981',
      '3981',
      '3981',
      '3981',
      '3981',
      '3981',
      '3981',
      '3981',
      '3981',
      '3981',
      '3981',
      '3981',
      '3981',
      '3981',
      '3981',
      '3981',
      '3981',
      '3981',
      '3981',
      '3981',
      '3981',
      '3981',
      '3981',
      '3981',
      '3981',
      '3981',
      '3981',
      '3981',
      '3981',
      '3984',
      '3985',
      '3985',
      '3985',
      '3985',
      '3985',
      '3985',
      '3985',
      '3985',
      '3985',
      '3985',
      '3985',
      '3985',
      '3985',
      '3985',
      '3985',
      '3985',
      '3985',
      '3981',
      '3981',
      '3981',
      '3981',
      '3981',
      '3981',
      '3981',
      '3981',
      '3981',
      '3981',
      '3981',
      '3981',
      '3981',
      '3981',
      '3981',
      '3981',
      '3981',
      '3981',
      '3981',
      '3981',
      '3981',
      '3981',
      '3981',
      '3981',
      '3981',
      '3981',
      '3981',
      '3981',
      '3981',
      '3981',
      '3981',
      '3981',
      '3981',
      '3981',
      '3981',
      '3981',
      '3981',
      '3981',
      '3981',
      '3981',
      '3981',
      '3981',
      '3986',
      '3986',
      '3986',
      '3986',
      '3986',
      '3986',
      '3986',
      '3986',
      '3986',
      '3986',
      '3986',
      '3986',
      '3986',
      '3986',
      '3986',
      '3986',
      '3986',
      '3986',
      '3986',
      '3986',
      '3951',
      '3951',
      '3964',
      '3964',
      '3964',
      '3964',
      '3964',
      '3964',
      '3964',
      '3964',
      '3964',
      '3964',
      '3964',
      '3964',
      '3964',
      '3964',
      '3964',
      '3964',
      '3964',
      '3964',
      '3964',
      '3964',
      '3964',
      '3964',
      '3964',
      '3964',
      '3964',
      '3964',
      '3968',
      '3970',
      '3970',
      '3970',
      '3971',
      '3972',
      '3972',
      '3972',
      '3971',
      '3971',
      '3972',
      '3972',
      '3972',
      '3973',
      '3973',
      '3973',
      '3973',
      '3973',
      '3973',
      '3973',
      '3973',
      '3972',
      '3972',
      '3972',
      '3973',
      '3973',
      '3973',
      '3973',
      '3973',
      '3973',
      '3973',
      '3973',
      '3973',
      '3973',
      '3973',
      '3973',
      '3973',
      '3973',
      '3973',
      '3973',
      '3973',
      '3973',
      '3973',
      '3973',
      '3973',
      '3975',
      '3976',
      '3976',
      '3976',
      '3976',
      '3976',
      '3976',
      '3976',
      '3978',
      '3978',
      '3978',
      '3978',
      '3978',
      '3978',
      '3978',
      '3978',
      '3978',
      '3978',
      '3978',
      '3980',
      '3980',
      '3821',
      '3821',
      '3964',
      '3964',
      '3964',
      '3964',
      '3964',
      '3964',
      '3964',
      '3964',
      '3964',
      '3964',
      '3964',
      '3964',
      '3964',
      '3964',
      '3964',
      '3964',
      '3964',
      '3964',
      '3964',
      '3964',
      '3965',
      '3965',
      '3965',
      '3965',
      '3965',
      '3965',
      '3965',
      '3965',
      '3967',
      '3967',
      '3967',
      '3967',
      '3967',
      '3967',
      '3967',
      '3967',
      '3957',
      '3957',
      '3957',
      '3957',
      '3957',
      '3957',
      '3957',
      '3957',
      '3957',
      '3957',
      '3907',
      '3907',
      '3907',
      '3907',
      '3907',
      '3944',
      '3944',
      '3944',
      '3944',
      '3944',
      '3944',
      '22',
      '22',
      '3949',
      '3950',
      '3950',
      '3950',
      '3950',
      '3950',
      '3950',
      '3952',
      '3952',
      '3952',
      '3952',
      '3952',
      '3952',
      '3952',
      '3952',
      '3952',
      '3949',
      '3954',
      '3777',
      '3777',
      '3777',
      '3777',
      '3777',
      '3777',
      '3777',
      '3777',
      '3777',
      '3777',
      '3777',
      ...],
     'OfferID': ['45436',
      '26000',
      '26000',
      '26000',
      '26000',
      '26000',
      '26000',
      '26000',
      '26000',
      '26000',
      '26000',
      '26000',
      '26000',
      '49124',
      '49124',
      '46287',
      '49124',
      '44862',
      '44862',
      '46287',
      '16067',
      '49340',
      '49329',
      '37819',
      '42609',
      '49327',
      '47607',
      '48725',
      '49322',
      '49330',
      '37819',
      '49331',
      '47607',
      '49339',
      '49331',
      '42609',
      '49325',
      '49340',
      '49197',
      '48725',
      '49330',
      '49338',
      '43621',
      '49338',
      '43621',
      '49337',
      '49325',
      '49326',
      '49322',
      '49197',
      '49339',
      '49336',
      '49336',
      '49329',
      '49327',
      '49329',
      '49326',
      '49337',
      '45227',
      '49349',
      '47303',
      '47303',
      '47303',
      '47303',
      '29759',
      '49349',
      '29759',
      '39319',
      '39315',
      '39319',
      '26198',
      '26199',
      '31719',
      '26203',
      '26193',
      '26199',
      '26203',
      '26198',
      '26204',
      '26193',
      '26205',
      '26206',
      '31719',
      '31719',
      '30687',
      '42593',
      '30687',
      '49070',
      '47303',
      '47303',
      '47303',
      '20459',
      '32321',
      '32321',
      '20459',
      '20459',
      '11846',
      '11846',
      '47303',
      '47303',
      '49069',
      '49069',
      '49070',
      '49070',
      '38665',
      '38665',
      '49349',
      '47303',
      '49348',
      '47303',
      '49348',
      '47303',
      '49349',
      '45227',
      '28943,29067,28939,29071,28754,28938,26000,28940,29070,29066,26260,32837,32778,32830,32998,29065,26280,33001,29069,32592,29073,29072,29068,26258,26259,',
      '37818,37819,44371,33292,49127,39831,39763,42696,39933,45532,45533,45303,45304,46849,46850,46851,47607,23080,47734,46558,45531,47681,30976,48139,44748,',
      '26098,28644,',
      '33292,48169,47559,40498,42607,',
      '17379,26000,26024,28644,',
      '48840,49069,47303,46250,45436,',
      '44393,46849,46591,41028,41031,36349,32269,32927,29827,29821,46012,29515,46593,33049,33996,46011,',
      '42593',
      '46850,45304,29477,29499,46851,29516,39933,29500,29511,39831,45533,37819,45303,33292,29510,28644,29513,37818,45532,29514,39763,44371,46849,42696,',
      '49336',
      '49336',
      '49336',
      '46257',
      '46257',
      '24977',
      '24977',
      '21024',
      '29515',
      '26580',
      '26578',
      '26573',
      '26574',
      '26575',
      '26576',
      '26579',
      '26000',
      '26594',
      '26594',
      '26579',
      '26000',
      '29515',
      '20097',
      '32773',
      '32773',
      '32773',
      '32773',
      '42593',
      '37819',
      '43887',
      '43887',
      '46558',
      '43887',
      '43887',
      '48139',
      '48139',
      '37819',
      '33292',
      '46558',
      '48139',
      '40827',
      '40827',
      '40827',
      '46011',
      '42593',
      '46011',
      '30619',
      '33996',
      '33996',
      '33996',
      '33996',
      '30619',
      '26146',
      '39319',
      '26298',
      '26626',
      '26465',
      '41331',
      '41331',
      '41331',
      '39319',
      '42593',
      '40498',
      '29658',
      '29658',
      '42607',
      '47559',
      '29658',
      '33292',
      '28644',
      '28644',
      '28644',
      '28644',
      '26098',
      '47303',
      '45931',
      '45932',
      '45930',
      '45931',
      '45930',
      '45930',
      '43887',
      '26298',
      '26626',
      '43887',
      '26146',
      '26211',
      '26465',
      '26211',
      '16148',
      '16148',
      '46243',
      '45969',
      '45969',
      '42825',
      '45950',
      '47303',
      '45340',
      '45950',
      '47303',
      '45950',
      '45950',
      '45335',
      '45340',
      '45335',
      '45340',
      '45340',
      '47303',
      '47303',
      '47303',
      '46260',
      '46260',
      '46260',
      '37274',
      '37274',
      '26146',
      '26298',
      '26626',
      '26000',
      '26465',
      '26000',
      '26000',
      '49069',
      '45957',
      '43887',
      '42593',
      '45957',
      '42593',
      '23080',
      '23080',
      '26465',
      '26298',
      '23080',
      '23080',
      '26626',
      '26146',
      '46259',
      '33292',
      '33292',
      '32528',
      '32528',
      '49069',
      '48840',
      '49069',
      '49069',
      '48840',
      '46259',
      '49069',
      '33885',
      '26626',
      '26298',
      '26146',
      '45620',
      '26465',
      '45620',
      '26465',
      '26626',
      '47978',
      '47981',
      '26298',
      '26626',
      '42593',
      '26146',
      '47981',
      '26298',
      '26146',
      '30617',
      '47978',
      '26465',
      '45953',
      '45227',
      '45953',
      '26000',
      '26000',
      '28041',
      '42593',
      '28041',
      '28270',
      '28062',
      '49068',
      '49068',
      '49067',
      '49067',
      '49067',
      '49067',
      '45949',
      '49067',
      '49070',
      '48172',
      '48172',
      '49070',
      '49067',
      '49069',
      '49069',
      '45949',
      '45949',
      '45949',
      '42593',
      '48858',
      '48855',
      '48858',
      '48858',
      '48858',
      '39316',
      '39316',
      '39316',
      '42438',
      '30617',
      '26146',
      '26298',
      '42593',
      '26465',
      '26626',
      '42593',
      '28913',
      '28913',
      '37274',
      '45626',
      '45626',
      '46885',
      '46885',
      '17379',
      '17379',
      '11844',
      '49133',
      '29739',
      '29739',
      '11844',
      '11844',
      '11844',
      '11844',
      '26016',
      '26016',
      '20855',
      '20855',
      '24391',
      '24391',
      '39319',
      '39319',
      '39319',
      '39319',
      '39319',
      '47622',
      '39319',
      '39319',
      '48281',
      '48281',
      '48281',
      '48281',
      '48281',
      '48281',
      '48645',
      '48645',
      '48645',
      '39319',
      '39319',
      '45950',
      '34461',
      '34461',
      '44237',
      '44237',
      '44237',
      '44237',
      '26360',
      '26631',
      '26360',
      '26631',
      '26370',
      '26000',
      '29515',
      '26000',
      '26370',
      '11845',
      '11845',
      '45337',
      '48426',
      '48426',
      '45337',
      '11844',
      '11850',
      '43621',
      '11846',
      '11850',
      '11846',
      '11844',
      '11850',
      '43621',
      '43621',
      '20087',
      '20087',
      '42593',
      '32831',
      '32831',
      '32833',
      '32833',
      '42593',
      '17379',
      '17379',
      '26000',
      '26000',
      '42593',
      '20089',
      '20089',
      '42593',
      '30617',
      '26626',
      '26465',
      '26146',
      '42593',
      '26298',
      '22674',
      '26298',
      '26146',
      '26465',
      '30617',
      '26626',
      '42593',
      '42593',
      '22674',
      '26844',
      '42593',
      '26844',
      '45961',
      '45961',
      '45953',
      '45953',
      '45961',
      '45961',
      '40322',
      '40322',
      '40322',
      '42593',
      '30617',
      '29442',
      '28644',
      '28644',
      '28644',
      '28644',
      '42593',
      '29442',
      '45949',
      '40322',
      '45227',
      '45227',
      '45229',
      '40322',
      '40322',
      '40322',
      '40322',
      '45955',
      '46258',
      '46256',
      '45953',
      '46260',
      '46260',
      '45952',
      '46260',
      '45961',
      '46260',
      '45957',
      '46259',
      '46257',
      '45951',
      '45958',
      '45957',
      '48420',
      '47565',
      '40322',
      '45229',
      '38665',
      '46260',
      '46261',
      '46260',
      '47303',
      '46256',
      '45953',
      '46258',
      '45951',
      '45949',
      '48886',
      '45955',
      '45227',
      '45953',
      '46257',
      '45950',
      '45961',
      '46882',
      '45953',
      '45953',
      '45952',
      '46259',
      '46570',
      '40322',
      '45229',
      '40322',
      '40322',
      '30364',
      '30364',
      '45970',
      '20616',
      '42593',
      '20459',
      '20459',
      '20459',
      '20616',
      '31642',
      '31642',
      '31642',
      '26724',
      '20242',
      '12599',
      '31642',
      '31642',
      '26724',
      '20242',
      '31642',
      '12599',
      '47981',
      '47981',
      '47981',
      '43887',
      '43887',
      '43887',
      '43887',
      '43887',
      '29067',
      '47873',
      '47873',
      '47873',
      '26465',
      '26298',
      '26146',
      '26626',
      '45958',
      '45958',
      '26849',
      '24376',
      '26846',
      '24376',
      '26846',
      '45917',
      '45918',
      '46250',
      '46250',
      '45917',
      '45953',
      '45953',
      '45918',
      '45951',
      '45951',
      '39315',
      '26465',
      '26146',
      '30944',
      '30944',
      '26298',
      '26626',
      '46540',
      '46541',
      '46536',
      '46540',
      '46541',
      '46541',
      '46541',
      '26000',
      '42593',
      '29442',
      '29442',
      '30547',
      '26198',
      '26198',
      '28094',
      '26000',
      '28094',
      '26000',
      '26849',
      '26183',
      '20459',
      '20459',
      '26183',
      '20459',
      '20459',
      '47113',
      '45970',
      '42593',
      '26465',
      '26626',
      '26146',
      '26298',
      '30617',
      '26465',
      '26626',
      '26298',
      '26146',
      '46260',
      '46260',
      '46257',
      '46260',
      '46260',
      '46260',
      '46260',
      '46260',
      '46260',
      '46257',
      '46260',
      '46260',
      '46260',
      '46257',
      '46257',
      '46260',
      '46260',
      '46260',
      '46260',
      '46260',
      '46260',
      '46260',
      '46260',
      '46260',
      '46260',
      '46260',
      '46260',
      '46260',
      '46253',
      '46253',
      '46253',
      '48169',
      '48169',
      '29065',
      '29065',
      '29065',
      '29065',
      '29065',
      '29065',
      '33292',
      '20459',
      '33292',
      '20459',
      '33292',
      '42593',
      '30364',
      '30364',
      '47367',
      '47274',
      '47367',
      '45874',
      '45874',
      '45909',
      '45914',
      '47274',
      '41951',
      '41951',
      '45909',
      '45914',
      '45914',
      '45914',
      '46536',
      '26000',
      '47556',
      '47556',
      '26318',
      '26318',
      '26280',
      '26280',
      '48203',
      '48203',
      '45931',
      '45932',
      '45932',
      '48203',
      '48203',
      '47113',
      '45917',
      '45917',
      '39319',
      '45932',
      '45932',
      '45932',
      '46260',
      '46260',
      '37818',
      '44371',
      '37818',
      '11927',
      '11927',
      '11927',
      '37819',
      '11927',
      '37818',
      '37819',
      '11927',
      '37818',
      '44371',
      '12496',
      '12496',
      '12575',
      '12575',
      '12671',
      '12575',
      '38689',
      '12575',
      '32528',
      '32528',
      '32528',
      '12678',
      '12678',
      '38689',
      '38689',
      '47886',
      '48540',
      '47886',
      '48540',
      '48540',
      '45337',
      '47873',
      '40507',
      '39553',
      '39553',
      '40507',
      '48203',
      '48203',
      '45958',
      '45958',
      '45917',
      '45961',
      '45961',
      '45917',
      '47113',
      '48203',
      '45918',
      '47113',
      '45918',
      '45744',
      '45337',
      '45744',
      '45742',
      '45742',
      '20113',
      '20113',
      '12496',
      '45747',
      '38617',
      '12496',
      '38617',
      '47558',
      '47558',
      '45747',
      '45748',
      '45748',
      '37818',
      '44371',
      '44371',
      '37819',
      '37819',
      '37818',
      '44371',
      '44371',
      '37818',
      '37818',
      '46035',
      '46849',
      '45741',
      '46858',
      '46849',
      '46035',
      '45744',
      '45744',
      '42982',
      '42982',
      '45741',
      '45337',
      '47886',
      '46858',
      '47886',
      '45955',
      '26146',
      '26626',
      '26298',
      '30617',
      '26465',
      '42593',
      '27113',
      '27113',
      '46258',
      '40322',
      '45961',
      '45961',
      '45950',
      '45950',
      '46260',
      '46258',
      '46260',
      '40322',
      '45955',
      '26132',
      '26132',
      '42607',
      '26465',
      '26626',
      '42607',
      '42609',
      '42593',
      '45576',
      '29740',
      '45576',
      '29740',
      '26379',
      '26146',
      '30617',
      '26298',
      '28049',
      '26375',
      '28002',
      '26375',
      '28002',
      '26379',
      '26356',
      '26356',
      '28049',
      '24495',
      '42609',
      '42593',
      '42593',
      '33747',
      '33308',
      '33747',
      '29477',
      '11834',
      '11834',
      '11834',
      '29477',
      '29477',
      '11850',
      '11850',
      '11850',
      '42593',
      '42593',
      '26146',
      '26626',
      '26298',
      '30617',
      '42593',
      '26465',
      '46759',
      '46759',
      '46759',
      '40415',
      '40415',
      '20737',
      '19871',
      '19871',
      '19372',
      '19372',
      '42593',
      '20742',
      '15937',
      '35170',
      '35170',
      '15937',
      '20742',
      '28644',
      '20288',
      '20288',
      '20737',
      '28644',
      '20742',
      '20742',
      '11836',
      '38665',
      '45961',
      '45961',
      '45958',
      '38665',
      '38665',
      '45958',
      '48420',
      '48420',
      '46260',
      '46260',
      '48420',
      '46257',
      '48203',
      '48203',
      '40685',
      '46257',
      '40685',
      '30617',
      '45335',
      '28943',
      '26258',
      '42593',
      '44371',
      '44371',
      '46929',
      '46929',
      '46929',
      '44371',
      '46929',
      '37819',
      '44371',
      '40824',
      '37819',
      '12768',
      '44409',
      '44409',
      '26849',
      '26849',
      '44409',
      '42593',
      '12768',
      '26221',
      '26221',
      '39114',
      '39114',
      '26221',
      '48027',
      '39114',
      '48027',
      '48477',
      '46424',
      '48477',
      '47942',
      '48477',
      '43887',
      '47942',
      '43887',
      '34974',
      '34974',
      '26238',
      '26000',
      '26238',
      '26000',
      '26069',
      '26069',
      '28017',
      '28017',
      '26146',
      '26298',
      '26465',
      '26626',
      '42593',
      '45932',
      '45932',
      '45932',
      '45932',
      '45932',
      '45932',
      '26425',
      '26425',
      '42593',
      '35176',
      '30458',
      '20850',
      '20850',
      '30458',
      '35176',
      '47565',
      '47565',
      '46257',
      '47303',
      '40322',
      '40322',
      '40322',
      '46257',
      '47303',
      '42593',
      '42593',
      '42044',
      '42044',
      '42044',
      '42044',
      '45918',
      '40322',
      '47251',
      '40322',
      '45918',
      '45918',
      '47251',
      ...]}




```python
my_df = graphlab.SFrame(features)
print my_df
```

    +------------+---------+
    | CustomerID | OfferID |
    +------------+---------+
    |    4078    |  45436  |
    |    4055    |  26000  |
    |    4055    |  26000  |
    |    4055    |  26000  |
    |    4055    |  26000  |
    |    4055    |  26000  |
    |    4055    |  26000  |
    |    4055    |  26000  |
    |    4055    |  26000  |
    |    4055    |  26000  |
    +------------+---------+
    [26312 rows x 2 columns]
    Note: Only the head of the SFrame is printed.
    You can use print_rows(num_rows=m, num_columns=n) to print more rows and columns.
    


```python
len(my_df)
```




    26312




```python
my_df['CustomerID'].show()
```



**Splitting the dataframe into trainset and testset for builing and testing the model**


```python
train_data,test_data = my_df.random_split(.8,seed=0)
```

## Simple popularity-based recommender



```python
popularity_model = graphlab.popularity_recommender.create(train_data,
                                                         user_id='CustomerID',
                                                         item_id='OfferID')
```


<pre>Recsys training: model = popularity</pre>



<pre>Preparing data set.</pre>



<pre>    Data has 21146 observations with 1276 users and 4110 items.</pre>



<pre>    Data prepared in: 0.090565s</pre>



<pre>21146 observations to process; with 4110 unique items.</pre>



```python
users = my_df['CustomerID'].unique()
```

**Use Popularity Model to make Some Prediction**


```python
popularity_model.recommend(users=[users[1]])
```




<div style="max-height:1000px;max-width:1500px;overflow:auto;"><table frame="box" rules="cols">
    <tr>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">CustomerID</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">OfferID</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">score</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">rank</th>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3952</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">20309</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">378.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3952</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">16146</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">255.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3952</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">26000</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">237.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3952</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">26465</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">122.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">4</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3952</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">15831</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">117.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3952</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">26298</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">117.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">6</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3952</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">26146</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">113.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">7</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3952</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">26626</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">109.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">8</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3952</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">42593</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">100.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">9</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3952</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">17379</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">85.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">10</td>
    </tr>
</table>
[10 rows x 4 columns]<br/>
</div>




```python
popularity_model.recommend(users=[users[2]])
```




<div style="max-height:1000px;max-width:1500px;overflow:auto;"><table frame="box" rules="cols">
    <tr>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">CustomerID</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">OfferID</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">score</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">rank</th>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2957</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">20309</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">378.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2957</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">16146</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">255.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2957</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">26000</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">237.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2957</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">26465</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">122.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">4</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2957</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">15831</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">117.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2957</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">26298</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">117.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">6</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2957</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">26146</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">113.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">7</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2957</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">26626</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">109.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">8</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2957</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">42593</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">100.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">9</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2957</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">17379</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">85.0</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">10</td>
    </tr>
</table>
[10 rows x 4 columns]<br/>
</div>



**In case of Popularity Based Recommender Model, the recommendations are same for every use, as it is not personilized**

## Build a recommender system with personalization


```python
personalized_model = graphlab.item_similarity_recommender.create(train_data,
                                                                user_id='CustomerID',
                                                                item_id='OfferID')
```


<pre>Recsys training: model = item_similarity</pre>



<pre>Preparing data set.</pre>



<pre>    Data has 21146 observations with 1276 users and 4110 items.</pre>



<pre>    Data prepared in: 0.084061s</pre>



<pre>Training model from provided data.</pre>



<pre>Gathering per-item and per-user statistics.</pre>



<pre>+--------------------------------+------------+</pre>



<pre>| Elapsed Time (Item Statistics) | % Complete |</pre>



<pre>+--------------------------------+------------+</pre>



<pre>| 1.509ms                        | 78.25      |</pre>



<pre>| 2.011ms                        | 100        |</pre>



<pre>+--------------------------------+------------+</pre>



<pre>Setting up lookup tables.</pre>



<pre>Processing data in one pass using dense lookup tables.</pre>



<pre>+-------------------------------------+------------------+-----------------+</pre>



<pre>| Elapsed Time (Constructing Lookups) | Total % Complete | Items Processed |</pre>



<pre>+-------------------------------------+------------------+-----------------+</pre>



<pre>| 70.056ms                            | 0                | 0               |</pre>



<pre>| 327.237ms                           | 100              | 4110            |</pre>



<pre>+-------------------------------------+------------------+-----------------+</pre>



<pre>Finalizing lookup tables.</pre>



<pre>Generating candidate set for working with new users.</pre>



<pre>Finished training in 1.33881s</pre>



```python
personalized_model.recommend(users=[users[1]])
```




<div style="max-height:1000px;max-width:1500px;overflow:auto;"><table frame="box" rules="cols">
    <tr>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">CustomerID</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">OfferID</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">score</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">rank</th>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3952</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">45229</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0.189393937588</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3952</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">46570</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0.189393937588</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3952</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">45952</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0.189393937588</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3952</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">48886</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0.189393937588</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">4</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3952</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">46261</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0.189393937588</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3952</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">48420</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0.166666656733</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">6</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3952</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">45227</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0.165178567171</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">7</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3952</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">46882</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0.164502158761</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">8</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3952</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">46258</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0.164502158761</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">9</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3952</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">45955</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0.135416671634</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">10</td>
    </tr>
</table>
[10 rows x 4 columns]<br/>
</div>




```python
personalized_model.recommend(users=[users[2]])
```




<div style="max-height:1000px;max-width:1500px;overflow:auto;"><table frame="box" rules="cols">
    <tr>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">CustomerID</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">OfferID</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">score</th>
        <th style="padding-left: 1em; padding-right: 1em; text-align: center">rank</th>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2957</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">34924</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0.0916666686535</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">1</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2957</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">32569</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0.0729166716337</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2957</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">34822</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0.0712963044643</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">3</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2957</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">34816</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0.070833325386</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">4</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2957</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">34983</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0.066666662693</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">5</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2957</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">35306</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0.0540935695171</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">6</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2957</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">33994</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0.0535714328289</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">7</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2957</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">34923</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0.0535714328289</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">8</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2957</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">11824</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0.0504658520222</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">9</td>
    </tr>
    <tr>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">2957</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">36311</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">0.0499999970198</td>
        <td style="padding-left: 1em; padding-right: 1em; text-align: center; vertical-align: top">10</td>
    </tr>
</table>
[10 rows x 4 columns]<br/>
</div>



**The personilized model, make better and different predictions for different users based on their preferences. Now, let's check the model comparison between these two models'**

# Quantitative comparison between the models


```python
%matplotlib inline
model_performance = graphlab.recommender.util.compare_models(test_data,
                                                             [popularity_model,personalized_model],
                                                             user_sample = 0.075)
```

    compare_models: using 66 users to estimate model performance
    PROGRESS: Evaluate model M0
    
    Precision and recall summary statistics by cutoff
    +--------+------------------+-----------------+
    | cutoff |  mean_precision  |   mean_recall   |
    +--------+------------------+-----------------+
    |   1    |       0.0        |       0.0       |
    |   2    |       0.0        |       0.0       |
    |   3    |       0.0        |       0.0       |
    |   4    | 0.00378787878788 | 0.0151515151515 |
    |   5    | 0.00909090909091 | 0.0328282828283 |
    |   6    | 0.00757575757576 | 0.0328282828283 |
    |   7    | 0.00649350649351 | 0.0328282828283 |
    |   8    | 0.00568181818182 | 0.0328282828283 |
    |   9    | 0.00505050505051 | 0.0328282828283 |
    |   10   | 0.00454545454545 | 0.0328282828283 |
    +--------+------------------+-----------------+
    [10 rows x 3 columns]
    
    PROGRESS: Evaluate model M1
    
    Precision and recall summary statistics by cutoff
    +--------+------------------+-----------------+
    | cutoff |  mean_precision  |   mean_recall   |
    +--------+------------------+-----------------+
    |   1    | 0.0606060606061  | 0.0479797979798 |
    |   2    |  0.030303030303  | 0.0479797979798 |
    |   3    |  0.020202020202  | 0.0479797979798 |
    |   4    | 0.0151515151515  | 0.0479797979798 |
    |   5    | 0.0121212121212  | 0.0479797979798 |
    |   6    |  0.010101010101  | 0.0479797979798 |
    |   7    | 0.00865800865801 | 0.0479797979798 |
    |   8    | 0.00757575757576 | 0.0479797979798 |
    |   9    | 0.00673400673401 | 0.0479797979798 |
    |   10   | 0.00606060606061 | 0.0479797979798 |
    +--------+------------------+-----------------+
    [10 rows x 3 columns]
    
    

**Yes, definitely. Personalized model predicts more better recommendations as compared to the Popularity based model.**


```python
# Let's also visualize it on Precision-Recall Curve
model_performance = graphlab.compare(test_data, [popularity_model, personalized_model])
graphlab.show_comparison(model_performance,[popularity_model, personalized_model])
```

    PROGRESS: Evaluate model M0
    
    Precision and recall summary statistics by cutoff
    +--------+------------------+-------------------+
    | cutoff |  mean_precision  |    mean_recall    |
    +--------+------------------+-------------------+
    |   1    | 0.00112866817156 | 0.000282167042889 |
    |   2    | 0.00451467268623 |  0.00358068727517 |
    |   3    | 0.0071482317532  |  0.00916428727187 |
    |   4    |  0.010158013544  |  0.0204509689874  |
    |   5    | 0.0158013544018  |  0.0383348955485  |
    |   6    | 0.0150489089541  |  0.0411774218023  |
    |   7    | 0.0132215414382  |  0.0414624105157  |
    |   8    | 0.0118510158014  |  0.0421521521761  |
    |   9    |  0.011161274141  |  0.0443826154675  |
    |   10   |  0.010158013544  |  0.0445236989889  |
    +--------+------------------+-------------------+
    [10 rows x 3 columns]
    
    PROGRESS: Evaluate model M1
    
    Precision and recall summary statistics by cutoff
    +--------+-----------------+-----------------+
    | cutoff |  mean_precision |   mean_recall   |
    +--------+-----------------+-----------------+
    |   1    | 0.0609480812641 |  0.030723668635 |
    |   2    | 0.0372460496614 | 0.0338750033192 |
    |   3    | 0.0267118133935 | 0.0352388106932 |
    |   4    | 0.0217268623025 | 0.0368579120583 |
    |   5    | 0.0187358916479 | 0.0396817999099 |
    |   6    | 0.0159894657637 | 0.0401991061552 |
    |   7    | 0.0140277329894 | 0.0404877597968 |
    |   8    | 0.0124153498871 | 0.0406288433183 |
    |   9    | 0.0112866817156 | 0.0408263602483 |
    |   10   | 0.0103837471783 | 0.0410803105869 |
    +--------+-----------------+-----------------+
    [10 rows x 3 columns]
    
    Model compare metric: precision_recall
    




```python

```
