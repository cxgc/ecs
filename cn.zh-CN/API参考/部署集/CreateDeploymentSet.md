# CreateDeploymentSet {#doc_api_910711 .reference}

在指定的地域内创建一个部署集。

## 调试 {#apiExplorer .section}

单击[这里](https://api.aliyun.com/#product=Ecs&api=CreateDeploymentSet)在OpenAPI Explorer中进行可视化调试，并生成SDK代码示例。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|RegionId|String|是|cn-hangzhou|部署集所属地域ID。您可以调用 [DescribeRegions](~~25609~~) 查看最新的阿里云地域列表。

 |
|Action|String|否|CreateDeploymentSet|系统规定参数。取值：CreateDeploymentSet

 |
|ClientToken|String|否|123e4567-e89b-12d3-a456-426655440000|保证请求幂等性。从您的客户端生成一个参数值，确保不同请求间该参数值唯一。**ClientToken** 只支持 ASCII 字符，且不能超过 64 个字符。更多详情，请参阅 [如何保证幂等性](~~25693~~)。

 |
|DeploymentSetName|String|否|FinanceDeployment|部署集名称。长度为 2~128 个英文或中文字符。必须以大小字母或中文开头，不能以 http:// 和 https:// 开头。可以包含数字、半角冒号（:）、下划线（\_）或者连字符（-）。

 |
|Description|String|否|FinanceJoshua|部署集描述信息。长度为 2~256 个英文或中文字符，不能以 http:// 和 https:// 开头。

 |
|Domain|String|否|Defalut|部署域。

 默认值：Defalut。

 **说明：** 该参数即将弃用，为提高兼容性，请尽量使用其他参数。

 |
|Granularity|String|否|Host|部署粒度。

 **说明：** 该参数即将弃用，为提高兼容性，请尽量使用其他参数。

 |
|OnUnableToRedeployFailedInstance|String|否|CancelMembershipAndStart|部署集内实例宕机迁移后，缺乏可供打散的实例库存的紧急处理方案。取值范围：

 -   CancelMembershipAndStart（默认）：将实例移出部署集，宕机迁移后即刻启动实例。
-   KeepStopped：保持异常状态等待补货充足后再启动实例。

 |
|OwnerAccount|String|否|ECSforCloud@Alibaba.com|RAM用户的账号登录名称。

 |
|Strategy|String|否|StrictDispersion|部署策略。

 **说明：** 该参数即将弃用，为提高兼容性，请尽量使用其他参数。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|DeploymentSetId|String|ds-bp1frxuzdg87zh4pzqkcm|部署集ID

 |
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|请求 ID。无论调用接口成功与否，我们都会返回请求 ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://ecs.aliyuncs.com/?Action=CreateDeploymentSet
&RegionId=cn-hangzhou
&DeploymentStrategy=Availability
&DeploymentSetName=AvailMySet
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<CreateDeploymentSetResponse>
  <RequestId>04F0F334-1335-436C-A1D7-6C044FE73368</RequestId>
  <DeploymentSetId>ds-bp1frxuzdg87zh4pzqkcm</DeploymentSetId>
</CreateDeploymentSetResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"04F0F334-1335-436C-A1D7-6C044FE73368",
	"DeploymentSetId":"ds-bp1frxuzdg87zh4pzqkc"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|InvalidDescription.Malformed|The specified parameter Description is not valid.|指定的资源描述格式不合法。长度为2-256个字符，不能以 http:// 和 https:// 开头。|
|400|InvalidDeploymentSetId.NotFound|The specified DeploymentSetId does not exist.|指定的参数 DeploymentSetId 不存在，请您检查 DeploymentSetId 是否正确。|
|400|MissingParameter|The input parameter DeploymentSetId that is mandatory for processing this request is not supplied.|未提供必需的 DeploymentSetId。|
|400|InvalidParameter.Domain|The specified parameter Domain is not valid.|指定的 Domain 参数不合法。|
|400|InvalidParameter.Strategy|The specified parameter Strategy is not valid|指定的 Strategy 不合法。|
|400|InvalidParameter.granularity|The specified parameter Granularity is not valid.|指定的 Granularity 参数不合法。|
|400|DependencyViolation.domain.granularity|The DeploymentSet domain and granularity is violation.|部署集域与数据粒度冲突。|
|400|DependencyViolation.strategy.granularity|The DeploymentSet strategy and granularity is violation.|部署集策略与数据粒度冲突。|
|400|DEPLOYMENTSET.QUOTA\_FULL|The deploymentSet quota is full|部署集配额已满，请您减少部署集数量。|

[查看本产品错误码](https://error-center.aliyun.com/status/product/Ecs)

