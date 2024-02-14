# How-to-solve-ImportError-lib-x86_64-linux-gnu-libstdc-.so.6-version-GLIBCXX_3.4.29-not-found

$ strings /usr/lib/x86_64-linux-gnu/libstdc++.so.6 | grep GLIBCXX
output: GLIBCXX_3.4
GLIBCXX_3.4.1
GLIBCXX_3.4.2
GLIBCXX_3.4.3
GLIBCXX_3.4.4
GLIBCXX_3.4.5
GLIBCXX_3.4.6
GLIBCXX_3.4.7
GLIBCXX_3.4.8
GLIBCXX_3.4.9
GLIBCXX_3.4.10
GLIBCXX_3.4.11
GLIBCXX_3.4.12
GLIBCXX_3.4.13
GLIBCXX_3.4.14
GLIBCXX_3.4.15
GLIBCXX_3.4.16
GLIBCXX_3.4.17
GLIBCXX_3.4.18
GLIBCXX_3.4.19
GLIBCXX_3.4.20
GLIBCXX_3.4.21
GLIBCXX_3.4.22
GLIBCXX_3.4.23
GLIBCXX_3.4.24
GLIBCXX_3.4.25
GLIBCXX_3.4.26
GLIBCXX_3.4.27
GLIBCXX_3.4.28
GLIBCXX_DEBUG_MESSAGE_LENGTH where can i get GLIBCXX_3.4.29

so as we can see there is no GLIBCXX_3.4.29

how to solve:

step 1: 

$ find /home/usrname -name "libstdc++.so.6*"
to use GLIBCXX_3.4.29, you should at least have version libstdc++.so.6.0.29 or higher
output should be:
/home/localstorage/miniconda3/envs/detector/  -name "libstdc++.so.6*"
/home/localstorage/miniconda3/envs/detector/lib/libstdc++.so.6
/home/localstorage/miniconda3/envs/detector/lib/libstdc++.so.6.0.32
/home/localstorage/miniconda3/envs/detector/x86_64-conda-linux-gnu/lib/libstdc++.so.6
/home/localstorage/miniconda3/envs/detector/x86_64-conda-linux-gnu/lib/libstdc++.so.6.0.32
as we can see there is libstdc++.so.6.0.32 avalible.

step 2: check it out

$ strings /home/localstorage/miniconda3/envs/detector/x86_64-conda-linux-gnu/lib/libstdc++.so.6.0.32 | grep GLIBCXX_3.4.29
output should be : GLIBCXX_3.4.29

step 3: since the error says lib-x86_64-linux-gnu-libstdc-.so.6-version-GLIBCXX_3.4.29-not-found, so we copy the ibstdc++.so.6.0.32 to /usr/lib/x86_64-linux-gnu/

$ sudo cp /home/localstorage/miniconda3/envs/detector/x86_64-conda-linux-gnu/lib/libstdc++.so.6.0.32 /usr/lib/x86_64-linux-gnu/

step 4: delate the old libstdc++.so.6 and create a new one

$sudo rm -rf ./libstdc++.so.6

$sudo ln -s ./libstdc++.so.6.0.32 ./libstdc++.so.6


then if you run the
$ strings /usr/lib/x86_64-linux-gnu/libstdc++.so.6 | grep GLIBCXX
again
you will see GLIBCXX_3.4.29!!!


GOOD LUCKKKKK!!!!




