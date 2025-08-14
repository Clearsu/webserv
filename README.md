## Webserv

<img width="100" height="100" style="transform: scaleX(-1);" src="tests/html/asset/index.ico/apple-icon.png">

#### My little web server

## Introduction

- A single-threaded asynchronous web server implemented in C++ 98, mimicking Nginx's behavior.

## Features

```
- Developed GET, POST, DELETE, PUT, HEAD methods compliant with the HTTP 1.1 protocol.
- Can be configured with a configuration file like Nginx.
- Supports virtual hosts with multiple ports.
- Made server-side advanced tasks easier with CGI functionality.
- Handles client requests asynchronously.
- Supports the default page (index.html) and error pages.
- Implemented external dependencies like configurations using the Singleton Pattern.
- Connection & Request Timeout
```

## How to Run
```
make
./webserv (option: [path_to_conf_file])
```

## Demo
### GET

`curl -i http://localhost:8100/`

<img width="294" height="118" alt="image" src="https://github.com/user-attachments/assets/bb85ddcb-eada-4772-ab8c-6756908502f6" />

`curl -i http://localhost:8100/not-found`

<img width="387" height="225" alt="image" src="https://github.com/user-attachments/assets/c3b63b65-c9bc-401a-8129-b515db2358e6" />

It supports redirection:

<img width="322" height="100" alt="image" src="https://github.com/user-attachments/assets/0e940e27-c958-4996-a703-bd4b3811a993" />

Unsupported HTTP method:

<img width="425" height="117" alt="image" src="https://github.com/user-attachments/assets/0a9cbe29-3778-4e6c-902a-088a285cef37" />

Request Timeout:

<img width="278" height="219" alt="image" src="https://github.com/user-attachments/assets/e4507de7-f785-4c5b-9fb1-ddadefecc472" />


### HEAD

`curl -I http://localhost:8100/`

<img width="288" height="113" alt="image" src="https://github.com/user-attachments/assets/7da66d87-2822-4559-b959-eb329a374fb0" />

### POST

`curl -i -X POST http://localhost:8100/post_body -F "file=@sample.txt"`

<img width="551" height="176" alt="image" src="https://github.com/user-attachments/assets/249c4829-313d-4ff1-88db-4ce72723db10" />

check the uploaded file: `curl -i http://localhost:8100/directory/sample.txt`

<img width="421" height="153" alt="image" src="https://github.com/user-attachments/assets/84aa5500-c6c4-4a6b-8b7c-cf69e699fd79" />


### PUT

`curl -i -T sample.txt http://localhost:8100/put_test/sample.txt`

<img width="522" height="197" alt="image" src="https://github.com/user-attachments/assets/ec2f6ee2-eb93-4fe9-96e6-2eb01278b9b5" />

Check the uploaded file:

<img width="406" height="149" alt="image" src="https://github.com/user-attachments/assets/eb534676-5af7-4f75-b9b2-624acdbb47cd" />

Replace the file with a new one: `curl -i -T new_sample.txt http://localhost:8100/put_test/sample.txt`

<img width="527" height="173" alt="image" src="https://github.com/user-attachments/assets/56e7fbc1-7863-4534-a604-7202a2db5a96" />

Check the changed content:

<img width="719" height="209" alt="image" src="https://github.com/user-attachments/assets/121cc559-edeb-4ac7-a577-ea0d4a5c18a7" />

### DELETE

`curl -i -X DELETE http://localhost:8100/put_test/sample.txt`

<img width="472" height="139" alt="image" src="https://github.com/user-attachments/assets/bf794a51-c29e-4f87-bd48-5eb2bf17519c" />

Check if the file is deleted:

<img width="444" height="216" alt="image" src="https://github.com/user-attachments/assets/f132c46a-24fc-43cf-8cc1-6b3cb79f54ef" />


It is not allowed to delete a directory. Upload deletion is only allowed per-file:

<img width="432" height="115" alt="image" src="https://github.com/user-attachments/assets/2d3cc999-5a85-48d3-9c03-d42cdf99c3e0" />

Calling a method to a location which does not allow the method:

<img width="379" height="135" alt="image" src="https://github.com/user-attachments/assets/9d5f69da-1969-4455-a420-c641a732e347" />


## Server Benchmark Comparison (vs. Nginx, measured over 3 runs)

| Response Size | TPS (webserv) | TPS (nginx) | Relative TPS (%) | Latency (webserv, s) | Latency (Nginx, s) | Failure Rate (webserv, %) | Failure Rate (nginx, %) | Longest Txn (webserv, s) | Longest Txn (Nginx, s) |
|---------------|-------------------|-------------|-------------------|----------------------------|----------------------|-------------------------------|---------------------------|-------------------------------|--------------------------|
| **0B**        | 13,756            | 25,828      | 53.3%             | 0.01                       | 0.01                 | 0.0104%                       | 0.0839%                   | 0.57                          | 0.06                     |
| **612B**      | 10,386            | 23,214      | 44.7%             | 0.02                       | 0.01                 | 0.0022%                       | 0.0821%                   | 0.75                          | 0.16                     |
| **974B**      | 9,660             | 23,270      | 41.5%             | 0.02                       | 0.01                 | 0.0027%                       | 0.0846%                   | 0.81                          | 0.16                     |
| **2000B**     | 6,530             | 23,402      | 27.9%             | 0.03                       | 0.01                 | 0.0075%                       | 0.0852%                   | 0.84                          | 0.14                     |


## Development Environment

![Generic badge](https://img.shields.io/badge/C++-98-lightgrey.svg)
![Generic badge](https://img.shields.io/badge/VSCode-1.79.2(Universal)-blue.svg)

## Tools

```
1. Github (Issue and configuration management)
2. Notion (Communication)
3. Slack (Communication)
4. VSCode (Development)
```

## Skills & Tech Stack

```
- C++98
- POSIX
- CGI
- Kernel Queue
- HTML
- CSS
```

## GIT

1. [Commit Conventions](https://github.com/MyLittleWebServer/webserv/discussions/3)
   - `feat`: Adding a new feature to the application or library.
   - `fix`: Fixing a bug.
   - `build`: Changes that affect the build system or external dependencies (e.g., gulp, broccoli, npm).
   - `ci`: Changes to CI configuration files and scripts (e.g., Travis, Circle, BrowserStack, SauceLabs).
   - `chore`: Other changes that don't modify source code.
   - `docs`: Documentation changes only.
   - `perf`: Code changes that improve performance.
   - `refactor`: Code changes that neither fix a bug nor add a feature.
   - `revert`: Reverting a previous commit.
   - `style`: Changes that do not affect the meaning of the code (white space, formatting, missing semicolons, etc.).
   - `test`: Adding or updating tests.
   - `wip`: Work in progress.

2. Git Branches
   - `main`: Deployment
   - `develop`: Branch for merging developed features.
   - `#[Tracker ID] [Commit Convention Name] / [Function Name]`: Branch for developing each feature.

## Directory Structure

```
📦srcs
 ┣ 📂clients
 ┃ ┣ 📂candidate_fields
 ┃ ┃ ┣ 📂include
 ┃ ┃ ┃ ┣ 📜CandidateFields.hpp
 ┃ ┃ ┃ ┗ 📜ICandidateFields.hpp
 ┃ ┃ ┗ 📂srcs
 ┃ ┃ ┃ ┗ 📜CandidateFields.cpp
 ┃ ┣ 📂cgi
 ┃ ┃ ┣ 📂include
 ┃ ┃ ┃ ┣ 📜CGI.hpp
 ┃ ┃ ┃ ┗ 📜ICGI.hpp
 ┃ ┃ ┗ 📂src
 ┃ ┃ ┃ ┗ 📜CGI.cpp
 ┃ ┣ 📂client
 ┃ ┃ ┣ 📂include
 ┃ ┃ ┃ ┗ 📜Client.hpp
 ┃ ┃ ┗ 📂src
 ┃ ┃ ┃ ┗ 📜Client.cpp
 ┃ ┣ 📂method
 ┃ ┃ ┣ 📂include
 ┃ ┃ ┃ ┣ 📜DELETE.hpp
 ┃ ┃ ┃ ┣ 📜DummyMethod.hpp
 ┃ ┃ ┃ ┣ 📜GET.hpp
 ┃ ┃ ┃ ┣ 📜IMethod.hpp
 ┃ ┃ ┃ ┗ 📜POST.hpp
 ┃ ┃ ┗ 📂src
 ┃ ┃ ┃ ┣ 📜DELETE.cpp
 ┃ ┃ ┃ ┣ 📜DummyMethod.cpp
 ┃ ┃ ┃ ┣ 📜GET.cpp
 ┃ ┃ ┃ ┗ 📜POST.cpp
 ┃ ┣ 📂request
 ┃ ┃ ┣ 📂include
 ┃ ┃ ┃ ┣ 📜IRequest.hpp
 ┃ ┃ ┃ ┗ 📜Request.hpp
 ┃ ┃ ┣ 📂request_parser
 ┃ ┃ ┃ ┣ 📂include
 ┃ ┃ ┃ ┃ ┣ 📜IRequestParser.hpp
 ┃ ┃ ┃ ┃ ┗ 📜RequestParser.hpp
 ┃ ┃ ┃ ┗ 📂src
 ┃ ┃ ┃ ┃ ┗ 📜RequestParser.cpp
 ┃ ┃ ┗ 📂src
 ┃ ┃ ┃ ┗ 📜Request.cpp
 ┃ ┣ 📂response
 ┃ ┃ ┣ 📂include
 ┃ ┃ ┃ ┣ 📜IResponse.hpp
 ┃ ┃ ┃ ┗ 📜Response.hpp
 ┃ ┃ ┗ 📂src
 ┃ ┃ ┃ ┗ 📜Response.cpp
 ┃ ┗ 📜.DS_Store
 ┣ 📂config
 ┃ ┣ 📂child_config
 ┃ ┃ ┣ 📂include
 ┃ ┃ ┃ ┗ 📜IChildConfig.hpp
 ┃ ┃ ┣ 📂location_config
 ┃ ┃ ┃ ┣ 📂include
 ┃ ┃ ┃ ┃ ┣ 📜ILocationConfig.hpp
 ┃ ┃ ┃ ┃ ┗ 📜LocationConfig.hpp
 ┃ ┃ ┃ ┗ 📂src
 ┃ ┃ ┃ ┃ ┗ 📜LocationConfig.cpp
 ┃ ┃ ┣ 📂mime_types_config
 ┃ ┃ ┃ ┣ 📂include
 ┃ ┃ ┃ ┃ ┣ 📜IMimeTypesConfig.hpp
 ┃ ┃ ┃ ┃ ┗ 📜MimeTypesConfig.hpp
 ┃ ┃ ┃ ┗ 📂src
 ┃ ┃ ┃ ┃ ┗ 📜MimeTypesConfig.cpp
 ┃ ┃ ┣ 📂proxy_config
 ┃ ┃ ┃ ┣ 📂include
 ┃ ┃ ┃ ┃ ┣ 📜IProxyConfig.hpp
 ┃ ┃ ┃ ┃ ┗ 📜ProxyConfig.hpp
 ┃ ┃ ┃ ┗ 📂src
 ┃ ┃ ┃ ┃ ┗ 📜ProxyConfig.cpp
 ┃ ┃ ┣ 📂root_config
 ┃ ┃ ┃ ┣ 📂include
 ┃ ┃ ┃ ┃ ┣ 📜IRootConfig.hpp
 ┃ ┃ ┃ ┃ ┗ 📜RootConfig.hpp
 ┃ ┃ ┃ ┗ 📂src
 ┃ ┃ ┃ ┃ ┗ 📜RootConfig.cpp
 ┃ ┃ ┗ 📂server_config
 ┃ ┃ ┃ ┣ 📂include
 ┃ ┃ ┃ ┃ ┣ 📜IServerConfig.hpp
 ┃ ┃ ┃ ┃ ┗ 📜ServerConfig.hpp
 ┃ ┃ ┃ ┗ 📂src
 ┃ ┃ ┃ ┃ ┗ 📜ServerConfig.cpp
 ┃ ┣ 📂include
 ┃ ┃ ┣ 📜Config.hpp
 ┃ ┃ ┗ 📜IConfig.hpp
 ┃ ┣ 📂parser
 ┃ ┃ ┣ 📂include
 ┃ ┃ ┃ ┣ 📜ConfigParser.hpp
 ┃ ┃ ┃ ┗ 📜IConfigParser.hpp
 ┃ ┃ ┗ 📂src
 ┃ ┃ ┃ ┗ 📜ConfigParser.cpp
 ┃ ┗ 📂src
 ┃ ┃ ┗ 📜Config.cpp
 ┣ 📂exception
 ┃ ┣ 📂include
 ┃ ┃ ┣ 📜ExceptionThrower.hpp
 ┃ ┃ ┗ 📜errorMessage.hpp
 ┃ ┗ 📂src
 ┃ ┃ ┗ 📜ExceptionThrower.cpp
 ┣ 📂server
 ┃ ┣ 📂include
 ┃ ┃ ┣ 📜EventHandler.hpp
 ┃ ┃ ┣ 📜Kqueue.hpp
 ┃ ┃ ┣ 📜Server.hpp
 ┃ ┃ ┗ 📜ServerManager.hpp
 ┃ ┗ 📂src
 ┃ ┃ ┣ 📜EventHandler.cpp
 ┃ ┃ ┣ 📜Kqueue.cpp
 ┃ ┃ ┣ 📜Server.cpp
 ┃ ┃ ┗ 📜ServerManager.cpp
 ┣ 📂utils
 ┃ ┣ 📂checker
 ┃ ┃ ┣ 📂include
 ┃ ┃ ┃ ┣ 📜FileChecker.hpp
 ┃ ┃ ┃ ┣ 📜IChecker.hpp
 ┃ ┃ ┃ ┗ 📜IFileChecker.hpp
 ┃ ┃ ┗ 📂src
 ┃ ┃ ┃ ┗ 📜FileChecker.cpp
 ┃ ┣ 📂reader
 ┃ ┃ ┣ 📂include
 ┃ ┃ ┃ ┣ 📜IReader.hpp
 ┃ ┃ ┃ ┗ 📜Reader.hpp
 ┃ ┃ ┗ 📂src
 ┃ ┃ ┃ ┗ 📜Reader.cpp
 ┃ ┗ 📂util
 ┃ ┃ ┣ 📂include
 ┃ ┃ ┃ ┣ 📜Color.hpp
 ┃ ┃ ┃ ┣ 📜Status.hpp
 ┃ ┃ ┃ ┣ 📜Utils.hpp
 ┃ ┃ ┃ ┗ 📜Utils.tpp
 ┃ ┃ ┗ 📂src
 ┃ ┃ ┃ ┣ 📜Status.cpp
 ┃ ┃ ┃ ┗ 📜Utils.cpp
 ┗ 📜main.cpp
```

## 🧑‍💻 Authors

[Chanheki](https://github.com/chanhihi)

[Jang-cho](https://github.com/cjho0316)

[Jincpark](https://github.com/Clearsu)

[Sechung](https://github.com/middlefitting)

