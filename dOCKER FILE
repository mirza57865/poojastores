# Use the official .NET SDK image as the base image
FROM mcr.microsoft.com/dotnet/sdk:3.1 AS build

# Set the working directory inside the container
WORKDIR /app

# Copy the .csproj and restore the dependencies
COPY PoojaStores.csproj ./
RUN dotnet restore

# Copy the rest of the source code
COPY . ./

# Build the application
RUN dotnet publish -c Release -o out

# Use the official .NET runtime image as the base image
FROM mcr.microsoft.com/dotnet/aspnet:3.1

# Set the working directory inside the container
WORKDIR /app

# Copy the published application from the build image
COPY --from=build /app/out ./

# Set the entry point for the application
ENTRYPOINT ["dotnet", "PoojaStores.dll"]
