# RobotFrameworkSelenium

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

     Sleep  1h
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

     Sleep  1h
```

