update-manifests：*
params.UPDATE_SCRIPT：
要引用镜像构建阶段中的result，也就是刚打出来的镜像名称，并且使用 yq 更新 yaml 文件
yq -i '.spec.template.spec.containers[0].image = "$(tasks.image.results.ociContainerImageBuild-url)"' deployment.yaml
