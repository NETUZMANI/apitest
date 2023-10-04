FROM mcr.microsoft.com/dotnet/core AS build-env
WORKDIR /app

COPY *.csproj .

RUN dotnet restore

COPY . ./

RUN dotnet publish --no-restore -c Release -o out

FROM mcr.microsoft.com/dotnet/core
WORKDIR /app
COPY  --from=build-env /pp/out .
ENTRYPOINT ["dotnet","Api.dll"]