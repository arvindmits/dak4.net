FROM mcr.microsoft.com/dotnet/core/sdk:3.0.100 as builder

WORKDIR /src
COPY src/Utilities.HttpCheck/Utilities.HttpCheck.csproj ./Utilities.HttpCheck/

WORKDIR /src/Utilities.HttpCheck
RUN dotnet restore

COPY src /src
RUN dotnet publish -c Release -o /out Utilities.HttpCheck.csproj

# app image
FROM mcr.microsoft.com/dotnet/core/runtime:3.0

WORKDIR /database-check
ENTRYPOINT ["dotnet", "Utilities.HttpCheck.dll"]

COPY --from=builder /out/ .