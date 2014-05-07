lazyxml
=======

.. image:: https://pypip.in/version/lazyxml/badge.png
    :target: https://pypi.python.org/pypi/lazyxml
    :alt: Latest Version
.. image:: http://b.repl.ca/v1/License-MIT-blue.png
    :target: https://pypi.python.org/pypi/lazyxml
    :alt: License
.. image:: https://pypip.in/download/lazyxml/badge.png?period=day
    :target: https://pypi.python.org/pypi/lazyxml
    :alt: Downloads
.. image:: https://pypip.in/download/lazyxml/badge.png?period=week
    :target: https://pypi.python.org/pypi/lazyxml
    :alt: Downloads
.. image:: https://pypip.in/download/lazyxml/badge.png?period=month
    :target: https://pypi.python.org/pypi/lazyxml
    :alt: Downloads

简单的xml解析/生成库. 类似于simplejson的用法.

使用示例
--------

* xml转换成python对象

.. code-block:: python

    >>> import lazyxml
    >>> xml = '<demo><foo>foo</foo><bar>bar</bar></demo>'
    >>> lazyxml.loads(xml)
    {'bar': 'bar', 'foo': 'foo'}
    >>> lazyxml.loads(xml, strip_root=False)
    {'demo': {'bar': 'bar', 'foo': 'foo'}}
    >>> xml = '<demo><foo>foo</foo><bar>1</bar><bar>2</bar></demo>'
    >>> lazyxml.loads(xml)
    {'bar': ['1', '2'], 'foo': 'foo'}

* python对象转换成xml

.. code-block:: python

    >>> data = {'demo':{'bar': ['1', '2'], 'foo': '<foo>'}}
    >>> lazyxml.dumps(data)
    '<?xml version="1.0" encoding="utf-8"?><demo><foo><![CDATA[<foo>]]></foo><bar><![CDATA[1]]></bar><bar><![CDATA[2]]></bar></demo>'
    >>> lazyxml.dumps(data, cdata=False)
    '<?xml version="1.0" encoding="utf-8"?><demo><foo>&lt;foo&gt;</foo><bar>1</bar><bar>2</bar></demo>'
    >>> print lazyxml.dumps(data, indent=' ' * 4)
    <?xml version="1.0" encoding="utf-8"?>
    <demo>
        <foo><![CDATA[<foo>]]></foo>
        <bar><![CDATA[1]]></bar>
        <bar><![CDATA[2]]></bar>
    </demo>

* 详细用法参见 `demo <https://github.com/heronotears/lazyxml/tree/master/demo>`_