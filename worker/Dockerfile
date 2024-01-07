FROM mcr.microsoft.com/dotnet/sdk:7.0 AS build
ARG TARGETPLATFORM
ARG TARGETARCH
ARG BUILDPLATFORM

# Display the build platform information (useful for debugging)
RUN echo "I am running on $BUILDPLATFORM, building for $TARGETPLATFORM"

# Set the working directory to /source
WORKDIR /source

# Debug: List files in the current directory
RUN ls -la

# Copy the .csproj file and restore any dependencies (via NuGet)
COPY *.csproj .
RUN dotnet restore

# Copy the project files into the container
COPY . .

# Debug: List files again
RUN ls -la

# Publish the application to the /app directory
RUN dotnet publish -c release -o /app --self-contained false --no-restore

# Define runtime stage with .NET runtime
FROM mcr.microsoft.com/dotnet/runtime:7.0

# Set the working directory to /app
WORKDIR /app

# Copy the published application from the build stage to the current stage
COPY --from=build /app .

# Define the command to run the application
ENTRYPOINT ["dotnet", "Worker.dll"]
