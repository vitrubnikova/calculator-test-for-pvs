# Инструкция по сборке и запуску Docker-образа 

**Предустановки**

- [Docker](https://docs.docker.com/engine/install/)
- открыто приложение Docker Desktop либо терминал с установленным Docker Engine (если через терминал - тогда можно начинать с шага 2)

**Шаги**

1. Клик на "*Terminal*" в правом нижнем углу
2. Выполнить команду `docker build -t calc .`
3. Выполнить команду `docker run --name calc calc`

# Как запустить Jenkins и выполнить pipeline

**Предустановки**

- [JDK](https://www.oracle.com/java/technologies/downloads/#java21) (подойдет версия 21)
- [Jenkins](https://www.jenkins.io/doc/book/installing/) (следовать инструкции)
- запущен Docker

**Шаги**

1. Открыть браузер
2. В адресную строку ввести *localhost* (указать порт, который был настроен при установке)
3. Ховер на имя нужного пайплайна
4. Клик на появившийся значок выпадающего списка
5. Клик на кнопку "*Собрать сейчас*"
