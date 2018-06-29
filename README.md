# Modular_study
组件化编程学习

## 开源组件化框架

- Arouter：路由引擎，诸多组件化框架使用(**推荐**)
- [MVPArms](https://github.com/JessYanCoding/MVPArms)  **4700** star,原理参见[armsComponent](https://github.com/JessYanCoding/ArmsComponent)
   - 利用Arouter作为路由引擎
   - MVP开发模式：MVP+Rxjava2+Retrofit2+Glide+Dagger2+ButterKnife
- [JIMU](https://github.com/mqzhangw/JIMU)：得到组件化框架 **3000** star
   - 自定义路由框架，也可以使用Arouter
   - ![arc](https://i.imgur.com/HYWGsTh.png)
   - 模块依赖图
         - **app**:演示app，根据需要配置需要的相关组件。
         - **basiclib**:基础库，如网络、图片加载、数据库、json、日志等
         - **basicres**:基础资源库，如通用样式，基础图片、selector，基础动画资源等
         - **build-gradle**:
            - 实现代码隔离、组件单独调试
            - 组件注册：利用TrasnformAPI + javassist将各组件的IApplicationLike的注册代码自定义到application.onCreate
            - 生成UIRouterTable：各组件路由映射表
         - **componentlib**:组件化核心：路由Router/UIRouter,IApplicationlike等管理
         - **componentservice**:所有组件对外提供服务接口定义
         - **router-annotation**:注解定义Autowired,RouteNode
         - **router-anno-compiler**:
            - 利用apt生成各组件UIRouter，路径均为com.luojilab.gen.router，页面路由的注册采用手动在组件IApplicationLike中进行注册
            - 利用apt进行页面参数的解析，借鉴Arouter
         - **readercomponent**:reader组件，依赖componentservice+router-anno-compiler
         - **sharecomponent**:分享组件，依赖componentservice+router-anno-compiler


- 百链 [CC](https://github.com/luckybilly/CC): **2300** star
- [T-MVP](https://github.com/north2016/T-MVP)：**2400** star ,原理参见[Moduler](https://github.com/north2016/Moduler)


## SPI面向接口编程 [学习demo](https://github.com/kithan/autoService)
接口下沉到base，模块进行具体实现。目前在组件化方案中，一般是在组件向外提供服务或组件注册借助SPI实现.

- 实现方案1：基于JAVA SPI：手动编写resources/META-INF配置文件
- 实现方案2：auto-service开源库：借助该库注解实现1。
- 开源框架应用：Arouter、JIMU(原得到DDComponentForAndroid)

## 代码隔离
通过代码隔离，实现在编译期间直接使用具体组件中的实现，即无需添加compile project(':share.aar')
		     
- 得到组件化方案：通过gradle插件实现只在assembleDebug或者assembleRelease时引入工程或aar


## 组件注册
在开源框架中组件注册一般的形式有
  - TransformApi+javaAssist/ASM
  - 反射
  - 手动注册
 
 ## 待完成
   - TransformApi demo
   - asm代码注入demo
   - 路由注册demo
   - 利用Tranform+asm进行埋点
 
