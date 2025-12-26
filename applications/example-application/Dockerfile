# Lightweight Python base image
FROM python:3.10-slim

# Create a simple application directory
WORKDIR /app

# Create a tiny web server that returns "Hello from example-application"
RUN echo "from http.server import BaseHTTPRequestHandler, HTTPServer\n\
class Handler(BaseHTTPRequestHandler):\n\
    def do_GET(self):\n\
        self.send_response(200)\n\
        self.send_header('Content-type','text/plain')\n\
        self.end_headers()\n\
        self.wfile.write(b'Hello from example-application!')\n\
\n\
server = HTTPServer(('0.0.0.0', 8080), Handler)\n\
print('Starting server on port 8080...')\n\
server.serve_forever()" > app.py

# Expose port 8080 to match your deployment.yaml
EXPOSE 8080

# Run the application
CMD ["python", "app.py"]
