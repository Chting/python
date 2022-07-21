#!/usr/bin/env python
#获取kafka最后消费时间
#coding=utf-8
import json
import time
from aliyunsdkcore.client import AcsClient
from aliyunsdkcore.request import CommonRequest
from aliyunsdkcore.auth.credentials import AccessKeyCredential
from aliyunsdkcore.auth.credentials import StsTokenCredential

credentials = AccessKeyCredential('xxxx', 'xxxxx')
# use STS Token
# credentials = StsTokenCredential('<your-access-key-id>', '<your-access-key-secret>', '<your-sts-token>')
client = AcsClient(region_id='cn-beijing', credential=credentials)

request = CommonRequest()
request.set_accept_format('json')
request.set_domain('alikafka.cn-beijing.aliyuncs.com')
request.set_method('POST')
request.set_protocol_type('https') # https | http
request.set_version('2019-09-16')
request.set_action_name('GetTopicList')
request.add_query_param('InstanceId', "alikafka_id")
response = client.do_action(request)
#print(str(response, encoding = 'utf-8'))
datas = (str(response, encoding = 'utf-8'))
datas = json.loads(datas)
topiclist = datas['TopicList']
topicvO = topiclist['TopicVO']
for i in topicvO:
    topic=i['Topic']
    request.set_action_name('GetTopicStatus')
    request.add_query_param('InstanceId', "alikafka_id")
    request.add_query_param('Topic', topic)
    remark=i['Remark']
    response = client.do_action(request)
    #print(str(response, encoding='utf-8'))
    topicjson = (str(response, encoding='utf-8'))
    topicjson = json.loads(topicjson)
    topicstatus = topicjson['TopicStatus']
    lasttimestamp = topicstatus['LastTimeStamp']
    lasttimestamp = lasttimestamp / 1000
    lasttime = time.strftime('%Y-%m-%d', time.localtime(lasttimestamp))
    offsettable1 = topicstatus['OffsetTable']
    offsettable = offsettable1['OffsetTable']
    topics = offsettable[0]['Topic']
    lastupdatetimestamp = offsettable[0]['LastUpdateTimestamp']
    lastupdatetimestamp = lastupdatetimestamp / 1000
    lastupdatetime = time.strftime('%Y-%m-%d', time.localtime(lastupdatetimestamp))
#    print (topics)
#    print (lastupdatetime)
#    print (lasttime)
    time.sleep(0.5)
    print ("%s %s %s %s" %(topic,remark,lasttime,lastupdatetime))
