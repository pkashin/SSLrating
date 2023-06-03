![version](https://img.shields.io/badge/version-1.0.1-brightgreen?style=plastic)
![GitHub](https://img.shields.io/github/license/pkashin/sslRating?style=plastic)
![Traefik](https://img.shields.io/badge/Traefik-2.10.1-blue?style=plastic)
![NextJS](https://img.shields.io/badge/Next.js-13.4.4-blue?style=plastic)
## 🏆 Получение рейтинга A+ в SSL Labs используя Traefik и Let's Encrypt

> Репозиторий создан для поддержания актуальной конфигурации SSL-сервера использующего Traefik с точки зрения развертывания защищенного сайта или веб-приложения. Рассматривается минимально возможная настройка Traefik (используются бесплатные сертификаты Let's Encrypt) для получения наивысшей оценки по данным тестирования [SSL Labs](https://www.ssllabs.com/ssltest/). В дальнейшем планируется расширить область тестирования с помощью [The Mozilla Observatory](https://observatory.mozilla.org/) и других сервисов.

<img src="misc/images/ratingSslLabs.png" alt="Rating" style="display: block; width: 100%; height: auto; max-width: 990px; margin: 0 auto">

## 💻 Как использовать

1. Клонировать репозиторий на ваш сервер:
```bash
git clone https://github.com/pkashin/sslRating.git
```

2. Создайте DNS-записи для вашего доменного имени (например `example.com`) и поддомена `traefik.example.com` для отображения панели мониторинга Traefik. В качестве значений указать IP-адрес вашего сервера, на котором будет развернут Traefik.

3. Открыть файл `.env.example` и изменить переменные окружения вашими реальными данными. Переименовать и сохранить файл `.env.example` в `.env`.
   - `ACME_EMAIL` - адрес электронной почты, который будет использован для регистрации сертификата.
   - `DOMAIN` - доменное имя, для которого будет выпущен сертификат.
```ini
# .env.example
ACME_EMAIL=email@example.com
DOMAIN=example.com
```

4. Перейти в директорию `sslRating` и запустить контейнеры:
```bash
cd sslRating/
docker-compose up -d
```

5. Сертификаты сформируются в файле `/sslRating/traefik/acme/acme.json`.

6. Перейти на сайт [SSL Labs](https://www.ssllabs.com/ssltest/) и ввести доменное имя, которое необходимо протестировать. Нажать кнопку `Submit`.

<img src="misc/images/SslServerTest.png" alt="SslServerTest" style="display: block; width: 100%; height: auto; max-width: 990px; margin: 0 auto">
