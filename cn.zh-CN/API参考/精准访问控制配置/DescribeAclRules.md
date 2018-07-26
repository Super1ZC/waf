# DescribeAclRules {#reference_is3_5kc_p2b .reference}

获取指定域名的精准访问控制规则列表。

## 请求参数 {#section_ybx_zfv_42b .section}

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是| 要执行的操作。 取值：

 DescribeAclRules

 |
|Domain|String|是|域名名称。|
|CurrentPage|Integer|是|分页查询请求时返回的页码。例如，查询第一页的返回结果，则填写1。|
|PageSize|Integer|是|页面显示最大记录数量。|

## 返回参数 {#section_ugs_f1g_cz .section}

|名称|类型|描述|
|:-|:-|:-|
|RequestId|String|请求ID。|
|Status|Integer|请求执行状态：-   0：表示该请求等待执行。
-   1：表示该请求正在执行中。
-   2：表示该请求已执行完成。

|
|WafTaskId|String|WAF的请求ID。|
|AclRules|List|精准访问控制规则列表，其中每条精准访问控制规则都会以AclRule子参数表述。AclRule子参数以JSON格式的字符串表述，具体参考AclRule参数格式说明。|
|Total|Integer|精准访问控制规则总数量。|

|名称|类型|描述|
|--|--|--|
|IsDefault|Integer|是否默认规则：-   0：表示否。
-   1：表示是。

|
|Order|Integer|规则顺序。**说明：** 该值越大，规则的优先级越高。

|
|ContinueBlockGeo|Integer|是否继续执行地区封禁，取值：-   0：表示否。
-   1：表示是。

|
|Action|Integer|规则的匹配动作，取值：-   0：表示阻断，即命中该规则的匹配条件，则阻断该访问请求。
-   1：表示放行，即命中该规则的匹配条件，则放行该访问请求。
-   2：表示告警，即命中该规则的匹配条件，将放行该访问请求，但会记录该请求并告警。

|
|ContinueWaf|Integer|是否继续执行Web攻击防护规则检测，取值：-   0：表示否。
-   1：表示是。

|
|ContinueSdk|Integer|是否继续执行SDK防护，取值：-   0：表示否
-   1：表示是。

|
|ContinueCc|Integer|是否继续执行CC防护规则检测，取值：-   0：表示否。
-   1：表示是。

|
|Conditions|Object|规则匹配条件，数组中具体定义参考[Conditions参数详细说明](#table_dfq_j5b_p2b)。|
|Name|String|规则名称。|
|ContinueDataRiskControl|Integer|是否继续执行数据风控防护，取值：-   0：表示否。
-   1：表示是。

|
|ContinueSA|Integer|是否继续执行智能防护引擎规则检测，取值：-   0：表示否。
-   1：表示是。

|

|参数|类型|描述|
|--|--|--|
|Key|String|匹配字段，包括IP、URL、Referer、User-Agent、Params、Cookie、Content-Type、X-Forwarded-For、Content-Length、Post-Body、Http-Method、Header。**说明：** 不同版本的WAF实例支持的匹配字段不同，您可以在Web应用防火墙管理控制台中查看您的实例当前所支持的匹配字段。

|
|Contain|Integer|逻辑符：-   0：表示不包含。
-   1：表示包含。
-   2：表示不存在。
-   10：表示不等于。
-   11：表示等于。
-   20：表示长度小于。
-   21：表示长度等于。
-   22：表示长度大于。
-   30：表示值小于。
-   31：表示值等于。
-   32：表示值大于。

|
|Value|String|匹配内容。|

## 示例 {#section_ix5_h1g_cz .section}

**请求示例**

``` {#createVPCpub}
https://wafopenapi.cn-hangzhou.aliyuncs.com/?Action=DescribeAclRules
&Domain=www.aliyun.com
&CurrentPage=1
&PageSize=50
&公共请求参数
```

**返回示例**

-   XML格式

    ```
    <?xml version="1.0" encoding="UTF-8"?>
    <DescribeAclRulesResponse>
        <RequestId>D7861F61-5B61-46CE-A47C-6B19160D5EB0</RequestId>
        <Result>
            <AclRules>
                <AclRule>
                    <IsDefault>1</IsDefault>
                    <Order>0</Order>
                    <ContinueBlockGeo>1</ContinueBlockGeo>
                    <Action>1</Action>
                    <ContinueWaf>1</ContinueWaf>
                    <ContinueSdk>0</ContinueSdk>
                    <Id>16572</Id>
                    <ContinueCc>1</ContinueCc>
                    <Conditions>
                        <condition>
                            <key>URL</key>
                            <contain>1</contain>
                            <value>asfas</value>
                        </condition>
                    </Conditions>
                    <Name>default</Name>
                    <ContinueDataRiskControl>1</ContinueDataRiskControl>
                    <ContinueSA>1</ContinueSA>
                 </AclRule>
            </AclRules>
            <Total>1</Total>
        </Result>
    </DescribeAclRulesResponse>
    ```

-   JSON格式

    ```
    {
        "RequestId":"D7861F61-5B61-46CE-A47C-6B19160D5EB0", 
        "Result":{
            "AclRules":{
                "AclRule":[
                    {
                        "IsDefault":1,
                        "Order":0,
                        "ContinueBlockGeo":1,
                        "Action":1,
                        "ContinueWaf":1,
                        "ContinueSdk":0,
                        "Id":16572,
                        "ContinueCc":1,
                        "Conditions":{
                            "condition":[
                                {
                                    "key":"URL",
                                    "contain":1,
                                    "value":"asfas"
                                }
                            ]
                        },
                        "Name":"default",
                        "ContinueDataRiskControl":1,
                        "ContinueSA":1
                }
            ]
        }, 
        "Total":1 
    }
    ```


