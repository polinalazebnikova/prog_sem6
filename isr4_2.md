venv
Создание виртуального окружения
Модуль, используемый для создания и управления виртуальными средами, называется venv (docs.python.org/3/library/venv.html#module-venv). Он обычно будет установлен большинством новых версий Python, которые вам доступны. Если вы имеете разные версии Python в вашей системы, то можете выбрать конкретную версию Python, выполнив команду python3 или какую версию захотите.

Чтобы создать виртуальную среду, выберите каталог для ее размещения и запустите модуль venv как скрипт с адресом директории:
```
python3 -m venv env
```
Это создаст каталог env, если он не существует, и также создаст директории внутри него, содержащие копию интерпретатора Python, стандартную библиотеку и различные вспомогательные файлы.

Создав виртуальную среду, вы можете ее активировать.

Активация виртуального окружения
В Windows командой:
```
env\Scripts\activate.bat
```
В Unix или MacOS:
```
source env/bin/activate
```
Управление пакетами с помощью pip

Можно устанавливать, обновлять и удалять пакеты, используя программу под названием pip. По умолчанию pip будет устанавливать пакеты из Индекса пакетов Python. Вы можете просматривать Python Packege Index с помощью браузера или можете использовать ограниченную функцию поиска pip:
```
skyfield               - Elegant astronomy for Python
gary                   - Galactic astronomy and gravitational dynamics.
novas                  - The United States Naval Observatory NOVAS astronomy library
astroobs               - Provides astronomy ephemeris to plan telescope observations
PyAstronomy            - A collection of astronomy related tools for Python.
...
```
У pip есть ряд подкоманд: "search", "install", "freeze" и др.

Можно установить последнюю версию пакета, указав его имя:
```
(env) $ pip install novas
```
```
Collecting novas
  Downloading novas-3.1.1.3.tar.gz (136kB)
Installing collected packages: novas
  Running setup.py install for novas
Successfully installed novas-3.1.1.3
```
Также можно установить конкретную версию пакета, задав имя пакета с последующим == и номером версии:
```
(env) $ pip install requests==2.6.0
```
```
Collecting requests==2.6.0
  Using cached requests-2.6.0-py2.py3-none-any.whl
Installing collected packages: requests
Successfully installed requests-2.6.0
```
Если перезапустить эту команду, pip заметит, что требуемая версия уже установлена и ничего не сделает. Вы можете указать другой номер версии, чтобы получить эту версию, или можете запустить pip install --upgrade для обновления пакета до последней версии:
```
(env) $ pip install --upgrade requests
```
```
Collecting requests
Installing collected packages: requests
  Found existing installation: requests 2.6.0
    Uninstalling requests-2.6.0:
      Successfully uninstalled requests-2.6.0
Successfully installed requests-2.7.0
```
pip uninstall с последующим одним или более именами пакетов удалит пакеты из виртуального окружения.

pip show выведет информацию о конкретном пакете:
```
(env) $ pip show requests
```
```
Metadata-Version: 2.0
Name: requests
Version: 2.7.0
Summary: Python HTTP for Humans.
Home-page: http://python-requests.org
Author: Kenneth Reitz
Author-email: me@kennethreitz.com
License: Apache 2.0
Location: /Users/akuchling/envs/tutorial-env/lib/python3.4/site-packages
Requires:
```
pip list выведет все пакеты, установленные в виртуальном окружении:
```
(env) $ pip list
novas (3.1.1.3)
numpy (1.9.2)
pip (7.0.3)
requests (2.7.0)
setuptools (16.0)
```
pip freeze произведет похожий список установленных пакетов, но вывод использует формат, который ожидает pip install. Общее соглашение состоит в том, чтобы поместить этот список в файл requirements.txt:
```
(env) $ pip freeze > requirements.txt
(env) $ cat requirements.txt
```
```
novas==3.1.1.3
numpy==1.9.2
requests==2.7.0
```
Затем файл requirements.txt может быть привязан к управлению версиями и отправлен как часть приложения. Потом пользователи могут установить все необходимые пакеты с помощью install -r.
```
(env) $ pip install -r requirements.txt
```
```
Collecting novas==3.1.1.3 (from -r requirements.txt (line 1))
  ...
Collecting numpy==1.9.2 (from -r requirements.txt (line 2))
  ...
Collecting requests==2.7.0 (from -r requirements.txt (line 3))
  ...
Installing collected packages: novas, numpy, requests
  Running setup.py install for novas
Successfully installed novas-3.1.1.3 numpy-1.9.2 requests-2.7.0
```
Деактивация:
```
(env) $ deactivate
```
