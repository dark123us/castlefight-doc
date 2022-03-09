Относительный путь lua
======================

.. code:: lua

    local CURPATH = debug.getinfo(1,"S").source:match[[^@scripts\vscripts?(.*[\/])[^\/]-$]]
    local logging = require(CURPATH .. "logging.logging")

