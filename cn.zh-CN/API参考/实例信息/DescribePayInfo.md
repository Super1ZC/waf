# DescribePayInfo {#reference_tmg_l5c_p2b .reference}

获取指定地域的WAF实例当前信息。

**说明：** 请求该API接口时，无需指定InstanceId公共请求参数。

## 请求参数 {#section_ybx_zfv_42b .section}

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是| 要执行的操作。 取值：

 DescribePayInfo

 |
|Region|String|是|地域ID，取值：-   cn：表示中国大陆地区。
-   cn-hongkong：表示海外地区。

|

## 返回参数 {#section_ugs_f1g_cz .section}

|名称|类型|描述|
|:-|:-|:-|
|RequestId|String|请求ID。|
|Status|Integer|WAF实例当前状态：-   0：表示已到期。
-   1：表示正常。

**说明：** 该参数仅对包年包月WAF实例有意义。

|
|Trial|Integer|是否试用版WAF实例：-   0：表示否。
-   1：表示是。

**说明：** 该参数仅对按量计费WAF实例有意义。

|
|InstanceId|String|实例ID。|
|InDebt|Integer|当前实例是否欠费：-   0：表示已欠费。
-   1：表示正常。

**说明：** 该参数按量计费WAF实例有意义。

|
|Region|String|所属地域：-   cn：表示中国大陆地区。
-   cn-hongkong：表示海外地区。

|
|RemainDay|Integer|试用版WAF实例剩余可用天数。**说明：** 该参数仅对按量计费WAF实例有意义。

|
|PayType|Integer|WAF实例类型：-   0：表示未购买或未开通。
-   1：表示包年包月实例。
-   2：表示按量付费实例。

|
|EndDate|Long|实例到期时间。**说明：** 对于按量付费实例，表示试用版到期时间。

|

## 示例 {#section_ix5_h1g_cz .section}

**请求示例**

``` {#createVPCpub}
https://wafopenapi.cn-hangzhou.aliyuncs.com/?Action=DescribePayInfo
&Region=cn
&公共请求参数
```

**返回示例**

-   XML格式

    ```
    <?xml version="1.0" encoding="UTF-8"?>
    <DescribePayInfoResponse>
        <RequestId>56B40D30-4960-4F19-B7D5-2B1F0EE6CB70</RequestId>
        <Result>
            <Status>1</Status>
            <Trial>0</Trial>
            <InstanceId>waf_elasticity-cn-0xldbqtm005</InstanceId>
            <InDebt>1</InDebt>
            <Region>cn</Region>
            <RemainDay>0</RemainDay>
            <PayType>2</PayType>
            <EndDate>1512921600</EndDate>
        </Result>
    </DescribePayInfoResponse>
    ```

-   JSON格式

    ```
    {
        "RequestId":"276D7566-31C9-4192-9DD1-51B10DAC29D2",
        "Result":{
            "Status":1,
            "Trial":0,
            "InstanceId":"waf_elasticity-cn-0xldbqtm005",
            "InDebt":1,
            "Region":"cn",
            "RemainDay":0,
            "PayType":2,
            "EndDate":1512921600
        }
    }
    ```


