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


