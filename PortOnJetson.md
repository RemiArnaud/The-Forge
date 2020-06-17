* TheForge on Jetson

sudo apt-get install curl
sudo apt-get install codelite

# Vulkan loader
git clone https://github.com/KhronosGroup/Vulkan-Loader.git

cd Vulkan-Loader && mkdir build && cd build
../scripts/update_deps.py
cmake -DCMAKE_BUILD_TYPE=Release -DVULKAN_HEADERS_INSTALL_DIR=$(pwd)/Vulkan-Headers/build/install ..
make -j8
sudo make install
sudo ldconfig

# Vulkan Headers
(I'm not sure this is needed - see Vulkan-Loader/build/Vulkan-Headers/include/ )
git clone https://github.com/KhronosGroup/Vulkan-Headers.git
cd Vulkan-Headers && mkdir build && cd build
cmake ..
sudo make install

# get The Forge
git clone https://github.com/ConfettiFX/The-Forge.git
chmod +x PRE_BUILD.command 

# compile forge (GCC)
cd The-Forge/Examples_3/Unit_Tests/UbuntuCodelite
codelite &
 (open UbuntuUnitTests.workspace)



