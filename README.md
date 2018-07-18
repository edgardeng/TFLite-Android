# TF Lite Android App

> Android Demo for Tensorflow Lite build from [Tensorflow](https://github.com/tensorflow)

## how to run

1. install Android Studio

2. git clone https://github.com/edgardeng/TFLite-Android.git

3. Open . And choose this project


## how to build aar

1. git clone https://github.com/tensorflow/tensorflow.git

2. cd tensorflow

3. [Edit your `WORKSPACE`]

4. bazel build --cxxopt='--std=c++11' -c opt --fat_apk_cpu=armeabi-v7a //tensorflow/contrib/lite/java:tensorflow-lite

5. if bazel not use, please install bazel


## Building from Source with Bazel

1. Follow the [Bazel steps for the TF Demo App](https://github.com/tensorflow/tensorflow/tree/master/tensorflow/examples/android#bazel):

  1. [Install Bazel and Android Prerequisites](https://github.com/tensorflow/tensorflow/tree/master/tensorflow/examples/android#install-bazel-and-android-prerequisites).
     It's easiest with Android Studio.

      - You'll need at least SDK version 23.
      - Make sure to install the latest version of Bazel. Some distributions
        ship with Bazel 0.5.4, which is too old.
      - Bazel requires Android Build Tools `26.0.1` or higher.
      - **Bazel is incompatible with NDK revisions 15 and above,** with revision
        16 being a compile-breaking change. [Download an older version manually
        instead of using the SDK Manager.](https://github.com/tensorflow/tensorflow/tree/master/tensorflow/examples/android#install-bazel-and-android-prerequisites)
      - You also need to install the Android Support Repository, available
        through Android Studio under `Android SDK Manager -> SDK Tools ->
        Android Support Repository`.

  2. [Edit your `WORKSPACE`](https://github.com/tensorflow/tensorflow/tree/master/tensorflow/examples/android#edit-workspace)
     to add SDK and NDK targets.

     NOTE: As long as you have the SDK and NDK installed, the `./configure`
     script will create these rules for you. Answer "Yes" when the script asks
     to automatically configure the `./WORKSPACE`.

      - Make sure the `api_level` in `WORKSPACE` is set to an SDK version that
        you have installed.
      - By default, Android Studio will install the SDK to `~/Android/Sdk` and
        the NDK to `~/Android/Sdk/ndk-bundle` (but the NDK should be a manual
        download until Bazel supports NDK 16. See bullet points under (1)).

2. Build the app with Bazel. The demo needs C++11:

  ```shell
  bazel build -c opt --cxxopt='--std=c++11' \
    //tensorflow/contrib/lite/java/demo/app/src/main:TfLiteCameraDemo
  ```

  ```shell
    bazel build -c opt --cxxopt='--std=c++11' \
      //tensorflow/contrib/lite/java/demo/app/src/main:TfLiteCameraDemo

    bazel build //tensorflow/contrib/lite/java::tensorflowlite_java

// Building tensorflow-lite.aar
    bazel build --cxxopt='--std=c++11' -c opt --fat_apk_cpu=x86,x86_64,arm64-v8a,armeabi-v7a \
    tensorflow/contrib/lite/java:tensorflow-lite


bazel build --cxxopt='--std=c++11' -c opt --fat_apk_cpu=armeabi-v7a //tensorflow/contrib/lite/java:tensorflow-lite

    ```


3. Install the demo on a
   [debug-enabled device](https://github.com/tensorflow/tensorflow/tree/master/tensorflow/examples/android#install):

  ```shell
  adb install bazel-bin/tensorflow/contrib/lite/java/demo/app/src/main/TfLiteCameraDemo.apk
  ```
