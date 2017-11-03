FROM microsoft/aspnetcore
ARG source

# Install Node (used for server pre-rendering)
RUN apt-get -qq update && apt-get -qqy --no-install-recommends install wget gnupg \
    git \
    unzip

RUN curl -sL https://deb.nodesource.com/setup_6.x |  bash -
RUN apt-get install -y nodejs

WORKDIR /app
EXPOSE 80
COPY . .
ENTRYPOINT ["dotnet", "Site.dll"]
