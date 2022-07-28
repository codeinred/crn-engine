cd crn-engine/CRNEngine
# Restore tools, like paket
dotnet tool restore

# Download dependencies
dotnet paket restore


env VCTargetsPath=./ dotnet build
# Install GCC Build Template for using C++ with dotnet on linux
# https://github.com/roozbehid/dotnet-vcxproj
dotnet new -i GCC.Build.Template


# Building CVode (dependency of SundialsSolver)

*Obtained from: https://computing.llnl.gov/projects/sundials/sundials-software*
```
cmake -B SundialsSolver/cvode-build \
    -G 'Ninja Multi-Config' \
    -S SundialsSolver/cvode \
    -DCMAKE_INSTALL_PREFIX=SundialsSolver/cvode-package
cmake --build SundialsSolver/cvode-build --config Release
cmake --install SundialsSolver/cvode-build --prefix=SundialsSolver/cvode-package
