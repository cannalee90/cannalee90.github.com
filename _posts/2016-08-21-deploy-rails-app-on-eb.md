---
layout: post
title:  "elastic beanstalk에 rails-app 배포하기"
categories: deploy rails
---

레일즈 앱을 elastic-beanstalk에 배포하는 위해서는 AWS_CONSOLE을 사용하거나 AWS_CLI가 설치되어 있어야 한다. 이번 포스트에서는 AWS_CLI를 사용해서 배포하기로 한다

```
brew update
brew install aws-elasticbeanstalk
```

배포할 레일즈 앱에서 가서 다음 명령어로 Elastic Beanstalk를 초기화 한다.

```
eb init
```

Elastic Beanstalk의 기본 셋팅을 해준다.

```
Select an application to use
1) My First Elastic Beanstalk Application
(default is 2): 2

Enter Application Name
(default is ".aws"): test-app
Application test-app has been created.


It appears you are using Ruby. Is this correct?
(y/n): y

Select a platform.
1) Ruby

.....
```

그냥 진행하게 될경우 아마 env값이 제대로 설정되지 않아서 오류가 날 것이다.
env값은 다음과 같이 지정한다.

```
eb setenv SECRET_KEY_BASE=MY_SECRET_KEY
```

만약 default 셋팅값이 아닌 저장된 값으로 새롭게 환경을 셋팅해보고 싶다면 [여기](http://docs.aws.amazon.com/elasticbeanstalk/latest/dg/environment-configuration-methods-before.html#configuration-options-before-savedconfig)를 참고해서 진행한다.(이미 디플로이가 된 상태의 환경을 파일로 저장한다.)

```
eb config save --cfg MY-APP

```

다음과 같이 사용하게 된다.

```
eb create --cfg MY-APP
```

Elastic Beanstalk의 env 값을 지정해보고 싶으면 saved_configs파일에 있는 nypc.cfg.yml에서 다음과 같이 값을 추가해준다

```
OptionSettings:
  aws:elasticbeanstalk:application:environment:
    AWS_ACCESS_KEY_ID: MY_AWS_KEY
    AWS_SECRET_ACCESS_KEY: MY_AWS_SECRET_KEY

```
