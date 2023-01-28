# 使用Bazel将golang应用程序打包成Docker镜像

文章请见：<https://juejin.cn/post/7193268970881810489>

## 相关命令

- 初始化Bazel依赖项

    ```bash
    bazel run //:gazelle
    ```

- 更新`go.mod`中的依赖项到`WORKSPACE`

    ```bash
    bazel run //:gazelle -- update-repos -from_file=go.mod
    ```

- 构建项目

    ```bash
    bazel build //...
    ```

- 运行项目

    ```bash
    bazel run //cmd/api
    ```

- 构建Docker镜像tar文件

    ```bash
    bazel build //cmd/api:image
    ```

- 构建并导入Docker镜像（等同于docker load）

    ```bash
    bazel run //cmd/api:image
    ```

- 推送Docker镜像到DockerHub（等同于docker push）

    ```bash
    bazel run //cmd/api:image-push
    ```
