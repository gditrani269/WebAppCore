FROM mcr.microsoft.com/dotnet/core/sdk:2.2 AS build
WORKDIR /source
COPY WebAppCore.csproj .
RUN dotnet restore
COPY . ./WebAppCore/
WORKDIR /source/WebAppCore
RUN dotnet publish -c Release -o /app


FROM mcr.microsoft.com/dotnet/core/aspnet:2.2
WORKDIR /app
COPY --from=build /app .
ENTRYPOINT ["dotnet", "WebAppCore.dll"]
