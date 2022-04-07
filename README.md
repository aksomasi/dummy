Slide - 1
-------------
Before knowing about the Kinesis, you should know about the streaming data.

What is streaming data?
Streaming data is data which is generated continuously from thousands of data sources, and these data sources can send the data records simultaneously and in small size.

Following are the examples of streaming data:
Purchases from online stores
People buying stuff on amazon.com and generates streaming data and that streaming data can be transactions, product, etc.
Stock prices
Stock price is also an example of streaming data.
Game data
Suppose the user is playing an angry bird game and the application is generating streaming data back to the central server. This streaming data could be "what the user is doing", "what is the score".
Social network data
Social network data is also another example of streaming data. Suppose you visit on Facebook, update your status, and put a post on your friend's wall. All these data would then be streamed.
Geospatial data
When you are using uber, and your device is connected to the internet. Uber application is constantly saying that where the uber driver is, where you are, and it is interrogating the map to give you the best possible route to your destination. This is also a good example of streaming data.
iOT Sensor Data
It senses the all around world monitoring temperature.


Slide -2
---------------
AWS Kinesis

Slide -3
---------------
Architecture of Kinesis Stream
Suppose we have got the EC2, mobile phones, Laptops, IOT which are producing the data. They are known as producers as they produce the data. The data is moved to the Kinesis streams and stored in the shard. By default, the data is stored in shards for 24 hours. You can increase the time to 7 days of retention. Once the data is stored in shards, then you have EC2 instances which are known as consumers. They take the data from shards and turned it into useful data. Once the consumers have performed its calculation, then the useful data is moved to either of the AWS services, i.e., DynamoDB, S3, EMR, Redshift.

Slid - 4
-------------
Suppose you have got the EC2, mobile phones, Laptop, IOT which are producing the data. They are also known as producers. Producers send the data to Kinesis Firehose. Kinesis Firehose does not have to manage the resources such as shards, you do not have to worry about streams, you do not have to worry about manual editing the shards to keep up with the data, etc. It?s completely automated. You do not have to worry even about the consumers. Data can be analyzed by using a Lambda function. Once the data has been analyzed, the data is sent directly over to the S3. The analytics of data is optional. One important thing about Kinesis Firehouse is that there is no automatic retention window, but the Kinesis stream has an automatic retention window whose default time is 24 hours and it can be extended up to 7 days. Kinesis Firehose does not work like this. It essentially either analyzes or sends the data over directly to S3 or other location.

The other location can be Redshift. First, you have to write to S3 and then copy it to the Redshift.

