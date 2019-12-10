# Selenium_IFC
IFC_index
package testing;

import java.awt.AWTException;
import java.util.concurrent.TimeUnit;

import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.interactions.Action;
import org.openqa.selenium.interactions.Actions;
import org.openqa.selenium.support.ui.Select;

public class IFCfill {

	public static void main(String[] args) throws InterruptedException, AWTException {
		// setting to open a chrome:
System.setProperty("webdriver.chrome.driver", "E:\\eclipse-java-neon-R-win32-x86_64\\chromedriver.exe");
WebDriver driver=new ChromeDriver();
driver.manage().window().maximize();
driver.get("https://indiatest.tti-global.com/serviceadvisor/ifc/#/login");
driver.manage().timeouts().implicitlyWait(2000, TimeUnit.MILLISECONDS);	
		
//1.Enter username:
WebElement user=driver.findElement(By.id("lusername"));
user.sendKeys("RRJACRESAL");

//2.Enter password:
WebElement pass=driver.findElement(By.id("lpassword"));
pass.sendKeys("123");

//3.Clicking login button:
WebElement login=driver.findElement(By.xpath("//span[contains(text(),'Login')]"));
login.click();



//4.Clicking the test drive option:
driver.navigate().to("https://indiatest.tti-global.com/serviceadvisor/ifc/testdrive/index.html#/");

Thread.sleep(2000);
//5.Want to fill customer mobile number:
WebElement mobile=driver.findElement(By.id("customer_mobile_no"));
mobile.sendKeys("9489373112");


//6.Want to fill customer name:
WebElement custname=driver.findElement(By.id("customer_name"));
custname.sendKeys("Baskaran");


//Selecting a vehicle source from dropdown:
Select vehicle=new Select(driver.findElement(By.xpath("//div/div/select[@type='text']")));
vehicle.selectByVisibleText("Others");

//Selecting a vechicle model:
Select model=new Select(driver.findElement(By.xpath("//div/div/select[@id='model' and @tabindex='5']")));
model.selectByVisibleText("KWID");

//Selecting a variant model:
Select variant= new Select(driver.findElement(By.xpath("//div/div/select[@id='model' and @tabindex='6']")));
variant.selectByVisibleText("RXL 1.0 EASY-R");

//Selecting a transmission:
Select transmission=new Select(driver.findElement(By.xpath("//div/div/select[@id='model' and @tabindex='7']")));
transmission.selectByVisibleText("AMT - 5 speed");

//Selecting a Place:
WebElement place=driver.findElement(By.xpath("//div[1]/label[@for='radio1' and @tabindex='8']"));
place.click();

//Enter a start kilometer:

WebElement strtkm=driver.findElement(By.xpath("//input[@id='start_km']"));
strtkm.clear();
strtkm.sendKeys("1200");


//Enter a end kilometer:

WebElement endkm=driver.findElement(By.xpath("//input[@id='end_km']"));
endkm.clear();
endkm.sendKeys("1500");

//Enter start-time:

WebElement strttime=driver.findElement(By.xpath("//input[@id='start_time']"));
strttime.clear();
strttime.sendKeys("0245PM");

//Enter a End-time:

WebElement endtime=driver.findElement(By.xpath("//input[@id='end_time']"));
endtime.clear();
endtime.sendKeys("0300PM");

//Choose a License
Thread.sleep(3000);
String path="D:\\License\\Image2.jpg";
WebElement chooseFile = driver.findElement(By.id("file"));
chooseFile.sendKeys(path);

//Digital signature:
WebElement sign=driver.findElement(By.xpath("/html/body/app-root/app-testdrivehome/div/div/form/div[6]/div[1]/div/signature-pad/canvas"));
//sign.click();
Thread.sleep(2000);
Actions builder = new Actions(driver);
Action drawAction = builder.moveToElement(sign,0,0) //start points x axis and y axis. 
          .click()
          .moveByOffset(2, 5) // 2nd points (x1,y1)
          .click()
          .moveByOffset(4, 5)// 3rd points (x2,y2)
          .click()
          .build();
drawAction.perform();

//Submit button:

WebElement submit=driver.findElement(By.xpath("//button[@name='Next']"));
submit.click();


}




	}


