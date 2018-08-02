# 在Web应用防火墙里无法上传私钥 {#concept_rbx_42l_q2b .concept}

## 问题描述 {#section_jhf_p2l_q2b .section}

在WAF里上传https证书时提示“Https私钥格式错误”。

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15609/15331812178005_zh-CN.png)

## 问题原因 {#section_lhf_p2l_q2b .section}

WAF无法识别被加密的私钥。

## 解决方案 {#section_ls3_q2l_q2b .section}

1.  查看私钥文件，确定包含如下图红框中的内容，说明私钥被加密了。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15609/15331812178006_zh-CN.png)

2.  执行如下命令，然后输入密码，进行解密操作。

    ```
    openssl rsa -in [$keyName] -text
    ```

    其中，`[$keyName]`为私钥文件名。

    系统返回类似如下，说明解密成功。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15609/15331812178007_zh-CN.png)

3.  在WAF里将解密后的私钥内容上传。

