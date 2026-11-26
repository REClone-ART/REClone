
add_executable(reclone_cli
    main.cpp
)

target_compile_features(reclone_cli
    PRIVATE
        cxx_std_20
)

set_target_properties(reclone_cli PROPERTIES
    OUTPUT_NAME "reclone"
)
