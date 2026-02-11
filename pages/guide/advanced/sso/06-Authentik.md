### 3.6. Authentik

#### 3.6.1. Authentik Setup { lang="en" }

#### 3.6.1. Authentik 设置 { lang="zh-CN" }

:::en
**Create a Provider for OpenList**

1. Menu -> Applications -> Providers -> Create
2. Select `OAuth2/OpenID Provider` and click next
3. Enter an application name, this guide assumes you will call the provider `OpenList`
4. Select your authorization flow. The built-in `default-provider-authorization-implicit-consent` is acceptable
5. Make note of the `Client ID` and `Client Secret` fields as provided by Authentik - save these values for later
6. For Redirect UDIs/Origins, enter the following, replacing [your.openlist.domain] with the FQDN for your OpenList installation:

```bash title="Callback" parameters
https://your.openlist.domain/api/auth/sso_callback\?method=sso_get_token
https://your.openlist.domain/api/auth/sso_callback\?method=get_sso_id
```

    Please note the \ character before ? as an escape character for the regex used for this URI is mandatory.

7. Make note of the signing key selected as you will need it later. This guide assumes you will use the default `authentik Self-signed Certificate`
8. Save the new provider

**Create an Application for OpenList**

1. Menu -> Applications -> Application -> Create
2. Enter an application name, recommended `OpenList`
3. An application slug of `openlist` will be automatically selected for you. This guide assumes you will keep this value
4. Select the provider by name you selected in Provider Setup step 3 - `OpenList`
5. Save the new application

**Retrieve the JWT certificate**

1. Menu -> System -> Certificates
2. Select the `>` next to the `authentik Self-signed Certificate`. If you chose another certificate for the application, select that certificate instead
3. Click Download Certificate to get a copy of the public JWT key

:::

::: zh-CN

**为 OpenList 创建提供程序**

1. 菜单 -> 应用程序 -> 提供程序 -> 创建
2. 选择 `OAuth2/OpenID 提供程序` 并点击下一步
3. 输入应用程序名称，本指南假设你将提供程序命名为 `OpenList`
4. 选择授权流。内置的 `default-provider-authorization-implicit-consent` 是可接受的
5. 记下由 Authentik 提供的 `Client ID` 和 `Client Secret` 字段—保存这些值以供后用
6. 对于重定向的 UDI/来源，输入以下内容，将 \[your.openlist.domain] 替换为你的 OpenList 安装的 FQDN：

```bash title="回调" 参数
https://your.openlist.domain/api/auth/sso_callback\?method=sso_get_token
https://your.openlist.domain/api/auth/sso_callback\?method=get_sso_id
```

```
请注意，? 前的 \ 字符作为正则表达式中 URI 的转义字符是必需的。
```

7. 记下所选的签名密钥，稍后会用到。假设你将使用默认的 `authentik 自签名证书`
8. 保存新的提供程序

**为 OpenList 创建应用程序**

1. 菜单 -> 应用程序 -> 应用程序 -> 创建
2. 输入应用程序名称，建议使用 `OpenList`
3. 应用程序 slug 将自动选择为 `openlist`。本指南假设你会保留此值
4. 选择在提供程序设置步骤 3 中选择的提供程序名称 — `OpenList`
5. 保存新的应用程序

**获取 JWT 证书**

1. 菜单 -> 系统 -> 证书
2. 选择 `>` 旁边的 `authentik 自签名证书`。如果你为应用选择了其他证书，选择该证书
3. 点击“下载证书”以获取公共 JWT 密钥的副本

:::

#### 3.6.2. OpenList Setup { lang="en" }

#### 3.6.2. OpenList 设置 { lang="zh-CN" }

::: en

- **Sso login enabled:** `yes`
- **Sso login platform:** `OIDC`
- **Sso client id:** [Client ID from Authentik]
- **Sso client secret:** [Client Secret from Authentik]
- **Sso oidc username key:** `preferred_username`
- **Sso organization name:** `user`
- **Sso application name:** `user`
- **Sso endpoint name:** `https://your.authentik.domain/application/o/openlist/`
  - **Note:** Replace [your.authentik.domain] with the FQDN for your Authentik installation. Mind the trailing `/` at the end of the path. If you chose a different application slug in Authentik Application setup 3, substitute that here
- **Sso jwt public key:** Open the certificate file downloaded in step 3.3 of the Authentik Application setup and paste the contents here. It will start with `-----BEGIN CERTIFICATE-----`
- **Sso compatability mode:** `no`

:::

::: zh-CN

- **启用 SSO 登录：** `是`
- **SSO 登录平台：** `OIDC`
- **SSO 客户端 ID：** \[来自 Authentik 的 Client ID]
- **SSO 客户端密钥：** \[来自 Authentik 的 Client Secret]
- **SSO OIDC 用户名键：** `preferred_username`
- **SSO 组织名称：** `user`
- **SSO 应用程序名称：** `user`
- **SSO 端点名称：** `https://your.authentik.domain/application/o/openlist/`
  - **注意：** 将 \[your.authentik.domain] 替换为你的 Authentik 安装的 FQDN。注意路径末尾的斜杠 `/`。如果你在 Authentik 应用程序设置第 3 步选择了不同的应用程序 slug，请在此处替换

- **SSO JWT 公钥：** 打开在 Authentik 应用程序设置第 3.3 步中下载的证书文件，并将内容粘贴在此处。它以 `-----BEGIN CERTIFICATE-----` 开头
- **SSO 兼容模式：** `否`

:::
