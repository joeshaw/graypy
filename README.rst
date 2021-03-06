Installing
==========

Using easy_install::

   easy_install graypy

Usage
=====

Messages are sent to Graylog2 using a custom handler for the builtin logging library in GELF format::

    import logging
    import graypy

    my_logger = logging.getLogger('test_logger')
    my_logger.setLevel(logging.DEBUG)

    handler = graypy.GELFHandler('localhost', 12201)
    my_logger.addHandler(handler)

    my_logger.debug('Hello Graylog2.')

Tracebacks are added as full messages::

    import logging
    import graypy

    my_logger = logging.getLogger('test_logger')
    my_logger.setLevel(logging.DEBUG)

    handler = graypy.GELFHandler('localhost', 12201)
    my_logger.addHandler(handler)

    try:
        puff_the_magic_dragon()
    except NameError:
        my_logger.debug('No dragons here.', exc_info=1)

Custom fields
=============

A number of custom fields are automatically added if available:
    * function
    * pid
    * process_name
    * thread_name
