FROM mcr.microsoft.com/dotnet/sdk:9.0 AS build
WORKDIR /app
COPY . .

RUN dotnet publish LoyaltyR.Service.Catalog.API/LoyaltyR.Service.Catalog.API.csproj -c release -o out

FROM mcr.microsoft.com/dotnet/aspnet:9.0
WORKDIR /app
COPY --from=build /app/out .

ENV ASPNETCORE_URLS=http://*80
ENV ASPNETCORE_ENVIRONMENT=development

ENTRYPOINT [ "dotnet","LoyaltyR.Service.Catalog.API.dll" ]