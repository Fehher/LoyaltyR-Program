FROM mcr.microsoft.com/dotnet/sdk:9.0 AS build
WORKDIR /app
COPY . .

RUN dotnet publish LoyaltyR.Service.Tracking.API/LoyaltyR.Service.Tracking.API.csproj -c release -o out

FROM mcr.microsoft.com/dotnet/aspnet:9.0 
WORKDIR /app
COPY --from=build /app/out .

ENV ASPNETCORE_URLS=http://*80
ENV ASPNETCORE_ENVIRONMENT=development


ENTRYPOINT [ "dotnet","LoyaltyR.Service.Tracking.API.dll" ]

# docker build -t loyalty/tracking-service .
# docker run -d -it -p 50006:80 --name loyalty-tracking-service loyalty/tracking-service