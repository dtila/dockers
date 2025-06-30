ARG ASPNETCORE_VERSION

FROM mcr.microsoft.com/dotnet/aspnet:${ASPNETCORE_VERSION}

WORKDIR /app

RUN mkdir -p /var/lib/apt/lists/partial \
 && chmod 755 /var/lib/apt/lists/partial \
 && apt-get update \
 && apt-get install -y --no-install-recommends \
      xorg \
      openbox \
      libnss3 \
      libasound2 \
      libglib2.0-0 \
      curl \
      wget \
      chromium \
 && rm -rf /var/lib/apt/lists/*

ENV CHROME_BIN=/usr/bin/chromium \
    CHROME_PATH=/usr/lib/chromium/

ENTRYPOINT ["dotnet"]
CMD ["--info"]
