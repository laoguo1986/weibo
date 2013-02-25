#创建程序

rails new weibo --skip-test-unit

cd weibo

bundle install --without production

rails 使用rspec: rails generate rspec:install

##初始化git仓库

git init

git add .

git commit -m "Initial commit"

##修改readme为markdown

git mv README.rdoc README.md

git commit -a -m "Improve the README"

##推送到github

###Create a new repository on the command line

touch README.md

git init

git add README.md

git commit -m "first commit"

git remote add origin https://github.com/laoguo1986/weibo.git

git push -u origin master

### Push an existing repository from the command line

git remote add origin https://github.com/laoguo1986/weibo.git

git push -u origin master

##部署到heroku

heroku create --stack cedar

git push heroku master

git push

git push heroku

#添加静态页面

##创建git分支

使用 Git 时，在一个有别于主分支的独立从分支中工作是一个好习惯。如果你使用 Git 做版本控制，可以执行下面的命令：

git checkout -b static-pages

##生成rspec测试用例

```sh
$ rails generate rspec:install
```
##创建控制器

rails generate controller StaticPages home help about contact --no-test-framework

`--no-test-framework` 选项禁止生成 RSpec 测试代码,手动生成

###撤销操作

<p>在 Rails 中，我们可以通过 <code>rails destroy</code> 命令完成这些操作。一般来说，下面的两个命令是相互抵消的：</p>
  <pre>
    $ rails generate controller FooBars baz quux
    $ rails destroy  controller FooBars baz quux
  </pre>
  <pre>
    $ rails generate model Foo bar:string baz:integer
  </pre>
  <p>生成的模型可通过下面的命令撤销：</p>
  <pre>
    $ rails destroy model Foo
  </pre>
  
  <pre>
    $ rake db:migrate
    $ rake db:rollback
  </pre>
  <p>如果要回到最开始的状态，可以使用：</p>
  <pre>
    $ rake db:migrate VERSION=0
  </pre>
  <p>将数字 <tt>0</tt> 换成其他的数字就会回到相应的版本状态，这些版本数字是按照迁移顺序排序的。</p>

##加入仓库

git add .

git commit -m "Add a StaticPages controller"

##测试驱动开发

###生成集成测试（request spec)

rails generate integration_test static_pages

###编辑测试代码

spec/requests/static_pages_spec.rb

#页面美化
##添加页面函数，简化页面代码


pp/helpers/application_helper.rb


module ApplicationHelper
  def full_title(page_title)
    base_title = "北京计量院专家信息系统"
		    if page_title.empty?
				      base_title
				else
		       "#{base_title} | #{page_title}"
			  end
     end
  end

##Bootstrap 和自定义的 CSS

###添加gem
	gem 'bootstrap-sass', '2.0.4'

	bundle install

###自定义css

创建全站使用的css

app/assets/stylesheets/custom.css.scss

静态文件可以存放在三个标准的目录中，各有各的用途：
1. app/assets：存放当前应用程序用到的资源文件
2. lib/assets：存放开发团队自己开发的代码库用到的资源文件
3. vendor/assets：存放第三方代码库用到的资源文件

###render 复用
#路由

root to: 'static_pages#home'

match '/help',    to: 'static_pages#help'
match '/about',   to: 'static_pages#about'
match '/contact', to: 'static_pages#contact''#''''#''''#''''#'

#用户注册
##user 控制器

rails generate controller Users new --no-test-framework

##注册页面的URL地址
match '/signup',  to: 'users#new'
###集成测试
我们希望“注册”页面的地址是 /signup,编写集成测试

rails generate integration_test user_pages

生成：spec/requests/user_pages_spec.rb

##用户模型

git checkout master

 git checkout -b modeling-users

 rails generate model User name:string email:string

###模型注释
 使用 annotate 注解一下 Rails 模型:gem 'annotate', '˜> 2.4.1.beta'

bundle exec annotate --position before

###创建用户对象

进入控制台沙盒模式

rails console --sandbox

### 验证 name 和 email 属性的存在性:

 validates :name, presence: true

 validates :email, presence: true

 validates :name, presence: true, length: { maximum: 50 }

validates :name,  presence: true, length: { maximum: 50 }

VALID_EMAIL_REGEX = /\A[\w+\-.]+@[a-z\d\-.]+\.[a-z]+\z/i

validates :email, presence: true, format: { with: VALID_EMAIL_REGEX },

uniqueness: { case_sensitive: false }

在数据库层加上唯一性限制，为email列建立索引，然后为索引加上唯一性限制

rails generate migration add_index_to_users_email

##加上安全密码
###加密密码

向user表中加入password_digest列，digest是加密哈希函数中的一个术语。

使用bcrypt对密码进行不可逆的加密，gemfile加入

gem 'bcrypt-ruby', '3.0.1'

生成迁移文件，添加password_digest 列

rails generate migration add_password_digest_to_users password_digest:string

rake db:migrate

###密码和密码确认

要把 password 和 password_confirmation 属性设为可访问的,才能在初始化参数中创建用户对象，把两个属性对应的symbol加到可访问的属性列表中
