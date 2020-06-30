# 用户管理 ELUserManager

管理当前登录用户相关的信息

## API介绍

**获取当前登录用户**

```java

    LoginResponse.DataBean.UserInfoBean userInfoBean = ELUserManager.getInstance().getUserInfoBean();

```

**获取指定用户信息**

此方法是用来获取指定用户的信息

```java
/**
 *  获取用户信息
 *
 *  @param userId 用户ID
 *  @param GetDetailCallBack 回调
 */
   ELUserManager.getInstance(). getUserInformation(userId, new NetworkManagerListener.GetDetailCallBack() {
            @Override
            public void onSucceed(UserDetailResponse userDetail) {

            }

            @Override
            public void onfailure(Exception e) {

            }
        });


```


**修改当前用户信息**


```java
/**
 *  修改用户信息
 
 *  @param avatar 头像地址
 *  @param nickName 昵称
 *  @param UpdateUserInformationWithAvatar 回调
 */
        ELUserManager.getInstance().updateUserInformationWithAvatar(avatar, nickName, new NetworkManagerListener.UpdateUserInformationWithAvatar() {
            @Override
            public void onSucceed(GeneralResponse generalResponse) {
                
            }

            @Override
            public void onfailure(Exception e) {

            }
        });
```

**发送邮箱验证码**


```java
/**
 *  发送邮箱验证码
 *
 *  @param email 邮箱
 *  @param type 验证码类型  4  IM修改密码  6  绑定邮箱
 *  @param VerificationCodeCallBack 回调
 */
               ELUserManager.getInstance().sendCodeToEmail(email, type, new NetworkManagerListener.VerificationCodeCallBack() {
            @Override
            public void onSucceed(GeneralResponse generalResponse) {

            }

            @Override
            public void onfailure(Exception e) {

            }
        });



```
>注：绑定邮箱 或者 修改密码 时，需要先调用此API来获取对应的验证码。



**绑定邮箱**


```java
/**
 *  绑定邮箱
 *
 *  @param email 邮箱地址
 *  @param code 邮箱验证码
 *  @param BindEmailCallBack 回调
 */
       ELUserManager.getInstance().bindEmail(email, code, new NetworkManagerListener.BindEmailCallBack() {
            @Override
            public void onSucceed(GeneralResponse generalResponse) {
                
            }

            @Override
            public void onfailure(Exception e) {

            }
        });


```


**修改密码**


```java
/**
 *  修改密码
 *
 *  @param newPassword 新密码（6~18位，字母+数字组合）
 *  @param account 账号
 *  @param code 邮箱验证码
 *  @param ChangePswCallBack 回调
 */
        ELUserManager.getInstance().changePsw(newPassword, account, code, new NetworkManagerListener.ChangePswCallBack() {
            @Override
            public void onSucceed(GeneralResponse generalResponse) {

            }

            @Override
            public void onfailure(Exception e) {

            }
        });



```