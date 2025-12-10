# Specify the base image
FROM almalinux

# Add LABEL metadata
LABEL mainter="user" \
    version="v0.1"

RUN dnf update -y && dnf install -y stress-ng

# Add app_user
RUN useradd -m app_user
# Switch to app_user
USER app_user

# Create the test1.txt file
#RUN touch test1.txt
# Create a working directory
WORKDIR /app
# Create the test2.txt file
RUN touch test2.txt

# Add the sample.txt file in the current directory
COPY --chown=app_user:app_user sample.txt ./
# Add the dir directory
COPY --chown=app_user:app_user dir ./

# Set environment variable
ENV SAMPLE=value
# Output the value of SAMPLE
RUN echo "SAMPLE=$SAMPLE"

# Define build arguments
ARG ARG_SAMPLE1
ARG ARG_SAMPLE2=default_value

RUN echo "ARG_SAMPLE1=$ARG_SAMPLE1"
RUN echo "ARG_SAMPLE2=$ARG_SAMPLE2"

# Display the current directory
CMD ["ls","-l"]