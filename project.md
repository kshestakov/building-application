# Проект

Нужно разработать приложение для публикации текстов.
Приложение должно реализовывать следующие сценарии(usecases):

+ регистрация пользователя
+ вход в систему
+ выход из системы
+ создание поста
+ редактирование поста
+ удаление поста
+ отображение поста
+ отображение списка всех постов

На старте проекта мы должны решить,какой язык программирования испльзовать.
В нашем случае это Clojure.

Заказчик еще не определился, как это приложение будет доставляться пользователям.
Будет ли это веб-приложение, мобильное приложение или одностраничное js приложение.

Мы ожидаем, что заказчик будет вносить изменения по ходу проекта.
Мы не хотим переделывать работу, поэтому будем реализовывать необходимый минимум и
откладывать принятие решений.

***

Чтобы реализовать задуманное мы будем строить проект на принципах Сlean Architecture:

+ [The Clean Architecture](https://8thlight.com/blog/uncle-bob/2012/08/13/the-clean-architecture.html)
+ [Architecture, Use Cases, and High Level Design](https://cleancoders.com/episode/clean-code-episode-7/show)
+ [Clean Architecture: A Craftsman's Guide to Software Structure and Design (Robert C. Martin Series)](https://www.amazon.com/Clean-Architecture-Craftsmans-Software-Structure/dp/0134494164)

<img src="https://raw.githubusercontent.com/darkleaf/building-application/master/img/clean_architecture.jpg" alt="Clean architecture">

Самый верхний слой - слой сущностей(entities) описывает самые общие бизнес-правила.
Если бы у нас не было компьютеров, бизнес все равно бы оперировал понятиями из этого слоя.
Т.е. вел бы бумажную картотеку пользователей и текстов.
Название entities в нашем случае довольно узко и вносит путаницу.
В дальнейшем я буду называть этот слой - слоем предметной области.

Следующий слой - слой сценариев использования описывают взаимодействие
пользователя с приложением.
В противоположность слою предметной области, зти бизнес-правила применимы
только в контексте компьютерной программы и не могут выполняться вручную,
т.е. связаны с автоматизацией.

Первые 2 слоя содержат бизнес правила - это и есть наше приложение.

Следующий слой - слой контроллеров, шлюзов, презентеров описывает способ
доставки приложения пользователю.

Clean architecture базируется на принципах SOLID, в особенности на принципе
инверсии зависимости(dependency inversion), с помощью которого пересекаются границы слоёв:

+ Модули верхних уровней не должны зависеть от модулей нижних уровней.
  Оба типа модулей должны зависеть от абстракций.
+ Абстракции не должны зависеть от деталей. Детали должны зависеть от абстракций.

Под модулями нижних уровней понимаются те, что расположены ближе к воводу/выводу.
Соответсвенно, модули верхних уровней расположены дальше от ввода/вывода.
Модули верхних уровней содержат бизнес-правила, которые не зависят от деталей реализации.

Подобно тому, как микросервисная архитектура разделяет труд разработчиков горизонтально,
Clean architecture способствует разделению труда по вертикали.
Т.е. для разработки модулей верхнего уровня(бизнес правил) не нужны сверхкомпетенции,
а разработка модулей нижнего уровня(детали) и проектирование абстракций
требуют глубоких знаний.
