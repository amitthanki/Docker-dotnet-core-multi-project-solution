FROM microsoft/dotnet:sdk AS build
WORKDIR /app

COPY *.csproj ./
RUN dotnet restore Aspnetcoreapp.csproj

COPY . ./
RUN dotnet publish Aspnetcoreapp.csproj -c Release -o publishdir

FROM microsoft/dotnet:aspnetcore-runtime AS runtime
EXPOSE 5555
WORKDIR /app
COPY --from=build /app/publishdir .
ENTRYPOINT ["dotnet", "Aspnetcoreapp.dll"]


