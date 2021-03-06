# QueryTaskList {#concept_ic1_wyk_c2b .concept}

QueryTaskList：分页查询自己账户下的域名任务列表。

## 请求参数 {#section_w3j_zsm_c2b .section}

公共请求参数，详见[公共参数](intl.zh-CN/API 参考/调用方式/公共参数.md#)。

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是|操作接口名，系统规定参数，取值：QueryTaskList。|
|PageNum|Integer|是|分页页码。|
|PageSize|Integer|是|分页大小。|
|BeginCreateTime|Long|否|到期日期范围查询开始时间，UTC时间1970年1月1日0点距离现在的毫秒数，目前只支持按天查询。|
|EndCreateTime|Long|否|到期日期范围查询结束时间，UTC时间1970年1月1日0点距离现在的毫秒数，目前只支持按天查询。|

## 返回参数 {#section_npt_ctm_c2b .section}

|名称|类型|描述|
|:-|:-|:-|
|RequestId|String|唯一请求识别码。|
|TotalItemNum|Integer|总数。|
|CurrentPageNum|Integer|当前页码。|
|TotalPageNum|Integer|总页数。|
|PageSize|Integer|分页大小。|
|PrePage|Boolean|是否有上一页。|
|NextPage|Boolean|是否有下一页。|
|Data|[TaskInfoType](#table_dhm_gtm_c2b)|任务列表。|

|类型|名称|描述|
|:-|:-|:-|
|String|TaskType|任务类型。枚举值范围： -   CHG\_HOLDER 修改所有者信息
-   CHG\_DNS 修改DNS
-   SET\_WHOIS\_PROTECT 设置隐私保护
-   UPDATE\_ADMIN\_CONTACT 修改管理者信息
-   UPDATE\_BILLING\_CONTACT 修改付费者信息
-   UPDATE\_TECH\_CONTACT 修改技术者信息
-   SET\_UPDATE\_PROHIBITED 设置域名安全锁
-   SET\_TRANSFER\_PROHIBITED 设置域名转移锁
-   ORDER\_ACTIVATE 创建注册订单
-   ORDER\_RENEW 创建续费订单
-   ORDER\_REDEEM 创建赎回订单
-   CREATE\_DNSHOST 创建DNS host
-   UPDATE\_DNSHOST 更新DNS host
-   SYNC\_DNSHOST 同步DNS host

 |
|Integer|TaskNum|任务包含域名数量。|
|String|TaskStatus|任务状态。可能值： -   WAITING\_EXECUTE 等待执行
-   EXECUTING 执行中
-   COMPLETE 执行完成

 |
|String|TaskStatusCode|任务状态码。可能值： -   1 等待执行
-   2 执行中
-   3 执行完成

 |
|String|CreateTime|任务创建时间。|
|String|Clientip|提交任务时用户IP。|
|String|TaskNo|任务编号。|
|String|TaskTypeDescription|任务类型描述。|

## 错误码 {#section_izl_ptm_c2b .section}

|错误代码|描述|HTTP状态码|语义|
|:---|:-|:------|:-|
|ParameterIllegal|Parameter illegal.|400|参数错误。|
|NetworkIOError|Network IO Error.|400|网络I/O异常。|

## 示例 {#section_lsg_stm_c2b .section}

**请求示例**

``` {#codeblock_c6y_9es_s1x}
http://domain-intl.aliyuncs.com/?Action=QueryTaskList
&PageNum=1
&PageSize=2
&<公共请求参数>
```

**返回示例**

-   XML示例

    ``` {#codeblock_ayj_0fj_wqi}
    <?xml version='1.0' encoding='UTF-8'?>
    <QueryTaskListResponse>
        <Data>
            <TaskInfo>
                <Clientip>127.0.0.1</Clientip>
                <TaskNo>8b1cd755-4928-4b02-adee-e5d41d7b1939</TaskNo>
                <CreateTime>Dec 26,2017 11:00:54</CreateTime>
                <TaskStatus>COMPLETE</TaskStatus>
                <TaskNum>1</TaskNum>
                <TaskType>CREATE_DNSHOST</TaskType>
            </TaskInfo>
            <TaskInfo>
                <Clientip>127.0.0.1</Clientip>
                <TaskNo>b0069db5-db21-4e57-842a-260c370a37e2</TaskNo>
                <CreateTime>Dec 26,2017 11:00:54</CreateTime>
                <TaskStatus>COMPLETE</TaskStatus>
                <TaskNum>2</TaskNum>
                <TaskType>CHG_DNS</TaskType>
            </TaskInfo>
        </Data>
        <TotalItemNum>43</TotalItemNum>
        <PageSize>2</PageSize>
        <CurrentPageNum>1</CurrentPageNum>
        <RequestId>8D7D294A-8E99-481F-B64C-017EFC793059</RequestId>
        <TotalPageNum>22</TotalPageNum>
    </QueryTaskListResponse>
    ```

-   JSON示例

    ``` {#codeblock_ooo_5p9_sb1}
    {
      "CurrentPageNum": 1,
      "Data": {
        "TaskInfo": [
          {
            "Clientip": "127.0.0.1",
            "CreateTime": "Dec 26,2017 11:00:54",
            "TaskNo": "8b1cd755-4928-4b02-adee-e5d41d7b1939",
            "TaskNum": 1,
            "TaskStatus": "COMPLETE",
            "TaskType": "CREATE_DNSHOST"
          },
          {
            "Clientip": "127.0.0.1",
            "CreateTime": "Dec 26,2017 11:00:54",
            "TaskNo": "b0069db5-db21-4e57-842a-260c370a37e2",
            "TaskNum": 2,
            "TaskStatus": "COMPLETE",
            "TaskType": "CHG_DNS"
          }
        ]
      },
      "PageSize": 2,
      "RequestId": "85C735DC-872F-423B-A728-C20C2924D3C6",
      "TotalItemNum": 43,
      "TotalPageNum": 22
    }
    ```


