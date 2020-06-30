# 群管理 ELGroupManager

## API介绍




**获取群列表**


```java

/**
 *  获取用户已加入的群组
 *
 *  @param GetMyGroupCallBack 完成的回调
 */
  ELGroupManager.getInstance().getMyGroup(new NetworkManagerListener.GetMyGroupCallBack() {

            @Override
            public void onSucceed(GetMyGroupResponse getMyGroupResponse) {
            }

            @Override
            public void onfailure(Exception e) {

            }
        });
```





**查询群详情**


```java

/**
 *  获取群组详情信息
 *
 *  @param groupId 群组ID
 *  @param GetGroupInfoCallBack 完成的回调
 */
   ELGroupManager.getInstance().getGroupInfo(groupId, new NetworkManagerListener.GetGroupInfoCallBack() {

                @Override
                public void onSucceed(GroupInfoResponpse GroupInfoResponpse) {
                   
                }

                @Override
                public void onfailure(Exception e) {

                }
            });
```





**创建群组**


```java

/**
 *  创建群组
 *
 *  @param groupName 群组名称（最多20位字符长度）
 *  @param CreateGroupCallback 完成的回调
 */
         ELGroupManager.getInstance().createGroup(groupName, new XHGroupManagerCallback.CreateGroupCallback() {
            @Override
            public void success(Object mGroupId) {
             
            }

            @Override
            public void failed(String s) {
               
            }
        });
```
>注：群名称的字符长度 SDK 内部做了限制，必须在 20 个字符以内（包括 20 个字符）。





**退出群组**


```java
/**
 *  退出群组（数据库中与本群相关的会话数据会被清除）
 *
 *  @param groupId         群组ID
 *  @param DeleteUserFormGroupCallback 完成的回调
 */
          ELGroupManager.getInstance().deleteUserFormGroup(groupId, userId, new XHGroupManagerCallback.DeleteUserFormGroupCallback() {
                        @Override
                        public void success(Object o) {

                        }

                        @Override
                        public void failed(String s) {
   
                        }
                    });
```
>注：只有群成员可以退群，群主不能退群，只能解散群。操作成功后，SDK 内部会删除与本群相关的会话数据。






**解散群组**


```java
/**
 *  解散群组（数据库中与本群相关的会话数据会被清除）
 *
 *  @param groupId 群组ID
 *  @param DeleteGroupCallback 完成的回调
 */
   ELGroupManager.getInstance().deleteGroup(groupId, new XHGroupManagerCallback.DeleteGroupCallback() {
                        @Override
                        public void success(Object o) {
                          
                        }

                        @Override
                        public void failed(String s) {
                         
                        }
                    });
```
>注：只能群主有权限解散群。群被解散后，群内的所有成员（群主除外）都会收到通知，同时 SDK 内部会删除与本群相关的会话数据。






**添加群成员**


```java
/**
 *  添加群组成员
 *
 *  @param selectedIds 被邀请的用户名列表
 *  @param groupId 群组ID
 *  @param AddUserToGroupCallback 完成的回调
 */
        ELGroupManager.getInstance().addUserToGroup(groupId, selectedIds, new XHGroupManagerCallback.AddUserToGroupCallback() {
            @Override
            public void success(Object o) {
                
            }

            @Override
            public void failed(String s) {
               
            }
        });
```






**删除群成员**


```java
/**
 *  将群成员移出群组
 *
 *  @param selectedIds 要移出群组的用户列表
 *  @param groupId 群组ID
 *  @param DeleteUserFormGroupCallback 完成的回调
 */
      ELGroupManager.getInstance().deleteUserFormGroup(groupId, selectedIds, new XHGroupManagerCallback.DeleteUserFormGroupCallback() {
            @Override
            public void success(Object o) {
              
            }

            @Override
            public void failed(String s) {
              
            }
        });
```
>注：只有群主有权限删除群成员，且群主不能删除自己。







**删除群成员**


```java
/**
 *  修改群信息（群名称、头像），传空则表示不修改此项
 *
 *  @param groupId 群组ID
 *  @param groupName 群名称
 *  @param groupAvatar 群头像
 *  @param EditGroupInfoCallBack 完成的回调
 *
        ELGroupManager.getInstance().editGroupInfo(groupId, groupName, groupAvatar, new NetworkManagerListener.EditGroupInfoCallBack() {
            @Override
            public void onSucceed(GeneralResponse generalResponse) {

            }

            @Override
            public void onfailure(Exception e) {

            }
        });
```
>注：只有群主有权限修改群信息。
