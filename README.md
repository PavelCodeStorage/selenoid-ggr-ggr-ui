Selenium with Selenoid
---
Overview:
---
 
Repository provide configuration example of Selenium with Selenoid

---
**What you need to do:**
1. Install docker (https://docs.docker.com/docker-for-windows/release-notes/#docker-community-edition-17031-ce-win12--2017-05-12)
3. Navigate to the folder with **docker-compose.yml** file and execute from command line command: **docker-compose up**
4. Wait until all necessary images are downloaded  :)
4. Download vnc image: **docker pull selenoid/vnc:chrome_65.0**
5. Download image for video recording **docker pull selenoid/video-recorder:latest-release**
6. From command line execude command: **docker ps -a**  (see created containers) 
7. Navigate to the localhost:8080 (see: ![selenoidui](https://user-images.githubusercontent.com/26840848/39272875-e926f05a-48e5-11e8-806f-9847aaa59e52.jpg)
7. Don't forget to add some changes in your code see :
```java
        if (driver == null) {
            DesiredCapabilities browser = new DesiredCapabilities();
            browser.setBrowserName("chrome");
            browser.setVersion("65.0");
            browser.setCapability("enableVNC", true);

            try {
                driver = new RemoteWebDriver(URI.create("http://localhost:4444/wd/hub").toURL(), browser);
            } catch (MalformedURLException e) {
                e.printStackTrace();
            }
        }
        return driver;
```
7. Run out tests : **mvn clean test**
8. See how tests pass (see: ![selenoidvnc](https://user-images.githubusercontent.com/26840848/39272905-fedb162e-48e5-11e8-9284-bdbb73b106dc.jpg))
8. Even with docker you can make screenshoots and added it in reporting (i.e add image see: 
![dockerimagesallureresults](https://user-images.githubusercontent.com/26840848/39099117-67de4f9e-467d-11e8-9f75-04155c2e0b58.jpg)


