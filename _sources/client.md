# 客户端 ELClient

## 1.1 初始化

```java
    ELClient.getInstance().init(getContext(),"您应用的AppId", "您应用的AppSecret");

```


## 1.2 配置类
 **ELOSSOptions**

阿里云OSS配置类，消息中的附件（音频、视频、图片等）是存储在阿里云OSS服务器上的。

| **属性**             | **类型** | **描述**                                      |
| :------------------- | :------- | :-------------------------------------------- |
| `bucketName`          | `String` | 默认：`szeling-master`                        |
| `endPoint`           | `String` | 默认：`http://oss-cn-shenzhen.aliyuncs.com/`  |
| `directoryName`      | `String` | 服务器上存储文件的一级目录名，默认：`ElingIm` |
| `fileDirectoryName`  | `String` | 文件目录名（二级目录），默认：`file`          |
| `imageDirectoryName` | `String` | 图片目录名（二级目录），默认：`images`        |
| `voiceDirectoryName` | `String` | 语音目录名（二级目录），默认：`voice`         |
| `videoDirectoryName` | `String` | 视频目录名（二级目录），默认：`video`         |

## 1.3 广播回调

```java
      ELClient.getInstance().setDispatchEvent(new DispatchEvent() {
            @Override
            public void dispatchEvent(String aEventID, boolean success, Object eventObj) {
                switch (aEventID) {
                    case AEvent.AEVENT_VOIP_REV_CALLING:
						//收到视频通话请求
                        break;
                    case AEvent.AEVENT_VOIP_REV_CALLING_AUDIO: {
                        //收到音频通话请求 
                    }
                    break;
                    case AEvent.AEVENT_C2C_REV_MSG:
                        //收到个人消息
                        if (eventObj instanceof Conversation) {
                            //会话消息
                        }
                        if (eventObj instanceof Message) {
                            //聊天消息
                        }
                        break;
                    case AEvent.AEVENT_REV_SYSTEM_MSG:
                        //接收到系统消息
                        if (eventObj instanceof SystemMessages) {
                            SystemMessages systemMessages = (SystemMessages) eventObj;
							//对方发来好友邀请
                            if (ADD_FRIEND_SYS_MSG.equals(systemMessages.getType())) {
                                
                            }
                            //接收删除好友消息
                            if (DEL_FRIEND_SYS_MSG.equals(systemMessages.getType())) {
                               
                            }
                            //对方同意好友请求
                            if (ACCEPTE_FRIEND_SYS_MSG.equals(systemMessages.getType())) {
                              
                            }
                            //群主解散广播给所有群成员
                            if (DISBANDED_GROUP_SYS_MSG.equals(systemMessages.getType())) {
                              
                            }
                            //群主解散广播给所有群成员
                            if (REMOVE_GROUP_MEMBER_SYS_MSG.equals(systemMessages.getType())) {
                               
                            }
                        }
                        break;
                    case AEvent.AEVENT_LOGOUT:

                        break;
                    case AEvent.AEVENT_USER_KICKED:
                       //在其他地方登陆

                        break;
                    case AEvent.AEVENT_CONN_DEATH:
					 //连接异常
                   
                        break;
                    case AEvent.AEVENT_USER_OFFLINE:
					 //用户下线
                      
                        break;
                    case AEvent.AEVENT_USER_ONLINE:
					 //用户已上线
                     
                        break;
                }
            }
        });

```