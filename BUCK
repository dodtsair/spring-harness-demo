# Root BUCK file for the project


# Root BUCK file for the project

genrule(
    name = "root",
    out = "dist",
    cmd = """
        # 1. Create the output directory structure
        mkdir -p $OUT/bin
        mkdir -p $OUT/reports/tests 

        # 2. Reference the java-app output from the 'buck' cell
        # Copy the JAR
        find $(location buck//java-app:gradle-build)/libs -maxdepth 1 -type f -name "*.jar" ! -name "*-plain.jar" -exec cp {} $OUT/bin/spring-harness-demo.jar \\;
        
        # Copy test results
        cp -R $(location buck//java-app:gradle-build)/reports/. $OUT/reports/
        cp -R $(location buck//java-app:gradle-build)/test-results/. $OUT/reports/tests/
    """,
    visibility = ["//..."],
)

# This single rule "claims" everything in the repo 
# and makes it available to the 'buck' cell.
# filegroup(
#     name = "all_sources",
#     srcs = [
#         "java-app/gradlew",
#         "java-app/gradle/wrapper/gradle-wrapper.jar",
#         "java-app/gradle/wrapper/gradle-wrapper.properties",
#         "java-app/build.gradle",
#         "java-app/settings.gradle",
#     ] + glob(["java-app/src/**/*"]),
#     visibility = ["buck//..."],
# )

filegroup(
    name = "all_sources",
    srcs = (
        glob(
            ["**/*"], 
            exclude = [
                ".buck/**", 
                ".git/**", 
                "buck-out/**", 
                ".gradle/**", 
                "build/**",
                "**/BUCK", # Often helpful to exclude BUCK files themselves
            ]
        )
    ),
    visibility = ["buck//..."],
)