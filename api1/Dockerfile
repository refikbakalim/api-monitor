FROM mcr.microsoft.com/dotnet/sdk:5.0 AS build-env
RUN mkdir /app
WORKDIR /app

# copy the project and restore as distinct layers in the image
COPY ./*.csproj ./
RUN dotnet restore

# copy the rest and build
COPY ./ ./
RUN dotnet build
RUN dotnet publish -c Release -o out

# build runtime image
FROM mcr.microsoft.com/dotnet/aspnet:5.0
RUN mkdir /app
WORKDIR /app

COPY --from=build-env /app/out ./
ENTRYPOINT ["dotnet", "api1.dll"]