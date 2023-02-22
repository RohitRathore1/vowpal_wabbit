## Exercise 1

For *Exercise 1*: Working with VW - The goal here was to compile VW source code and make a minor modification to it and see that the modification actually worked.  I added the code to VW itself that prints "Hello World" when it runs. 

The steps were following:

Step 1: Clone the VW repository from GitHub:
git clone https://github.com/VowpalWabbit/vowpal_wabbit.git

Step 2: Change the directory to the cloned repository and build the source code:

```
cd vowpal_wabbit

cmake -S . -B build -G Ninja \
    -DCMAKE_BUILD_TYPE:STRING="Release" \
    -DFMT_SYS_DEP:BOOL="ON" \
    -DRAPIDJSON_SYS_DEP:BOOL="ON" \
    -DSPDLOG_SYS_DEP:BOOL="ON" \
    -DVW_BOOST_MATH_SYS_DEP:BOOL="ON" \
    -DVW_GTEST_SYS_DEP:BOOL="ON" \
    -DVW_ZLIB_SYS_DEP:BOOL="ON" \
    -DBUILD_TESTING:BOOL="OFF"

cmake --build build
```

Before building the source code, I made a minor change to the source code to print `Hello World` after running `vw`.  I added the following line to the file `vowpalwabbit/cli/src/main.cc` in the `main` function:

```
int main(int argc, char *argv[])
{
    std::cout << "Hello World" << std::endl;
    vw* all = VW::initialize(argc, argv);
    ...
}
```

Step 3: Run the VW executable and see the output:

![output of the Exercise 1](tasks_image/Exercise1_Output.jpeg)