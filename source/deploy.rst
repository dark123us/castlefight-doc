Развертывание
=============

Запуск окружения
----------------

git
+++

git bash

.. code:: console

    $ cd /d/project/castlefight
    $ cd /d/project/castlefight/develop/submodules/ecs-dota
    $ cd /d/project/castlefight/develop/submodules/debug-dota
    $ cd /d/project/castlefight/develop/submodules/castlefight-doc

dota custom + tools
+++++++++++++++++++

командная строка

.. code:: console


   >d:
   >cd project\castlefight\deploy 
   >run-tools.bat

запуск кастомки, подсказка в выводе run-tools.bat

.. code:: console
    
    dota_launch_custom_game castlefight castle_story_1 jointeam good

устранение проблем с запуском sh файлов

.. code:: console

   $ vim run-doc.sh +"set ff=unix" +wq

ide
+++

Запуск

.. code:: console

    $ cd ~/projects/castlefight/deploy/
    $ bash run-ide.sh

Подключиться к запущенному сеансу

.. code:: console

    $ docker exec -it vim_ide-v1 bash

doc
+++

Путь к докам для редактирования

.. code:: console

   # su dark123us
   $ cd /home/dark123us/app/develop/submodules/castlefight-doc/source

сборка документации

.. code:: console

    $ cd ~/projects/castlefight/deploy/
    $ bash run-doc.sh

    # cd /docs
    # while true; do echo $(date); inotifywait -e modify -r ./source ; sleep 1; make html; done

Просмотр собранной документации

file:///D:/tmp/html/html/index.html

https://dark123us.github.io/castlefight-doc/index.html

https://caslefight-doc.readthedocs.io/en/latest/index.htmlt




