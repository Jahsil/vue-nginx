## Checking Deployment of Custom Vue.js Application on Nginx Server

# Introduction

This documentation provides a step-by-step guide to check the deployment of a custom Vue.js application on an Nginx server. Ensure that the Vue.js project has been built successfully before proceeding.
Prerequisites

    Vue.js project source code
    Nginx server installed and running
    Basic knowledge of Vue.js and Nginx configurations

## Steps

1. Build the Vue.js Project

Navigate to the directory of your Vue.js project and build the project using the following command:

bash

npm run build

This command compiles and minifies the project files, creating a dist directory containing the static assets. 2. Configure Nginx Server

Create an Nginx server block configuration or modify an existing one to serve the built Vue.js project. Example configuration:

nginx

server {
listen 80;
server_name your-domain.com; # Change to your domain or server IP

    root /path/to/your/vue/project/dist;
    index index.html;

    location / {
        try_files $uri $uri/ /index.html;
    }

    # Additional configurations for static files, caching, etc.

}

3. Create Symbolic Link

Create a symbolic link to the Nginx configuration file in the sites-enabled directory:

bash

sudo ln -s /etc/nginx/sites-available/vue /etc/nginx/sites-enabled/

4. Test Nginx Configuration

Test the Nginx configuration to ensure there are no syntax errors:

bash

sudo nginx -t

If successful, restart Nginx to apply the changes:

bash

sudo systemctl restart nginx

5. DNS or Hosts File (Optional)

Ensure your domain points to the server's IP address or update the hosts file if running locally. 6. Access Your Vue.js App

Open a web browser and navigate to your Vue.js application. Ensure that the application is served correctly by Nginx.
Conclusion

By following these steps, you can check the successful deployment of your custom Vue.js application on an Nginx server. Verify that the application is accessible and functions as expected.
