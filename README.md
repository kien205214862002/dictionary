Main dependencies:
- HTTP Server: [fiber](https://github.com/gofiber/fiber)
- Database : [elasticsearch](https://github.com/elastic/go-elasticsearch)
- Message Broker: [kafka](https://github.com/segmentio/kafka-go)
- Cron: [gocron](https://github.com/go-co-op/gocron)
- google api: [sheet](https://developers.google.com/sheets/api/quickstart/go?hl=vi)


```
## Project Architecture

![Screenshot](Project-Architecture.png)
<img width="1455" alt="Project-Architecture" src="https://github.com/tanphattrc/dictionary/assets/76809323/08164535-b2c0-4417-947d-e13055fb8415">
## Motivation

Imagine you have English words with their meanings and example sentences in your Excel sheet in your drive. However, because you are really hardworking, these sheets' size is expanding day by day. You can not search words quickly because the sheet is frozen. As a result, you need an application to search your words quickly.

Our aim is to transform data from an Excel sheet to an elastic search to do a fast search. Therefore, let's know our applications:

Ingester: Retrieve data from the Excel sheet and compare them. If there is any change, it sends the changed data as a message to the Kafka broker.

Consumer: Read messages from Kafka Broker and sends these messages to Word API

Word API: Enables us to communicate Elastic Search, which provides full-text search very fast and stores our data.

All these applications are dockerized, and the docker-composed file is used to run Elastic Search, Kafka, Kibana, and Zookeeper containers.
