#-----------------------------------------------------------------------------
#
#  CMake Config
#
#  OSMCoastline
#
#-----------------------------------------------------------------------------

add_executable(osmcoastline osmcoastline.cpp coastline_ring.cpp coastline_ring_collection.cpp coastline_polygons.cpp output_database.cpp srs.cpp options.cpp)
target_link_libraries(osmcoastline ${OSMIUM_IO_LIBRARIES} ${GDAL_LIBRARIES} ${GEOS_C_LIBRARIES} ${GETOPT_LIBRARY})
set_pthread_on_target(osmcoastline)
install(TARGETS osmcoastline DESTINATION bin)

add_executable(osmcoastline_filter osmcoastline_filter.cpp)
target_link_libraries(osmcoastline_filter ${OSMIUM_IO_LIBRARIES} ${GETOPT_LIBRARY})
set_pthread_on_target(osmcoastline_filter)
install(TARGETS osmcoastline_filter DESTINATION bin)

add_executable(osmcoastline_segments osmcoastline_segments.cpp srs.cpp)
target_link_libraries(osmcoastline_segments ${GDAL_LIBRARIES} ${GETOPT_LIBRARY})
install(TARGETS osmcoastline_segments DESTINATION bin)

add_executable(osmcoastline_ways osmcoastline_ways.cpp return_codes.hpp)
target_link_libraries(osmcoastline_ways ${OSMIUM_IO_LIBRARIES} ${GDAL_LIBRARIES})
set_pthread_on_target(osmcoastline_ways)
install(TARGETS osmcoastline_ways DESTINATION bin)

