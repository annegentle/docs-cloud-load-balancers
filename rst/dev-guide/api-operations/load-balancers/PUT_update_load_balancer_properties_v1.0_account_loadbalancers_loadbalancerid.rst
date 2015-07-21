=============================================================================
Update Load Balancer Properties -  Rackspace Cloud Load Balancers Developer Guide
=============================================================================

Update Load Balancer Properties
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <PUT_update_load_balancer_properties_v1.0_account_loadbalancers_loadbalancerid_.rst#request>`__
`Response <PUT_update_load_balancer_properties_v1.0_account_loadbalancers_loadbalancerid_.rst#response>`__

.. code-block:: javascript

    PUT /v1.0/{account}/loadbalancers/{loadBalancerId}

Updates the properties for a specified load balancer.

This operation asynchronously updates the attributes for a specified load balancer. Upon successful validation of the request, the service returns a 202 (Accepted) response code. A caller can poll the load balancer with its ID to wait for the changes to be applied and the load balancer to return to an ``ACTIVE`` status.

The load balancer's ID and status are immutable attributes and cannot be modified by the caller. Supplying an unsupported attribute results in a 400 (badRequest) fault.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|202                       |                         |                         |
+--------------------------+-------------------------+-------------------------+
|400 500                   |                         |                         |
+--------------------------+-------------------------+-------------------------+
|503                       |                         |                         |
+--------------------------+-------------------------+-------------------------+
|400                       |                         |                         |
+--------------------------+-------------------------+-------------------------+
|401                       |                         |                         |
+--------------------------+-------------------------+-------------------------+
|413                       |                         |                         |
+--------------------------+-------------------------+-------------------------+
|404                       |                         |                         |
+--------------------------+-------------------------+-------------------------+


Request
^^^^^^^^^^^^^^^^^

This table shows the URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|{account}                 |xsd:string               |The ID for the tenant or |
|                          |                         |account in a multi-      |
|                          |                         |tenancy cloud.           |
+--------------------------+-------------------------+-------------------------+
|{loadBalancerId}          |xsd:string *(Required)*  |The ID for the load      |
|                          |                         |balancer.                |
+--------------------------+-------------------------+-------------------------+





This table shows the body parameters for the request:

+--------------------+-------------------+-------------------------------------+
|Name                |Type               |Description                          |
+====================+===================+=====================================+
|name                |xsd:string         |Name of the load balancer to update. |
|                    |*(Required)*       |The name must be 128 characters or   |
|                    |                   |fewer in length, and all UTF-8       |
|                    |                   |characters are valid. See            |
|                    |                   |`http://www.utf8-chartable.de/       |
|                    |                   |<http://www.utf8-chartable.de/>`__   |
|                    |                   |for information about the UTF-8      |
|                    |                   |character set.                       |
+--------------------+-------------------+-------------------------------------+
|protocol            |xsd:string         |Protocol of the service that is      |
|                    |*(Required)*       |being load balanced.                 |
+--------------------+-------------------+-------------------------------------+
|halfClosed          |xsd:boolean        |Enables or disables Half-Closed      |
|                    |*(Required)*       |support for the load balancer. Half- |
|                    |                   |Closed support provides the ability  |
|                    |                   |for one end of the connection to     |
|                    |                   |terminate its output, while still    |
|                    |                   |receiving data from the other end.   |
|                    |                   |Only available for                   |
|                    |                   |TCP/TCP_CLIENT_FIRST protocols.      |
+--------------------+-------------------+-------------------------------------+
|algorithm           |xsd:string         |Algorithm that defines how traffic   |
|                    |*(Required)*       |should be directed between back-end  |
|                    |                   |nodes.                               |
+--------------------+-------------------+-------------------------------------+
|port                |xsd:string         |Port number for the service you are  |
|                    |*(Required)*       |load balancing.                      |
+--------------------+-------------------+-------------------------------------+
|timeout             |xsd:string         |The timeout value for the load       |
|                    |*(Required)*       |balancer and communications with its |
|                    |                   |nodes. Defaults to 30 seconds with a |
|                    |                   |maximum of 120 seconds.              |
+--------------------+-------------------+-------------------------------------+
|httpsRedirect       |xsd:boolean        |Enables or disables HTTP to HTTPS    |
|                    |*(Required)*       |redirection for the load balancer.   |
|                    |                   |When enabled, any HTTP request       |
|                    |                   |returns status code 301 (Moved       |
|                    |                   |Permanently), and the requester is   |
|                    |                   |redirected to the requested URL via  |
|                    |                   |the HTTPS protocol on port 443. For  |
|                    |                   |example,                             |
|                    |                   |`http://example.com/page.html        |
|                    |                   |<http://example.com/page.html>`__    |
|                    |                   |would be redirected to               |
|                    |                   |`https://example.com/page.html       |
|                    |                   |<https://example.com/page.html>`__.  |
|                    |                   |Only available for HTTPS protocol (  |
|                    |                   |``port=443`` ), or HTTP protocol     |
|                    |                   |with a properly configured SSL       |
|                    |                   |termination (                        |
|                    |                   |``secureTrafficOnly=true``,          |
|                    |                   |``securePort=443`` ).                |
+--------------------+-------------------+-------------------------------------+





**Example Update Load Balancer Properties: JSON request**


.. code::

    {"loadBalancer":{
        "name": "sample-loadbalancer",
        "algorithm": "RANDOM",
        "protocol": "HTTP",
        "port": 80,
        "timeout": 60,
        "connectionLogging": true,
        "httpsRedirect": true
        }
    }


**Example Update Load Balancer Properties: XML request**


.. code::

    <loadBalancer xmlns="http://docs.openstack.org/loadbalancers/api/v1.0"
        name="sample-loadbalancer"
        algorithm="RANDOM"
        protocol="HTTP"
        port="80"
        timeout="60"
        connectionLogging="true"
        httpsRedirect="true"/>


Response
^^^^^^^^^^^^^^^^^^




