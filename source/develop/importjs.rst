Js использование модулей
========================

Новые модули регистрируем в index.js, при этом имеет значение порядка 
загрузки.

.. code:: xml

   <scripts>
        <include src="file://{resources}/vendors/debug-dota/vendors/moment/moment.min.js" />
        <include src="file://{resources}/vendors/debug-dota/vendors/js-logger/logger.min.js" />
        <include src="file://{resources}/vendors/debug-dota/console.js" />
        <include src="file://{resources}/vendors/debug-dota/logging.js" />
        <include src="file://{resources}/script/ui.js" />
        <include src="file://{resources}/script/tooltip.js" />
        <include src="file://{resources}/script/rnd.js" />
        <include src="file://{resources}/script/index.js" />
    </scripts>

https://github.com/jonnyreeves/js-logger/blob/master/src/logger.js

.. code:: js

  (function (global) {
    "use strict";
    var Logger = {};

    // Export to popular environments boilerplate.
    if (typeof define === "function" && define.amd) {
      define(Logger);
    } else if (typeof module !== "undefined" && module.exports) {
      module.exports = Logger;
    } else {
      Logger._prevLogger = global.Logger;

      Logger.noConflict = function () {
        global.Logger = Logger._prevLogger;
        return Logger;
      };

      global.Logger = Logger;
    }
  })(this);

Boilerplates
------------

Без инициализации
+++++++++++++++++

.. code:: js

    (function (global) {
        const log = (...msgs) => {
            if (msgs.length == 1){
                $.Msg(msgs[0]);
            } else {
                $.Msg(msgs);
            }
        };

        const NAME = "console"
        const UNIT = {[NAME]: log}
        if (typeof define === "function" && define.amd) {
            define(UNIT[NAME]);
        } else if (typeof module !== "undefined" && module.exports) {
            module.exports = UNIT[NAME];
        } else {
            const prev = "_prev" + NAME
            UNIT[NAME][prev] = global[NAME];
            UNIT[NAME].noConflict = function () {
                global[NAME] = UNIT[NAME][prev];
                return UNIT[NAME];
            };
            global[NAME] = UNIT[NAME];
        }
    })(this)

можно сразу использовать аля

.. code:: js

    console.log(данные)

С инициализацией
----------------

перед использованием необходима инициализация

.. code:: js

    const boiler = boilerplate()


.. code:: js

    (function (global) {
        const unit = (...msgs) => {
            data = () => {}
            data.init = () => {
                console.log("init")
            }
            return data
        };

        const NAME = "boilerplate"
        const UNIT = {[NAME]: unit}
        if (typeof define === "function" && define.amd) {
            define(UNIT[NAME]);
        } else if (typeof module !== "undefined" && module.exports) {
            module.exports = UNIT[NAME];
        } else {
            const prev = "_prev" + NAME
            UNIT[NAME][prev] = global[NAME];
            UNIT[NAME].noConflict = function () {
                global[NAME] = UNIT[NAME][prev];
                return UNIT[NAME];
            };
            global[NAME] = UNIT[NAME];
        }
    })(this)

интересная фича, если после инициализации вывести дебаг можно увидеть
содержимое

.. code:: console

   log.debug(rnd())
   log.debug(rnd)

    [2022-03-07 13:03:17:903][DEBUG] () => {}   [(__root__)script\index.js:4]
    [2022-03-07 13:03:17:903][DEBUG] () => {
            const data = () => {}

            data.init = () => {
                // $.Msg("init");
                log.debug("init rnd")
            }
            return data;
        }                                       [(__root__)script\index.js:5]
