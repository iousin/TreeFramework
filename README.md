# A framework to try and get bitcode enabled in the x86_64 simulator build. 
# Tried various build options as follows nothing works.

xcodebuild ENABLE_BITCODE[sdk=iphone*]=YES BITCODE_GENERATION_MODE=bitcode DYLIB_COMPATIBILITY_VERSION=1 -sdk iphonesimulator -configuration Release -target TreeFramework clean build

xcodebuild OTHER_CFLAGS="-fembed-bitcode" ENABLE_BITCODE[sdk=iphone*]=YES BITCODE_GENERATION_MODE=bitcode -sdk iphonesimulator -configuration Release -target TreeFramework clean build

otool -arch x86_64 -l build/Release-iphonesimulator/TreeFramework.framework/TreeFramework | grep LLVM
Doesn't output anything.
 
In the arm64 build it does emits the bitcode, even without any settings

xcodebuild -sdk iphoneos -configuration Release -scheme TreeFramework clean build
otool -arch arm64 -l  build/Release-iphoneos/TreeFramework.framework/TreeFramework | grep LLVM


 
 
 
