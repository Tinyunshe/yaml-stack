**update-manifests：**

params.UPDATE_SCRIPT：

1、要引用镜像构建阶段中的result，也就是刚打出来的镜像名称，并且使用 yq 更新 yaml 文件

yq -i '.spec.template.spec.containers[0].image = "$(tasks.image.results.ociContainerImageBuild-url)"' deployment.yaml

2、如果 git 密码结尾是"@"，那么需要在写成%40，否则会出现格式化错误

比如密码为123@，那么要写成 kubernetes secret 中为123%40

3、生成 git 账户与密码时，使用的命令。echo需要加"-n"，否则会有换行导致 git 出错

echo -n "xxxx" | base64
