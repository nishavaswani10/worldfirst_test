# worldfirst trade application

Required:
Java 8
Maven
GIT

Checkout the project from 
git clone 
cd robo-hoover

mvn clean install

java -jar target/trade-0.0.1.jar

From any browser open the URL http://localhost:8093/swagger-ui.html the swagger REST API Documentation will be loaded and will be possible to call the endpoint using the button "try it out".

Assumption:
1.you can not bid/ask if no share present in the order book,so please add before bidding/asking.
2. you can cancel bid/offer before calling match/unmatch trades

 By default it has Test share already in market,if you want you can add more shares in market by using below method
 /add/share/{name} 
just add the name of share on which you want to do trading ,example:/add/share/Test1  it will add Test1 share in the list.

offer(ask) method:
{
  "companyName": "Test1",// this is the company name which you added earlier in the order book
  "currency": "GBP",
  "price": 12.1,
  "quantity": 1,
  "type": "ASK",
  "userId": "Test User"
}
bid method example:

{
  "companyName": "Test1",
  "currency": "GBP",
  "price": 12.1,
  "quantity": 1,
  "type": "BID",
  "userId": "Test User"
}

match trades:GET METHOD to fetch all match trades
example
[
  "User: Test User CompanyName : Test1 Number of Shares: 1 shares traded for $14.641 per share... total amount was :14.641"
]

unmatch trades:GET METHOD to fetch all un matched trades,it will give bid and offer both detail.
"User: Test User Bid for CompanyName :Test2 Number of Shares: 1 shares for $14.52 per share failed to trade...total amount was :14.52",
"User: Test User offer forCompanyName :Test2 Number of Shares: 1 shares for $14.52 per share failed to trade...total amount was :14.52"
******************************************************************************************************************************************************

Introduction

The Service should provide the following functionalities:
1) For this simple version the current price is static and it is supplied via config file (E.g. GBP/USD = 1.2100).
2) Order registration.
-The order contains fields ? userId, orderType: BID or ASK, currency(GBP/USD), price(E.g. 1.2100), amount(E.g. 8500).
3) Cancel an order.
4) Return summary regarding live not matched orders.
5) Return a summary of matched trades.
