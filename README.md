# wxpay
php版,修改了官方提供SDK

## 使用方法
> 1.   在[微信支付](http://pay.weixin.qq.com) 申请到了微信支付的商户号后,将商户号(appid),key配置到WxPay/WxPayConfig.php中,证书放到WxPay/cert目录下.
> 2.   在你的项目中引入WxPay/WxPayApi.php.

## 接口介绍
#### 三种支付方式,都有共同的调用接口流程,主要包括以下几种需要用到的请求接口
> 1.  统一下单
<pre class="brush: php;gutter: true">
<code>require_once '/WxPay/WxPayApi.php';  
$input = new \WxPayUnifiedOrder();  
$input->SetBody("test");  
$input->SetAttach("test");  
$input->SetOut_trade_no(\WxPayConfig::MCHID.date("YmdHis"));  
$input->SetTotal_fee("1");  
$input->SetTime_start(date("YmdHis"));  
$input->SetTime_expire(date("YmdHis", time() + 600));  
$input->SetGoods_tag("test");
//设置支付结果通知回调地址
$input->SetNotify_url("http://paysdk.weixin.qq.com/example/notify.php");  
$input->SetTrade_type("APP");  
$order = \WxPayApi::unifiedOrder($input);  
dump($order);</code>
</pre>
> 2.  查询订单  
  > WxPayApi::orderQuery  
> 3.  关闭订单  
  > WxPayApi::closeOrder  
> 4.  申请退款  
  > WxPayApi::refund  
> 5.  查询退款  
  > WxPayApi::refundQuery    
> 6.  下载对账单  
  > WxPayApi::downloadBill  
> 7.  支付结果通用通知  
  > WxPayApi::notify  
