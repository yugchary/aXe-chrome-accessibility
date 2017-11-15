# aXe-chrome-accessibility README #

aXe-chrome-accessibility is used for automating the accessibility audit of your web site with the help of selenium and Java. This repo is built with two popular accessibility scanners [GoogleChrome accessibility-developer-tools][2] and [aXe-core][1]. 

As discussed above, once you call the method "ProcessResponse.scanner(driver);" (you have to pass your driver object as parameter to this method), it first scans the website using  [GoogleChrome accessibility-developer-tools][2] to run the audit. Once the audit is run, the tool returns a meaningful Java object which is used for reporting later. And then it uses [aXe-core][1] for scanning the website. This [aXe-core][1] returns violation in form of json response. This response is parsed for reporting purpose. After scanning with both the tools is done, it creates a folder called "Accessibility Results" and inside that folder, it creates a Time stamped PDF file with all the violations listed. So, each time when you call this method, it generates the PDF with the violations at that point of time.

## Better Practices ##

As we generate PDF report every time when you call the method, it is effective, if you navigate to each page and call this method.

## To use the aXe-chrome-accessibility library in your own tests ##

As this library is not available in maven repo, you would need to clone this project and deploy locally by running `mvn clean install`.

Once the library is available in your local/internal maven repository, please add dependency like below to project.

```
<dependency>
   <groupId>com.accessibility</groupId>
   <artifactId>aXe-chrome-accessibility</artifactId>
   <version>1.0.0-SNAPSHOT</version>
</dependency>
```

In this project, you can find one example testcase of how to use this library using TestNG and Selenium under `src/test/java/com/accessibility/examples/test/WebDrivera11yTest.java`. Test is written to run in chrome browser. Before running the tests, make sure you have driver.exe file downloaded and add the corresponding path to `System.setProperty("webdriver.chrome.driver", "<you chromedriver.exe file path here>");` .  

## Reference ##

I have used the below repos as reference for this tool. Thanks to Nilesh and Dian Fay.

https://github.com/nikulkarni/webdriver-accessibility

https://github.com/dequelabs/axe-selenium-java

## Contributing ##

Fork the project and submit pull request if you like to add a feature/fix bugs etc.
	
## Disclaimer ##

I am not a accessibility expert. I am open for suggestions.

This is the basic version. I will work on to improve this repo.

## Known Issues ##
As we create PDF file for every call, we have to call this method, if there is any dynamic content in the page. In that case, tool may report duplicate issues in each report. I am working on resolving this issue.

## Contact ##

Email Id: illi.nainappa@gmail.com

Blog Link: https://seleniumocean.blogspot.com/


[1]: https://github.com/dequelabs/axe-core/tree/master "aXe-core"
[2]: https://github.com/GoogleChrome/accessibility-developer-tools "GoogleChrome accessibility-developer-tools"
