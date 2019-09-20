[TOC]
## Spring Data JPA 的Repository是怎么从接口转化为Bean的

1. 从@EnableJpaRepositories 注解开始
2. @Import(JpaRepositoriesRegistrar.class)
3. JpaRepositoriesRegistrar 返回 JpaRepositoryConfigExtension
  3.1  JpaRepositoryConfigExtension.getRepositoryFactoryBeanClassName() 返回一个 JpaRepositoryFactoryBean类名
4. JpaRepositoriesRegistrar 继承 RepositoryBeanDefinitionRegistrarSupport
  4.1 RepositoryBeanDefinitionRegistrarSupport.registerBeanDefinitions(AnnotationMetadata annotationMetadata, BeanDefinitionRegistry registry)
      注册Bean定义的方法
  4.2 delegate.registerRepositoriesIn(registry, extension)

5. JpaRepositoryConfigExtension  继承 RepositoryConfigurationExtensionSupport
  5.1 RepositoryConfigurationExtensionSupport.getRepositoryConfigurations() 获取Repository配置

6. JpaRepositoriesRegistrar.getExtension() -> JpaRepositoryConfigExtension.getRepositoryFactoryBeanClassName() -> JpaRepositoryFactoryBean.createRepositoryFactory()
  6.1 JpaRepositoryFactory.getTargetRepository() 创建 Repository

![JpaRepositoriesRegistrar](/assets/JpaRepositoriesRegistrar.png)<img alt="Spring Date JPA 的Repository是怎么从接口化成Bean的？-fc6f0e20.png" src="assets/Spring Date JPA 的Repository是怎么从接口化成Bean的？-fc6f0e20.png" width="" height="" >

## 接口中自定义的方法是如何被解释的

1. RepositoryFactorySupport
