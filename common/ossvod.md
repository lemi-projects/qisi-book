# 阿里云存储 oss vod

## 阿里云OSS存储

### - OSS web直传

[上传DEMO](https://admins.huitianyouwo.com/shequ-api/sapi/api/alioss/php/index.html)

### - OSS获取指定目录下文件列表

#### 接口URL：
/sapi/userOss.php?cmd=list&prefix=osspath/&max=2

[测试接口](https://admins.huitianyouwo.com/shequ-api/sapi/userOss.php?cmd=list&prefix=osspath/&max=2)

#### 传入参数:
 
```
参数1：cmd 操作方法 
    示例：list（固定值）
参数2：prefix 目录地址  
    示例：osspath/（变量值）
参数3：max 获取数量
    示例：2
```

#### 返回结果：
```
{
    "error": 0,
    "msg": "done",
    "data": [
        "https://oss.vecommunity.com/yll2/osspath/common/",
        "https://oss.vecommunity.com/yll2/osspath/test/",
        "https://oss.vecommunity.com/yll2/osspath/uploads/"
    ]
}
```

## 阿里云VOD存储

### - 上传测试Demo

[上传DEMO](https://admins.huitianyouwo.com/shequ-api/sapi/api/alijsup/uploadauth.html)

### - 搜索视频列表

#### 接口URL：
sapi/userVod.php?cmd=searchmedia&tags='X','Y'&pageno=1&pagesize=10&searchtype=video

[测试接口](https://admins.huitianyouwo.com/shequ-api/sapi/userVod.php?cmd=searchmedia&tags='X','Y'&pageno=1&pagesize=10&searchtype=video)

#### 传入参数:
 
```
参数1：cmd 操作方法 
    示例：searchmedia（固定值）
参数2：tags 视频标签  
    示例：'X','Y','Z'（变量值，多个标签同时成立）
参数3：pageno 页数 1是第1页
    示例：1
参数4：pagesize 每页数量
    示例：10
参数5：searchtype 获取类型（vedio audio image）
    示例：vedio
```

#### 返回结果：

```
{
    "error": 0,
    "msg": "done",
    "data": {
        "MediaList": [
            {
                "AttachedMedia": {},
                "MediaId": "d935fbb3ff334f8e91be27dddf1547dd",
                "Video": {
                    "Status": "Normal",
                    "VideoId": "d935fbb3ff334f8e91be27dddf1547dd",
                    "Title": "英语学习",
                    "CoverURL": "http://outin-42dd273e835111e994b900163e1c8dba.oss-cn-shanghai.aliyuncs.com/d935fbb3ff334f8e91be27dddf1547dd/snapshots/cd19d300dd0f43b1b3888f18be5f25cd-00004.jpg?Expires=1604605831&OSSAccessKeyId=LTAIrkwb21KyGjJl&Signature=yltHIatoYdGzHi12AHqlEGPwPEE="
                },
                "CreationTime": "2020-11-02T02:05:08Z",
                "MediaType": "video",
                "Audio": {},
                "Image": {}
            },
            {
                "AttachedMedia": {},
                "MediaId": "527d320d716545f386f04fc37321496f",
                "Video": {
                    "Status": "Normal",
                    "VideoId": "527d320d716545f386f04fc37321496f",
                    "Title": "kangjialameiDJ-0722.mp4",
                    "CoverURL": "http://outin-42dd273e835111e994b900163e1c8dba.oss-cn-shanghai.aliyuncs.com/527d320d716545f386f04fc37321496f/snapshots/cab15459c3a94503aec5de56df060bfe-00005.jpg?Expires=1604605831&OSSAccessKeyId=LTAIrkwb21KyGjJl&Signature=eC+WOu6QUTXbtnisRilv1MWEACc="
                },
                "CreationTime": "2019-07-22T01:48:20Z",
                "MediaType": "video",
                "Audio": {},
                "Image": {}
            }
        ],
        "RequestId": "FFE22323-C057-46C0-8517-1EC60C113FFC",
        "ScrollToken": "af6864ce3e3d94ce7abfb288cf7e2aee",
        "Total": 2
    }
}
```

### - 查询视频详情

#### 接口URL：
sapi/userVod.php?cmd=getplayinfo&videoid=d935fbb3ff334f8e91be27dddf1547dd

[测试接口](https://admins.huitianyouwo.com/shequ-api/sapi/userVod.php?cmd=getplayinfo&videoid=d935fbb3ff334f8e91be27dddf1547dd)

#### 传入参数:

```
参数1：cmd 操作方法 
    示例：getplayinfo（固定值）
参数2：videoid 视频ID 
    示例：d935fbb3ff334f8e91be27dddf1547dd（变量值）
```

#### 返回结果:

```
{
    "error": 0,
    "msg": "done",
    "data": {
        "Status": "Normal",
        "StreamType": "video",
        "Size": 4084981,
        "Definition": "OD",
        "Fps": "25",
        "Duration": "76.76",
        "ModificationTime": "2020-11-02T02:05:08Z",
        "Specification": "Original",
        "Bitrate": "425.74",
        "Encrypt": 0,
        "PreprocessStatus": "UnPreprocess",
        "Format": "mp4",
        "PlayURL": "https://outin-42dd273e835111e994b900163e1c8dba.oss-cn-shanghai.aliyuncs.com/sv/20f7ae07-17586b37106/20f7ae07-17586b37106.mp4?Expires=1604688970&OSSAccessKeyId=LTAIrkwb21KyGjJl&Signature=xt3f6pQ7lGCrvtKjNdIlph4EUu4=",
        "NarrowBandType": "0",
        "CreationTime": "2020-11-02T02:05:08Z",
        "Height": 938,
        "Width": 1208,
        "JobId": "d935fbb3ff334f8e91be27dddf1547dd02"
    }
}
```
### - 查询视频类型

#### 接口URL：
sapi/userVod.php?cmd=getcategories

[测试接口](https://admins.huitianyouwo.com/shequ-api/sapi/userVod.php?cmd=getcategories)

#### 传入参数：
```
参数1：cmd 操作方法 
    示例：getcategories（固定值）
```

#### 返回结果：
```
{
    "error": 0,
    "msg": "done",
    "data": {
        "Category": {},
        "RequestId": "36D0344E-0E13-4842-87C9-B6CA20CCB627",
        "SubTotal": 2,
        "SubCategories": {
            "Category": [
                {
                    "ParentId": -1,
                    "Type": "default",
                    "Level": 0,
                    "CateId": 1000208389,
                    "CateName": "默认分类",
                    "SubTotal": 0
                },
                {
                    "ParentId": -1,
                    "Type": "default",
                    "Level": 0,
                    "CateId": 1000046426,
                    "CateName": "最新活动",
                    "SubTotal": 0
                }
            ]
        }
    }
}
```