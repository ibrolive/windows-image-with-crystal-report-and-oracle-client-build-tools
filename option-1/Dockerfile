FROM quay.io/emiratesgroup/dotnet-buildtools:16.0.28714.193
#FROM microsoft/iis

RUN ["powershell.exe", "Install-WindowsFeature NET-Framework-45-ASPNET"]  
RUN ["powershell.exe", "Install-WindowsFeature Web-Asp-Net45"]

WORKDIR c:/temp
COPY CRRuntime_64bit_13_0_23.msi .
RUN powershell.exe -Command Start-Process c:\temp\CRRuntime_64bit_13_0_23.msi -ArgumentList '/l*v c:\temp\install.log' -Wait