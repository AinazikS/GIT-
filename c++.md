# C / C++
```
sudo apt install g++
```
```
sudo apt install gcc
```
```
find /usr/bin/ -name 'g++'
```
```json
{
    "configurations": [
        {
            "name": "Linux",
            "includePath": [
                "${workspaceFolder}/**"
            ],
            "defines": [],
            "compilerPath": "/usr/bin/g++",
            "cStandard": "gnu17",
            "cppStandard": "c++17",
            "intelliSenseMode": "linux-gcc-x64"
        }
    ],
    "version": 4
}
```
# Compile
```
g++ -E square.cpp -o square_preproccessed.cpp
```
```
g++ -E source.cpp -o source_preproccessed.cpp
```
>neither
```
g++ -c source.cpp
```
```
g++ -c square.cpp
```
```
g++ source.o square.o -o program
```
> or
```
g++ source.cpp square.cpp -o program
```
> Assembly version
```
 g++ -S square.cpp
```
```
c++filt -n _Z6squarei
```
