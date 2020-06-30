# 客户端 ELLoginManager

登录管理类，负责IM用户的注册、登录、登出以及监听登录状态相关的逻辑。

## API介绍

**用户注册**


```java

/**
 *  用户注册
 *
 *  @param username 用户名
 *  @param password 密码（6~18位，字母+数字组合）
 *  @param RegisterCallBack 完成的回调
 */
        ELLoginManager.getInstance().register(phone, pwd, new NetworkManagerListener.RegisterCallBack() {

            @Override
            public void onSucceed(GeneralResponse generalResponse) {
               if (generalResponse.getCode() == 200) {
                    UIUtils.showToast("注册成功");
                } 
            }

            @Override
            public void onfailure(Exception e) {
                loadError(e);
            }
        });

```



**登录IM服务器**

登录成功后，用户信息会被缓存在本地，可以通过 ELUserManager 类来获取当前登录的用户信息。

```java

/**
 *  用户登录
 *
 *  @param username 用户名
 *  @param password 密码（6~18位，字母+数字组合）
 *  @param LoginCallBack 完成的回调
 */
 ELLoginManager.getInstance().login(username, password, new NetworkManagerListener.LoginCallBack() {
            @Override
            public void onSucceed(LoginResponse loginResponse) {
                if (generalResponse.getCode() == 200) {
                    UIUtils.showToast("登录成功");
                } 
            }

            @Override
            public void onfailure(int errerCode, Exception e) {
                loadError(e);
            }

        });

```

**登出**

退出登录后，SDK 会清空缓存在本地的用户数据。

```java

/**
 *  登出
 *
 *  @param LoginOutCallBack 完成的回调
 */
  ELLoginManager.getInstance().loginOut(new NetworkManagerListener.LoginOutCallBack() {
                    @Override
                    public void onSucceed(GeneralResponse generalResponse) {
                       if (generalResponse.getCode() == 200) {
                    		UIUtils.showToast("登出成功");
               		    } 
                    }

                    @Override
                    public void onfailure(Exception e) {

                    }
                });
            }

```