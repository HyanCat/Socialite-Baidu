# Socialite-Baidu
百度 OAuth2 账号连接 for Laravel 5.x.

## Installation

1. 安装 composer package:

		composer require hyancat/socialite-baidu

2. config/app.php 中 `Laravel\Socialite\SocialiteServiceProvider` 替换成 `SocialiteProviders\Manager\ServiceProvider`

3. `app/Providers/EventServiceProvider.php` 中添加一个监听器：`SocialiteProviders\Manager\SocialiteWasCalled`，如果已存在则忽略；并添加监听响应事件：`Hyancat\SocialiteBaidu\BaiduExtendSocialite@handle`

	```
	'SocialiteProviders\Manager\SocialiteWasCalled' => [
		// ...
		'Hyancat\SocialiteBaidu\BaiduExtendSocialite@handle',
	],
	```

4. config/service.php 中添加一个配置项：

	```
	'baidu' => [
		'client_id'     => env('BAIDU_KEY'),
		'client_secret' => env('BAIDU_SECRET'),
		'redirect'      => env('BAIDU_REDIRECT_URL'),
	],
	```

## Usage

详见官方文档 [socialite](http://laravel.com/docs/5.1/authentication#social-authentication) 用法。


## License

MIT License.
