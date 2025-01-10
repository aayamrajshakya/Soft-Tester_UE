.. note:: 

    Soft-Tester UE is designed to run on Ubuntu and is tested on Ubuntu 24.04.


============
Installation
============

Build Tools and Dependencies
----------------------------

The Soft-Tester UE system has the following necessary dpendencies. Please install them beforehand.

    - `Docker <https://docs.docker.com/engine/install/ubuntu/>`_
    - `pip <https://pip.pypa.io/en/stable/installation/>`_
    - `venv <https://pypi.org/project/virtualenv/>`_


UE side (Machine A)
-------------------

Clone Soft-Tester UE repository:

.. code-block:: bash

   git clone https://github.com/oran-testing/soft-t-ue && git submodule update --init --recursive

To build the UE controller and webGUI, run:

.. code-block:: bash

   cd soft-t-ue/docker
   sudo docker compose build controller webui  --no-cache

gNB side (Machine B)
--------------------

Clone Soft-Tester UE repository and srsRAN Project separately:

.. note:: 

    Please refer to the official installation guide for `srsRAN Project <https://docs.srsran.com/projects/project/en/latest/user_manuals/source/installation.html>`_ .

.. code-block:: bash

   git clone https://github.com/oran-testing/soft-t-ue && git submodule update --init --recursive
   git clone https://github.com/srsran/srsRAN_Project


Install dockerized Open5GS:

.. code-block:: bash

   cd srsRAN_Project/docker
   sudo systemctl restart docker
   sudo docker compose build 5gc

Running
#######

.. warning::
    Always begin the experiment with UE first, otherwise, the connection will fail.

UE side (Machine A):
-------------------

To run the UE with controller and webGUI:

.. code-block:: bash

   cd soft-t-ue/docker
   sudo docker compose up controller webui

To see the metrics, open `http://localhost:3000/ <http://localhost:3000/>`_ in the browser.


gNB side (Machine B):
--------------------

To run the Open5GS:

.. code-block:: bash

   cd srsRAN_Project/docker
   sudo docker compose up 5gc


To run the gNB:

.. code-block:: bash

   sudo gnb -c ./soft-t-ue/configs/zmq/gnb_zmq_docker.yaml

.. note:: 

   If running with ZMQ, use either `gnb_zmq_docker.yaml` or `gnb_zmq.yaml`. Otherwise, use `.../uhd/gnb_uhd.yaml`.

Once the connection establishes, you can check the webGUI localhost interface to collect the logs.
