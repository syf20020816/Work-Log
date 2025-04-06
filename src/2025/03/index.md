## Ract (v0.1.7)

- [x] fix ios xcode-select check
- [x] fix macos pkg resources

## GenUI component

- [x] new getter
- [x] new setter
- [x] better macros
- [x] 减少render
- [x] 使用feature区分

## GenUI Book

- [x] update v0.1.1

## GenUI V0.1.2 (04-12)

- [x] if_else_if_else 语法糖
  - [x] only if
  - [x] if else
  - [x] multi_if
  - [x] if else_if
  - [x] if else_if else
  - [x] if else_if else_if .. else
  - [x] if else if else
  - [x] if if else
  - [x] if else_if if else_if if else
  - [x] if nested
- [x] router路由
  - [x] 声明式
  - [x] 编程式
- 生命周期
  - [x] before_update
  - [x] updated
- [x] 自闭合标签
- [x] 允许single_script策略使用genui api
- [x] fix 常规方法若使用(self)需要添加cx作为常规参数
- [x] 自动id策略(see utils::Ulid), 所有组件都会有一个id
- [x] 页面自动集成Gview属性的get|set
- [x] 更强大的Value::Bind (允许绑定方法)
- [x] 在调用到set_方法的函数最后增加redraw执行重绘
- [x] 调整getter｜setter使得原始对象和ref都具有双向绑定调整
  - [x] genui
  - [x] builtin
- [x] setter使用Result<(), Box<Error>>作为返回值
- [x] use gen_component::* -> use gen_components::{themes::*, utils::*, *};
- [x] Deref Prop struct add Default trait
- [x] computed计算属性: `#[computed(args...)]`

## livekit

- [x] 弹出share screen询问
- [x] 去除外部prejoin screen share 设置
- [x] 调整prejoin大小
- [x] setting默认开启视频和音频
- [x] ontrol bar剧中显示
- [x] wave pin增加音效
- [x] settings中去除preview image，改外外部预览
- [x] control_audio_toggle使用Mircophone
- [x] control_video_toggle使用Camera
- [x] share_screen_toggle设置开启和关闭状态 
- [ ] 屏幕分享，https://docs.livekit.io/home/client/data/rpc/
- [x] 用户状态（设置，显示）（Discord）
- [x] 虚拟人物
- [ ] 人声分离
- [x] 视频模糊区分用户 (前端可以区分，但是聊天室中没有后端无法同步)
- [ ] 名字修改

### 优先级

- [x] 权限
- [x] i18n
1. [x] 名字修改
3. [x] 用户状态
4. [x] 屏幕分享显示其他用户鼠标位置
5. [x] 虚拟人物
   1. [x] 人物模型
   2. [x] 优化追踪
   3. [x] 虚拟背景
6. [ ] 人声分离，降噪相关
7. [x] 设置
8. [ ] 后端传递用户配置
9. [ ] 去除Custom
10. [ ] control bar 弹出
11. [ ] common -> general
12. [ ] Chrome 不会自动跳出权限提醒
13. [ ] main 分支 prejoin 重写浏览器授权