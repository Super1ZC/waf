# CreateCertAndKey {#reference_c5y_dx1_p2b .reference}

为已添加的域名配置记录上传证书及私钥信息。

您也可以调用该接口为指定域名配置更新已上传的证书及私钥信息。

## 请求参数 {#section_ybx_zfv_42b .section}

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是| 要执行的操作。 取值：

 CreateCertAndKey

 |
|Domain|String|是|域名名称。|
|Cert|String|是|证书文件内容。|
|Key|String|是|私钥文件内容|
|HttpsCertName|String|是|证书名称。|

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
https://wafopenapi.cn-hangzhou.aliyuncs.com/?Action=DeleteDomainConfig
&Domain=www.aliyun.com
&Cert="-----BEGIN CERTIFICATE----------END CERTIFICATE-----"
&Key="-----BEGIN RSA PRIVATE KEY----------END RSA PRIVATE KEY-----"
&HttpsCertName=www.aliyun.com
&公共请求参数
```

**返回示例**

-   XML格式

    ```
    <?xml version="1.0" encoding="UTF-8"?>
    <CreateCertAndKeyResponse>
        <RequestId>D7861F61-5B61-46CE-A47C-6B19160D5EB0</RequestId>
        <Result>
            <Status>2</Status>
            <WafTaskId>aliyun.waf.20180712214032277.qmxI9a</WafTaskId>
        </Result>
    </CreateCertAndKeyResponse>
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


