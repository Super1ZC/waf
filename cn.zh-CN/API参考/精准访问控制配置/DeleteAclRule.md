# DeleteAclRule {#reference_cwk_2hc_p2b .reference}

删除指定精准访问控制规则。

## 请求参数 {#section_ybx_zfv_42b .section}

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是| 要执行的操作。 取值：

 DeleteAclRule

 |
|Domain|String|是|域名名称。|
|RuleId|Long|是|精准访问控制规则ID。|

## 返回参数 {#section_ugs_f1g_cz .section}

|名称|类型|描述|
|:-|:-|:-|
|RequestId|String|请求ID。|
|Status|Integer|请求执行状态：-   0：表示该请求等待执行。
-   1：表示该请求正在执行中。
-   2：表示该请求已执行完成。

|
|WafTaskId|String|WAF的请求ID。|

## 示例 {#section_ix5_h1g_cz .section}

**请求示例**

``` {#createVPCpub}
https://wafopenapi.cn-hangzhou.aliyuncs.com/?Action=DeleteAclRule
&Domain=www.aliyun.com
&RuleId=65899
&公共请求参数
```

**返回示例**

-   XML格式

    ```
    <?xml version="1.0" encoding="UTF-8"?>
    <DeleteAclRuleResponse>
        <RequestId>D7861F61-5B61-46CE-A47C-6B19160D5EB0</RequestId>
        <Result>
            <Status>2</Status>
            <WafTaskId>aliyun.waf.20180712214032277.qmxI9a</WafTaskId>
        </Result>
    </DeleteAclRuleResponse>
    ```

-   JSON格式

    ```
    {
        "RequestId":"D7861F61-5B61-46CE-A47C-6B19160D5EB0", 
        "Result":{
            "Status":2,
            "WafTaskId":"aliyun.waf.20180712214032277.qmxI9a"
        } 
    }
    ```


