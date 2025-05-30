# sampleapplication

A simple static site deployment example using AWS CodeDeploy and Apache HTTP Server.

## Features

- Static HTML landing page
- Automated deployment using AWS CodeDeploy
- Custom lifecycle hooks for installing dependencies, starting, and stopping the server

## Getting Started

### Prerequisites

- An Amazon EC2 instance running Amazon Linux or CentOS
- AWS CodeDeploy agent installed and running on the instance
- AWS CLI configured
- Git installed

### Installation & Local Test

1. **Clone the repository**
    ```sh
    git clone https://github.com/kanagrasuaws/sampleapplication.git
    cd sampleapplication
    ```

2. **Install dependencies (locally)**
    ```sh
    sudo bash scripts/install_dependencies
    ```

3. **Copy index.html to Apache web root**
    ```sh
    sudo cp index.html /var/www/html/
    ```

4. **Start Apache server**
    ```sh
    sudo bash scripts/start_server
    ```

5. **Open your browser:**  
   Visit [http://localhost](http://localhost) to see the landing page.

### Stopping the Server

```sh
sudo bash scripts/stop_server
```

## Deployment (with AWS CodeDeploy)

This application uses an `appspec.yml` file for AWS CodeDeploy. The deployment process:

- Installs Apache HTTP Server (httpd)
- Copies `index.html` to `/var/www/html/`
- Uses lifecycle hooks to install dependencies, start, and stop the server

**To deploy:**
1. Zip your application files (including appspec.yml and scripts).
2. Upload to an S3 bucket or push to your source version control.
3. Create a CodeDeploy application and deployment group in AWS.
4. Start the deployment using the AWS Console or AWS CLI.

## Project Structure

```
.
├── appspec.yml
├── index.html
├── scripts/
│   ├── install_dependencies
│   ├── start_server
│   └── stop_server
└── README.md
```

## Contributing

Pull requests are welcome. For major changes, please open an issue first.

## License

[MIT](LICENSE) (or specify your license)

## Contact

Maintained by [kanagrasuaws](https://github.com/kanagrasuaws)
