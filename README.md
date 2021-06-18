# ansible-roles

常用的 role

#### 使用方法

在 requirements.yml 写入

```

roles:
  - src: https://github.com/36node/ansible-roles/
    name: ansible-roles
    version: main
    scm: git

```

执行 ansible-galaxy install -r requirements.yml
