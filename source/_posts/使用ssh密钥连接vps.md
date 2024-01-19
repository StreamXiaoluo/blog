---
title: 使用ssh密钥连接vps
date: 2024-01-19 14:27:34
tags: VPS
catagories: 基础命令
---
### 在本地机器上生成SSH密钥：

1. 打开终端（如果使用Linux或Mac）或使用SSH客户端（如PuTTY，如果使用Windows）。

2. 在终端中执行以下命令来生成SSH密钥对：

    ```bash
    ssh-keygen -t rsa -b 4096
    ```

   这将生成一个4096位的RSA密钥对。按照提示，您可以选择为密钥对选择保存路径和设置密码（可选）。

3. 在生成密钥对后，您将在指定路径下找到公钥（通常为`~/.ssh/id_rsa.pub`）和私钥（通常为`~/.ssh/id_rsa`）。

### 将公钥添加到VPS上：

4. 使用SSH工具连接到VPS。如果您是第一次连接，您将需要使用VPS提供的用户名和密码进行身份验证。

    ```bash
    ssh username@your_vps_ip
    ```

5. 打开或创建`authorized_keys`文件。这是存储允许访问VPS的SSH密钥的文件。

    ```bash
    nano ~/.ssh/authorized_keys
    ```

   如果文件不存在，可以使用以上命令创建一个新文件。

6. 在本地机器上生成的公钥文件（通常为`~/.ssh/id_rsa.pub`）中找到公钥内容，并将其复制到VPS上的`authorized_keys`文件中。

7. 保存文件并退出。如果您使用的是`nano`，按 `Ctrl + X`，按 `Y` 确认，然后按 `Enter` 退出。

### 配置SSH服务器：

8. 确保SSH服务器允许公钥身份验证。在VPS上打开SSH服务器配置文件：

    ```bash
    sudo nano /etc/ssh/sshd_config
    ```

   确保以下行被设置为 `yes`：

    ```plaintext
    PubkeyAuthentication yes
    ```

   保存文件并重启SSH服务：

    ```bash
    sudo systemctl restart ssh
    ```

9. 使用以下命令退出当前的SSH连接：

    ```bash
    exit
    ```

10. 然后尝试重新连接到VPS。这次您应该不再需要输入密码。

    ```bash
    ssh -i ~/.ssh/id_rsa username@your_vps_ip
    ```

请确保您具有足够的权限来修改`authorized_keys`文件，并小心不要在没有备份的情况下修改关键文件，以防止错误操作。
