## Rails 路由学习
#### Rails 路由的作用
     - Rails 路由能识别URL,将其分发给控制器的动作进行处理，还能生成路径和URL,无需直接在试图中硬编码字符串
#### Rails的默认值：资源路径
     - index show new edit create update
#### resources :photos
#### resources 一次生成多个路由
#### resouce :geocoder 单次资源
#### 命名空间 app/controller/admin
     namespace :admin do
          resouces :articles, :comments
     end
     生成的路由
     GET    /admin/articles(.:format)          admin/articles#index
#### Scope
	 scope module: 'admin' do
  		resources :articles, :comments
	 end
	 GET    /articles(.:format)          admin/articles#index
##### 嵌套路由
	 嵌套路由不要超过一层
	 使用shallow: true做浅嵌套
	 resources :magazines do
    	resources :ads, shallow: true
  	 end
  	 
  	 //在成员路径前加上指定的前缀
  	 scope shallow_path: "sekret" do
  		resources :articles do
    		resources :comments, shallow: true
  		end
	 end
	 
	 //在方法前加上指定的前缀
	 scope shallow_prefix: "sekret" do
  		resources :articles do
    		resources :comments, shallow: true
  		end
	 end