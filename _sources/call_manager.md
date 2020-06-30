# 实时音视频 ELCallManager



目前只支持1对1音视频通话，包括语音通话和视频通话。




## 通话配置 ELCallOptions

| 属性 | 类型 | 描述 |
| :-----| :----- | :----- |
|openGLEnable |	boolean |	是否使用 openGL 渲染，默认 true |
|hwEncodeEnable |	boolean |	是否使用硬编码，默认 false |
|dynamicBitrateAndFPSEnable |	boolean |	是否动态调节帧率码率，默认 false |
|bigVideoBitrate|int |	大图码率，默认 500|
|bigVideoFPS |	int | 大图帧率，默认 15 |
|smallVideoBitrate |	int |	小图码率，默认 100 |
|smallVideoFPS |	int |	小图帧率，默认 15 |
|resolution |	ELCallVideoResolution |	视频分辨率，默认 ELCallVideoResolution_360BW_640BH_180SW_320SH |
|videoCodecType |	ELCallVideoCodecType |	视频编码格式，默认 ELCallVideoCodecTypeH264 |
|audioCodecType |	ELCallAudioCodecType |音频编码格式配置，默认 ELCallAudioCodecTypeAAC|







## API介绍

**主叫方：**  通话发起方。

**被叫方：**  通话接收方





**发起语音通话：** 

```java
/**
 *  发起语音通话
 *
 *  @param sessionId 接收人ID
 *  @param AudioCallCallback 回调
 */
        ELCallManager.getInstance().audioCall(sessionId, new VoipManagerCallback.AudioCallCallback() {
                @Override
                public void success(Object mSessionId) {

                }

                @Override
                public void failed(String s) {
                   
                }
            });


```







**发起视频通话：** 

```java
/**
 *  发起视频通话
 *
 *  @param sessionId 接收人ID
 *  @param targetPlayer 显示本地摄像头图像
 *  @param VideoCallCallback 回调
 */
          ELCallManager.getInstance().videoCall(sessionId, targetPlayer, new VoipManagerCallback.VideoCallCallback() {
                @Override
                public void success(Object mSessionId) {

                }

                @Override
                public void failed(String s) {
                    stopAndFinish();
                }
            });


```









**取消呼叫（主叫方调用）：** 

```java
/**
 *  取消呼叫
 *
 *  @param HangupCallCallback 回调
 */
   ELCallManager.getInstance().cancel(new VoipManagerCallback.HangupCallCallback() {
                    @Override
                    public void success(Object mSessionId) {
                        
                    }

                    @Override
                    public void failed(String s) {
                        
                    }


```










**挂断语音通话 / 视频通话：** 

```java
/**
 *  挂断语音通话 / 视频通话
 *
 *  @param HangupCallCallback 回调
 */
         ELCallManager.getInstance().hangup(new VoipManagerCallback.HangupCallCallback() {
                    @Override
                    public void success(Object mSessionId) {
                        stopAndFinish();
                    }

                    @Override
                    public void failed(String s) {
                        stopAndFinish();
                    }
                });


```









**设置显示双方画面：** 

```java
/**
 *  设置显示双方画面的Player，不需要显示视频时可以传null
 *  @param selfPlayer 远程画面
 *  @param targetPlayer 本地相机画面
 *  @param SetupViewCallback 回调
 */
      ELCallManager.getInstance().setupView(selfPlayer, targetPlayer, new VoipManagerCallback.SetupViewCallback() {
            @Override
            public void success(Object mSessionId) {

            }

            @Override
            public void failed(String s) {
              
            }
        });


```




**关闭本地画面：** 

```java
/**
 *  关闭本地画面
 */
      ELCallManager.getInstance().stopPerview();


```







**接听语音通话 / 视频通话：** 

```java
/**
 *  接听语音通话 / 视频通话
 *  
 *  @param sessionId 接收人ID
 *  @param AcceptCallCallback 回调
 */
        ELCallManager.getInstance().accept(sessionId, new VoipManagerCallback.AcceptCallCallback() {
            @Override
            public void success(Object mSessionId) {

            }

            @Override
            public void failed(String s) {
                stopAndFinish();
            }
        });


```









**拒绝接听（被叫方调用）：** 

```java
/**
 *  拒绝接听（被叫方调用）
 *  
 *  @param RefuseCallback 回调
 */
       ELCallManager.getInstance().refuse(new VoipManagerCallback.RefuseCallback() {
                    @Override
                    public void success(Object mSessionId) {
                        finish();
                    }

                    @Override
                    public void failed(String s) {
                        finish();
                    }
                });


```









**切换摄像头方向：** 

```java
/**
 *  切换摄像头方向
 *  
 *  @param RefuseCallback 回调
 */
       ELCallManager.getInstance().switchCamera();


```

**动态开关视频：** 

```java
/**
 *  动态开关视频
 *  @param isEnable true 开 false 关
 */
       ELCallManager.getInstance().setVideoEnable(isEnable);


```

**动态开关音频：** 

```java
/**
 *  动态开关音频
 *  @param isEnable true 开 false 关
 */
       ELCallManager.getInstance().setVideoEsetAudioEnablenable(isEnable);


```

**设置扬声器：** 

```java
/**
 *  设置扬声器
 *  @param isEnable true 开 false 关
 */
       ELCallManager.getInstance().setSpeakerphoneOn(isEnable);


```


**打开音频管理器：** 

```java
/**
 *  打开音频管理器
 */
       ELCallManager.getInstance().startAudio();


```

**关闭音频管理器：** 

```java
/**
 *  关闭音频管理器
 */
       ELCallManager.getInstance().stopAudio();


```









**通话状态监听：** 

```java
/**
 *  通话状态监听
 */
        ELCallManager.getInstance().setDispatchEvent(new DispatchEvent() {
            @Override
            public void dispatchEvent(String aEventID, boolean success, Object eventObj) {
                switch (aEventID){
                    case AEvent.AEVENT_VOIP_REV_BUSY:
                        MLOC.d("","对方线路忙");
                     
                        break;
                    case AEvent.AEVENT_VOIP_REV_REFUSED:
                        MLOC.d("","对方拒绝通话");
                      
                        break;
                    case AEvent.AEVENT_VOIP_REV_HANGUP:
                        MLOC.d("","对方已挂断");
                       
                        break;
                    case AEvent.AEVENT_VOIP_REV_CONNECT:
                        MLOC.d("","对方允许通话");
                      
                        break;
                    case AEvent.AEVENT_VOIP_REV_ERROR:
                     	MLOC.d("","连接异常");
                        break;
                }
            }
        });;


```