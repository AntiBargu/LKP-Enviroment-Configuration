记录在Opencloud OS/Tencent OS配置LKP-Tests时遇到缺失依赖的问题及解决方案。



#### 镜像研发进度

|            容器镜像名称             |               base镜像                | 研发进度 |
| :---------------------------------: | :-----------------------------------: | :------: |
| antibargu/lkp-extent:opencloudos8.6 |      opencloudos/opencloudos:8.6      |  研发中  |
| antibargu/lkp-extent:opencloudos8.8 |      opencloudos/opencloudos:8.8      |  研发中  |
| antibargu/lkp-extent:opencloudos9.0 |      opencloudos/opencloudos:9.0      |  研发中  |
|  antibargu/lkp-extent:tencentos3.1  | tencentos/tencentos_server31:20230628 |  研发中  |

> 此镜像并非lkp-extent项目运行时的容器镜像。



#### 测试用例及测试进度

|   测试用例   | 测试进度 |
| :----------: | :------: |
|   stress*    |  测试中  |
|     vm*      |  未测试  |
|     ltp*     |  未测试  |
|     fio*     |  未测试  |
| kernel-self* |  未测试  |