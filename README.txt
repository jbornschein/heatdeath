
 Overview
==========

This repository contains two watchdog deamons which monitor the 
temperature sensors on linux compute nodes and shutdown the
nodes if neccessary.

The goal is to prevent hardware damange in case the cooling system
within a datacenter facility fails.



heatdeath:
    Locally monitor the temperature sensors and shutdown if critical 
    temerature is surpassed.


heatdeath-master:
    Run this deamon on a master-node that uses collectd to gather
    system statistics from multiple nodes. This daemon reads current 
    temerature values from *.rrd files and uses ssh to shutdown an e
    ntire cluster if neccessary.



For maximal reliability run both daemons in parallel. Adjust critical temperatures
such that the heatdaeth-master daemon would shutdown the cluster in case of a cooling
failure. Only for the case that both the master-node is unreachable, the local 
daemons should individually trigger an emergency shutdown.



