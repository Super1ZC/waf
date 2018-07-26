# DescribeAsyncTaskStatus {#reference_ivv_jmj_p2b .reference}

查询WAF任务执行状态。

## 请求参数 {#section_ybx_zfv_42b .section}

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是| 要执行的操作。 取值：

 DescribeAsyncTaskStatus

 |
|WafRequestId|String|是|WAF任务ID。|

## 返回参数 {#section_ugs_f1g_cz .section}

|名称|类型|描述|
|:-|:-|:-|
|RequestId|String|请求ID。|
|Status|Integer|请求执行状态：-   0：表示该请求等待执行。
-   1：表示该请求正在执行中。
-   2：表示该请求已执行完成。

|
|Progress|Integer|异步任务执行进度（百分比）。|
|AsyncTaskStatus|Integer|异步任务执行状态：-   0：表示该请求等待执行。
-   1：表示该请求正在执行中。
-   2：表示该请求已执行完成。

|
|ErrMsg|String|错误信息描述。**说明：** 该参数仅在请求执行发生错误时返回。

|
|ErrCode|String|错误代码。**说明：** 该参数仅在请求执行发生错误时返回。

|

## 示例 {#section_ix5_h1g_cz .section}

**请求示例**

``` {#createVPCpub}
https://wafopenapi.cn-hangzhou.aliyuncs.com/?Action=DescribeAsyncTaskStatus
&WafRequestId=aliyun.waf.20180719140433783.SvaZeY
&公共请求参数
```

**返回示例**

-   XML格式

    ```
    <?xml version="1.0" encoding="UTF-8"?>
    <DescribeAsyncTaskStatusResponse>
        <RequestId>12EF3845-CCEB-4B84-AE60-2B49B2FF1EE5</RequestId>
        <Result>
            <DomainConfig>
                <Progress>100</Progress>
                <AsyncTaskStatus>2</AsyncTaskStatus>
            </DomainConfig>
        </Result>
    </DescribeAsyncTaskStatusResponse>
    ```

-   JSON格式

    ```
    {
        "RequestId":"12EF3845-CCEB-4B84-AE60-2B49B2FF1EE5",
        "Result":{
            "DomainConfig":{
                "Progress":100,
                "AsyncTaskStatus":2
            }
        }
    }
    ```


