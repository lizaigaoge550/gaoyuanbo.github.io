## 微博申请token
* 先登录自己的微博账号
* 先打开一个界面，输入https://api.weibo.com/oauth2/authorize?action=login&display=js&withOfficalFlag=0&response_type=token&regCallback=https%253A%252F%252Fapi.weibo.com%252F2%252Foauth2%252Fauthorize%253Fclient_id%253D2323547071%2526response_type%253Dtoken%2526display%253Djs%2526redirect_uri%253Dhttps%253A%252F%252Fapi.weibo.com%252Foauth2%252Fxd.html%2526from%253D%2526with_cookie%253D&redirect_uri=https%3A%2F%2Fapi.weibo.com%2Foauth2%2Fxd.html&appkey62=3KeSKP&client_id=2323547071&verifyToken=null

## 获取某一个微博的评论list
  ```python
  import urllib
  import urllib2
import json
req = urllib2.Request("https://api.weibo.com/2/statuses/user_timeline/ids.json?"
                      "access_token=2.00HhKNQCfj3PXCa57fba7999JYpQWE&&uid=1648007681")
res_data = urllib2.urlopen(req)
dic = json.loads(res_data.read())

ids = []
for id in dic['statuses']:
    ids.append(id)
