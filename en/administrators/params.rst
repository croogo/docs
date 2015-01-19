.. _parameters:

Parameters
==========

In many some administration page, you will notice a `Params` field where you
can enter parameters. Theses fields expects a key/value pair using equal sign
as a separator per line::

    my_param_key=value_here
    another_key=another_value

For example, the above parameters when applied to a menu will be included in
the query result as follows::

    array(
        'Menu' => array(
            'id' => '3',
            'title' => 'Main Menu',
            'alias' => 'main',
            'params' => 'my_param_key=value_here\nanother_key=another_value',
        ),
        'Params' => array(
            'my_param_key' => 'value_here',
            'another_key' => 'another_value'
        )
    )

The code responsible for this functionality is `ParamsBehavior <http://github.com/croogo/croogo/blob/master/Croogo/Model/Behavior/ParamsBehavior.php>`_.
