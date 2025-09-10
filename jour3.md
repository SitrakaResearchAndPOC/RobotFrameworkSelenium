# RobotFrameworkSelenium
* Installation python / cocher toutes les options
[python](https://www.python.org/downloads/)
* Installation pycharm / cocher toutes les options
[pycharm](https://www.jetbrains.com/fr-fr/pycharm/download/download-thanks.html?platform=windows)
* Demarrez pycharm et installer :
Installer via terminal de pycharm :
```
pip install selenium webdriver-manager
````
```
pip install robotframework robotframework-seleniumlibrary
````
* Avant d'installer codegen :
Telecharger nvm </br>
[nvm](https://github.com/coreybutler/nvm-windows/releases/tag/1.2.2)
Installations </br> 
```
nvm install 20
```
```
nvm use 20
```
```
node -v   # → v20.x.x
```

* Installer playwright

````
pip install playwright
````
````
playwright install
````
## Cas de problèmes persistant uniquement
Remove-Item -Recurse -Force "C:\Users\Esti\AppData\Local\ms-playwright" </br>
 Remove-Item -Recurse -Force "C:\Users\Esti\AppData\Local\Temp\playwright_*"

Installer plugin : Hyper roboframework

## Alternatives pour playwright avec des problèmes :
```
npm install -g playwright
```
```
npx playwright install
```

## Learning first code 1 
Fichier TC1.robot
```
*** Settings ***
Library   SeleniumLibrary

*** Variables ***

*** Test Cases ***
TC1
    # Les test

*** Keywords ***
# Les mots clés
```
```
robot TC1.robot
```
## Open Browser
```
*** Settings ***
Library   SeleniumLibrary

*** Variables ***

*** Test Cases ***
TC1
    # Les test
    open browser  https://demo.nopcommerce.com   chrome
    sleep  1h
```

## Open Browser with variable

* With chrome

```
*** Settings ***
Library   SeleniumLibrary

*** Variables ***
${URL}  https://demo.nopcommerce.com 
${BROW}  chrome
*** Test Cases ***
TC1
    # Les test
    open browser  ${URL}  ${BROW}
    sleep  1h
```

* Correction With edge
<details>

```
*** Settings ***
Library   SeleniumLibrary

*** Variables ***
${URL}  https://demo.nopcommerce.com 
${BROW}  edge
*** Test Cases ***
TC1
    # Les test
    open browser  ${URL}  ${BROW}
    sleep  1h
```
</details>

* Corrections With firefox

<details>

```
*** Settings ***
Library   SeleniumLibrary

*** Variables ***
${URL}  https://demo.nopcommerce.com 
${BROW}  firefox
*** Test Cases ***
TC1
    # Les test
    open browser  ${URL}  ${BROW}
    sleep  1h
```
</details>

# Application LoginTest
```
*** Settings ***
Library    SeleniumLibrary

*** Variables ***
${browser}  chrome
${url}  https://demo.nopcommerce.com

*** Test Cases ***
LoginTest
    Open Browser   ${url}  ${browser}

    # xpath du logo : 
    Click Link    xpath:???
    Sleep  3s

    # Tester login by name 
    Input Text  name:???  pavanoltraining@gmail.com
    Sleep  3s

    # Tester password by name 

    Input Text  name:???   Test@123
    Sleep  3s

    # Cliquer element par xpath
    Click Element   xpath:???

    Sleep  1h
```

* corrections

<details>
  
```
*** Settings ***
Library    SeleniumLibrary

*** Variables ***
${browser}  chrome
${url}  https://demo.nopcommerce.com

*** Test Cases ***
LoginTest
    Open Browser   ${url}  ${browser}

    # xpath du logo : //a[@class='ico-login']
    Click Link    xpath://a[@class='ico-login']
    Sleep  3s

    Input Text  name:Email  pavanoltraining@gmail.com
    Sleep  3s

    Input Text  name:Password   Test@123
    Sleep  3s

    Click Element   xpath://button[normalize-space()='Log in']

    Sleep  1h
```
</details>  

# Application LoginTest Keywords

```
*** Settings ***
Library    SeleniumLibrary

*** Variables ***
${browser}  chrome
${url}  https://demo.nopcommerce.com

*** Test Cases ***
LoginTest
    Open Browser   ???  ???
    LoginToApplication
    Sleep  1h

*** Keywords ***
LoginToApplication
    
    Click Link    xpath:???
    Sleep  3s

    # Login by name
    Input Text  name:???  pavanoltraining@gmail.com
    Sleep  3s

    # Password by name
    Input Text  name:???   Test@123
    Sleep  3s
    # Click by xpath
    Click Element   xpath:???]
```

* Corrections

<details>

```
*** Settings ***
Library    SeleniumLibrary

*** Variables ***
${browser}  chrome
${url}  https://demo.nopcommerce.com

*** Test Cases ***
LoginTest
    Open Browser   ${url}  ${browser}
    LoginToApplication
    Sleep  1h

*** Keywords ***
LoginToApplication
    # xpath du login : //a[@class='ico-login']
    Click Link    xpath://a[@class='ico-login']
    Sleep  3s

    Input Text  name:Email  pavanoltraining@gmail.com
    Sleep  3s

    Input Text  name:Password   Test@123
    Sleep  3s
    Click Element   xpath://button[normalize-space()='Log in']
```

</details>

# InputBox 

```
*** Settings ***
Library    SeleniumLibrary

*** Variables ***
${BROWSER}    chrome
${URL}        https://demo.nopcommerce.com
${EMAIL_TXT}  id:Email

*** Test Cases ***
TestingInputBox
    # Open Browser
    Open Browser    ???    ???
    Maximize Browser Window

    # Assertion title
    Title Should Be    ???

    # Click login
    Click Link    xpath:???

    Sleep    2s

    # Assertion visibilty of email
    Element Should Be Visible   ???

    # Assertion if email is enable
    Element Should Be Enabled    ???
    #  Element Should Not Be Enabled    ${EMAIL_TXT}
    Sleep    1h
```

<details>

```
*** Settings ***
Library    SeleniumLibrary

*** Variables ***
${BROWSER}    chrome
${URL}        https://demo.nopcommerce.com
${EMAIL_TXT}  id:Email

*** Test Cases ***
TestingInputBox
    Open Browser    ${URL}    ${BROWSER}
    Maximize Browser Window

    Title Should Be    nopCommerce demo store. Home page title

    Click Link    xpath://a[@class='ico-login']
    Sleep    2s

    Element Should Be Visible    ${EMAIL_TXT}
    Element Should Be Enabled    ${EMAIL_TXT}
    #  Element Should Not Be Enabled    ${EMAIL_TXT}
    Sleep    1h
```


</details>

## Timing : 

* Set selenium speed

```
*** Settings ***
Library    SeleniumLibrary

*** Test Cases ***
RegTest
    Open Browser    https://demowebshop.tricentis.com/register  chrome
    Maximize Browser Window
    # Chaque instruction à partir d'ici attend 3s pour chaque execution
    Set Selenium Speed    3s
    Select Radio Button    Gender  F
    Input Text    name:FirstName  David
    Input Text    name:LastName   John
    Input Text    name:Email   anhc@gmail.com
    Input Text    name:Password   davidjohn
    Input Text    name:ConfirmPassword   davidjohn
    # Click Element    xpath://input[@id='register-button']

    Sleep  1h
```

Avec affichage : 

```
*** Settings ***
Library    SeleniumLibrary


*** Test Cases ***
RegTest
    Open Browser    https://demowebshop.tricentis.com/register  chrome
    Maximize Browser Window
    ${spead}=  get selenium speed
    Log To Console   Temps initial : ${spead}

    # Chaque instruction à partir d'ici attend 3s pour chaque execution
    Set Selenium Speed    2s

    Select Radio Button    Gender  F
    Input Text    name:FirstName  David
    Input Text    name:LastName   John
    Input Text    name:Email   anhc@gmail.com
    Input Text    name:Password   davidjohn
    Input Text    name:ConfirmPassword   davidjohn
    # Click Element    xpath://input[@id='register-button']

    ${spead}=  get selenium speed
    Log To Console   Temps final : ${spead}

    # Sleep  1h
```

# Chargement de page : connaître la valeur de temps timeout par defaut
```
*** Settings ***
Library    SeleniumLibrary


*** Test Cases ***
RegTest
    Open Browser    https://demowebshop.tricentis.com/register  chrome
    Maximize Browser Window
    Wait Until Page Contains    Register
    # ${spead}=  get selenium speed
    # Log To Console   Temps initial : ${spead}

    # Chaque instruction à partir d'ici attend 3s pour chaque execution
    # Set Selenium Speed    2s

     Select Radio Button    Gender  F
     Input Text    name:FirstName  David
     Input Text    name:LastName   John
     Input Text    name:Email   anhc@gmail.com
     Input Text    name:Password   davidjohn
     Input Text    name:ConfirmPassword   davidjohn
    # Click Element    xpath://input[@id='register-button']

    # ${spead}=  get selenium speed
    # Log To Console   Temps final : ${spead}

     Sleep  1h
```
* La valeur est 5s, voir log de ce test 
```
*** Settings ***
Library    SeleniumLibrary


*** Test Cases ***
RegTest
    Open Browser    https://demowebshop.tricentis.com/register  chrome
    Maximize Browser Window
    Wait Until Page Contains    Register123
    # ${spead}=  get selenium speed
    # Log To Console   Temps initial : ${spead}

    # Chaque instruction à partir d'ici attend 3s pour chaque execution
    # Set Selenium Speed    2s

     Select Radio Button    Gender  F
     Input Text    name:FirstName  David
     Input Text    name:LastName   John
     Input Text    name:Email   anhc@gmail.com
     Input Text    name:Password   davidjohn
     Input Text    name:ConfirmPassword   davidjohn
    # Click Element    xpath://input[@id='register-button']

    # ${spead}=  get selenium speed
    # Log To Console   Temps final : ${spead}

     Sleep  3s
```

* Connaitre le 5s en calculant le temps :

```
*** Settings ***
Library    SeleniumLibrary


*** Test Cases ***
RegTest
    Open Browser    https://demowebshop.tricentis.com/register  chrome
    Maximize Browser Window
    Wait Until Page Contains    Register
    ${spead}=  Get Selenium Timeout
    Log To Console   Temps timeout par defaut : ${spead}

    # Chaque instruction à partir d'ici attend 3s pour chaque execution
    # Set Selenium Speed    2s

     Select Radio Button    Gender  F
     Input Text    name:FirstName  David
     Input Text    name:LastName   John
     Input Text    name:Email   anhc@gmail.com
     Input Text    name:Password   davidjohn
     Input Text    name:ConfirmPassword   davidjohn
    # Click Element    xpath://input[@id='register-button']

    # ${spead}=  get selenium speed
    # Log To Console   Temps final : ${spead}

     Sleep  3s
```
## Timining Implicit wait

* Test Implicit wait

```
*** Settings ***
Library    SeleniumLibrary


*** Test Cases ***
RegTest
    Open Browser    https://demowebshop.tricentis.com/register  chrome
    Maximize Browser Window
    Wait Until Page Contains    Register
    # ${spead}=  Get Selenium Timeout
    # Log To Console   Temps timeout par defaut : ${spead}

     Set Selenium Implicit Wait   10s

     Select Radio Button    Gender  F

     # Ajout Erreur
     Input Text    name:FirstName  David

     Input Text    name:LastName   John
     Input Text    name:Email   anhc@gmail.com
     Input Text    name:Password   davidjohn
     Input Text    name:ConfirmPassword   davidjohn
    # Click Element    xpath://input[@id='register-button']

    # ${spead}=  get selenium speed
    # Log To Console   Temps final : ${spead}

     Sleep  3s
```

* Implicit wait en calculant le temps de fonctionnement

```
*** Settings ***
Library    SeleniumLibrary


*** Test Cases ***
RegTest
    Open Browser    https://demowebshop.tricentis.com/register  chrome
    Maximize Browser Window
    Wait Until Page Contains    Register

    ${spead}=  Get Selenium Implicit Wait
    Log To Console   Temps Implicit wait par defaut : ${spead}

     Set Selenium Implicit Wait   10s

     Select Radio Button    Gender  F

     # Ajout Erreur
     Input Text    name:FirstName  David

     Input Text    name:LastName   John
     Input Text    name:Email   anhc@gmail.com
     Input Text    name:Password   davidjohn
     Input Text    name:ConfirmPassword   davidjohn
    # Click Element    xpath://input[@id='register-button']

    ${spead}=  Get Selenium Implicit Wait
    Log To Console   Temps Implicit wait final : ${spead}

     Sleep  3s

```

## Exercices Radio button
# Simple RadioButton : 

```
*** Settings ***
Library    SeleniumLibrary
Suite Teardown    Close All Browsers

*** Variables ***
${BROWSER}    chrome
${URL}        https://testpages.herokuapp.com/styled/basic-html-form-test.html

*** Test Cases ***
SelectRadioButton_Option1
    Open Browser    ${URL}    ${BROWSER}
    Maximize Browser Window
    Sleep    2s

    # Selection RadioButton 1
    Select Radio Button    ???    ???
    # Assertion pour radio button
    Radio Button Should Be Set To    ???    ???

    Sleep    2s
    Close Browser


SelectRadioButton_Option2
    Open Browser    ${URL}    ${BROWSER}
    Maximize Browser Window
    Sleep    2s

    # Selection RadioButton 2
    Select Radio Button    ???    ???
    # Assertion pour radio button
    Radio Button Should Be Set To    ???    ???


SelectRadioButton_Option3
    Open Browser    ${URL}    ${BROWSER}
    Maximize Browser Window
    Sleep    2s

    # Selection RadioButton 2
    Select Radio Button    ???    ???
    # Assertion pour radio button
    Radio Button Should Be Set To    ???    ???
    Sleep    2s

    Close Browser
```

<details>

```
*** Settings ***
Library    SeleniumLibrary
Suite Teardown    Close All Browsers

*** Variables ***
${BROWSER}    chrome
${URL}        https://testpages.herokuapp.com/styled/basic-html-form-test.html

*** Test Cases ***
SelectRadioButton_Option1
    Open Browser    ${URL}    ${BROWSER}
    Maximize Browser Window
    Sleep    2s

    Select Radio Button    radioval    rd1
    Radio Button Should Be Set To    radioval    rd1
    Sleep    2s
    Close Browser


SelectRadioButton_Option2
    Open Browser    ${URL}    ${BROWSER}
    Maximize Browser Window
    Sleep    2s

    Select Radio Button    radioval    rd2
    Radio Button Should Be Set To    radioval    rd2
    Sleep    2s
    Close Browser


SelectRadioButton_Option3
    Open Browser    ${URL}    ${BROWSER}
    Maximize Browser Window
    Sleep    2s

    Select Radio Button    radioval    rd3
    Radio Button Should Be Set To    radioval    rd3
    Sleep    2s
    Close Browser
```

</details>

## Exercice copie coller
```
*** Settings ***
Library    SeleniumLibrary

*** Variables ***
${URL1}    https://example.com
${URL2}    https://testpages.herokuapp.com/styled/basic-html-form-test.html

*** Test Cases ***
Copier Coller Entre Deux Navigateurs
    # Ouvrir premier navigateur
    Open Browser    ${URL1}    chrome
    Maximize Browser Window

    # Récupérer le texte de la page
    ${texte}=    Get Text    xpath=//h1

    Log    Texte récupéré : ${texte}

    # Ouvrir un deuxième navigateur
    Open Browser    ${URL2}    firefox
    Maximize Browser Window

    # Coller le texte dans le champ "username"
    Input Text    name=username    ${texte}

    # Petite vérification
    ${valeur}=    Get Value    name=username
    Should Be Equal    ${valeur}    ${texte}
``` 
