# Copyright: (C) 2010 RobotCub Consortium
# Authors: Lorenzo Natale
# CopyPolicy: Released under the terms of the GNU GPL v2.0.

yarp_prepare_plugin(socketcan
    CATEGORY device
    TYPE yarp::dev::SocketCan
    INCLUDE SocketCan.h 
    EXTRA_CONFIG WRAPPER=controlboard)

IF (NOT SKIP_socketcan)
 
    if (WIN32)
		MESSAGE("socketcan: sorry not available in windows. Turn off the device.") 
    ELSE(WIN32) 
	    INCLUDE_DIRECTORIES(${CMAKE_CURRENT_SOURCE_DIR} ${YARP_INCLUDE_DIRS})
	    yarp_add_plugin(socketcan SocketCan.cpp SocketCan.h)
	    TARGET_LINK_LIBRARIES(socketcan ${YARP_LIBRARIES})   
	    icub_export_plugin(socketcan)
       yarp_install(FILES socketcan.ini  DESTINATION ${ICUB_PLUGIN_MANIFESTS_INSTALL_DIR})
    ENDIF(WIN32)

ENDIF (NOT SKIP_socketcan)
