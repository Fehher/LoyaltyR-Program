FROM mcr.microsoft.com/dotnet/sdk:9.0 AS build
WORKDIR /app
COPY . .

RUN dotnet publish LoyaltyR.Service.Recommendation.API/LoyaltyR.Service.Recommendation.API.csproj -c release -o out

FROM mcr.microsoft.com/dotnet/aspnet:9.0
WORKDIR /app
COPY --from=build /app/out .

ENV ASPNETCORE_URLS=http://*80
ENV ASPNETCORE_ENVIROMENT=development

ENTRYPOINT [ "dotnet","LoyaltyR.Service.Recommendation.API.dll" ]

# docker build -t loyalty/recommendation-service .
# docker run -d -it -p 50005:80 --name loyalty-recommendation-service loyalty/recommendation-service