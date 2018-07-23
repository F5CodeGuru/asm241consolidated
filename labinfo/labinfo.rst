Lab Environment & Tools
~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. WARNING:: All work for this lab will be performed exclusively from the Linux
   Jumphost/Client (client01). The client is accessed via RDP (Windows Remote Desktop) or ssh. No installation or interaction with your local system is
   required.

All pre-built environments implement the Lab Topology shown below.  Please
review the topology first, then find the section matching the lab environment
you are using for connection instructions.

Environment
-----------

Linux Client (Client01):

* Web Attack Tools:

 * `Burp Suite Community Edition <https://portswigger.net/burp>`_ - HTTP Request Manipulation
 * `iMacros <https://imacros.net/>`_ - Web Scraping
 * `ab (Apache Bench) <https://httpd.apache.org/docs/2.4/programs/ab.html>`_ - HTTP Load Testing

Kali Client (Kali-BaDOS):

 * `ab (Apache Bench) <https://httpd.apache.org/docs/2.4/programs/ab.html>`_ - HTTP Load Testing

Linux Server (Server01):

 * `WebGoat 8 <https://github.com/WebGoat/WebGoat/wiki>`_ - deliberately insecure application

LAMP Server (LAMPv4):

 * `Hackazon <https://github.com/rapid7/hackazon`_ - deliberately insecure application

BIG-IP (bigip01):

* Provisioned Software Modules
 
 * Local Traffic Manager
 * Application Security Manager


.. _lab-topology:

Lab Topology
------------

The network topology implemented for this lab is very simple, since the
focus of the lab is Control Plane programmability rather than Data Plane
traffic flow we can keep the data plane fairly simple. The following
components have been included in your lab environment:

-  1 x Ubuntu Linux 16.04 client - aptly named: client01
-  1 x F5 BIG-IP VE (v13.1.0.5) running ASM and LTM - aptly named: bigip01
-  1 x Ubuntu Linux 16.04 server - aptly named: server01 

.. nwdiag:: labtopology.diag
   :width: 800
   :caption: Lab Topology
   :name: lab-topology-diagram
   :scale: 110%

The following table lists VLANS, IP Addresses and Credentials for all
components:

.. list-table::
   :widths: 15 15 15 15 15 
   :header-rows: 1
   :stub-columns: 1


   * - **Component**
     - **mgmtnet IP**
     - **clientnet IP**
     - **servernet IP**
     - **Credentials**
   * - Linux Client (client01)
     - 10.1.1.51
     - 10.1.10.51
     - N/A
     - https-``f5student:f5DEMOs4u!``
   * - Bigip (bigip01)
     - 10.1.1.245
     - 10.1.10.245
     - 10.1.20.245
     - https - ``admin:f5DEMOs4u!`` ssh - ``f5student:f5DEMOs4u!``
   * - Linux Server (server01)
     - 10.1.1.252
     - N/A
     - 10.1.20.252
     - ssh - ``f5student:f5DEMOs4u!``
   * - Kali (Kali-BaDOS)
     - 10.1.1.245
     - 10.1.10.100 / 10.1.10.200
     - N/A
     - ssh - ``f5student:f5DEMOs4u!``
   * - Linux Server (LAMPv4)
     - 10.1.1.250
     - N/A
     - 10.1.20.250
     - N/A



A graphical representation of the lab:

.. image:: images/ASM241_2018LabDiagram.png

|

.. note:: 
        
        External links are not required reading for the lab, rather supplemental if you you would like to get a different take or additional info.

