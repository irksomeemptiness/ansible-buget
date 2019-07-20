FROM microsoft/dotnet:2.2-aspnetcore-runtime AS base
WORKDIR /app
EXPOSE 80

FROM microsoft/dotnet:2.2-sdk AS build
RUN curl -sL https://deb.nodesource.com/setup_8.x | bash -
RUN apt-get install -y nodejs
RUN useradd -m baget

USER baget

WORKDIR /src
COPY /src .

USER root

RUN dotnet restore BaGet
RUN dotnet build BaGet -c Release -o /app
USER baget
FROM build AS publish
USER root
RUN dotnet publish BaGet -c Release -o /app

USER baget
FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "BaGet.dll"]