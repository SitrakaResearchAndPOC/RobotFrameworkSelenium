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
````
pip install playwright
````
````
playwright install
````

Installer plugin : Hyper roboframework

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

* With edge

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

* With firefox

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

# Application LoginTest Keywords
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

## RadioButton avec publicités
```
*** Settings ***
Library    SeleniumLibrary

*** Test Cases ***
test1
    # Ouvre Edge et attend que la page soit complètement chargée
    Open Browser    https://demoqa.com/automation-practice-form    edge
    Maximize Browser Window
    Wait Until Page Contains Element    xpath://form[@id="userForm"]    timeout=10s

    # Select Radio Button    gender  Male
    Click Element    xpath://label[@for="gender-radio-1"]
    Sleep  2s

    # Sélection de la case Hobbies (Sports)
    Wait Until Element Is Visible    xpath://label[@for="hobbies-checkbox-3"]    timeout=10s
    Scroll Element Into View    xpath://label[@for="hobbies-checkbox-3"]
    Click Element    xpath://label[@for="hobbies-checkbox-3"]
    Sleep  3s

    [Teardown]    Close Browser

```


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

## Handle alert


```
*** Settings ***
Library    SeleniumLibrary

*** Variables ***
${BROWSER}    chrome
${URL}        https://the-internet.herokuapp.com/javascript_alerts

*** Test Cases ***
Test Simple Alert
    Open Browser    ${URL}    ${BROWSER}
    Click Button    xpath=//button[text()="Click for JS Alert"]
    Handle Alert    action=ACCEPT
    Page Should Contain    You successfully clicked an alert

Test Confirm Alert
    Open Browser    ${URL}    ${BROWSER}
    Click Button    xpath=//button[text()="Click for JS Confirm"]
    Handle Alert    action=DISMISS
    Page Should Contain    You clicked: Cancel

Test Prompt Alert
    Open Browser    ${URL}    ${BROWSER}
    Click Button    xpath=//button[text()="Click for JS Prompt"]
    Handle Alert    action=ACCEPT    prompt=RobotFramework
    Page Should Contain    You entered: RobotFramework
```


## Multiple browser
```

*** Settings ***
Library    SeleniumLibrary


*** Test Cases ***
MyTestCase
    Open Browser    https://demowebshop.tricentis.com/register   chrome
    Maximize Browser Window

    Open Browser    https://google.com  chrome
    Maximize Browser Window

    Sleep  30s
    # close
    Close Browser
```


## IFRAME Radiobutton
```
*** Settings ***
Library    SeleniumLibrary
Suite Teardown    Close All Browsers

*** Variables ***
${BROWSER}    chrome
${URL}        https://www.w3schools.com/html/tryit.asp?filename=tryhtml_input_radio

*** Test Cases ***
RadioButton_W3Schools
    Open Browser    ${URL}    ${BROWSER}
    Maximize Browser Window
    Sleep    10s

    # Entrer dans l'iframe
    Select Frame    xpath://iframe[@id='iframeResult']

    Select Radio Button    fav_language    HTML
    Radio Button Should Be Set To    fav_language    HTML

    Unselect Frame
    Sleep    1h
```
## NoCode Playwright testing
```
playwright codegen https://demoqa.com/automation-practice-form --target=python --output demoqa_form1.py
```
```
python demoqa_form1.py
```
```
playwright codegen https://opensource-demo.orangehrmlive.com/web/index.php/auth/login --target=python --output demoqa_form2.py
```
```
python demoqa_form2.py
```
```
playwright codegen  --help
```
```
playwright codegen  https://demoblaze.com/index.html --browser=firefox
```
```
playwright codegen  https://demoblaze.com/index.html --device="iphone 13"
```
```
playwright codegen  https://demoblaze.com/index.html --viewport-size="1280,720"
```
## AI Driven Test Code + TDD
* Install plugin copilot on pycharm
* login on github.com + add with copilot on pycharm
* Add this context with copilot
```
You are a Playwright test generator.
You are provided with a scenario and your task is to generate a Playwright test for it.
DO NOT generate the test code based on the scenario alone.
Run each step one by one using the tools provided by the Playwright MCP.
Only after completing all steps, generate a Playwright TypeScript test that utilizes @playwright/test based on the message history.
Save the generated test file in the tests directory.
Execute the test file and iterate until the test passes.
```
# Ressources

* [jour1](https://www.youtube.com/playlist?list=PLUDwpEzHYYLseflPNg0bUKfLmAbO2JnE9)
* [jour2_jour3](https://www.youtube.com/playlist?list=PLUDwpEzHYYLsCHiiihnwl3L0xPspL7BPG)
* [jour4_1](https://www.youtube.com/watch?v=T0CT2xxC3JM)
* [jour4_2](https://www.youtube.com/watch?v=cvQFtzj8Qmo)
* [jour4_3](https://www.youtube.com/watch?v=cNh3_r6UjKk)
* [jour4_5](https://www.youtube.com/watch?v=paSwmp-z9wc)
* [jour4_6](https://www.youtube.com/watch?v=FGwtDhjnBMc)
* [jour4_7](https://www.youtube.com/watch?v=E2DEHOEbzks&pp=0gcJCbIJAYcqIYzv)
* [jour4_8](https://www.youtube.com/watch?v=blmnQN7YY00&pp=0gcJCbIJAYcqIYzv)
* [sites_testing1](https://demoqa.com/automation-practice-form)
