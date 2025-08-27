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


