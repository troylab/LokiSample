# build
FROM mcr.microsoft.com/dotnet/sdk:5.0 AS build-env
WORKDIR /app
COPY . ./
RUN dotnet restore
RUN dotnet publish -c Release -o dist

# runtime
FROM mcr.microsoft.com/dotnet/aspnet:5.0
EXPOSE 80/tcp
WORKDIR /app
COPY --from=build-env /app/dist .
ENTRYPOINT ["dotnet", "API.dll"]