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

   ### valine 头像配置
   
   目前`非自定义头像`有以下 7 种`默认值`可选:
   
   | 参数值       | 表现形式                                                     | 备注                             |
   | :----------- | :----------------------------------------------------------- | :------------------------------- |
   | 空字符串`''` | ![img](https://img-blog.csdnimg.cn/20200207232029388.jpg#alt=Gravatar%E5%AE%98%E6%96%B9%E5%9B%BE%E5%BD%A2) | Gravatar 官方图形                |
   | `mp`         | ![img](https://img-blog.csdnimg.cn/20200207231815493.png#alt=%E7%A5%9E%E7%A7%98%E4%BA%BA%28%E4%B8%80%E4%B8%AA%E7%81%B0%E7%99%BD%E5%A4%B4%E5%83%8F%29) | 神秘人(一个灰白头像)             |
   | `identicon`  | ![img](https://img-blog.csdnimg.cn/20200207231835995.png#alt=%E6%8A%BD%E8%B1%A1%E5%87%A0%E4%BD%95%E5%9B%BE%E5%BD%A2) | 抽象几何图形                     |
   | `monsterid`  | ![img](https://img-blog.csdnimg.cn/20200207231850268.png#alt=%E5%B0%8F%E6%80%AA%E7%89%A9) | 小怪物                           |
   | `wavatar`    | ![img](https://img-blog.csdnimg.cn/20200207231902977.png#alt=%E7%94%A8%E4%B8%8D%E5%90%8C%E9%9D%A2%E5%AD%94%E5%92%8C%E8%83%8C%E6%99%AF%E7%BB%84%E5%90%88%E7%94%9F%E6%88%90%E7%9A%84%E5%A4%B4%E5%83%8F) | 用不同面孔和背景组合生成的头像   |
   | `retro`      | ![img](https://img-blog.csdnimg.cn/20200207231915298.png#alt=%E5%85%AB%E4%BD%8D%E5%83%8F%E7%B4%A0%E5%A4%8D%E5%8F%A4%E5%A4%B4%E5%83%8F) | 八位像素复古头像                 |
   | `robohash`   | ![img](https://img-blog.csdnimg.cn/20200207231932699.png#alt=%E4%B8%80%E7%A7%8D%E5%85%B7%E6%9C%89%E4%B8%8D%E5%90%8C%E9%A2%9C%E8%89%B2%E3%80%81%E9%9D%A2%E9%83%A8%E7%AD%89%E7%9A%84%E6%9C%BA%E5%99%A8%E4%BA%BA) | 一种具有不同颜色、面部等的机器人 |
   | `hide`       |                                                              | 不显示头像                       |