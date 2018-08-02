# CC自定义防护验证 {#concept_frw_dgl_q2b .concept}

本文主要介绍CC自定义防护验证是否生效的方法。

## 操作步骤 {#section_vz3_hgl_q2b .section}

1.  CC自定义防护配置，详见[自定义CC防护](../../../../intl.zh-CN/用户指南/防护配置/自定义CC防护.md#)。
2.  配置后可在测试账号的域名下，配置相同的路径。然后使用测试命令测试对应的路径，验证是否生效，测试验证脚本如下。

    ```
    for i in ;do curl  -o /dev/null -s -w % http://vip5-kf9.xxxxxx.cn/bs/ks.j;echo " ";echo $i ;date ; done
    ab -c 10 -n 100 http://www.aliyun.com/
    ```

3.  CC自定义防护配置不生效检查。

    -   CC安全防护**状态**是否开启。
    -   **自定义规则**开关是否开启。
    -   **规则配置**是否正确。
    ![](https://cdn.yuque.com/lark/0/2018/png/100213/1528869162966-8bdea36d-7fbb-49b6-85b1-9ecec5680376.png)


更多信息，请参考[选择CC防护模式](../../../../intl.zh-CN/用户指南/防护配置/CC安全防护.md#)。

