# HEXO博客更改/美化

---

# 美化

- https://tzy1997.com/articles/hexo1606/
- https://guole.fun/posts/butterfly-custom/
- https://yisous.xyz/posts/895003b5/#%E6%98%BE%E7%A4%BA%E6%A0%87%E9%A2%98
- https://fontawesome.com/v4/icons/

# Valine添加评论功能或留言板

1. 注册LeanCloud

   https://console.leancloud.cn/login

   国内版需要国内手机号

   国际版只需要邮箱![image-20230119204016773](/Users/chenduo/Library/Application Support/typora-user-images/image-20230119204016773.png)

2. 注册完成后进入app控制面板->创建应用->创建开发版应用。

   ![image-20230119204322795](/Users/chenduo/Library/Application Support/typora-user-images/image-20230119204322795.png)

   

3. 创建后打开设置

   ![image-20230119204606177](/Users/chenduo/Library/Application Support/typora-user-images/image-20230119204606177.png)

4. 打开应用凭证

   ![image-20230119204825369](/Users/chenduo/Library/Application Support/typora-user-images/image-20230119204825369.png) 

   

   复制APPID 和APPKEY到主题YML中的配置文件位置（ex. _config.butterfly.yml）

   国际版leancloud 要将**REST API 服务器地址**复制到图中 *serverURLs* 位置即可

   ![image-20230119231713997](/Users/chenduo/Library/Application Support/typora-user-images/image-20230119231713997.png)

   (可选)接下来我们配置一下我们的leancloud。点击设置->安全中心->Web 安全域名，输入你的域名来保证其他人就算获取了你的appid也没办法操作你的数据库。

   ![image-20230119205422384](/Users/chenduo/Library/Application Support/typora-user-images/image-20230119205422384.png)

5. 重启hexo

   ```html
   hexo clean
   hexo g
   hexo s (预览)/ hexo d（上传）
   ```

   