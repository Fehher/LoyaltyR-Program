FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build
WORKDIR /app
COPY . .
RUN dotnet publish src/LoyaltyR.Service.Tracking.API/LoyaltyR.Service.Tracking.API.csproj -c release -o out 

FROM mcr.microsoft.com/dotnet/aspnet:6.0
WORKDIR /app
COPY --from=build /app/out .

ENV ASPNETCORE_URLS=http://*80
ENV ASPNETCORE_ENVIRONMENT=Development

ENTRYPOINT dotnet LoyaltyR.Service.Tracking.API.dll

# docker build -t loyaltyr/service-tracking .
# docker run --rm -it -p 50500:80 --name loyaltyr-service-tracking loyaltyr/service-tracking