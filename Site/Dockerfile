FROM microsoft/aspnetcore-build:2.0.4-2.1.3-jessie as builder
WORKDIR /source
COPY *.csproj ./
RUN dotnet restore

COPY . ./
RUN dotnet publish --output /app/ --configuration Release

FROM microsoft/aspnetcore

# Install Node (used for server pre-rendering)
RUN apt-get -qq update && apt-get -qqy --no-install-recommends install wget gnupg \
    git \
    unzip

RUN curl -sL https://deb.nodesource.com/setup_6.x |  bash -
RUN apt-get install -y nodejs


WORKDIR /app
COPY --from=builder /app .
EXPOSE 80

ENTRYPOINT ["dotnet", "Site.dll"]
