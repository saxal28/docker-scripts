FROM microsoft/dotnet:2.2-sdk

RUN curl -sL https://deb.nodesource.com/setup_8.x |  bash -
RUN apt-get install -y nodejs

WORKDIR /app
COPY . .
RUN mkdir -p uploads

WORKDIR /app/xxx/ReactApp
RUN npm rebuild node-sass

ENV ASPNETCORE_ENVIRONMENT Test

EXPOSE 80
EXPOSE 8001
EXPOSE 1433

WORKDIR /app/xxx
RUN dotnet publish -c Release -o out

WORKDIR /app/Drury.xxx/out
ADD https://github.com/ufoscout/docker-compose-wait/releases/download/2.2.1/wait /wait
RUN chmod +x /wait

## Launch the wait tool and then your application
CMD /wait && dotnet xxx.dll
