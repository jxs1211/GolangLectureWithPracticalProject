
# 本次课程是给哪些想要了解企业中真实开发工作流的人准备的

## 你可从本课程获得： 
- 如何从零构建一个高效的开发环境，更容易的学习语言的基础知识
  ```go
  func main() {
    variable()
    structs()
    pointer()
    constants()
    functions()
    arrays()
    slices()
    maps()
    methods()
    interfaces()
    embedding()
    exporting()
  }
  ```

- 使用企业中开发工作流真实用到的开发工具和技术栈帮助你构建应用
  - ![Git](https://git-scm.com/images/logos/2color-lightbg@2x.png)
  - ![Docker](https://lh3.googleusercontent.com/bip/APOwr80jUFXwCb1f7mLFr2epoQfM3gInpjgoEP-exK66Tz3l1L_UPPg1-yrCgecQZghf5kkO23eATm40RRKtlMwsSYUEtnOsxiQOMgPKt9ofNOpYfH4-tlceNUENmLfXEbrRGwy9fKtaMxK3HhMCzWgn9_UPSKf47w=w250-h200-p)
  - ![Compose](https://iescelia.org/ciberseguridad/wp-content/uploads/2021/02/docker-compose-logo.png)
  - ![Go](https://upload.wikimedia.org/wikipedia/commons/thumb/0/05/Go_Logo_Blue.svg/512px-Go_Logo_Blue.svg.png)
  - ![Gin](https://th.bing.com/th/id/R.3fc54a72f46b217517be25ea04cabc10?rik=CKyJyazfHPMWdg&pid=ImgRaw&r=0)
  - ![DBeaver](https://upload.wikimedia.org/wikipedia/commons/thumb/b/b5/DBeaver_logo.svg/256px-DBeaver_logo.svg.png?20210313151619)
- 为每次课程提供Q&A环节，解决你实际动手中遇到的问题
- 使用流行的开源工具帮助你记录开发过程中遇到的所有问题，便于溯源和巩固学习的知识

  [bug-tracker](https://github.com/jxs1211/GolangLectureWithPracticalProject/issues/1)
- 学习最差的可以获得一对一和群友的帮助，在你入门编程的道路上扶你一把。
- 复购系列课程或老带新的可以获得讲师一对一VIP咨询，内容包括但不限于课程相关咨询，工作经验分享，个人职业发展建议，更有可能获得全球内推机会

## 虽然你可能认为自己对编程一窍不通，但是你可能具备一些成为程序员的基本素质：

- 韧性
- 努力
- 善于总结和回顾
- 做笔记
- 乐于助人
- 乐观

### Season 1


#### Basic knowledge of the language
- Install Golang and IDE(windows WSL and mac)
- 安装Golang和IDE
- 语言基础
  - Variables
  - Struct
  - Pointers
  - Constants
- 语言基础2
  - Functions
  - Arrays
  - Slices
  - Maps
- 语言基础3 
  - Methods
  - Interfaces
  - Embedding
  - Exporting


#### 正式开始写代码前，你需要知道的： 
- 安装Git和Go
- 如何使用github创建你自己的项目，并管理你的代码仓库
- 使用github issues跟踪你的bug
- 使用docker创建一个数据库和可视化工具
- 使用Makefile管理你的项目

#### 开始编码：CRUD
- 设计数据库业务模型，使用dbdiagram生成SQL代码
  https://dbdiagram.io/d/64d708c302bd1c4a5ea8e59b
- 如何在Golang中编写和运行数据库迁移脚本
- 从SQL生成Golang CRUD代码 
- 编写单元测试

#### 开始编码：REST API
- 使用Gin实现RESTful HTTP API
- 使用Viper管理应用的配置文件和环境变量
- 通过事务实现数据库转账功能
- 实现转账功能
- 自定义校验

### Season 2


#### Start coding CRUD 2

- Write utils package for your project
  - use package for organizing your code
  - implement function for util package
- Write UT for CRUD using local package


#### Start coding REST API 2

- Implement transfer money API with a custom params validator


#### Ship the application
- Build a minimal Golang Docker image with a multistage Dockerfile
- How to use docker network to connect 2 stand-alone containers
- How to write docker-compose file to compose your app and DB and control service start-up orders using service_healthy condition


#### Deploy the application to production


### Season 3


#### Start coding CRUD 2


#### Start coding REST API 2


#### Season 4 - tool chain: tproxy

#### Season 5 - Specific field: znix

#### Season 6 operator

#### Season 7 DevOps

