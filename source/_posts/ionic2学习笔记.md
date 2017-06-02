---
title: ionic2学习笔记
date: 2017-04-18 09:24:22
tags: js
categories: hybrid
---
Ionic(ionicframework)一款接近原生的HTML5移动App开发框架。

IONIC 是目前最有潜力的一款 HTML5 手机应用开发框架。通过 SASS 构建应用程序，它提供了很多 UI 组件来帮助开发者开发强大的应用。 它使用 JavaScript MVVM 框架和AngularJS 来增强应用。提供数据的双向绑定，使用它成为 Web 和移动开发者的共同选择。Ionic是一个专注于用WEB开发技术，基于HTML5创建类似于手机平台原生应用的一个开发框架。Ionic框架的目的是从web的角度开发手机应用，基于PhoneGap的编译平台，可以实现编译成各个平台的应用程序。

注意：这里讲的是ionic2的知识点，毕竟它与ionic 1.0有着较显著的区别。
<!-- more -->

 

 
### Ionic 的安装与运行

 

1、 下载安装 Node.js，可以在命令行中使用node–v 命令查看当前安装的node.js的版本；

2、 使用 npm install ionic –g命令可以安装Ionic，不过需要注意的是此时安装的版本为Ionic 1.0版本。可以使用npm install ionic@beta–g 安装beta版本，如可以使用npm installionic@2.0.0-beta.22 –g安装beta.22版本；

3、 安装Ionic 后，可以使用 ionic start ionicdemo --v2初始化一个空项目，默认采用tabs template作为初始化项目的模板，如果需要其他的模板，那么在项目名称后面添加上对应的模板名称即可，如：ionic start ionicdemo tutorial --v2；（--v2参数明确了使用2.0版本去初始化项目）

4、 使用 ionic serve可以运行Ionic项目；

5、 使用 ionic platform add Android或ionic platform add iOS命令可以添加两个手机平台的部署文件（使用ionicplatform list 命令可以查看当前的平台信息）；

6、 在项目中添加了两个平台的部署文件，可以通过platform文件夹下进行查看，相应地，在Xcode导入ios部署文件或在Android studio导入Android部署文件，可以进行相应地真机调试；

 

 
### Ionic页面的生命周期
~~~
// 页面被加载完成后调用的函数，切换页面时并不会进行重新加载，因为有cache的存在  
onPageLoaded() {  
  console.log('page 1: page loaded.');  
}  
  
// 页面即将进入的时候  
onPageWillEnter() {  
  // 在这里可以做页面初始化的一些事情  
  console.log('page 1: page will enter.');  
}  
  
// 页面已经进入的时候  
onPageDidEnter() {  
  console.log('page 1: page did enter.');  
}  
  
// 页面即将离开的时候  
onPageWillLeave() {  
  console.log('page 1: page will leave.');  
}  
  
// 页面已经离开的时候  
onPageDidLeave() {  
  console.log('page 1: page did leave.');  
}  
  
// 从 DOM 中移除的时候执行的生命周期  
onPageWillUnload() {  
  
}  
  
// 从 DOM 中移除执行完成的时候  
onPageDidUnload() {  
  
}
~~~
 
### Ionic组件

1、Tab控件

图标：http://ionicframework.com/docs/v2/ionicons/ 

tabs.html
~~~
<ion-tabs>  
  <ion-tab [root]="tab1Root" tabTitle="Home" tabIcon="home"></ion-tab>  
  <ion-tab [root]="tab2Root" tabTitle="About" tabIcon="information-circle"></ion-tab>  
  <ion-tab [root]="tab3Root" tabTitle="Contact" tabIcon="contacts"></ion-tab>  
</ion-tabs>  
 



 

<ion-tabs>  
  <ion-tab [root]="tab1Root" tabTitle="Home" tabIcon="home"></ion-tab>  
  <ion-tab [root]="tab2Root" tabTitle="About" tabIcon="information-circle"></ion-tab>  
  <ion-tab [root]="tab3Root" tabTitle="Contact" tabIcon="contacts" tabBadge="3"></ion-tab>  
</ion-tabs>  



 

 

<ion-tabs>  
  <ion-tab [root]="tab1Root" tabTitle="Home" tabIcon="home"></ion-tab>  
  <ion-tab [root]="tab2Root" tabTitle="About" tabIcon="information-circle"></ion-tab>  
  <ion-tab [root]="tab3Root" tabTitle="Contact" tabIcon="contacts" tabBadge="3" tabBadgeStyle="danger"></ion-tab>  
</ion-tabs>  
~~~



 

 

默认首先进入第三个tab页面：

Html控制

 
~~~
<ion-tabs selectedIndex="2">  
  <ion-tab [root]="tab1Root" tabTitle="Home" tabIcon="home"></ion-tab>  
  <ion-tab [root]="tab2Root" tabTitle="About" tabIcon="information-circle"></ion-tab>  
  <ion-tab [root]="tab3Root" tabTitle="Contact" tabIcon="contacts" tabBadge="3" tabBadgeStyle="danger"></ion-tab>  
</ion-tabs>  
~~~ 

 

JS控制
~~~
<ion-tabs #mainTabs>  
  <ion-tab [root]="tab1Root" tabTitle="Home" tabIcon="home"></ion-tab>  
  <ion-tab [root]="tab2Root" tabTitle="About" tabIcon="information-circle" tabBadge="3" tabBadgeStyle="danger"></ion-tab>  
  <ion-tab [root]="tab3Root" tabTitle="用户中心" tabIcon="person"></ion-tab>  
</ion-tabs>  
 

import {Component} from '@angular/core';  
import {HomePage} from '../home/home';  
import {AboutPage} from '../about/about';  
import {ContactPage} from '../contact/contact';  
  
import {Tabs} from 'ionic-angular';  
import {Injectable, ViewChild} from '@angular/core';  
  
@Component({  
  templateUrl: 'build/pages/tabs/tabs.html'  
})  
export class TabsPage {  
  @ViewChild('mainTabs') tabRef: Tabs;  
  
  private tab1Root: any;  
  private tab2Root: any;  
  private tab3Root: any;  
  
  constructor() {  
    // this tells the tabs component which Pages  
    // should be each tab's root Page  
    this.tab1Root = HomePage;  
    this.tab2Root = AboutPage;  
    this.tab3Root = ContactPage;  
  }  
  
  ionViewDidEnter() {  
    this.tabRef.select(2);  
  }  
}  
~~~ 

2、Button控件
~~~
<button>Basic Button</button>  
<button gray>Gray Button</button>  
<button danger>Danger Button</button>  
<button outline>Outline Button</button>  
<button clear>Clear Button</button>  
<button round>Round Button</button>  
<button block>Block Button</button>  
<button small>Small Button</button>  
<button large>Large Button</button>  
<button>  
  <ion-icon name="home"></ion-icon>  
  Button  
</button>  
<button>  
  Button  
  <ion-icon name="home"></ion-icon>  
</button>  
<button>  
  <ion-icon name="home"></ion-icon>  
</button>  
~~~

 

 

3、Input控件
~~~
<ion-list>  
  <ion-item>  
    <ion-label floating>用户名</ion-label>  
    <ion-input type="text" value="" [(ngModel)]="user.username"></ion-input>  
  </ion-item>  
  <ion-item>  
    <ion-label stacked>密码</ion-label>  
    <ion-input type="password" value="" [(ngModel)]="user.password"></ion-input>  
  </ion-item>  
</ion-list>  
<button block (click)="showFill()">登录</button>  
 

export class ContactPage {  
  public user = {  
    username: 'parry',  
    password: ''  
  };  
  
  constructor(private navCtrl: NavController) {  
  
  }  
  
  showFill() {  
    alert(this.user.username);  
    console.log(this.user.password);  
  }  
}  
~~~ 

4、Loading控件、Alert控件
~~~
import { Component } from '@angular/core';
import { NavController,LoadingController,AlertController } from 'ionic-angular';

@Component({
  selector: 'page-home',
  templateUrl: 'home.html'
})
export class HomePage {
  public user = {  
    username: '',  
    password: ''  
  };  
  constructor(public navCtrl: NavController,
  public loadingCtrl: LoadingController,
  public alertCtrl: AlertController) {
  }
  login(){
  	if(this.user.username == ''){
  		let alertUsernameError = this.alertCtrl.create({
  			title: '用户中心',
  			subTitle: '用户名不能为空',
  			buttons: ['OK']
  		});
  		alertUsernameError.present();
  	}else{
  		let loading = this.loadingCtrl.create({
  		content: "正在登陆",
  		duration: 3000
	  	});
	  	loading.present();
  	}
  }
}
~~~ 

5、Toast控件
~~~
// 2. 使用 Toast 控件  
let toast = this.toastCtrl.create({  
  message: '输入的用户名格式不正确！',  
  duration: 3000,  
});  
toast.present();  
~~~ 

6、Grid布局
~~~
<ion-row>  
  <ion-col>  
    <div class="textAlignRight marginTop10"><button clear>还没有账号？点击注册</button></div>  
  </ion-col>  
</ion-row>  
~~~ 

7、 modal控件
~~~
// 导入注册页面  
import {Register} from '../contact/register';  
 

// 打开注册页面  
openRegisterPage() {  
  let modal = this.modalCtrl.create(Register);  
  modal.present();  
}  
 

import {Component} from '@angular/core';  
  
@Component({  
  templateUrl: 'build/pages/contact/register.html'  
})  
export class Register {  
  
}  
~~~ 

8、 Toolbar控件
~~~
<ion-toolbar>  
  <ion-title>用户注册</ion-title>  
  <ion-buttons end>  
    <button (click)="dismiss()">  
      <span showWhen="ios">取消</span>  
      <ion-icon name="md-close" showWhen="android,windows"></ion-icon>  
    </button>  
  </ion-buttons>  
</ion-toolbar>  
 

修改：

<ion-header>  
  <ion-toolbar>  
    <ion-title>用户注册</ion-title>  
    <ion-buttons end>  
      <button (click)="dismiss()">  
        <span showWhen="ios">取消</span>  
        <ion-icon name="md-close" showWhen="android,windows"></ion-icon>  
      </button>  
    </ion-buttons>  
  </ion-toolbar>  
</ion-header>  
  
  
<ion-content padding>  
    <h5>Parameters passed:</h5>  
</ion-content>  
~~~ 

9、 List控件
~~~
<ion-list>  
  <ion-item>  
    <ion-avatar item-left><img src="../images/1.jpg" alt="头像"></ion-avatar>  
    <h2>哈哈</h2>  
    <p>(ˇˍˇ) 想～</p>  
  </ion-item>  
  <ion-item>  
    <ion-avatar item-left><img src="../images/2.jpg" alt="头像"></ion-avatar>  
    <h2>美女</h2>  
    <p>(ˇˍˇ) 想～</p>  
  </ion-item>  
</ion-list>  
 

绑定数据源：

数据源的声明

// 一般数据源都是从 api 进行获取，这里我们只是模拟一些已经取到了数据  
public contacts = [  
  {'contactid': 1, 'contactname': '梦小白', 'contacttext': '18888888888'},  
  {'contactid': 2, 'contactname': '梦小白2', 'contacttext': '18888888888'},  
  {'contactid': 3, 'contactname': '梦小白3', 'contacttext': '18888888888'},  
  {'contactid': 4, 'contactname': '梦小白4', 'contacttext': '18888888888'},  
  {'contactid': 5, 'contactname': '梦小白5', 'contacttext': '18888888888'},  
  {'contactid': 6, 'contactname': '梦小白6', 'contacttext': '18888888888'},  
  
  {'contactid': 1, 'contactname': '梦小白7', 'contacttext': '18888888888'},  
  {'contactid': 2, 'contactname': '梦小白8', 'contacttext': '18888888888'},  
  {'contactid': 3, 'contactname': '梦小白9', 'contacttext': '18888888888'},  
  {'contactid': 4, 'contactname': '梦小白10', 'contacttext': '18888888888'},  
  {'contactid': 5, 'contactname': '梦小白11', 'contacttext': '18888888888'},  
  {'contactid': 6, 'contactname': '梦小白12', 'contacttext': '18888888888'},  
];  
 

<ion-list>  
  <ion-item *ngFor="let contact of contacts" (click)="itemClick($event, contact)">  
    <ion-avatar item-left><img src="../images/{{contact.contactid}}.jpg" alt="头像"></ion-avatar>  
    <h2>{{contact.contactname}}</h2>  
    <p>{{contact.contacttext}}</p>  
  </ion-item>  
</ion-list>  
~~~ 

10、卡片布局
~~~
<ion-card>  
  <ion-item>  
    <ion-avatar item-left>  
      <img src="../images/6.jpg" alt="头像">  
    </ion-avatar>  
    <h2>Elon Musk</h2>  
    <p>来自 iPhone 6s</p>  
  </ion-item>  
  <img src="../images/c1.jpg" alt="图片">  
  <ion-card-content>  
    <p>我又发布了一辆新车，上天入地舍我其谁？呵呵</p>  
  </ion-card-content>  
  <ion-item>  
    <button primary clear item-left><ion-icon name="thumbs-up"></ion-icon><div>888 赞</div></button>  
    <button primary clear item-left><ion-icon name="text"></ion-icon><div>600 评论</div></button>  
    <ion-note item-right>  
      1小时前  
    </ion-note>  
  </ion-item>  
</ion-card>  
~~~ 

11、navigation控件
~~~
itemClick(event, contact) {  
  //console.log(event);  
  //console.dirxml(contact);  
  //alert(contact.contactname);  
  
  this.navCtrl.push(ContactDetails, {item: contact});  
}  
 

ContactDetails页面

/** 
 * Created by Administrator on 2016/8/23 0023. 
 */  
import {Component} from '@angular/core';  
import {NavParams} from 'ionic-angular';  
  
@Component({  
  templateUrl: 'build/pages/about/contactdetails.html'  
})  
export class ContactDetails {  
  private item = '';  
  
  constructor(public params: NavParams) {  
    this.item = params.data.item;  
  }  
}  
 

<ion-header>  
  <ion-navbar>  
    <ion-title>{{item.contactname}}</ion-title>  
  </ion-navbar>  
</ion-header>  
<ion-content padding>  
  {{item.contactname}} 的手机号码为：{{item.contacttext}}  
</ion-content>  
~~~


 
### Cordova组件介绍

1、Image Picker组件

 

2、Geolocation组件

 
~~~
// 获取位置信息  
Geolocation.getCurrentPosition().then((resp) => {  
  console.log(resp.coords.latitude);  
  console.log(resp.coords.longitude);  
});  
~~~ 

 

3、Local Notifications组件
~~~
// 本地提醒组件  
LocalNotifications.schedule({  
  text: '本地化提醒-您启动了Ionic App',  
  at: new Date(new Date().getTime() + 10000),  
  sound: null  
});  
~~~ 

### 项目实战

1、快速生成App图标和启动页面

MakeAppicon

Ios.hvims.com

Launcher Icon Generator

iconhandbook.co.uk/reference/chart/android



 

2、使用localStorage存储状态信息
~~~
localStorage.setItem(key, value)

localStorage.getItem(key)

 

注：Modal页面的关闭需要使用到ViewController中的dismiss方法。
~~~
 

3、Modal关闭后父页面的概念和方法

 

4、Ionic中的网络请求
~~~
跨域请求问题： http://enable-cors.org/ （当然在App中不会出现，只会在浏览器调试的过程中出现）

 

// 这里是请求 API 的实现，注意跨域请求的问题，请参见 http://enable-cors.org/  
this.http.get('http://xxx/account/Login?email=' + this.user.username + '&password=' + this.user.password)  
  .subscribe(data => {  
    let res = data.json();  
    if(res.LoginStatus == 1) {  
      localStorage.setItem('username', this.user.username);  
      localStorage.setItem('logined', 'true');  
      //自身 modal 隐藏  
      this.viewCtrl.dismiss(this.user.username);  
      loading.dismiss(); //登录进度隐藏  
    } else {  
      let toast = this.toastCtrl.create({  
        message: '登录失败！',  
        duration: 2000,  
      });  
      toast.present();  
    }  
  
  }, err => {  
    let toast = this.toastCtrl.create({  
      message: '登录失败！',  
      duration: 2000,  
    });  
    toast.present();  
  
  });  
~~~ 

 

5、List中滑动删除数据
~~~
<ion-list>  
  <ion-item-sliding *ngFor="#contact of contacts">  
    <ion-item (click)="itemClick($event, contact)">  
      <ion-avatar item-left><img src="images/{{contact.contactid}}.jpg" alt="头像"></ion-avatar>  
      <h2>{{contact.contactname}}</h2>  
      <p>{{contact.contacttext}}</p>  
    </ion-item>  
    <ion-item-options>  
      <button danger (click)="removeContact(contact)">  
        <span padding><ion-icon name="trash"></ion-icon> 删除</span>  
      </button>  
    </ion-item-options>  
  </ion-item-sliding>  
</ion-list>  
~~~ 

6、集成极光推送实现消息推送

~~~
// 设置客户端的别名，用于定向接收消息的推送

window.plugins.jPushPlugin.setAlias(‘Client’ + loginResult.UserId);

 

// Client（只能是单一值）：单独的一台设备绑定到jPush，就相当于设备的ID号码，server端推送的时候只能推送到ID级别的。

 

var arrayObj = new Array(‘Tags’ + loginResult.UserId);

window.plugins.jPushPlugin.setTags(arrayObj);

//Tags：其实就是分组的意思，那么这样指定后，在用户登录的时候 分配一个分组名给用户，那么推送消息的时候，就可以推送给这个分组。 应用场景：如果用户有多个设备，并且这些设备上可以同时登录app，那么我们推送消息应该推送给这几个设备。
~~~
 

//Client – 1，只是这一台设备收到通知。

//Tag – 1，多台设备都设置叫 Tag – 1。

 

7、iOS打包与AppStore上架

8、Android打包与发布


参考学习：

https://babeljs.io

http://kangax.github.io/compat-table/es6/

https://github.com/driftyco

https://github.com/driftyco/ionic-preview-app/

http://www.typescriptlang.org/docs/

http://mhartington.io/post/ionic2-external-libraries
