cmake_minimum_required(VERSION 3.13)
project(webrtc_raspberrypi_test)

set(CMAKE_CXX_STANDARD 20)

#add_executable(webrtc_raspberrypi_test send_only_unidirectional.cpp)
#add_executable(webrtc_raspberrypi_test send_recv.cpp)
#add_executable(webrtc_raspberrypi_test send_only_uni_ocv_mod_v1.cpp)
#add_executable(webrtc_raspberrypi_test data_probes_test_roi_copy_ocv_uni_webrtc.cpp)
#add_executable(webrtc_raspberrypi_test data_probes_test_roi_copy_ocv_uni_webrtc_gst_embedded.cpp)
add_executable(webrtc_raspberrypi_test data_probes_test_roi_copy_ocv_uni_webrtc_gst_embedded_test.cpp)
#add_executable(webrtc_raspberrypi_test
#add_executable(webrtc_raspberrypi_test

find_package(OpenCV REQUIRED)
include_directories(${OpenCV_INCLUDE_DIRS})
target_link_libraries(webrtc_raspberrypi_test ${OpenCV_LIBS})

find_package(PkgConfig)
if (PKG_CONFIG_FOUND)
    pkg_check_modules(GLIB "glib-2.0")
    if (GLIB_FOUND)
        target_link_libraries(webrtc_raspberrypi_test ${GLIB_LIBRARIES})
        add_definitions(${GLIB_CFLAGS} ${GLIB_CFLAGS_OTHER})
    endif()
endif()

find_package(PkgConfig)
if (PKG_CONFIG_FOUND)
    pkg_check_modules(GST "gstreamer-1.0")
    if (GST_FOUND)
        target_link_libraries(webrtc_raspberrypi_test ${GST_LIBRARIES})
        add_definitions(${GST_CFLAGS} ${GST_CFLAGS_OTHER})
    endif()
endif()

find_package(PkgConfig)
if (PKG_CONFIG_FOUND)
    pkg_check_modules(SPD "gstreamer-sdp-1.0")
    if (SPD_FOUND)
        target_link_libraries(webrtc_raspberrypi_test ${SPD_LIBRARIES})
        add_definitions(${SPD_CFLAGS} ${SPD_CFLAGS_OTHER})
    endif()
endif()

find_package(PkgConfig)
if (PKG_CONFIG_FOUND)
    pkg_check_modules(WEBRTC "gstreamer-webrtc-1.0")
    if (WEBRTC_FOUND)
        target_link_libraries(webrtc_raspberrypi_test ${WEBRTC_LIBRARIES})
        add_definitions(${WEBRTC_CFLAGS} ${WEBRTC_CFLAGS_OTHER})
    endif()
endif()

find_package(PkgConfig)
if (PKG_CONFIG_FOUND)
    pkg_check_modules(JSON "json-glib-1.0")
    if (JSON_FOUND)
        target_link_libraries(webrtc_raspberrypi_test ${JSON_LIBRARIES})
        add_definitions(${JSON_CFLAGS} ${JSON_CFLAGS_OTHER})
    endif()
endif()

find_package(PkgConfig)
if (PKG_CONFIG_FOUND)
    pkg_check_modules(SOUP "libsoup-2.4")
    if (SOUP_FOUND)
        target_link_libraries(webrtc_raspberrypi_test ${SOUP_LIBRARIES})
        add_definitions(${SOUP_CFLAGS} ${SOUP_CFLAGS_OTHER})
    endif()
endif()