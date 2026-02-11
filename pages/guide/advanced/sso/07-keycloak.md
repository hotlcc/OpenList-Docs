### 3.7. Keycloak

::: zh-CN
Keycloak 通过 OIDC（OpenID Connect）协议实现与 OpenList 的单点登录对接，可以作为 OpenList 的身份提供者，下面是配置步骤。
:::
::: en
Keycloak is integrated via the OIDC (OpenID Connect) protocol and can serve as an identity provider for OpenList. The steps below explain how to configure Keycloak for OpenList SSO.
:::

#### 3.7.1. Keycloak 设置 { lang="zh-CN" }

#### 3.7.1. Keycloak Setup { lang="en" }

##### 3.7.1.1. Create Realm { lang="en" }

##### 3.7.1.1. 新建 Realm { lang="zh-CN" }

::: zh-CN

- 登录到 Keycloak 管理控制台。
- 在左侧导航栏点击 `Manage realms`，选择`Create Realm`新建领域，或选用现有领域。

:::
::: en

- Log in to the Keycloak admin console.
- Click `Manage realms` in the left navigation bar, select `Create Realm` to create a new realm or use an existing one.

:::

##### 3.7.1.2. Create Client { lang="en" }

##### 3.7.1.2. 新建 Client { lang="zh-CN" }

::: zh-CN
选择领域后，在左侧菜单中找到 `Clients`并且进入该页面，点击`Create Client`。
:::
::: en
After selecting the realm, click `Clients` → `Create Client`.
:::

- **General settings**
  ![](/img/advanced/sso/keycloak-01.png)

  ::: en
  ::: details see the details
  |Name|Value|
  -|----
  |Client type|OpenID Connect|
  |Client ID| OpenList (or any name you prefer)|
  |Name| OpenList (or any name you prefer)|
  |Description| optional|
  |Always display in UI| select as needed|

  :::

  ::: zh-CN
  ::: details 查看详情
  |配置名|配置值|
  -|----
  |客户端类型|OpenID Connect|
  |客户端ID| OpenList（或你喜欢的任何名称）|
  |名称| OpenList（或你喜欢的任何名称）|
  |描述| 可选|
  |始终在 UI 中显示| 根据需要选择|

  :::

- **Capability config**
  ![](/img/advanced/sso/keycloak-02.png)
  ::: zh-CN
  ::: details 查看详情
  |配置名|配置值|
  -|----
  Client authentication| On|
  Authorization| Off|
  Authentication flow|`Standard Flow`，`Service account roles`|
  PKCE Method | 留空|
  Require DPoP bound tokens | Off|

  :::
  ::: en
  ::: details see the details
  |Name|Value|
  -|----
  Client authentication| On|
  Authorization| Off|
  Authentication flow|`Standard Flow`，`Service account roles`|
  PKCE Method | Leave blank|
  Require DPoP bound tokens | Off|

  :::

- **Login settings**
  ![](/img/advanced/sso/keycloak-03.png)
  ::: zh-CN
  ::: details 查看详情
  |配置名|配置值|
  -|----
  Root URL |留空
  Home URL |填入你OpenList的访问地址，如：https://your.openlist.domain
  Valid redirect URIs|`https://your.openlist.domain/api/auth/sso_callback?method=get_sso_id`<br>`https://your.openlist.domain/api/auth/sso_callback?method=sso_get_token`<br>`https://your.openlist.domain/api/auth/sso_get_token`<br>`https://your.openlist.domain/api/auth/get_sso_id`
  Valid post logout redirect URIs|留空
  Web origins |留空

  :::
  ::: en
  ::: details see the details
  |Name|Value|
  -|----
  Root URL |Leave blank
  Home URL |Enter your OpenList access address, e.g.: https://your.openlist.domain
  Valid redirect URIs|`https://your.openlist.domain/api/auth/sso_callback?method=get_sso_id`<br>`https://your.openlist.domain/api/auth/sso_callback?method=sso_get_token`<br>`https://your.openlist.domain/api/auth/sso_get_token`<br>`https://your.openlist.domain/api/auth/get_sso_id`
  Valid post logout redirect URIs|Leave blank
  Web origins |Leave blank

  :::

##### 3.7.1.3. 获取JWT公钥 { lang="zh-CN" }

##### 3.7.1.3. Retrieve JWT public key { lang="en" }

::: zh-CN

- 在左侧找到 `Clients`，选择刚创建的 Client 进入设置页面。
- 在 Client 设置页面，切换到 `Keys` 选项卡。
- 在 `Public Key` 字段中复制公钥内容，稍后在 OpenList 配置中使用。
- 如果没有看到公钥，可以点击 `Generate RSA Keys` 生成

:::
::: en

- In the left menu, find `Clients`, select the newly created Client to enter the settings page.
- In the Client settings page, switch to the `Keys` tab.
- Copy the content in the `Public Key` field for later use in OpenList configuration.
- If the public key is not visible, click `Generate RSA Keys` to generate it.

:::

##### 3.7.1.4. 获取Client Secret { lang="zh-CN" }

##### 3.7.1.4. Retrieve Client Secret { lang="en" }

::: zh-CN

- 在 Client 设置页面，切换到 `Credentials` 选项卡。
- 在 `Client Secret` 字段中复制客户端密钥内容，稍后在 OpenList 配置中使用。

:::
::: en

- In the Client settings page, switch to the `Credentials` tab.
- Copy the content in the `Client Secret` field for later use in OpenList configuration.

:::

#### 3.7.2. OpenList 设置 { lang="zh-CN" }

#### 3.7.2. OpenList Setup { lang="en" }

::: zh-CN
在 OpenList 的单点登录配置填写如下参数：

- **启用 SSO 登录**：`是`
- **SSO 登录平台**：`OIDC`
- **SSO 客户端ID**：Keycloak 客户端 ID（见上文[新建 Client](#_3-7-1-2-新建-client)）
- **SSO 客户端密钥**：Keycloak 客户端 Secret（见上文[获取Client Secret](#_3-7-1-4-获取client-secret)）
- **SSO OIDC 用户名键**：`preferred_username` 或按你的 Mapper 设置
- **SSO 组织名称**：`master` （与上文[新建 Realm](#_3-7-1-1-新建-realm)名称对应）
- **SSO 应用名**：`OpenList` （见上文[新建 Client](#_3-7-1-2-新建-client)）
- **SSO 端点名称**：`https://your.keycloak.domain/realms/{realm-name}` （realm-name与组织名一致）
- **SSO JWT 公钥**：见上文[获取JWT公钥](#_3-7-1-3-获取JWT公钥)
- **自动注册为 OpenList 帐号**：根据需要开启
- **SSO 兼容模式**：`否` （如果需要兼容可开启）

如有特殊需求，根据实际 Keycloak 部署调整 claims 和端点。

详细操作请参考 [Keycloak 官方 OIDC 文档](https://www.keycloak.org/documentation)。

:::

::: en
Fill in the following parameters in OpenList's SSO configuration:

- **SSO login enabled:** `yes`
- **SSO login platform:** `OIDC`
- **SSO client id:** Keycloak Client ID (from [Create Client](#_3-7-1-2-create-client) above)
- **SSO client secret:** Keycloak Client Secret (from [Retrieve Client Secret](#_3-7-1-4-retrieve-client-secret) above)
- **SSO oidc username key:** `preferred_username` or as per your Mapper settings
- **SSO organization name:** `master` (from [Create Realm](#_3-7-1-1-create-realm) above)
- **SSO application name:** `OpenList` (from [Create Client](#_3-7-1-2-create-client) above)
- **SSO endpoint name:** `https://your.keycloak.domain/realms/{realm-name}` (where realm-name matches the organization name)
- **SSO jwt public key:** from [Retrieve JWT public key](#_3-7-1-3-retrieve-jwt-public-key) above
- **SSO auto register as OpenList account:** Enable as needed
- **SSO compatibility mode:** `no` (enable if compatibility is required)

Adjust claims and endpoints based on your specific Keycloak deployment if needed.
For detailed operations, refer to the [Keycloak official OIDC documentation](https://www.keycloak.org/documentation).
:::
