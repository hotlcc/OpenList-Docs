---
title:
  en: Third-party single sign-on
  zh-CN: 单点登录
categories:
  - guide
  - advanced
top: 60
---

## 1. Single sign-on client id { lang="en" }

## 1. 单点登录客户端ID { lang="zh-CN" }

::: en
client ID.
:::
::: zh-CN
客户端ID。
:::

## 2. Single sign-on client secrets { lang="en" }

## 2. 单点登录客户端秘钥 { lang="zh-CN" }

::: en
client secrets.
::: warning matters needing attention

1. Remember to write and save the background parameters of OpenList. After writing and saving, you have to go back to the bottom of the personal data and there will be a button that needs to be bound, otherwise it cannot be used
2. Only one of the four types of single sign-on can be enabled temporarily. If you used other single sign-on methods before and then changed to a new single Unbind (just one click) and then bind the single sign-on method you want to use now.
3. If you use **`GitHub,Microsoft,Google,DingTalk`**, you only need to fill in the client ID and secret key, and select the corresponding platform in the options.
   - If you use **`Casdoor`** the following parameters need to be filled in, just follow the tutorial to fill in

:::

::: zh-CN
客户端秘钥

::: warning 注意事项

1. OpenList 后台参数也记得写好保存，写好保存后也要回到个人资料下方会有一个需要绑定的按钮进行绑定，否则无法使用

2. 四种单点登录暂时只能启用一种，如果你之前用的是别的单点登录方式然后换了新的单点登录方式 那么你回到个人资料绑定的时候需要先将之前的解绑（点击一下即可）然后再绑定现在你要使用的单点登录方式。

3. 如果使用 **`GitHub,微软,谷歌,钉钉`**，只需要填写客户端ID和秘钥，选项中选择对应的平台即可
   - 如果使用 **`Casdoor`** 以下的参数都需要填写，照着教程填写即可

:::

## 3. Registration binding single sign-on { lang="en" }

## 3. 注册绑定单点登录 { lang="zh-CN" }

## <!--@include: ./sso/01-GitHub.md -->

## <!--@include: ./sso/02-Dingtalk.md -->

## <!--@include: ./sso/03-Microsoft.md -->

## <!--@include: ./sso/04-Google.md -->

## <!--@include: ./sso/05-Casdoor.md -->

## <!--@include: ./sso/06-Authentik.md-->

## <!--@include: ./sso/07-keycloak.md-->

## 4. SSO automatically registers as an OpenList account { lang="en" }

## 4. 单点登录自动注册为OpenList帐号 { lang="zh-CN" }

::: en

- **OpenList Version > **v3.22.1** New Features**
  Before using single sign-on to register as an OpenList account, we need to bind the single sign-on of OpenList first, the binding method is explained above
- Supports the `five` single sign-on methods mentioned above
- Do not use the default organization (**app-built-in**) directly, because all users in this organization are global administrator accounts
- Except `CASDOOR`, you only need to fill in the` Client id` and the `Client secrets`and the newly added single login account registered as OpenList account configuration

:::
::: zh-CN

- **OpenList 版本 > **v3.22.1** 新增功能**
  在使用单点登录注册为OpenList帐号前，我们需要先将OpenList的单点登录进行绑定，绑定方法在上面有说明
- 支持上述提到的`五个`单点登录方法
- 如果使用`Casdoor`,请勿直接使用默认组织(**app-built-in**),因为这个组织内的用户都是全局管理员帐号
- 除了`Casdoor`其它的只需要填写`客户端ID`和`客户端秘钥`以及下面新增的单点登录帐号注册为OpenList帐号的配置

:::

### 4.1. <i class="fa-solid fa-circle-0" style="color: #409eff;"></i>SSO Full Fill Demo { lang="en" }

### 4.1. <i class="fa-solid fa-circle-0" style="color: #409eff;"></i>SSO完整填写示例 { lang="zh-CN" }

::: en
Please refer to the detailed description below for how to fill in, the schematic diagram is just a reference for filling in and not suitable for everyone’s user habits

![](/img/advanced/sso-add.png)
:::

::: zh-CN
分别如何填写看下面的详细说明，示意图只是一个填写参考并不适合每个人的用户习惯

![](/img/advanced/sso-add.png)
:::

### 4.2. <i class="fa-solid fa-circle-1" style="color: #409eff;"></i>SSO auto register { lang="en" }

### 4.2. <i class="fa-solid fa-circle-1" style="color: #409eff;"></i>SSO自动注册 { lang="zh-CN" }

::: en
If we want SSO single sign-on to be registered as an OpenList account, we need to enable this option before it can be used
:::
::: zh-CN
如果我们想让SSO单点登录注册为OpenList帐号我们需要打开这个选项才可以使用
:::

### 4.3. <i class="fa-solid fa-circle-2" style="color: #409eff;"></i>SSO default dir { lang="en" }

### 4.3. <i class="fa-solid fa-circle-2" style="color: #409eff;"></i>SSO默认路径 { lang="zh-CN" }

::: en
That is to say, the default path used by the registered account is equivalent to the `Base path` in the OpenList user settings.

It can be the root directory `/`, or the path `/path/test/Demo` specified by the user

![](/img/advanced/sso-dir.png)
:::
::: zh-CN
也就是说注册的帐号默认使用的路径，相当于OpenList用户设置里面的`基本路径`

可以是根目录`/`，也可以是用户指定的路径`/path/test/Demo`

![](/img/advanced/sso-dir.png)
:::

### 4.4. <i class="fa-solid fa-circle-3" style="color: #409eff;"></i>SSO default permission { lang="en" }

### 4.4. <i class="fa-solid fa-circle-3" style="color: #409eff;"></i>SSO默认权限 { lang="zh-CN" }

::: en
It is equivalent to which permissions are enabled by default for registered users, as shown below

![](/img/advanced/sso-permission_b.png#light)

![](/img/advanced/sso-permission_h.png#dark)

The default is 0, no permission is enabled

If we need to enable some permissions during registration, we only need the sum of the numbers of different permissions.

For example：

1. We need to open the user's `WebDav reading` and `WebDav manage ` by default, that is 256+512=768, we just fill in `768` in the options
2. If we need to open the three permissions of `Make dir or upload`, `Rename` and `Delete` by default when registering, then it is 8+16+128=152, we can fill in `152` in the background
   I won’t say much about the examples, just add the permissions you need

:::
::: zh-CN

相当于注册的用户默认开通哪些权限，就如下面所示的
![](/img/advanced/sso-permission_b.png#light)
![](/img/advanced/sso-permission_h.png#dark)
默认为0，不开通任何权限
如果在注册时我们需要开通一些权限我们只需要不同权限的数字相加即可
例如：

1. 我们需要默认开通用户的`WebDav读取`和`WebDav管理`那就是256+512=768，我们就在填写选项填写`768`即可
2. 如果我们需要注册时默认开通`创建目录或上传`和`重命名`和`删除`这三个权限 那就是8+16+128=152，我们在后台填写`152`即可
   例子就不多说了，需要那个权限自己相加就可以

:::

### 4.5. <i class="fa-solid fa-circle-4" style="color: #409eff;"></i>Precautions and instructions { lang="en" }

### 4.5. <i class="fa-solid fa-circle-4" style="color: #409eff;"></i>注意事项以及说明 { lang="zh-CN" }

::: en
**4.1-There is already this user in the OpenList user database**

| username           | password | base\*path | role | permission | opt_secret | github_id | disabled | sso_id      |
| ------------------ | -------- | ---------- | ---- | ---------- | ---------- | --------- | -------- | ----------- |
| anyi               | FzdDfkmU | /test1     | 0    | 3          |            |           | 0        |             |
| anyi**\*dc188911** | RUCtgqCw | /test1     | 0    | 3          |            |           | 0        | **dc18891** |

As shown in the above table, a string of redundant ids is added after the newly registered single sign-on user name

This is because the same user already exists in the OpenList user database, so the sso_id is also added after the user name

If your newly registered single sign-on user name does not exist in the OpenList user database, it will not add the sso_id after the name

**4.2-What should I do if I don’t want the SSO account to be registered as an OpenList account?**

Just turn `SSO auto register` off,This will not affect the use of accounts that have been registered using Sso

**4.3-If I turn off the single sign-on option, what should I do with the account registered with Sso?**

Don't worry, after using single sign-on to register and log in to OpenList, log in in the background, and find `personal information` after logging in

- You can modify **`username`** and **`password`** by yourself, save it after modification, so that you can log in with the OpenList account normally
- At this time, you can click `Unbind Single Sign-On Platform`, you can unbind or not unbind, and the subsequent [**default path**](#sso-default-dir) and [**default permissions**](#sso-default-permission) of this user can only be modified by the administrator in the OpenList background user

**4.4-Why is this error code displayed when using sso?**

```json{3}
{
    "code": 400,
    "message": "The single sign on platform is not bound to any users: record not found",
    "data": null
}
```

This is because [Single Sign-On Automatic Registration](#sso-auto-register) is not enabled for the OpenList account, and the single sign-on cannot be registered as an OpenList account

- If you are an administrator, you can turn it on

- If you are a user, you can contact the administrator to enable

:::
::: zh-CN
**4.1-OpenList用户数据库已存在同名的帐号**

| username           | password | base_path | role | permission | opt_secret | github_id | disabled | sso_id      |
| ------------------ | -------- | --------- | ---- | ---------- | ---------- | --------- | -------- | ----------- |
| anyi               | FzdDfkmU | /本地1    | 0    | 3          |            |           | 0        |             |
| anyi\_**dc188911** | RUCtgqCw | /本地1    | 0    | 3          |            |           | 0        | **dc18891** |

如上表格所示，新注册的单点登录用户名称后增加了一串多余的id

这是因为OpenList用户数据库中已有了相同的用户，所以在用户名后把单点登录ID也添加上去了

如果你新注册的单点登录用户名在OpenList用户数据库中没有，它就不会在名字后面添加单点登录ID

**4.2-如果不想让单点登录的帐号注册为OpenList帐号了怎么办?**

把`Sso自动注册`关闭就可以，这样不影响已经使用单点登录注册好的帐号使用

**4.3-如果我把单点登录选项关闭，使用单点登录注册的帐号怎么办?**

不用担心，使用单点登录注册好登录OpenList后，在后台登录，登录好后找到`个人资料`

- 可以自行修改 **`用户名`**和**`密码`** ，修改好后保存，这样就可以正常使用OpenList帐号来登录了
- 这时候可以点击`解绑单点登录平台`了，解绑和不解绑都可以，后续该用户的[**默认路径**](#sso默认路径)和[**默认权限**](#sso默认权限)只能通过管理员在OpenList后台用户进行修改

**4.4-使用单点登录提示这个错误码是怎么回事?**

```json{3}
{
    "code": 400,
    "message": "The single sign on platform is not bound to any users: record not found",
    "data": null
}
```

这是因为[单点登录自动注册](#sso自动注册)为OpenList帐号的选项没开启，无法将单点登录注册为OpenList帐号

- 如果你是管理员，你可以开启一下
- 如果你是用户，你可以去联系管理员开启

:::

## 5. Sso compatibility mode { lang="en" }

## 5. SSO兼容模式 { lang="zh-CN" }

::: en
OpenList single -point login is bound to Dingtalk, and then opens OpenList in the **`Dingtalk`** application, When you log in, choose Dingtalk login and jump to your computer browser. After authorization, you find that there is no response, because the browser cannot jump to the Dingtalk application inner browser page

At this time, you need to open the **`sso compatability mode`** again to click on the login to log in successfully

**OpenList applied in Dingtalk and opened as shown in the figure：**

![](/img/advanced/sso_cm.png)

:::
::: zh-CN
OpenList单点登录绑定了钉钉，然后在 **`钉钉`** 应用内打开OpenList，登录时选择钉钉登录会跳到自己电脑浏览器，授权后你会发现没有后续反应了，因为浏览器无法跳回钉钉应用內浏览器页面

这时候就需要打开 **`SSO兼容模式`** 再去点击登录就可以登录成功了

**OpenList应用在钉钉软件内打开如图所示：**

![](/img/advanced/sso_cm.png)

:::

## 6. How to create the application in Dingtalk workbench { lang="en" }

## 6. 如何创建钉钉工作台內应用 { lang="zh-CN" }

::: en
A picture teaches you to create a new application and add it

- LOGO is not modified when the newly -built newly built, you can wait for the newly built and then modify <sup>See_Figure_2</sup>
- If you just browse OpenList in the Dingtalk application, you do n’t need a single -point login management, you do n’t need to set up a single -point login configuration, you can just add an application
  ![](/img/advanced/sso_add_app.png)

:::
::: zh-CN
一张图教你新建一个应用并且添加

- LOGO是默认的新建时不可修改，可以等新建好后再修改 <sup>(看图二)</sup>
- 如果你只是在钉钉应用內浏览OpenList，不使用单点登录后台管理，可以不用设置单点登录配置只添加应用就可以
  ![](/img/advanced/sso_add_app.png)

:::

### 6.1. Modify the application logo { lang="en" }

### 6.1. 修改应用LOGO { lang="zh-CN" }

::: en
Open [**DingTalk open platform management**](https://open-dev.dingtalk.com/fe/app#/corp/app) Find your newly built app to modify the logo.

![](/img/advanced/sso_fix_logo.png)

:::
::: zh-CN
打开 [**钉钉开放平台后台**](https://open-dev.dingtalk.com/fe/app#/corp/app) 找到你新建的应用进去修改LOGO就可以

![](/img/advanced/sso_fix_logo.png)

:::

## 7. redirect url { lang="en" }

## 7. 回调参数(重定向链接) { lang="zh-CN" }

::: en
After turning on **`Sso compatibility mode`** Then you need to log in to the corresponding software to modify the redirect url to change it to the two redirect url below

- `GitHub` only needs to add one：`http(s)://You_Url/api/auth/sso_get_token`
- `Microsoft` and` Google` both need to be added, you can add multiple Redirect urls, so you only need to add two Redirect URLs.

```
http(s)://You_Url/api/auth/get_sso_id
http(s)://You_Url/api/auth/sso_get_token
```

If you enable the **Sso compatibility mode** if you do not modify it, you will prompt `Invalid Redirect URL` Error

:::

::: zh-CN
开启 **`SSO兼容模式`** 后需要将单点登录对应的软件内修改一下回调参数链接改成下面的两个回调参数

- `GitHub` 只需要添加一条：`http(s)://You_Url/api/auth/sso_get_token`
- `微软`和`谷歌`两个都需要添加，可以添加多个，所以只需要新增两条就可以不用删除旧的

```
http(s)://You_Url/api/auth/get_sso_id
http(s)://You_Url/api/auth/sso_get_token
```

如果启用 SSO兼容模式 不修改则会提示 `invalid redirect url` 错误

:::
