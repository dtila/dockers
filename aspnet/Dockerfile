ARG ASPNETCORE_VERSION="8.0"

FROM  mcr.microsoft.com/dotnet/aspnet:${ASPNETCORE_VERSION}

USER $APP_UID
WORKDIR /app

USER root
RUN mkdir -p /var/lib/apt/lists/partial && \
    chmod 755 /var/lib/apt/lists/partial

RUN apt-get update && apt-get install -y xorg openbox libnss3 libasound2 libglib2.0-0 curl wget

USER app

