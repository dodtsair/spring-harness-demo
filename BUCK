# BUCK at repo root

genrule(
    name = "root",
    # We define an output directory
    out = "dist", 
    cmd = """
        # Create the output directory structure
        mkdir -p $OUT/bin
        mkdir -p $OUT/reports

        # Copy the JAR file (referenced by its key in srcs)
        # location ... resolves the path to the target's output
        find $(location //java-app:gradle-all-in-one)/libs -maxdepth 1 -type f -name "*.jar" ! -name "*-plain.jar" \
            -exec cp {} $OUT/bin/spring-harness-demo.jar \\;
        # Copy the test results directory
        cp -R $(location //java-app:gradle-all-in-one)/reports/tests/test/. $OUT/reports/
    """,
    visibility = ["//..."],
)