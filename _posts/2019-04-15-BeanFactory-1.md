---
layout: post
title: "Bean Factory - 1"
---

## Bean Factory

### 스프링의 빈(객체)을 관리하는 공장

ApplicationContext 에서 중요한 부분을 차지하는 BeanFactory 는 스프링에서 사용되는 모든 빈들을 관리해요.

관리라는 말을 조금 더 분해하면 크게 생성/수정/삭제/조회(CRUD) 의 기능을 한다고 볼 수 있겠네요.

하지만 신기한 건 BeanFactory interface 에는 getBean 이라는 조회 기능의 메소드만 들어가 있죠. 왜 그럴까요

BeanFactory 의 기초적인 메소드를 구현하는 Spring 의 AbstractBeanFactory 를 통해서 이유를 찾을 수 있을 거 같아요

![AbstractBeanFactory Diagrams](https://raw.githubusercontent.com/YounHyunJun/YounHyunJun.github.io/master/img/AbstractBeanFactory_Digagram.PNG)

여기서 중요하게 봐야할 부분은 AbstractBeanFactory 는 ConfigurableBeanFactory 를 구현하고 이는 HierarchicalBeanFactory 와 SingletonBeanRegistry 를 구현해요

골자는 BeanFactory 를 지원하기 위한 Registry 가 존재한다는 점이고 이는 빈을 공장에서 가져오기 위한 빈들의 저장소가 필요하다는 것을 의미해요  

여기서는 SingletonBean 저장소를 통해 빈을 관리하고 그 빈들을 BeanFactory 가 가져온 다는 것을 알 수 있죠.

> 정리하자면 BeanFactory 는 빈을 조회하는 인터페이스이지만 BeanRegistry 함께 쓰여 애플리케이션 내의 빈들을 관리하는 역할이라고 생각되요

이 빈팩토리를 구체적으로 알아보기 위해 앞으로 찾아봐야 할 클래스들은 다음과 같아요

![DefaultListableBeanFactory Diagrams](https://raw.githubusercontent.com/YounHyunJun/YounHyunJun.github.io/master/img/DefaultListableBeanFactory_Digagram.PNG)

다음은 SimpleAliasRegistry 에 대해서 포스팅할 예정이에요