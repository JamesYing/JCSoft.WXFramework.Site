FROM microsoft/aspnetcore-build:2.0.4-2.1.3-jessie as builder
WORKDIR /source
COPY *.csproj ./
RUN dotnet restore

COPY . ./
RUN dotnet publish --output /app/ --configuration Release

FROM microsoft/aspnetcore
WORKDIR /app
COPY --from=builder /app .
EXPOSE 80

ENTRYPOINT ["dotnet", "Site.dll"]
