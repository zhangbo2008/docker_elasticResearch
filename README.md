# docker_elasticResearch





2019-10-29,21点11

docker es:

docker pull docker.elastic.co/elasticsearch/elasticsearch:6.3.2


nohup docker run -p 0.0.0.0:9200:9200 -e "http.host=0.0.0.0" -e "transport.host=127.0.0.1" docker.elastic.co/elasticsearch/elasticsearch:6.3.2  &



# -e 表示配置环境变量.
#等几秒之后,服务器来了,再curl

//注意curl命令的url 在winodws里面需要加双引号才行
curl -X GET 'http://localhost:9200'

curl -H "Content-Type: application/json" -X POST 'http://localhost:9200/tutorial/helloworld/1' -d ' { "message": "Hello World!" }'   #存点数据

curl  -H "Content-Type: application/json" -X GET 'http://localhost:9200/tutorial/helloworld/1'   #再获取下

curl -H "Content-Type: application/json" -X PUT 'localhost:9200/tutorial/helloworld/1?pretty' -d ' 
{ "message": "Hello People!" }'   #更新一下

curl -H "Content-Type: application/json" -XGET 'http://localhost:9200/_count?pretty' -d ' { "query": { "match_all": {} } }'   #计算文档数量


