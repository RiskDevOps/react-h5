## TODO-LIST

暂定的待办事项, 按照Scrum模型中的Sprint进行划分迭代, 如果有非常紧急的需求可以在提交Issues时Title 以 urgent: 开头, 如下

> urgent: 在打包的时候Webpack提示xx错误, <br> Issue内容....

这一条Issue将会被标注为紧急问题, 将会优先得到查看和解决


### Sprint 01

- [x] 搭建基础架子
- [x] 将px转换为rem, 处理动态计算Html字体
- [x] 集成dva数据流
- [x] intl 国际化和document-title的title国际化问题
- [x] 最基础版Demo实现和部署
- [ ] 打包需要排除node_modules中除antd-mobile外的包
- [ ] webpack 集成内网穿透工具, 进行手机调试
- [ ] Flow 静态类型分析支持

### Sprint 02

- [ ] 自动化测试Cypress
- [ ] Cypress + Sizzy 进行自动化多端测试
- [ ] git hook 做提交前检查和webhook推送
- [ ] TypeScript 版本支持

### Sprint 03

- [ ] 打包深度优化, 更改打包
- [ ] Node Cli 工具