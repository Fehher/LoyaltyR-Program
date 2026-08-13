FROM mcr.microsoft.com/dotnet/sdk:9.0 AS build
WORKDIR /app
COPY . . 
RUN dotnet publish LoyaltyR.Service.Cart.API/LoyaltyR.Service.Cart.API.csproj -c release -o out

FROM mcr.microsoft.com/dotnet/aspnet:9.0
WORKDIR /app
COPY --from=build /app/out .

ENV ASPNETCORE_ENVIRONMENT=development
ENV ASPNETCORE_URLS=http://*80

ENTRYPOINT [ "dotnet","LoyaltyR.Service.Cart.API.dll" ]

# docker build -t loyalty/cart-service .
# docker run -d -it -p 50002:80 --name loyalty-cart-service loyalty/cart-service