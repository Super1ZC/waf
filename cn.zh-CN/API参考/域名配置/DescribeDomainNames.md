# DescribeDomainNames {#reference_dj3_xdv_42b .reference}

获取指定WAF实例中已添加的域名名称列表。

## 请求参数 {#section_ybx_zfv_42b .section}

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是| 要执行的操作。 取值：

 DescribeDomainNames

 |

## 返回参数 {#section_ugs_f1g_cz .section}

|名称|类型|描述|
|:-|:-|:-|
|RequestId|String|请求ID。|
|DomainNames|Array|已添加的域名名称列表。|

## 示例 {#section_ix5_h1g_cz .section}

**请求示例**

``` {#createVPCpub}
https://wafopenapi.cn-hangzhou.aliyuncs.com/?Action=DescribeDomainNames
&公共请求参数
```

**返回示例**

-   XML格式

    ```
    <?xml version="1.0" encoding="UTF-8"?>
    <DescribeDomainNamesResponse>
        <RequestId>56B40D30-4960-4F19-B7D5-2B1F0EE6CB70</RequestId>
        <DomainNames>["rstest.cdn.com","rstest1.cdn.com","rstest2.cdn.com","rstest3.cdn.com"]</DomainNames>
    </DescribeDomainNamesResponse>
    ```

-   JSON格式

    ```
    { 
        "RequestId": "56B40D30-4960-4F19-B7D5-2B1F0EE6CB70", 
        "DomainNames": "["rstest.cdn.com","rstest1.cdn.com","rstest2.cdn.com","rstest3.cdn.com"]"
    }
    ```


