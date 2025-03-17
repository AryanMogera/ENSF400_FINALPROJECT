# Use Gradle 7.6 with JDK 11 as the base image
FROM gradle:7.6-jdk11

# Set the working directory inside the container
WORKDIR /app

# Copy everything from the project directory to /app inside the container
COPY . .

# Ensure gradlew has execution permissions
RUN chmod +x gradlew

# Expose port 8080 for the application
EXPOSE 8080

# Set correct Java memory options
ENV JAVA_TOOL_OPTIONS="-XX:+UseContainerSupport -XX:MaxRAMPercentage=75"

# Run the application using Gradle
CMD ["./gradlew", "apprun"]


# CMD ["sh", "-c", "./gradlew apprun && tail -f /dev/null"] (This works too!)