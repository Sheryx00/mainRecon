<br />
<p align="center">
  <a href="https://hub.docker.com/u/l34r00t">
    <img
      alt="mainRecon for bugbounty hunter"
      src="img/banner.png"
      width="600"
    />
  </a>

  <h3 align="center">mainRecon</h3>
</p>

<p align="center">
  <a href="https://github.com/l34r00t/"><img alt="GitHub code size in bytes" src="https://img.shields.io/github/languages/code-size/l34r00t/mainRecon"></a>
  <a href="https://github.com/l34r00t/"><img alt="GitHub repo size" src="https://img.shields.io/github/repo-size/l34r00t/mainRecon"></a>
  <a href="https://github.com/l34r00t/"><img alt="GitHub last commit" src="https://img.shields.io/github/last-commit/l34r00t/mainRecon"></a>
  <a href="https://github.com/l34r00t/"><img alt="GitHub issues" src="https://img.shields.io/github/issues/l34r00t/mainRecon"></a>
  <a href="https://hub.docker.com/r/l34r00t/mainrecon"><img alt="Docker Cloud Build Status" src="https://img.shields.io/docker/cloud/build/l34r00t/mainrecon"></a>
  <a href="https://hub.docker.com/r/l34r00t/mainrecon"><img alt="Docker Automated build" src="https://img.shields.io/docker/cloud/automated/l34r00t/mainrecon"></a>
  <a href="https://hub.docker.com/r/l34r00t/mainrecon"><img alt="Docker Pulls" src="https://img.shields.io/docker/pulls/l34r00t/mainrecon"></a>
  <a href="https://hub.docker.com/r/l34r00t/mainrecon"><img alt="Docker Image Size (latest by date)" src="https://img.shields.io/docker/image-size/l34r00t/mainrecon"></a>
  <a href="https://hub.docker.com/r/l34r00t/mainrecon"><img alt="Docker Image Version (latest by date)" src="https://img.shields.io/docker/v/l34r00t/mainrecon"></a>
  <a href="https://hub.docker.com/r/l34r00t/mainrecon"><img alt="Docker Stars" src="https://img.shields.io/docker/stars/l34r00t/mainrecon"></a>
  <a href="https://github.com/l34r00t/mainRecon/blob/master/LICENSE"><img alt="GitHub" src="https://img.shields.io/github/license/l34r00t/mainRecon"></a>

  mainRecon for bugbounty hunter is an image with a bash script with some of the tools used at recon workflow.
</p>

## Table of Contents

- [Table of Contents](#table-of-contents)
- [About mainRecon](#about-mainrecon)
- [Features](#features)
- [Flow](#flow)
- [mainRecon.sh](#mainreconsh)
- [Usage](#usage)
  - [Prerequisites](#prerequisites)
  - [Option 1 - Use the github repository](#option-1---use-the-github-repository)
  - [Option 2 - Use the image from docker hub](#option-2---use-the-image-from-docker-hub)
  - [Considerations to run the container](#considerations-to-run-the-container)
  - [targets.txt](#targetstxt)
  - [Create telegram webhook](#create-telegram-webhook)
- [mainRecon scan results](#mainrecon-scan-results)
  - [h1-Recon](#h1-recon)
  - [mainRecon Alert](#mainrecon-alert)
- [Environment tested](#environment-tested)
- [Coffee Time](#coffee-time)
- [Contributing](#contributing)
- [Stargazers over time](#stargazers-over-time)
- [Credits](#credits)
- [Disclaimer](#disclaimer)
- [License](#license)

## About mainRecon

mainRecon is an automated reconnaissance docked image for bugbounty hunter write in bash script. This image has the basic tools used in the recognition workflow. The purpose it`s to simplify the recon flow in a simple way.

You can run the docker image in your PC o [VPS](https://www.digitalocean.com/?refcode=b5a9fc36fd95&utm_campaign=Referral_Invite&utm_medium=Referral_Program).

## Features

- Subdomain Enumeration
- Checks alive subdomain
- Search URLs at Wayback Machine
- Screenshots of the subdomains
- Headers responses files
- Finds js files
- Finds tokes in js files
- Finds endpoints in js files
- Finds parameters from subdomains
- Finds directories
- Telegram notifications

## Flow
<p align="center">
  <a href="https://hub.docker.com/u/l34r00t">
    <img
      src="img/mainRecon_flow.png"
      width="600"
    />
  </a>
</p>

## mainRecon.sh

| **Name**          | **Repository**                                        |
| ----------------- | ----------------------------------------------------- |
| findomain         |  https://github.com/Edu4rdSHL/findomain               |                                     
| assetfinder       |  https://github.com/tomnomnom/assetfinder             |                                               
| Amass             |  https://github.com/OWASP/Amass                       |                                              
| subfinder         |  https://github.com/projectdiscovery/subfinder        |
| httprobe          |  https://github.com/tomnomnom/httprobe                |
| waybackurls       |  https://github.com/tomnomnom/waybackurls             |
| aquatone          |  https://github.com/michenriksen/aquatone             |
| subjs             |  https://github.com/lc/subjs                          |
| new-zile          |  https://github.com/bonino97/new-zile                 |    
| LinkFinder        |  https://github.com/GerbenJavado/LinkFinder           |
| paramspider       |  https://github.com/devanshbatham/ParamSpider         |
| dirsearch         |  https://github.com/maurosoria/dirsearch              |
| TelegramBot       |  https://core.telegram.org/bots                       |

## Usage
### Prerequisites

- [Docker](https://docs.docker.com/get-docker/) service installed

You can use the docker image by the next two options:

### Option 1 - Use the github repository

First, must clone the mainRecon repository.

    git clone --depth 1 https://github.com/l34r00t/mainRecon.git
    cd mainRecon
    docker build -t mainrecon .
    docker run --rm -it -v /path/to/local/directory:/mainData mainrecon -p [--program] <hackerone> -f [--file] targets.txt 

Then, modify telegram bot_token and telegram chat_ID in mainRecon.sh

### Option 2 - Use the image from docker hub

Use image from docker hub: [l34r00t/mainrecon](https://hub.docker.com/u/l34r00t/mainRecon)

    docker pull l34r00t/mainrecon
    docker run --rm -it --env chat_ID="your_chat_ID" --env token="your_token" \
    --env findomain_fb_token="fb_token" \
    --env findomain_spyse_token="spyse_token" \
    --env findomain_virustotal="virustotal_token" \
    --env findomain_securitytrails_token="securitytrails_token" \
    -v /path/to/local/directory:/mainData --name mainrecon l34r00t/mainrecon -p [--program] <hackerone> -f [--file] targets.txt

### Considerations to run the container

There are differents use cases for use the image and you should know how to run the container properly.

1. Share information from your local directory to container directory and save information on your local directory. You should save information under /mainData directory.

        docker run --rm -it -v /path/to/local/directory:/mainData --name mainrecon l34r00t/mainrecon -p [--program] <hackerone> -f [--file] targets.txt 

2. I you use the telegram bot youmust modify telegram bot_token and telegram chat_ID in mainRecon.sh

### targets.txt

Your targets.txt should include a list of domains you're checking and should look something like:

        hackerone.com
        hackerone-ext-content.com
        hackerone-user-content.com

### Create telegram webhook        

Thank you [Edu4rdSHL](https://github.com/Edu4rdSHL/) for you telegram webhook write-up.

- [create_telegram_webhook](https://github.com/Edu4rdSHL/findomain/blob/master/docs/create_telegram_webhook.md)

## mainRecon scan results

### h1-Recon
[![asciicast](https://asciinema.org/a/356881.svg)](https://asciinema.org/a/356881)

In the following repository you will obtain all [h1 recon results](https://github.com/l34r00t/mainRecon-h1-enum)

### mainRecon Alert

<img
      alt="mainRecon for bugbounty hunter"
      src="img/h1-recon.png"
      width="600"
/>

## Environment tested

The image was tested in the following environments:

- Docker service for Mac: Docker version 19.02.7, build afacb8b

- Docker service for Ubuntu 19.20 in [Digital Ocean VPS](https://www.digitalocean.com/?refcode=b5a9fc36fd95&utm_campaign=Referral_Invite&utm_medium=Referral_Program): Docker version 18.09.7, build build 2d0083d

## Coffee Time

If you like my content, please consider inviting me to a coffee. Thank you for your support!

[![Buy me a coffee](https://www.buymeacoffee.com/assets/img/custom_images/orange_img.png)](https://www.buymeacoffee.com/l34r00t)

## Contributing

[Contributing](CONTRIBUTING.md)

## Stargazers over time

[![Stargazers over time](https://starchart.cc/l34r00t/mainRecon.svg)](https://starchart.cc/l34r00t/mainRecon)

## Credits

mainRecon has been possible thank you to the following projects.

- [Edu4rdSHL](https://github.com/Edu4rdSHL/)                                               
- [tomnomnom](https://github.com/tomnomnom/)         
- [OWASP](https://github.com/OWASP/)               
- [michenriksen](https://github.com/michenriksen/)
- [bonino97](https://github.com/bonino97/)
- [GerbenJavado](https://github.com/GerbenJavado/)
- [devanshbatham](https://github.com/devanshbatham/)
- [subjs](https://github.com/lc/subjs/)
- [maurosoria](https://github.com/maurosoria/)
- [Telegram BOT](https://core.telegram.org/bots)
- [LazyRecon](https://github.com/capt-meelo/LazyRecon)
- [SubEnum](https://github.com/bing0o/SubEnum)
- [aaaguirre](https://github.com/aaaguirrep/pentest)

## Disclaimer

- mainRecon was written for education purposes only.

## License

[MIT](LICENSE)
Copyright (c) 2020, L34r00t