# Jour2
## Test de Selenium
* Pour navigateur EDGE
```
from selenium import webdriver
from selenium.webdriver.common.by import By
import time

# 🚀 Lancer Edge avec le DriverManager intégré de Selenium
driver = webdriver.Edge()   # Plus besoin de Service() ni webdriver_manager
driver.maximize_window()

# 2) Ouvrir l’URL
driver.get("https://opensource-demo.orangehrmlive.com")

# (Optionnel) pause pour laisser charger la page
time.sleep(2)

# 3) Entrer le username
driver.find_element(By.NAME, "???").send_keys("???")

# 4) Entrer le mot de passe
driver.find_element(By.NAME, "???").???("???")

# 5) Cliquer sur Login
driver.find_element(By.XPATH, "???").click()

# 6) Capturer le titre
time.sleep(2)
actual_title = driver.title
print("Titre capturé :", actual_title)

# 7) Vérifier le titre attendu avec assert
expected_title = "OrangeHRM"
assert actual_title == expected_title, f"❌ Test Failed : attendu '{expected_title}', obtenu '{actual_title}'"
print("✅ Test Passed")

# 8) Fermer le navigateur
driver.quit()
```

* Correction  EDGE

<details>

```
from selenium import webdriver
from selenium.webdriver.common.by import By
import time

# 🚀 Lancer Edge avec le DriverManager intégré de Selenium
driver = webdriver.Edge()   # Plus besoin de Service() ni webdriver_manager
driver.maximize_window()

# 2) Ouvrir l’URL
driver.get("https://opensource-demo.orangehrmlive.com")

# (Optionnel) pause pour laisser charger la page
time.sleep(2)

# 3) Entrer le username
driver.find_element(By.NAME, "username").send_keys("Admin")

# 4) Entrer le mot de passe
driver.find_element(By.NAME, "password").send_keys("admin123")

# 5) Cliquer sur Login
driver.find_element(By.XPATH, "//button[@type='submit']").click()

# 6) Capturer le titre
time.sleep(2)
actual_title = driver.title
print("Titre capturé :", actual_title)

# 7) Vérifier le titre attendu avec assert
expected_title = "OrangeHRM"
assert actual_title == expected_title, f"❌ Test Failed : attendu '{expected_title}', obtenu '{actual_title}'"
print("✅ Test Passed")

# 8) Fermer le navigateur
driver.quit()
```
* Assertion modifiée :
```
from selenium import webdriver
from selenium.webdriver.common.by import By
import time

# 🚀 Lancer Edge avec le DriverManager intégré de Selenium
driver = webdriver.Edge()   # Plus besoin de Service() ni webdriver_manager
driver.maximize_window()

# 2) Ouvrir l’URL
driver.get("https://opensource-demo.orangehrmlive.com")

# (Optionnel) pause pour laisser charger la page
time.sleep(2)

# 3) Entrer le username
driver.find_element(By.NAME, "username").send_keys("Admin")
time.sleep(2)

# 4) Entrer le mot de passe
driver.find_element(By.NAME, "password").send_keys("admin123")


# 5) Cliquer sur Login
driver.find_element(By.XPATH, "//button[@type='submit']").click()

# 6) Capturer le titre
time.sleep(2)
actual_title = driver.title
print("Titre capturé :", actual_title)

time.sleep(2)

# 7) Vérifier le titre attendu avec assert
expected_word = "Time at Work"
assert expected_word in driver.page_source, f"❌ Test Failed : attendu '{expected_title}', obtenu '{actual_title}'"
print("✅ Test Passed")

# 8) Fermer le navigateur
driver.quit()
```


</details>




* Exercices pour chrome
```
from selenium import webdriver
from selenium.webdriver.common.by import By
import time

# 🚀 Lancer Chrome automatiquement sans installer de driver (Selenium 4.11+)
driver = webdriver.Chrome()
driver.maximize_window()

# 2) Ouvrir l’URL
driver.get("https://opensource-demo.orangehrmlive.com")

# (Pause pour charger la page de login)
time.sleep(5)

# 3) Entrer le username
driver.find_element(By.NAME, "???").send_keys("????")
time.sleep(5)

# 4) Entrer le mot de passe
driver.find_element(By.NAME, "????").???("???")

# (Pause avant de cliquer, pour être sûr que le bouton est dispo)
time.sleep(2)

# 5) Cliquer sur Login
driver.find_element(By.XPATH, "???").click()

# (Pause pour charger le tableau de bord)
time.sleep(5)

# 6) Capturer le titre
actual_title = driver.title
print("Titre capturé :", actual_title)

# 7) Vérifier le titre attendu avec assert
expected_title = "OrangeHRM"
assert actual_title == expected_title, f"❌ Test Failed : attendu '{expected_title}', obtenu '{actual_title}'"
print("✅ Test Passed")

# 8) Fermer le navigateur
driver.quit()
```
* Correction chrome
<details>

```
from selenium import webdriver
from selenium.webdriver.common.by import By
import time

# 🚀 Lancer Chrome automatiquement sans installer de driver (Selenium 4.11+)
driver = webdriver.Chrome()
driver.maximize_window()

# 2) Ouvrir l’URL
driver.get("https://opensource-demo.orangehrmlive.com")

# (Pause pour charger la page de login)
time.sleep(5)

# 3) Entrer le username
driver.find_element(By.NAME, "username").send_keys("Admin")

# 4) Entrer le mot de passe
driver.find_element(By.NAME, "password").send_keys("admin123")

# (Pause avant de cliquer, pour être sûr que le bouton est dispo)
time.sleep(2)

# 5) Cliquer sur Login
driver.find_element(By.XPATH, "//button[@type='submit']").click()

# (Pause pour charger le tableau de bord)
time.sleep(5)

# 6) Capturer le titre
actual_title = driver.title
print("Titre capturé :", actual_title)

# 7) Vérifier le titre attendu avec assert
expected_title = "OrangeHRM"
assert actual_title == expected_title, f"❌ Test Failed : attendu '{expected_title}', obtenu '{actual_title}'"
print("✅ Test Passed")

# 8) Fermer le navigateur
driver.quit()
```
</details>

* Pour firefox pas integré
```
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.firefox.service import Service
from webdriver_manager.firefox import GeckoDriverManager
import time

# 🚀 Lancer Firefox avec WebDriver Manager (téléchargement automatique)
driver = webdriver.Firefox(service=Service(GeckoDriverManager().install()))
driver.maximize_window()

driver.get("https://opensource-demo.orangehrmlive.com")
time.sleep(5)

driver.find_element(By.NAME, "???").send_keys("???")
driver.find_element(By.NAME, "???").???("???")
time.sleep(2)
driver.find_element(By.XPATH, ???).click()
time.sleep(5)

actual_title = driver.title
print("Titre capturé :", actual_title)

expected_title = "OrangeHRM"
assert actual_title == expected_title, f"❌ Test Failed : attendu '{expected_title}', obtenu '{actual_title}'"
print("✅ Test Passed")

driver.quit()

```

* correction firefox

<details>

```
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.firefox.service import Service
from webdriver_manager.firefox import GeckoDriverManager
import time

# 🚀 Lancer Firefox avec WebDriver Manager (téléchargement automatique)
driver = webdriver.Firefox(service=Service(GeckoDriverManager().install()))
driver.maximize_window()

driver.get("https://opensource-demo.orangehrmlive.com")
time.sleep(5)

driver.find_element(By.NAME, "username").send_keys("Admin")
driver.find_element(By.NAME, "password").send_keys("admin123")
time.sleep(2)
driver.find_element(By.XPATH, "//button[@type='submit']").click()
time.sleep(5)

actual_title = driver.title
print("Titre capturé :", actual_title)

expected_title = "OrangeHRM"
assert actual_title == expected_title, f"❌ Test Failed : attendu '{expected_title}', obtenu '{actual_title}'"
print("✅ Test Passed")

driver.quit()

```
</details>

