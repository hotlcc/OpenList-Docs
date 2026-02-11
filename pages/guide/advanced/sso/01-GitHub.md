### 3.1. Github { lang="en" }

::: en
::: warning
If you want to use GitHub to log in, you first need the machine you built OpenList to be able to connect to GitHub before you can call and use it, otherwise you cannot use it if the link is not connected
:::
::: en
Open **https://github.com/settings/developers** Click **`New OAuth App`**
:::

### 3.1. GitHub { lang="zh-CN" }

::: zh-CN
::: warning
若想使用GitHub登录，首选需要你搭建OpenList的机器能连接访问GitHub才可以调用使用，不然连接不上无法使用
:::
::: zh-CN
打开 **https://github.com/settings/developers** 点击 **`New OAuth App`**
:::

#### 3.1.1. Register OAuth Instructions { lang="en" }

#### 3.1.1. Register OAuth 填写说明 { lang="zh-CN" }

::: en

- Application name
  - Write whatever you want to call it
- **Homepage URL**
  - home URL address
    - Both **http** and **https** can be used
- Application description
  - write whatever you want
- **Authorization callback URL**
  - Callback URL address
  - **https://your_domain/api/auth/sso_callback** - Both **http** and **https** can be used
    Remember to get **Client secrets** after filling it out, and then fill it in the OpenList background.
    Remember to write and save the background parameters of OpenList. After writing and saving, you have to go back to the bottom of the personal data and there will be a button that needs to be bound, otherwise it cannot be used

:::

::: zh-CN

- Application name
  - 随便写想叫什么叫什么
- **Homepage URL**
  - 主页网址地址
    - 可以使用http https都可以
- Application description
  - 随便写
- **Authorization callback URL**
  - 回调URL地址
  - **https://你的域名/api/auth/sso_callback** - 可以使用http https都可以
    填写完毕后记得获取一下 **Client secrets**，然后填写到OpenList后台。

:::

#### 3.1.2. Completely fill in the reference schematic { lang="en" }

#### 3.1.2. 完整填写参考示意图 { lang="zh-CN" }

::: en
![sso](/img/advanced/github.png)
:::
::: zh-CN
![sso](/img/advanced/github.png)
:::

#### 3.1.3. GitHub login Video Tutorials { lang="en" }

#### 3.1.3. GitHub视频教程 { lang="zh-CN" }

<BiliBili bvid="BV1KA41117m5" ratio="16:9" />
