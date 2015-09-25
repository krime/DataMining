# Global Tasks
* Front Page
 1. 首页-日息宝类产品接口
 2. 首页-省心赚类产品接口
 3. 首页-标类产品接口
 4. 首页-债权类产品接口
* Register/Login
 1. 注册登录-用户注册类接口修改
* Invest Combinatory
 1. 投资组合-活期宝类接口
 2. 投资组合-省心赚类接口
 3. 投资组合-债权类接口
* Account Management 
 1. 账户管理-个人信息类接口
 2. 账户管理-认证类接口
 3. 账户管理-银行卡类接口

# Initialize Touna-OneShop Server
* Update touna-jrhui-server to touna-oneshop-server
 - Remove ${SERVER}/api
 - Remove ${SERVER}/impl
 - Change "jrhui" to oneshop

* Project Logic
 - Web API Layers
  * /api
  * /impl

 - Logic Implementation Layer:
  * /logic
 
 - Message Push Layer:
  * /logic/notify
 
 - 
  * /support

 - Database Accessor Layer:
  * /accessor

# 金融汇账号
user: kings
pass: abc123

# Note
省心赚累计收益=省心赚已赚利息之和+购买转让的省心赚获得的奖励
债权累计收益=【债权已赚利息之和】+返还利息管理费+罚息收入+购买普通债权获得的奖励- 已付利息管理费+【转让收益】


# Interfaces
* Front Page
 1. 首页-日息宝类产品接口
```java
/**
 * @brief get daily interest informations
 * @param page integer, the nth page daily interest informations
 * @param size integer, the page size
 * @param status integer, the product status
 * @return List<DailyInterestBean>, a list of daily interest informations
 */
public List<DailyInterestBean> getDailyInterestList(page, size, status);
```
 2. 首页-省心赚类产品接口
```java
/**
 * @brief get smart plan informations
 * @param page integer, the nth page smart plan informations
 * @param size integer, the page size
 * @param status integer, the product status
 * @return List<SmartPlanBean>, a list of smart plan informations
 */
public List<SmartPlanBean> getSmartPlanList(page, size, status);
```
 3. 首页-标类产品接口
```java
/**
 * @brief get smart tender informations
 * @param page integer, the nth page smart tender informations
 * @param size integer, the page size
 * @param status integer, the product status
 * @return List<SmartTenderBean>, a list of smart tender informations
 */
public List<SmartTenderBean> getSmartTenderList(page, size, status);
```
 4. 首页-债权类产品接口
```java
/**
 * @brief get obligation informations
 * @param page integer, the nth page obligation informations
 * @param size integer, the page size
 * @param status integer, the product status
 * @return List<ObligationBean>, a list of obligation informations
 */
public List<ObligationBean> getObligationList(page, size, status);
```
* Register/Login
 1. 注册登录-用户注册类接口修改
```java
```
* Invest Combinatory
 1. 投资组合-活期宝类接口
  * 转入
```java
void doTransferIn();
```
  * 转出
```java
void doTransferOut();
```
  * 年化收益率表
```java
getDemandTenderList();
```
 2. 投资组合-省心赚类接口
  * API
   - 投资本金：原持有本金
   - 累计收益：同账户总览页省心赚累计收益
   - 购买金额：同原来已购买债权的购买金额
   - 收益中：原锁定中(lock)
  * 转让计划、计划设置操作流程同原有，点击转让计划的省心赚转移到债权-转让专区
  * 省心赚详情
  * 加入中、收益中状态的省心赚卡片，可转让的省心赚卡片
```java
getSmartPlanInfo();
getSmartPlanList();
```
 3. 投资组合-债权类接口
  * API
   - 投资本金：原待收本金
   - 待收利息：同原待收利息
   - 累计收益：同账户总览页债权累计收益
   - 购买金额：同原来已购买债权的购买金额
   - 转让收益：同账户总览页定义
   - 未来还款：新增“备注”，合并原有“还款笔数”和“详情”
```java
getObligationList();
```
* Account Management 
 1. 账户管理-个人信息类接口
  * API
   - QQ
   - 所在城市
   - 月收入
   - 最高学历
   - 毕业院校
   - 婚姻状况
   - 所在行业：
  * Dependency
   已登录
  * 获取用户详情
```java
User getUserDetail();
```
  * 更新用户详情
```java
void doUpdateUserInfo();
```
 2. 账户管理-认证类接口
  * Dependency
   已登录
  * 实名认证
```java
void doRealNameAuthenticate();
```
  * 手机认证
```java
void doMobileAuthenticate();
```
  * 邮箱认证
```java
void doEmailAuthenticate();
```
  * 交易密码认证
```java
void doTransactPassAuthenticate();
```
 3. 账户管理-银行卡类接口
```java
void doBankCardAuthenticate();
```
