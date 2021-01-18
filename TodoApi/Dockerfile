FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS build
WORKDIR /app

COPY . ./TodoApi/
RUN dotnet restore TodoApi

WORKDIR /app/TodoApi
RUN dotnet publish -c Release -o output

FROM mcr.microsoft.com/dotnet/core/aspnet:3.1 AS runtime
WORKDIR /app

# remove this after ssl is configured
# ENV ASPNETCORE_ENVIRONMENT="Development"

COPY --from=build /app/TodoApi/output .

ENTRYPOINT ["dotnet", "TodoApi.dll"]
