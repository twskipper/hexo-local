delete index.jade
删除使用多说后，在index页面显示评论数
if theme.duoshuo
       a.ds-thread-count(data-thread-key=post.path, href=url_for(post.path) + '#comments')
