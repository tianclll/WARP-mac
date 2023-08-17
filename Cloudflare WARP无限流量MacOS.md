# 一、下载Cloudflare WARP

官网地址:https://1.1.1.1/,

下载macOS版本，解压后安装，并启动

<img src="/Users/liuhongdi/Library/Application Support/typora-user-images/image-20230817161955566.png" alt="image-20230817161955566" style="zoom:25%;" />

启动后会在状态栏中显示出来。

# 二、升级为Warp+ 24PB版

- 1.打开网址：https://blog.upx8.com/warp.html，点击生成密钥；![image-20230817161633313](/Users/liuhongdi/Library/Application Support/typora-user-images/image-20230817161633313.png)

- 2.将生成的密钥复制到Cloudflare WARP中：

  - 点击状态栏上的Cloudflare WARP程序

  - 点击右上角的设置

    <img src="/Users/liuhongdi/Library/Application Support/typora-user-images/image-20230817162359527.png" alt="image-20230817162359527" style="zoom:25%;" />

  - 点击‘’Preferences‘’

    <img src="/Users/liuhongdi/Library/Application Support/typora-user-images/image-20230817162612030.png" alt="image-20230817162612030" style="zoom:25%;" />

  - 点击‘’Account‘’ ---> "Use Different Key"

    ![image-20230817163009169](/Users/liuhongdi/Library/Application Support/typora-user-images/image-20230817163009169.png)

​		若报错key无效或者不是24PB，就重复第一个步骤，重新生成密钥（建议一次性多生成几个,然后一个一个的试）

# 三、再升级成Zero Trust(无限流量)

这一步，升不升都可以，因为Warp+版本已经有24PB流量了，相当于无限了。因为这一步会比较麻烦。。

## 1.创建Cloudflare账号

- (1)打开 Cloudflare 的控制台：https://dash.cloudflare.com/ ，注册一个账号。然后点击左侧栏的“Zero Trust”按钮，进入 Zero Trust 页面。

## 2.添加团队

- (1)输入组织名称(自己命名)，点击“Next”按钮

![image-20230817164408303](/Users/liuhongdi/Library/Application Support/typora-user-images/image-20230817164408303.png)

- (2)选择最左边那个“Free”计划

  ![image-20230817164741675](/Users/liuhongdi/Library/Application Support/typora-user-images/image-20230817164741675.png)

- (3)点击“Proceed to payment”按钮

- (4)回到控制台，然后登出并重新登录自己的 CloudFlare 账户，进入 Zero Trust 主页，依次点击左侧栏的“My Team”→“Devices”，点击蓝色的“Connect a device”按钮

- (5)输入邮箱后缀（例如，support@qq.com，其后缀为@qq.com）然后点击“Save”保存即可。

## 3.升级为Zero Trust

- (1)然后又点击状态栏上的Cloudflare WARP程序到‘Accouut’‘

![image-20230817163009169](/Users/liuhongdi/Library/Application Support/typora-user-images/image-20230817163009169.png)

- (2)点击右下角的"Login to Cloudflare Zero Trust",然后输入刚刚创建的团队名称，然后点‘’Accept‘’这些。

- (3)会弹出一个页面，输入自己的邮箱就行，注意输入邮箱的后缀要和刚刚第2.(5)保持一致。然后接受验证码，输入验证码。

- (4)变成这种就成功了

  <img src="/Users/liuhongdi/Library/Application Support/typora-user-images/image-20230817165937072.png" alt="image-20230817165937072" style="zoom:25%;" />



# 四、配置优选IP

## 1.获取优选IP

- 下载获取对端IP脚本,并执行

```
cd 优选IP脚本 && chomod +x warp && bash warp-yxip-mac.sh
```

![image-20230817171831153](/Users/liuhongdi/Library/Application Support/typora-user-images/image-20230817171831153.png)

选择1，然后回车

- 然后等待结果，会提示**测试结果已经写入result.csv**，越靠前，速度越快。

  <img src="/Users/liuhongdi/Library/Application Support/typora-user-images/image-20230817172049718.png" alt="image-20230817172049718" style="zoom:33%;" />

- 选择一个IP

## 2.配置

- 再终端中输入：

  ```
  cd /Applications/Cloudflare\ WARP.app/Contents/Resources
  ```

  

- 然后再输入

  ```
  sudo ./warp-cli set-custom-endpoint IP
  ```

  IP为刚刚选择的IP，如：

   sudo ./warp-cli set-custom-endpoint 162.159.192.137:4500





最后将Cloudflare WARP打开就可以使用了。

<img src="/Users/liuhongdi/Library/Application Support/typora-user-images/image-20230817172947149.png" alt="image-20230817172947149" style="zoom:33%;" />

