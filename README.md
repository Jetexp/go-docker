<div align="center">
  <img width="686" height="439" src="https://github.com/goavengers/go-docker/blob/master/img/go-docker.png">
  <h1>Go :heart: Docker</h1>
  <h5>Вместе мы разберемся!</h5>
</div>

## Содержание

1. [Вступление](#1)
2. [Концепции, идея](#2)
    1. [Идея](#2.1)
    2. [Концепции](#2.2)
        1. [Виртуальные машины](#2.2.1)
        2. [Образ контейнера Docker](#2.2.2)
        3. [Файл Dockerfile](#2.2.3)
        4. [Контейнер Docker](#2.2.4)
        5. [Репозиторий контейнеров](#2.2.6)

### <a name="1"></a>  Вступление

Технологии контейнеризации приложений нашли широкое применение в сферах разработки ПО и анализа данных. Эти технологии помогают сделать приложения более безопасными, облегчают их развёртывание и улучшают возможности по их масштабированию. Рост и развитие технологий контейнеризации можно считать одним из важнейших трендов современности.

__Docker__ — это платформа, которая предназначена для разработки, развёртывания и запуска приложений в контейнерах. Слово «Docker» в последнее время стало чем-то вроде синонима слова «контейнеризация». И если вы ещё не пользуетесь Docker, но при этом работаете или собираетесь работать в сферах разработки приложений или анализа данных, то Docker — это то, с чем вы непременно встретитесь в будущем.

### <a name="2"></a> Концепции, идея

#### <a name="2.1"></a> Идея

Как вы понимаете, мы собираемся начать разговор о Docker с понятия «контейнер».

Как и обычный пластиковый контейнер, контейнер Docker обладает следующими характеристиками:

1. В нём можно что-то хранить. Нечто может находиться либо в контейнере, либо за его пределами.
2. Его можно переносить. Контейнер Docker можно использовать на локальном компьютере, на компьютере коллеги, на сервере поставщика облачных услуг (вроде AWS). Это роднит контейнеры Docker с обычными контейнерами, в которых, например, перевозят разные милые сердцу безделушки при переезде в новый дом.
3. В контейнер удобно что-то класть и удобно что-то из него вынимать. У обычного контейнера есть крышка на защёлках, которую надо снять для того, чтобы что-то положить в контейнер или что-то из него вынуть. У контейнеров Docker есть нечто подобное, представляющее их интерфейс, то есть — механизмы, позволяющие им взаимодействовать с внешним миром. Например, у контейнера есть порты, которые можно открывать для того, чтобы к приложению, работающему в контейнере, можно было бы обращаться из браузера. Работать с контейнером можно и средствами командной строки.
4. Если вам нужен контейнер, его можно заказать в интернет-магазине. Пустой контейнер можно купить, например, на сайте Amazon. В этот магазин контейнеры попадают от производителей, которые делают их в огромных количествах, используя пресс-формы. В случае с контейнерами Docker то, что можно сравнить с пресс-формой, а именно — образ контейнера, хранится в специальном репозитории. Если вам нужен некий контейнер, вы можете загрузить из репозитория соответствующий образ, и, используя его, этот контейнер создать.

Конечно, пластиковые контейнеры, в отличие от контейнеров Docker, никто вам не будет присылать бесплатно, да и когда вы их получите, они будут пустыми. А вот в контейнерах Docker всегда есть что-то интересное.

Контейнеры Docker можно сравнивать не только с обычными контейнерами или с живыми организмами. Их можно сравнить и с программами. В конце концов, контейнеры — это программы. И, на фундаментальном уровне, контейнер представляет собой набор инструкций, который выполняется на некоем процессоре, обрабатывая какие-то данные.

> Контейнер — это программа

Во время выполнения контейнера Docker внутри него обычно выполняется какая-то программа. Она выполняет в контейнере некие действия, то есть — делает что-то полезное.

Например, код, который работает в контейнере Docker, возможно, отправил на ваш компьютер тот текст, который вы сейчас читаете. Вполне возможно и то, что именно код, выполняющийся в контейнере Docker, принимает голосовые команды, которые вы даёте Amazon Alexa, и преобразует их в инструкции для ещё каких-нибудь программ, работающих в других контейнерах.

Благодаря использованию Docker можно, на одном и том же компьютере, одновременно запускать множество контейнеров. И, как и любые другие программы, контейнеры Docker можно запускать, останавливать, удалять. Можно исследовать их содержимое и создавать их.

#### <a name="2.2"></a> Концепции

<a name="2.2.1"></a> **Виртуальные машины**

Предшественниками контейнеров Docker были виртуальные машины. Виртуальная машина, как и контейнер, изолирует от внешней среды приложение и его зависимости. Однако контейнеры Docker обладают преимуществами перед виртуальными машинами. Так, они потребляют меньше ресурсов, их очень легко переносить, они быстрее запускаются и приходят в работоспособное состояние. В этом материале можно найти подробное сравнение контейнеров и виртуальных машин.

<a name="2.2.2"></a> **Образ контейнера Docker**

Выше мы уже говорили об «образах». Что это такое? Хороший вопрос. То, что в терминологии Docker называется «образом», или, по-английски, «image», это совсем не то же самое, что, например, фотография (это — одно из значений слова «image»).

> Образы Docker — это не фотографии

Образы контейнеров Docker можно сравнить с чертежами, с формочками для печенья, или с пресс-формами для изготовления пластиковых изделий. Образы — это неизменные шаблоны, которые используются для создания одинаковых контейнеров.

В образе контейнера Docker содержится образ базовой операционной системы, код приложения, библиотеки, от которого оно зависит. Всё это скомпоновано в виде единой сущности, на основе которой можно создать контейнер.

<a name="2.2.3"></a> **Файл Dockerfile**

Файл Dockerfile содержит набор инструкций, следуя которым Docker будет собирать образ контейнера. Этот файл содержит описание базового образа, который будет представлять собой исходный слой образа. Среди популярных официальных базовых образов можно отметить python, ubuntu, alpine.

В образ контейнера, поверх базового образа, можно добавлять дополнительные слои. Делается это в соответствии с инструкциями из **Dockerfile**. Например, если Dockerfile описывает образ, который планируется использовать для решения задач машинного обучения, то в нём могут быть инструкции для включения в промежуточный слой такого образа библиотек __NumPy__, __Pandas__ и __Scikit-learn__.

И, наконец, в образе может содержаться, поверх всех остальных, ещё один тонкий слой, данные, хранящиеся в котором, поддаются изменению. Это — небольшой по объёму слой, содержащий программу, которую планируется запускать в контейнере.

<a name="2.2.4"></a> **Контейнер Docker**

Для того чтобы запустить контейнер, нам нужен, во-первых, образ контейнера, во-вторых — среда, в которой установлен Docker, способная понять команду вида `docker run image_name`. Эта команда создаёт контейнер из образа и запускает его.

<a name="2.2.5"></a> **Репозиторий контейнеров**

Если вы хотите дать возможность другим людям создавать контейнеры на основе вашего образа, вы можете отправить этот образ в облачное хранилище. Самым крупным подобным хранилищем является репозиторий [Docker Hub](https://hub.docker.com/). Он используется при работе с Docker по умолчанию.

Мы уже довольно много всего обсудили. Пришло время собрать всё это вместе и сравнить работу с контейнерами Docker с приготовлением пиццы.
