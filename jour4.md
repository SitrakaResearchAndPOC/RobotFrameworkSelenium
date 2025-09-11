## Portée variable keyword personnalisé : TC


```
*** Settings ***
Library    SeleniumLibrary

*** Variables ***
${URL1}    https://google.com
${URL2}    https://youtube.com


*** Test Cases ***
TC1
#    OpenBrowserTC1
     OpenBrowserTC    ${URL1}  


TC2
    #OpenBrowserTC2
     OpenBrowserTC    ${URL2}  

*** Keywords ***
# OpenBrowserTC1
#    Log To Console    valeur de url dans TC1: ${URL1}
#    Open Browser    ${URL1}   chrome
    
    
# OpenBrowserTC2
#    Log To Console    valeur de url dans TC2: ${URL2}
#    Open Browser    ${URL2}   chrome
    
OpenBrowserTC
    [Arguments]    ${URL}
    Log To Console    valeur de url dans TC: ${URL}
    Open Browser    ${URL}   chrome       
 
 ```

## Temps d'attente
```
*** Settings ***
Library   SeleniumLibrary

**** Variables ***
${BROWSER}    chrome
${URL}     https://opensource-demo.orangehrmlive.com
${USER}     Admin
${PASS}    admin123

${EXPECTED_WORD}   Time at Work

*** Test Cases ***
TC1
     Open Browser     ${URL}     ${BROWSER}
     Sleep    2s 
     Input Text       name:username    ${USER}
    Sleep    2s 
    Input Text     name:password     ${PASS}
    Sleep    2s 
    Click Element    xpath://button[@type='submit'] 
    Sleep   2s 
    # Assertions : 
    Page Should Contain   ${EXPECTED_WORD} 
    Sleep    4s
```

## Explicit wait

```
*** Settings ***
Library    SeleniumLibrary

**** Variables ***
${BROWSER}    chrome
${URL}     https://opensource-demo.orangehrmlive.com
${USER}     Admin
${PASS}    admin123
${EXPECTED_WORD}      Time at Work

*** Test Cases ***
TC1
     Open Browser     ${URL}     ${BROWSER}
     Wait Until Element Is Visible    name:username     10s

     Set Selenium Speed    2s

     Input Text       name:username    ${USER}
     Input Text     name:password     ${PASS}
     Click Element    xpath://button[@type='submit']

     Wait Until Page Contains       ${EXPECTED_WORD}   10s
     # Sleep   10s
     # Assertions :
     # Page Should Contain   ${EXPECTED_WORD}
     # Sleep    4s
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
