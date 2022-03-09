Event
=====

Система событий достаточно замороченная, поэтому привожу ее к более простому
виду. Подписка на все события в одном месте в index.js, затем в модули, 
которым нужна подписочная система прокидываем этот Event, к примеру в 
tooltip

.. code:: js

    const event = Event().init()
    const toolTip = ToolTip(event).init()

Затем просто подписываемся на события

.. code:: js

   const showid = Event.subscribe(
       'DOTAShowAbilityTooltipForEntityIndex',
       params => { log.debug(params) })

Отписаться

.. code:: js
       
    Event.unsubscribe(
        'DOTAShowAbilityTooltipForEntityIndex',
        showid)

