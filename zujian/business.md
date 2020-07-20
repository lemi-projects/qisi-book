 # 业务组件 business
 
 ## Team 组织
 * #### TeamList 组织列表 
 * #### TeamPublish 组织发布


 ## Comment 评论
  * ### 评论条
    > 评论发布公告模块，如参考图：
    
    ![社区公告](http://ckfhq.oss-cn-beijing.aliyuncs.com/images/ulinli/doc/pingluntiao.png)
    
    * #### CommentAdd 评论提交 
    * #### Zan 点赞
    * #### Cang 收藏
    * #### Share 分享
  * ### 查看评论
    ```
    请求参数：
     评论范围 scope
       - topic 话题
       - event 活动
     范围ID scope_id
    
    返回参数：
      - user_id 用户ID
      - topic_id 评论id
      - content 内容
      - is_show 显示状态
      - create_time 评论时间
      
   
    ```

     
 ## Notice 公告
 * ### NoticeAdd 发布公告
   > 社区发布公告信息模块
   ```
    请求参数：
      发布范围 scope
        - st 街道 street     street_id
        - cy 社区 community  community_id
        - aa 小区 area       area_id
      范围ID  scope_id
      公告分类 category
        - xx
        - yy
      标题 title
      内容 content
    
    返回参数：
       成功 success
       失败 fail

   ```
  
 * ### NoticeDetail 公告详情
    > 社区公告信息详情查看模块
    
  
 * #### NoticeList 公告列表
   > 社区发布公告信息模块，如参考图：
         
   ![社区公告](http://ckfhq.oss-cn-beijing.aliyuncs.com/images/ulinli/doc/shequgonggao_list.png)
 
   ```
      请求参数：
        小区ID  area_id
      
      返回参数：
        公告类型 notice_class
            - 文化中心公告 whzx
            - 物业公告 wy
        公告标题 notice_title
            - 长度16个字符
      
   ```
 
 ## Discuss 话题
 * DiscussList 话题列表
 * DiscussHot 热门话题
 * DiscussClass 分类话题
 * DiscussPublish 议事发布
 
 ## Activity 活动
 * ActivityList 活动列表
 * ActivityHot 热门活动
 * ActivityMore 报名最多
 * ActivityNear 离我最近 
 
 ## Message 信箱
 * MessagePublish 发布表单
 * MessageList 反馈列表

 ## Area 场地
 * AreaPublish 发布场地
 * AreaList 场地列表
 

