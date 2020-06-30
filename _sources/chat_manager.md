# 消息管理 ELChatManager

管理所有与聊天相关的逻辑，包括单聊和群聊消息的查询、发送、更新、删除的功能。






## 消息 Message
**消息：**IM 交互的实体,目前的消息体的类型有：文本消息、图片消息、文件消息、语音消息、视频消息、音频通话、视频通话。

**构造文本消息**
```java
/**
 *  初始化消息实例
 *
 *  @param mSessionId 会话ID（接收方的ID）
 *  @param mSessionType 接收方类型 
 *  @param content 文本内容
 */
   TextMessage obtain = TextMessage.obtain(content, mSessionType, mSessionId);
```
**发送文本消息**

```java
/**
 *  发送文本消息
 *
 *  @param obtain 消息对象
 *  @param onAttached 本地添加消息成功
 *  @param success 发送消息成功
 *  @param failed 发送消息失败
 */
        ELChatManager.getInstance().sendTextMsg(obtain, new XHResultCallback.SendMessageCallback() {
    
            @Override
            public void onAttached(Message message) {
              
            }
    
            @Override
            public void success(Object o, Message message) {
    
            }
    
            @Override
            public void failed(String s, Message message) {
    
            }
        });
```


**构造图片消息**
```java
/**
 *  初始化消息实例
 *
 *  @param mSessionId 会话ID（接收方的ID）
 *  @param mSessionType 接收方类型
 *  @param imageFileSource  图片文件File对象
 */
   ImageMessage obtain = ImageMessage.obtain(mSessionType, mSessionId,  imageFileSource);
```
**发送图片消息**

```java
/**
 *  发送图片消息
 *
 *  @param obtain 消息对象
 *  @param mContext 上下文对象
 *  @param onProgress 文件上传进度
 *  @param onAttached 保存数据库成功
 *  @param success 发送消息成功
 *  @param failed 发送消息失败
 */
   ELChatManager.getInstance().sendImgMsg(mContext, obtain, new XHResultCallback.ISendMediaMessageCallback() {

            @Override
            public void onProgress(int progress, Message message) {
             
            }

            @Override
            public void onAttached(Message message) {
             
            }

            @Override
            public void success(Object o, Message message) {
               
            }

            @Override
            public void failed(String s, Message message) {
             
            }

        });
```




**构造语音消息**
```java
/**
 *  初始化消息实例
 *
 *  @param mSessionId 会话ID（接收方的ID）
 *  @param mSessionType 接收方类型
 *  @param duration 语音时长
 *  @param file  音频文件File对象
 */
   VoiceMessage obtain = VoiceMessage.obtain(mSessionType, mSessionId, duration, file);
```
**发送语音消息**

```java
/**
 *  发送语音消息
 *
 *  @param obtain 消息对象
 *  @param mContext 上下文对象
 *  @param onProgress 文件上传进度
 *  @param onAttached 保存数据库成功
 *  @param success 发送消息成功
 *  @param failed 发送消息失败
 */
  ELChatManager.getInstance().sendVoiceMsg(mContext, obtain, new XHResultCallback.ISendMediaMessageCallback() {
                @Override
                public void onProgress(int progress, Message message) {

                }

                @Override
                public void onAttached(Message message) {
                  
                }

                @Override
                public void success(Object o, Message message) {
                   
                }

                @Override
                public void failed(String s, Message message) {
                  
                }
            });
```





**构造视频消息**
```java
/**
 *  初始化消息实例
 *
 *  @param mSessionId 会话ID（接收方的ID）
 *  @param mSessionType 接收方类型
 *  @param file  视频频文件File对象
 */
    VideoMessage obtain = VideoMessage.obtain(mSessionType, mSessionId, file);
```
**发送视频消息**

```java
/**
 *  发送视频消息
 *
 *  @param obtain 消息对象
 *  @param mContext 上下文对象
 *  @param onProgress 文件上传进度
 *  @param onAttached 保存数据库成功
 *  @param success 发送消息成功
 *  @param failed 发送消息失败
 */
   ELChatManager.getInstance().sendVideoMsg(mContext, obtain, new XHResultCallback.ISendMediaMessageCallback() {
            @Override
            public void onProgress(int progress, Message message) {
                
            }

            @Override
            public void onAttached(Message message) {
              
            }

            @Override
            public void success(Object o, Message message) {
             
            }

            @Override
            public void failed(String s, Message message) {
            
            }

        });

```



**获取历史消息**
```java
/**
 *  获取指定会话的消息，如果数据库中不存在，则从服务器中取，按时间顺序 升序 排列（服务器中的数据会同步到本地数据库）
 *
 *  @param conversationId 会话ID
 *  @param page 第几页（从 1 开始）
 *  @param size 每页显示的条数
 */
  ELChatManager.getInstance().getMessageList(conversationId, page, size, new NetworkManagerListener.GetMessageListCallBack() {
            @Override
            public void onSucceed(List<Message> messages) {
                
            }

            @Override
            public void onfailure(Exception e) {
                
            }
        });
```



**删除单条消息**

```java
/**
 *  获取指定会话的消息，如果数据库中不存在，则从服务器中取，按时间顺序 升序 排列（服务器中的数据会同步到本地数据库）
 *
 *  @param messageId 消息ID
 */
               ELChatManager.getInstance().deleteMsg(messageId, new NetworkManagerListener.DeleteMsgCallBack() {
                                @Override
                                public void onSucceed(GeneralResponse generalResponse) {
                                    
                                }

                                @Override
                                public void onfailure(Exception e) {

                                }
                            });
```



**获取会话列表**

```java
/**
 *  获取当前用户的所有会话数据，会按照最新的那一条消息进行 降序 排列
 *
 *  @param messageId 消息ID
 */
 
 List<Conversation> list = ELChatManager.getInstance().getConversations();
```




**删除会话**

```java
/**
 *  当会话被删除后，它底下的所有消息数据都会被删除。
 *
 *  @param messageId 消息ID
 */
 
   ELChatManager.getInstance().deleteConversation(item.getConversationId());
```