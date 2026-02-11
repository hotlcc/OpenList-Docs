### 3.4. Google { lang="en" }

### 3.4. 谷歌 { lang="zh-CN" }

::: en
::: warning
If you want to use Google to log in, you first need the machine you built OpenList to be able to connect to Google before you can call and use it, otherwise you cannot use it if the link is not connected
:::

::: en

1. First open **https://console.cloud.google.com/projectselector2/apis/dashboard?hl=zh-cn**
2. If you are using it for the first time, you need to create a new project first (just write whatever you want, skip it if it has already been created)
3. Then configure the [consent screen](#agree-to-screen-configuration) (there is a separate instruction on how to configure the document, if it is already configured, skip it)
4. After configuring the unified screen, we click the credentials on the left, create credentials, and select OAuth client ID

- Application Type Select Web Application, and write the name as you like
- Then add our two callback parameters in the authorized redirect URI

```bash title="Callback" parameter example
http://127.0.0.1:5244/api/auth/sso_callback?method=get_sso_id
http://127.0.0.1:5244/api/auth/sso_callback?method=sso_get_token
```

- Write **http(s):\//your own domain name/api/auth/sso_callback?method=get_sso_id** when filling in and using it by yourself
- Write **http(s):\//your own domain name/api/auth/sso_callback?method=sso_get_token** when filling in and using it by yourself
  After filling it out, click Create to get the OAuth client ID and secret key
- (It doesn't matter if you accidentally close it here, just click on the name of the application we created and enter it in the upper right position to see it)
  We have got the client ID and secret key and fill them in the OpenList single sign-on configuration.
  Remember to write and save the background parameters of OpenList. After writing and saving, you have to go back to the bottom of the personal data and there will be a button that needs to be bound, otherwise it cannot be used

:::

::: zh-CN
::: warning
若想使用Google登录，首选需要你搭建OpenList的机器能连接访问Google才可以调用使用，不然连接不上无法使用
:::
::: zh-CN

1. 首先打开 **https://console.cloud.google.com/projectselector2/apis/dashboard?hl=zh-cn**
2. 如果是第一次使用需要先新建一个项目（随便写就行，如果已创建跳过）
3. 然后配置[同意屏幕](#同意屏幕配置)（如何配置文档中有单独说明，如果已经配置好跳过）
4. 配置好统一屏幕后我们点左侧的凭据，创建凭据，选择OAuth 客户端ID

- 应用类型 选择 Web 应用，名称随便写
- 然后在 已获授权的重定向 URI 添加我们的两个回调参数

```bash title="回调参数示例"
http://127.0.0.1:5244/api/auth/sso_callback?method=get_sso_id
http://127.0.0.1:5244/api/auth/sso_callback?method=sso_get_token
```

- 大家使用的时候写 **http(s):\//自己域名/api/auth/sso_callback?method=get_sso_id**
- 大家使用的时候写 **http(s):\//自己域名/api/auth/sso_callback?method=sso_get_token**
  填写好后，点击创建就能拿到 OAuth的客户端ID和秘钥
- （在这里如果你不小心关闭了也没关系，点击我们创建的应用名称进去在右上的位置就能看到）
  客户端ID和秘钥我们都拿到了填写到OpenList单点登录配置里面去即可
  OpenList 后台参数也记得写好保存，写好保存后也要回到个人资料下方会有一个需要绑定的按钮进行绑定，否则无法使用

:::

#### 3.4.1. Agree to screen configuration { lang="en" }

#### 3.4.1. 同意屏幕配置 { lang="zh-CN" }

::: en
If it has been configured, just ignore this picture (you can zoom in if you can’t see it clearly)
![google-oauth-00](/img/drivers/google/google-oauth-eng-00.png)
![google-oauth-01](/img/drivers/google/google-oauth-eng-01.png)
![google-oauth-02](/img/drivers/google/google-oauth-eng-02.png)
:::
::: zh-CN
如已配置好 忽略本图即可(如果看不清楚可以放大)
![google-oauth-00](/img/drivers/google/google-oauth-00.png)
![google-oauth-01](/img/drivers/google/google-oauth-01.png)
![google-oauth-02](/img/drivers/google/google-oauth-02.png)
:::

#### 3.4.2. Completely fill in the reference schematic { lang="en" }

#### 3.4.2. 完整填写参考示意图 { lang="zh-CN" }

::: en
![sso](/img/advanced/google.png)
:::
::: zh-CN
![sso](/img/advanced/google.png)
:::
