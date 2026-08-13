# A docker multi-stage to not ship more than minimum expected

FROM mcr.microsoft.com/dotnet/sdk:9.0 AS build
WORKDIR /app
COPY . .
RUN dotnet publish LoyaltyR.Service.Gateway.API/LoyaltyR.Service.Gateway.API.csproj -c release -o out

FROM mcr.microsoft.com/dotnet/aspnet:9.0
WORKDIR /app
COPY --from=build /app/out .

ENV ASPNETCORE_ENVIRONMENT=development
ENV ASPNETCORE_URLS=http://*80


ENTRYPOINT ["dotnet", "LoyaltyR.Service.Gateway.API.dll"]

# docker build -t loyalty/gateway-service
# docker run-d -it -p 50001:80 --name loyalty-gateway-service loyalty/gateway-service