This is a fork of `os/slacker <https://github.com/os/slacker>`_
############################################################

It's only purpose is to allow `slack-export <https://github.com/jonpas/slack-export>`_ to function to a usable degree.

=======
Slacker
=======

|pypi|_
|build status|_
|pypi downloads|_
|license|_
|gitter chat|_

.. image:: https://raw.githubusercontent.com/os/slacker/master/static/slacker.jpg

About
=====

Slacker is a full-featured Python interface for the `Slack API
<https://api.slack.com/>`_.

Installation
============

.. code-block:: bash

    $ pip install slacker

Examples
========
.. code-block:: python

    from slacker import Slacker

    slack = Slacker('<your-slack-api-token-goes-here>')

    # Send a message to #general channel
    slack.chat.post_message('#general', 'Hello fellow slackers!')

    # Get users list
    response = slack.users.list()
    users = response.body['members']

    # Upload a file
    slack.files.upload('hello.txt')

    # If you need to proxy the requests
    proxy_endpoint = 'http://myproxy:3128'
    slack = Slacker('<your-slack-api-token-goes-here>',
                    http_proxy=proxy_endpoint,
                    https_proxy=proxy_endpoint)

    # Advanced: Use `request.Session` for connection pooling (reuse)
    from requests.sessions import Session
    with Session() as session:
        slack = Slacker(token, session=session)
        slack.chat.post_message('#general', 'All these requests')
        slack.chat.post_message('#general', 'go through')
        slack.chat.post_message('#general', 'a single https connection')


Documentation
=============

https://api.slack.com/methods


.. |build status| image:: https://img.shields.io/travis/os/slacker.svg
.. _build status: http://travis-ci.org/os/slacker
.. |pypi downloads| image:: https://img.shields.io/pypi/dm/slacker.svg
.. _pypi downloads: https://pypi.org/project/slacker/
.. |pypi| image:: https://img.shields.io/pypi/v/Slacker.svg
.. _pypi: https://pypi.python.org/pypi/slacker/
.. |license| image:: https://img.shields.io/github/license/os/slacker.svg
.. _license: https://pypi.org/project/slacker/
.. |gitter chat| image:: https://badges.gitter.im/Join%20Chat.svg
.. _gitter chat: https://gitter.im/os/slacker?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge
