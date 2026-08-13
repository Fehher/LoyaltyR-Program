FROM mcr.microsoft.com/dotnet/sdk:9.0 AS build
WORKDIR /app
COPY . .

RUN dotnet publish LoyaltyR.Service.Price.API/LoyaltyR.Service.Price.API.csproj -c release -o out

FROM mcr.microsoft.com/dotnet/aspnet:9.0
WORKDIR /app
COPY --from=build /app/out .

ENV ASPNETCORE_URLS=http://*80
ENV ASPNETCORE_ENVIRONMENT=development

ENTRYPOINT [ "dotnet","LoyaltyR.Service.Price.API.dll" ]

# docker build -t loyalty/price-service .
# docker run -d -it -p 50004:80 --name loyalty-price-service loyalty/price-service