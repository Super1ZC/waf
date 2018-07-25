# CreateAclRule {#reference_wlc_f4b_p2b .reference}

为指定域名添加精准访问控制规则。

## 请求参数 {#section_ybx_zfv_42b .section}

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是| 要执行的操作。 取值：

 CreateAclRule

 |
|Domain|String|是|域名名称。|
|Rules|String|是|精准访问控制规则详细信息，采用JSON格式的字符串表述，具体参考[Rules参数格式说明](#table_k1x_44b_p2b)。|

|名称|类型|是否必须|描述|
|--|--|----|--|
|Id|Long|否|规则ID。|
|Name|String|是|规则名称。|
|Action|Integer|是|规则的匹配动作，取值：-   0：表示阻断，即命中该规则的匹配条件，则阻断该访问请求。
-   1：表示放行，即命中该规则的匹配条件，则放行该访问请求。
-   2：表示告警，即命中该规则的匹配条件，将放行该访问请求，但会记录该请求并告警。

|
|ContinueComponent|String|否|是否继续执行其它WAF防护策略，采用JSON格式的字符串表述，具体参考[ContinueComponent参数格式说明](#table_cvb_rrb_p2b)。|
|Conditions|Array|否|规则匹配条件，数组中具体定义参考[Conditions参数详细说明](#table_dfq_j5b_p2b)。|

|参数|类型|是否必须|描述|
|--|--|----|--|
|post\_action\_cc|Integer|否|是否继续执行CC防护规则检测，取值：-   0：表示否。
-   1：表示是。

|
|post\_action\_waf|Integer|否|是否继续执行Web攻击防护规则检测，取值：-   0：表示否。
-   1：表示是。

|
|post\_action\_sa|Integer|否|是否继续执行智能防护引擎规则检测，取值：-   0：表示否。
-   1：表示是。

|
|post\_action\_block\_geo|Integer|否|是否继续执行地区封禁，取值：-   0：表示否。
-   1：表示是。

|
|post\_action\_data\_risk\_control|Integer|否|是否继续执行数据风控防护，取值：-   0：表示否。
-   1：表示是。

|
|post\_action\_sdk|Integer|否|是否继续执行SDK防护，取值：-   0：表示否
-   1：表示是。

|

|参数|类型|是否必须|描述|
|--|--|----|--|
|Key|String|是|匹配字段，取值包括IP、URL、Referer、User-Agent、Params、Cookie、Content-Type、X-Forwarded-For、Content-Length、Post-Body、Http-Method、Header。**说明：** 不同版本的WAF实例支持的匹配字段不同，您可以在Web应用防火墙管理控制台中查看您的实例当前所支持的匹配字段。

|
|Contain|Integer|是|逻辑符，取值：-   0：表示不包含。
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
|Value|String|是|匹配内容。|

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
https://wafopenapi.cn-hangzhou.aliyuncs.com/?Action=CreateAclRule
&Domain=www.aliyun.com
&ServiceOn=1
&Rules={...}
&公共请求参数
```

**Rules参数示例**

```
{
    "name":"leidan3",
    "action":1,
    "conditions":[{
        "key":"URL",
        "contain":1,
        "value":"asfas"}],
    "continueComponent":{
        "post_action_cc":"1",
        "post_action_waf":"1",
        "post_action_sa":"1",
        "post_action_block_geo":"1",
        "post_action_data_risk_control":"0"
    }
} 


```

**返回示例**

-   XML格式

    ```
    <?xml version="1.0" encoding="UTF-8"?>
    <CreateAclRuleResponse>
        <RequestId>D7861F61-5B61-46CE-A47C-6B19160D5EB0</RequestId>
        <Status>2</Status>
        <WafTaskId>aliyun.waf.20180712214032277.qmxI9a</WafTaskId>
    </CreateAclRuleResponse>
    ```

-   JSON格式

    ```
    {
        "RequestId":"D7861F61-5B61-46CE-A47C-6B19160D5EB0", 
        "Status":2,
        "WafTaskId":"aliyun.waf.20180712214032277.qmxI9a" 
    }
    ```


