# Use a lightweight Python image
FROM python:3.10-slim

# Set the working directory
WORKDIR /app

# Copy the requirements file and install dependencies
COPY requirement.txt .
RUN pip install -r requirement.txt

# Copy the Streamlit application
COPY stream.py .

# Expose the default Streamlit port
EXPOSE 8501

# Run the application
CMD ["streamlit", "run", "stream.py", "--server.port=8501", "--server.address=0.0.0.0"]
