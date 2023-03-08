FROM docker.elastic.co/elasticsearch/elasticsearch:8.0.0
# 日本語解析用　必要かわからない。
RUN elasticsearch-plugin install analysis-kuromoji
# 下記入れないと　elastic migration 通らない
RUN elasticsearch-plugin install analysis-icu