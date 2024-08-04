FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build
WORKDIR /app
COPY . .
RUN dotnet publish src/LoyaltyR.Service.Price.API/LoyaltyR.Service.Price.API.csproj -c release -o out


FROM mcr.microsoft.com/dotnet/aspnet:6.0
WORKDIR /app
COPY --from=build /app/out .

ENV ASPNETCORE_URLS=http://*80
ENV ASPNETCORE_ENVIRONMENT=Development

ENTRYPOINT dotnet LoyaltyR.Service.Price.API.dll

# docker build -t loyaltyr/service-price
# docker run --rm -it -p 50300:80 --name loyaltyr-service-price loyaltyr/service-price 