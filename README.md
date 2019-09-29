# shopping-web
Function and performance optimization

When the user registers to send the activation email, it may take a long time to send the email, the client will need to wait, and the user experience is not good.
Improvement: asynchronous execution put time-consuming tasks in the background, and the use of celery task queue, which use redis as middleware.
Redis stores user history browsing history with list data structure: History_ user id: [skuid1,skuid2,skuid3]
Redis is used to store the information of the user's shopping cart, and hash data structure is adopted: cart_userid: {'sku_id1': num, 'sku_id2': num}
The distributed file system is adopted to store commodity pictures and other information in the FastDFS system. Nginx+FastDFS cooperate to reduce the pressure on the server.
Page static: home page, product list page, product details page and other common pages, the page static, to reduce the operation of the database. Automatically regenerates static pages when background data changes.
Page data cache, the data used by the page is stored in the cache. When the data is used again, it should be obtained from the cache first. If it cannot be obtained, it can query the database to reduce the number of database queries.
The order of concurrent
