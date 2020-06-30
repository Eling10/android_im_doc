# 好友管理 `ELContactManager`

管理好友的基本功能，比如添加、移除代理，添加、删除好友等。

非好友关系的双方是不能进行单聊的。


## API介绍





**获取好友列表**


```java

/**
 *  获取好友列表
 *
 *  @param GetFriendsCallBack 完成的回调
 */
   ELContactManager.getInstance().getFriends(new NetworkManagerListener.GetFriendsCallBack() {

            @Override
            public void onSucceed(FriendsResponse friendsResponse) {
               
            }

            @Override
            public void onfailure(Exception e) {
                loadError(e);
            }
        });
```
>注：好友数据都是从服务器上获取的，SDK 内部不会对好友数据做存储。



**查找联系人**


```java

/**
 *  搜索联系人
 *
 *  @param username 用户名
 *  @param SearchSriUsersCallBack 完成的回调
 */
   ELContactManager.getInstance().searchSriUsers(username, new NetworkManagerListener.SearchSriUsersCallBack() {
            @Override
            public void onSucceed(SearchContentResponse searchContentResponse) {
              
            }

            @Override
            public void onfailure(Exception e) {
                loadError(e);
            }

        });
```





**添加好友**


```java

/**
 *  添加好友
 *
 *  @param userId 用户ID
 *  @param etMsg 邀请信息
 */
  ELContactManager.getInstance().sendAddFriendSysMsg(userId,etMsg, new NetworkManagerListener.AddFriendBeanCallBack() {
            @Override
            public void onSucceed(GeneralResponse generalResponse) {
               
            }

            @Override
            public void onfailure(Exception e) {
                loadError(e);
            }
        });
```





**删除好友**

好友删除成功后，会删除与该好友之间的会话数据。

```java

/**
 *  删除好友
 *
 *  @param userId 用户ID
 */
 ELContactManager.getInstance().deleteFriend(userId, new NetworkManagerListener.DeleteFriendCallBack() {
                    @Override
                    public void onSucceed(GeneralResponse generalResponse) {
                    }

                    @Override
                    public void onfailure(Exception e) {

                    }
                });
```



**同意好友申请**


```java

/**
 *  同意好友申请
 *
 *  @param userId 用户ID
 */
ELContactManager.getInstance().acceptAddFriend(userId, new NetworkManagerListener.AcceptAddFriendCallBack() {
            @Override
            public void onSucceed(GeneralResponse generalResponse) {
   
            }

            @Override
            public void onfailure(Exception e) {

            }
        });
```


