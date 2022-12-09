# Random Wikipedia walker

Using Selenium, create a small program that, starting from the main page https://www.wikipedia.org/, walks trough a sequence of random links and takes a snapshot of the last page.
The process is as follows:

 1. Navigate to the main page https://www.wikipedia.org/
 2. Select a random link in the page
 3. Navigate to the link
 4. Repeat steps 2 to 3 until you have visited 10 different pages
 5. Take a snapshot of the current page and save it

Include the code of the walker and the snapshot in this document.

## Answer

Pour créer un petit programme utilisant Selenium qui navigue vers une séquence de liens aléatoires sur la page principale de Wikipédia, prend un instantané de la dernière page et enregistre l'instantané, on peut utiliser l'interface WebDriver pour contrôler un navigateur Web et l'interface TakesScreenshot pour prendre un instantané de la page actuelle.

Voici un exemple de la façon dont cela peut être fait :

import org.openqa.selenium.*;
import org.openqa.selenium.chrome.ChromeDriver;

import java.io.File;
import java.util.*;

public class WikipediaWalker {

    public static void main(String[] args) {
        // Create a new ChromeDriver instance
        WebDriver driver = new ChromeDriver();

        // Navigate to the Wikipedia main page
        driver.get("https://www.wikipedia.org/");

        // Set of visited pages
        Set<String> visitedPages = new HashSet<>();

        // Select random links and navigate to them until 10 different pages have been visited
        while (visitedPages.size() < 10) {
            // Select a random link on the page
            List<WebElement> links = driver.findElements(By.tagName("a"));
            WebElement link = links.get(new Random().nextInt(links.size()));

            // Navigate to the link
            driver.navigate().to(link.getAttribute("href"));

            // Add the current page to the set of visited pages
            visitedPages.add(driver.getCurrentUrl());
        }

        // Take a snapshot of the current page
        File screenshot = ((TakesScreenshot) driver).getScreenshotAs(OutputType.FILE);

        // Save the snapshot to a file
        screenshot.renameTo(new File("screenshot.png"));

        // Close the driver
        driver.close();
    }
}

Dans cet exemple, la classe WikipediaWalker utilise l'interface WebDriver pour contrôler un navigateur Web Chrome et naviguer vers une séquence.
