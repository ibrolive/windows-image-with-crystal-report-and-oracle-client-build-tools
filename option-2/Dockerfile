FROM mcr.microsoft.com/windows:1809 as dll_source
FROM microsoft/iis

#hack in oledlg dll!!
COPY --from=dll_source /windows/system32/oledlg.dll /windows/system32/oledlg.dll 
COPY --from=dll_source /windows/syswow64/oledlg.dll /windows/syswow64/oledlg.dll 

RUN ["powershell.exe", "Install-WindowsFeature NET-Framework-45-ASPNET"]  
RUN ["powershell.exe", "Install-WindowsFeature Web-Asp-Net45"]

WORKDIR c:/temp
COPY CRRuntime_64bit_13_0_21.msi . 
RUN powershell.exe -Command Start-Process c:\temp\CRRuntime_64bit_13_0_21.msi -ArgumentList '/l*v c:\temp\install.log' -Wait