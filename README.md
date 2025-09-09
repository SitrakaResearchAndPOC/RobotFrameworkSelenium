# Jour2
## Test de Selenium
* Pour navigateur chrome
```
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.chrome.service import Service
from webdriver_manager.chrome import ChromeDriverManager
import time

# Lancer Chrome automatiquement avec WebDriverManager
driver = webdriver.Chrome(service=Service(ChromeDriverManager().install()))
driver.maximize_window()

# 2) Ouvrir l’URL
driver.get("https://opensource-demo.orangehrmlive.com")

# (Optionnel) petite pause pour laisser charger la page
time.sleep(2)

# 3) Entrer le username
driver.find_element(By.NAME, "username").send_keys("Admin")

# 4) Entrer le mot de passe
driver.find_element(By.NAME, "password").send_keys("admin123")

# 5) Cliquer sur Login
driver.find_element(By.XPATH, "//button[@type='submit']").click()

# 6) Capturer le titre
time.sleep(2)  # attendre un peu le chargement du tableau de bord
actual_title = driver.title
print("Titre capturé :", actual_title)

# 7) Vérifier le titre attendu
expected_title = "OrangeHRM"
# if actual_title == expected_title:
#    print("✅ Test Passed")
# else:
#    print("❌ Test Failed")

# Les asserts
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
from selenium.webdriver.chrome.service import Service
from webdriver_manager.chrome import ChromeDriverManager
import time

# Lancer Chrome automatiquement avec WebDriverManager
driver = webdriver.Chrome(service=Service(ChromeDriverManager().install()))
driver.maximize_window()

# 2) Ouvrir l’URL
driver.get("https://opensource-demo.orangehrmlive.com")

# (Optionnel) petite pause pour laisser charger la page
time.sleep(2)

# 3) Entrer le username
driver.find_element(By.NAME, "username").send_keys("Admin")

# 4) Entrer le mot de passe
driver.find_element(By.NAME, "password").send_keys("admin123")

# 5) Cliquer sur Login
driver.find_element(By.XPATH, "//button[@type='submit']").click()

# 6) Capturer le titre
time.sleep(2)  # attendre un peu le chargement du tableau de bord
actual_title = driver.title
print("Titre capturé :", actual_title)

# 7) Vérifier le titre attendu
expected_title = "OrangeHRM"
# if actual_title == expected_title:
#    print("✅ Test Passed")
# else:
#    print("❌ Test Failed")

# Les asserts
assert actual_title == expected_title, f"❌ Test Failed : attendu '{expected_title}', obtenu '{actual_title}'"
print("✅ Test Passed")

# 8) Fermer le navigateur
driver.quit()
```
</details>


