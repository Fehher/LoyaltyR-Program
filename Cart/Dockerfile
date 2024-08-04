FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build
WORKDIR /app
COPY . .
RUN dotnet publish src/LoyaltyR.Service.Cart.API/LoyaltyR.Service.Cart.API.csproj -c release -o out

FROM mcr.microsoft.com/dotnet/aspnet:6.0
WORKDIR /app
COPY --from=build /app/out .

ENV ASPNETCORE_URLS=http://*80
ENV ASPNETCORE_ENVIRONMENT=Development

ENTRYPOINT dotnet LoyaltyR.Service.Cart.API.dll

# docker build -t loyaltyr/service-cart .
# docker run --rm -it -p 50100:80 loyaltyr/service-cart