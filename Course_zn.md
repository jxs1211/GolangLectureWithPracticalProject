## 本次课程是给哪些想要了解企业中真实开发工作流的人准备的

### Season 1

#### Basic knowledge
- Install Golang and IDE(windows wsl and mac)
  - install vscode
  - open powershell and run `wsl --install`
    ```
    PS D:\> wsl --install -d Ubuntu-20.04
    Ubuntu 20.04 LTS is already installed.
    Launching Ubuntu 20.04 LTS...

    ```
  - install code
    ```
    Installing, this may take a few minutes...
    Please create a default UNIX user account. The username does not need to match your Windows username.
    For more information visit: https://aka.ms/wslusers
    Enter new UNIX username: root
    adduser: The user `root' already exists.
    Enter new UNIX username: going
    New password:
    Retype new password:
    passwd: password updated successfully
    Installation successful!
    To run a command as administrator (user "root"), use "sudo <command>".
    See "man sudo_root" for details.

    ```
  - install code for open project in wsl with vscode ??
    ```
    Welcome to Ubuntu 20.04.6 LTS (GNU/Linux 5.10.16.3-microsoft-standard-WSL2 x86_64)
    sudo -i
    going@CTU-WKS-AA578:~$ mkdir workspace
    going@CTU-WKS-AA578:~$ cd workspace/
    going@CTU-WKS-AA578:~/workspace$ code .
    Installing VS Code Server for x64 (660393deaaa6d1996740ff4880f1bad43768c814)
    Downloading: 100%
    Unpacking: 100%
    Unpacked 1781 files and folders to /home/going/.vscode-server/bin/660393deaaa6d1996740ff4880f1bad43768c814.
    going@CTU-WKS-AA578:~/workspace$
    ```
  - install golang and go plugin in vscode
    ```
    # open powershell and enter wsl
    PS D:\> wsl
    going@CTU-WKS-AA578:/mnt/d$ sudo -i
    # install golang: https://go.dev/dl/go1.20.6.linux-amd64.tar.gz
    $ wget https://go.dev/dl/go1.20.6.linux-amd64.tar.gz -O /tmp/go1.20.6.linux-amd64.tar.gz
    # if you can't download the zip file, you can download it directly on golang offical site and mv it to /tmp
    $ cp /mnt/c/Users/xjshen/Downloads/go1.20.6.linux-amd64.tar.gz ./
    $ mkdir -p $HOME/go
    $ tar -xvzf /tmp/go1.20.6.linux-amd64.tar.gz -C $HOME/go
    $ mv $HOME/go/go $HOME/go/go1.20.6
    root@CTU-WKS-AA578:/tmp# $HOME/go/go1.20.6/bin/go version
    go version go1.20.6 linux/amd64
    # sed -i '/^root.*ALL=(ALL).*ALL/a\going\tALL=(ALL) \tALL' /etc/sudoers
tee -a $HOME/.bashrc <<'EOF'
# Go envs
export LANG="en_US.UTF-8"
export WORKSPACE="$HOME/workspace"
export GOVERSION=go1.20.6
export GO_INSTALL_DIR=$HOME/go
export GOROOT=$GO_INSTALL_DIR/$GOVERSION
export GOPATH=$WORKSPACE/golang
export PATH=$GOROOT/bin:$GOPATH/bin:$PATH
export GO111MODULE="on"
export GOPROXY=https://goproxy.cn,direct
export GOPRIVATE=
export GOSUMDB=off
EOF
source $HOME/.bashrc
tee -a $HOME/.bashrc <<'EOF'

# Go envs
export LANG="en_US.UTF-8" # 设置系统语言为 en_US.UTF-8，避免终端出现中文乱码
export WORKSPACE="$HOME/workspace" # 设置工作目录
export GOVERSION=go1.20.6 # Go 版本设置
export GO_INSTALL_DIR=$HOME/go # Go 安装目录
export GOROOT=$GO_INSTALL_DIR/$GOVERSION # GOROOT 设置
export GOPATH=$WORKSPACE/golang # GOPATH 设置
export PATH=$GOROOT/bin:$GOPATH/bin:$PATH # 将 Go 语言自带的和通过 go install 安装的二进制文件加入到 PATH 路径中
export GO111MODULE="on" # 开启 Go moudles 特性
export GOPROXY=https://goproxy.cn,direct # 安装 Go 模块时，代理服务器设置
export GOPRIVATE=
export GOSUMDB=off # 关闭校验 Go 依赖包的哈希值
EOF

    root@CTU-WKS-AA578:~# mkdir workspace
    root@CTU-WKS-AA578:~# cd workspace/
    root@CTU-WKS-AA578:~/workspace#

    ```
- Language Mechanics [ref](https://tour.ardanlabs.com/tour/variables/1)
  - Variables
  - Struct Types
  - Pointers
    # Note
    Use pointers to share data.
    Values in Go are always pass by value.
    "Value of", what's in the box. "Address of" ( & ), where is the box.
    The ( * ) operator declares a pointer variable and the "Value that the pointer points to".    
    # escape analysis
    Does the value being constructed still have to exist when the owning function returns? 
    - If the answer is no, the value can be constructed on the stack. 
    - If the answer is yes, the value must be constructed on the heap.

  - Constants
    # Note
    Constants are not variables.
    They exist only at compilation.
    Untyped constants can be implicitly converted where typed constants and variables can't.
    Think of untyped constants as having a Kind, not a Type.
    Learn about explicit and implicit conversions.
    See the power of constants and their use in the standard library.
- Language Mechanics 2
  - Functions
  - Arrays
  - Slices
  - Maps
- Language Mechanics 3
  - Methods
  - Interfaces
  - Embedding
  - Exporting


#### What you should prepare for developing a real project before start coding
- install Git
  - download and install git
    ```
    $ apt-get install git
    $ git version
    $ git version 2.25.1
    ```      
  - set git config
    ```
    git config --global user.name "Your Name"
    git config --global user.email "your.email@example.com"
    git config --global core.editor "vim"
    ```
  - https://initialcommit.com/blog/Git-Cheat-Sheet-Beginner
  - https://initialcommit.com/blog/git-cheat-sheet-intermediate   
- create a db with docker and visualization tool
  - install docker [https://gist.github.com/xiaopeng163/f3e72bb1990860859076985d5a723cba]
  ```sh
  # install docker
  curl -fsSL get.docker.com -o get-docker.sh
  sh get-docker.sh

  if [ ! $(getent group docker) ];
  then 
      sudo groupadd docker;
  else
      echo "docker user group already exists"
  fi

  sudo gpasswd -a $USER docker
  sudo service docker restart

  rm -rf get-docker.sh
  ```
  - start db with installing docker and create test db
    ```sh
    docker run --name postpres -e POSTGRES_DB=simple_bank -e POSTGRES_USER=root -e POSTGRES_PASSWORD=root -p 5432:5432 postgres:12-alpine
    ```
  - install db visualization tools(DBeaver)
- How to use github to public your project and develop with the team collaterally
  <!-- - install openssl -->
  - generate rsa private and public key
  - save the public key to github account setting
  - create a repository on github and pull the repo to local
- Manage your project with makefile
  - understand base syntax
    ```
    targets: prerequisites
      command
      command
      command
    ```
  - use PHONY to avoid same name of file 
  - https://makefiletutorial.com/

#### Start coding CRUD
- Design DB schema and generate SQL code with dbdiagram.io
  - db schema with dbdiagram.io
    ```dbml
    Table "accounts" {
      "id" bigserial [pk, increment, ref: < entries.account_id]
      "owner" varchar [not null]
      "balance" bigint [not null]
      "currency" varchar [not null]
      "created_at" timestamptz [not null, default: `now()`]

      Indexes {
        owner
      }
    }

    Table "entries" {
      "id" bigserial [pk, increment]
      "account_id" bigint [not null]
      "amount" bigint [not null, note: 'can be negative']
      "created_at" timestamptz [not null, default: `now()`]

      Indexes {
        account_id
      }
    }

    Table "transfers" {
      "id" bigserial [pk, increment]
      "from_account_id" bigint [not null, ref: > accounts.id]
      "to_account_id" bigint [not null, ref: > accounts.id]
      "amount" bigint [not null, note: 'must be postive']
      "created_at" timestamptz [not null, default: `now()`]

      Indexes {
        from_account_id
        to_account_id
        (from_account_id, to_account_id)
      }
    }
    ```
    generate sql
    ```
    CREATE TABLE "accounts" (
      "id" BIGSERIAL PRIMARY KEY,
      "owner" varchar NOT NULL,
      "balance" bigint NOT NULL,
      "currency" varchar NOT NULL,
      "created_at" timestamptz NOT NULL DEFAULT (now())
    );

    CREATE TABLE "entries" (
      "id" BIGSERIAL PRIMARY KEY,
      "account_id" bigint NOT NULL,
      "amount" bigint NOT NULL,
      "created_at" timestamptz NOT NULL DEFAULT (now())
    );

    CREATE TABLE "transfers" (
      "id" BIGSERIAL PRIMARY KEY,
      "from_account_id" bigint NOT NULL,
      "to_account_id" bigint NOT NULL,
      "amount" bigint NOT NULL,
      "created_at" timestamptz NOT NULL DEFAULT (now())
    );

    CREATE INDEX ON "accounts" ("owner");

    CREATE INDEX ON "entries" ("account_id");

    CREATE INDEX ON "transfers" ("from_account_id");

    CREATE INDEX ON "transfers" ("to_account_id");

    CREATE INDEX ON "transfers" ("from_account_id", "to_account_id");

    COMMENT ON COLUMN "entries"."amount" IS 'can be negative';

    COMMENT ON COLUMN "transfers"."amount" IS 'must be postive';

    ALTER TABLE "entries" ADD FOREIGN KEY ("account_id") REFERENCES "accounts" ("id");

    ALTER TABLE "transfers" ADD FOREIGN KEY ("from_account_id") REFERENCES "accounts" ("id");

    ALTER TABLE "transfers" ADD FOREIGN KEY ("to_account_id") REFERENCES "accounts" ("id");

    ```
  
- Generate CRUD Golang code from SQL
  - install sqlc
  - write sql with sqlc
  - generate sql with sqlc
- How to write & run database migration in Golang
  - add sql of table creation to migration file
  - add sql of table deletion to migration file
  - compose the db migration with makefile
- Write utils package for your project
  - use package for organizing your code
  - implement function for util package
- Write UT for CRUD using local package
  - write UT for creation
  - write UT for retrieve
  - write UT for update
  - write UT for delete
  - go test ./... (search all test case in the current module)

#### Start coding REST API
- Implement RESTful HTTP API in Go using Gin
- Load config from file & environment variables in Go with Viper
- Mock DB for testing HTTP API in Go and achieve 100% coverage
- Implement transfer money API with a custom params validator

### Season 2


#### Ship the application
- Build a minimal Golang Docker image with a multistage Dockerfile
- How to use docker network to connect 2 stand-alone containers
- How to write docker-compose file to compose your app and DB and control service start-up orders using service_healthy condition

#### Deploy the application to production

### Season 3

#### Start coding CRUD 2

#### Start coding REST API 2