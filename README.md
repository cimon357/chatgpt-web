luci-app-chatgpt - клиент ChatGPT в OpenWRT, для своей работы использует API OpenAI. Для использования нужен ключ (токен) API.
Исходная версия модуля: https://github.com/sirpdboy/chatgpt-web

Мной сделан перевод на русский язык:
- добавлен файл /chatgpt-web/po/ru-ru/chatgpt-web.po
- переведены строки в файле /chatgpt-web/luasrc/view/chatgpt-web.htm

Есть еще файлы с промптами (запросами)
	prompts-zh-TW.json
	prompts-zh.json
пока их оставлю так, как есть. 

Есть озвучка ответов. Как бы добавить поддержку русского языка?

Дальше перевод README на исходной странице проекта.

Связанные проекты: 
[markdown-it](https://github.com/markdown-it/markdown-it), 
[highlight.js](https://github.com/highlightjs/highlight.js), 
[github-markdown-css](https://github.com/sindresorhus/github-markdown-css), 
[chatgpt-html](https://github.com/slippersheepig/chatgpt-html), 
[markdown-it-copy](https://github.com/ReAlign/markdown-it-copy), 
[markdown-it-texmath](https://github.com/goessner/markdown-it-texmath), 
[awesome-chatgpt-prompts-zh](https://github.com/PlexPt/awesome-chatgpt-prompts-zh)


## Способ компиляции:

- Добавляем luci-app-chatgpt в исходники LEDE/OpenWRT.

### Загрузка исходного кода и настройка меню конфигурации:

	# git clone https://github.com/sirpdboy/chatgpt-web.git package/luci-app-chatgpt
	git clone https://github.com/cimon357/chatgpt-web.git package/luci-app-chatgpt
    	make menuconfig
	# Выбрать в меню конфигурации LuCI -> Applications, отметить luci-app-chatgpt, сохранить и выйти из меню.
 
### Компиляция:

     make package/luci-app-chatgpt/compile V=s
 
## Настройки модуля:

    - Откройте основные настройки luci-app-chatgpt, укажите ключ API, используемую модель ChatGPT, укажите интерфейс OpenAI, 
выберите аватарку пользователя и т.д. 
    
    - Необязательно. Укажите модель ChatGPT, 
по умолчанию используется gpt-3.5, а модель gpt-4 необходимо использовать через форму openai.
    
    - Интерфейс OpenAI обычно имеет локальный доступ к `api.openai.com`, укажите `https://api.openai.com/`.
    
    - Невозможно получить доступ к `api.openai.com` в обычном режиме, заполните его адрес антигенерации, обратите внимание: ответ интерфейса антигенерации должен добавить междоменный заголовок `Access-Control-Allow-Origin`.

    - Веб-страницу chatgpt можно использовать в обычном режиме. Если вам нужно установить дополнительные параметры, см. Пользовательские настройки для установки голосовых и системных ролей.
    
## Возможности модуля, параметры пользователя:

- Поддержка левой боковой панели, очистка диалогов, поиск в диалогах, создание/переименование/удаление (папок/диалогов), экспорт/импорт/сброс данных диалогов и настроек, локальное хранилище.

- Дополнительные системные роли, не включенные по умолчанию. 
Есть четыре предустановленных роли, другие роли будут добавлены позже.
Четыре предустановленные роли: помощник, девочка-кошка, эмодзи, образ (роль). 

- 可选角色性格，默认灵活创新，对应接口文档的top_p参数。

- 可选回答质量，默认平衡，对应接口文档的temperature参数。

- Настройка скорости вывода ответа, по умолчанию - быстро. Чем больше значение, тем выше скорость.

- Режим непрерывного диалога включен по умолчанию. В диалог включается контекстная информация, что приводит к увеличению затрат на API.

- Можно включить получение развернутого ответа ChatGPT (по умолчанию отключено). 
После включения плата за API может увеличиться и большая часть контекста может быть утрачена. 

- Можно выбрать голос для озвучки ответов ChatGPT. По умолчанию это голос Bing. Поддерживаются Azure и голос, использующийся в вашей системе. Вы можете установить разные голоса для озвучки вопросов и ответов.

- 音量，默认最大。

- 语速，默认正常。

- 音调，默认正常。

- 允许连续朗读，默认开启，连续郎读到所有对话结束。

- 允许自动朗读，默认关闭，自动朗读新的回答。**（iOS需打开设置-自动播放视频预览，Mac上Safari需打开此网站的设置-允许全部自动播放）**

- 支持语音输入，默认识别为普通话，可长按语音按钮修改识别选项。**语音识别必需条件：使用chrome内核系浏览器 + https网页或本地网页。** 如点击语音按钮没反应，可能是未授予麦克风权限或者没安装麦克风设备。

## Скриншоты интерфейса:

![screenshots](https://raw.githubusercontent.com/sirpdboy/openwrt/master/doc/chatgpd1.png)

![screenshots](https://raw.githubusercontent.com/sirpdboy/openwrt/master/doc/chatgpd2.png)

![screenshots](https://raw.githubusercontent.com/sirpdboy/openwrt/master/doc/chatgpd3.png)

## Использование этого модуля:
 
- Вы можете использовать исходный код, но, пожалуйста, укажите источник: https://github.com/sirpdboy/chatgpt-web
Использование в коммерческих целях без разрешения автора запрещено.

На странице https://github.com/sirpdboy/chatgpt-web можно найти ссылки на другие интересные авторские проекты для OpenWrt.
