# windows-image-with-crystal-report-and-oracle-client-build-tools

docker cp ./WINDOWS.X64_193000_client dotnet-buildtools-slave:/WINDOWS.
X64_193000_client

###################################################################################################################################
# Docker commands
###################################################################################################################################

cls
docker container stop dotnet-buildtools-slave
docker container rm dotnet-buildtools-slave
docker image pull quay.io/emiratesgroup/dotnet-buildtools:16.0.28714.193
docker container run --tty --detach --name dotnet-buildtools-slave --publish-all=true quay.io/emiratesgroup/dotnet-buildtools:16.0.28714.193 cmd.exe
docker container exec -it dotnet-buildtools-slave cmd.exe
exit
docker image rm quay.io/emiratesgroup/dotnet-buildtools:16.0.28714.193

###################################################################################################################################

###################################################################################################################################

cd C:\WINDOWS.X64_193000_client\client

setup.exe -silent -nowait -nowelcome -noconfig -ignoreSysPrereqs -ignorePrereqFailure -skipPrereqs -waitForCompletion -force -responsefile filename "ORACLE_BASE=c:\oracle\product" "ORACLE_HOME=c:\oracle\product\12.2\Client_x64" "oracle.install.IsBuiltInAccount=true" "oracle.install.client.installType=Custom" "oracle.install.client.customComponents=oracle.rdbms.util:12.2.0.1.0,oracle.sqlplus:12.2.0.1.0,oracle.odbc:12.2.0.1.0"