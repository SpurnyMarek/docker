# Inicializacia noveho buildu zo zadaneho imagu
FROM mcr.microsoft.com/dotnet/sdk:5.0 AS build-env
# Nastavenie pracovneho adresara na /app
WORKDIR /app

# Skopirovanie csproj suboru do danej cesty
COPY *.csproj ./
# Spustenie prikazu dotnet restore
RUN dotnet restore

# Skopirovanie všetkych suborov do app ktory sa nachadza v kontajnery
COPY . /app
# Spustenie prikazu dotnet publish -c Release -o out
RUN dotnet publish -c Release -o out

FROM mcr.microsoft.com/dotnet/aspnet:5.0
WORKDIR /app
COPY --from=build-env /app/out .
ENTRYPOINT ["dotnet", "aspnetcoreapp.dll"]