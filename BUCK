# Root BUCK file
load("@prelude//java:java.bzl", "java_binary", "java_test")

# Define the main application target
java_binary(
    name = "spring-harness-demo",
    srcs = glob(["java-app/src/main/java/**/*.java"]),
    deps = [
        "//java-app:spring-boot",
    ],
    main_class = "com.example.demo.DemoApplication",
    visibility = ["PUBLIC"],
)

# Test target
java_test(
    name = "test",
    srcs = glob(["java-app/src/test/java/**/*.java"]),
    deps = [
        ":spring-harness-demo",
        "//java-app:spring-boot-test",
    ],
    visibility = ["PUBLIC"],
)
