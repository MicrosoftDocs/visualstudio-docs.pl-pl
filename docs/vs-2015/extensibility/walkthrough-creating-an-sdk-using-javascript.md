---
title: 'Przewodnik: Tworzenie zestawu SDK przy użyciu języka JavaScript | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: a8c89d5d-5b78-4435-817f-c5f25ca6d715
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3e953d9051b9bc7e95dc29e02eb580c4d93fca26
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60066952"
---
# <a name="walkthrough-creating-an-sdk-using-javascript"></a>Przewodnik: Tworzenie zestawu SDK przy użyciu języka JavaScript
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym przewodniku pokazano, jak utworzyć proste matematyczne SDK jako programu Visual Studio rozszerzenia (VSIX) za pomocą języka JavaScript.  Instruktażu jest podzielony na te części:  
  
- [Aby utworzyć projekt zestawu SDK rozszerzenia SimpleMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSimpleMathVSIX)  
  
- [Aby utworzyć przykładową aplikację, która korzysta z zestawu SDK](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSampleApp)  
  
  Dla języka JavaScript nie ma żadnych typów projektów biblioteki klas. W tym przewodniku utworzono przykładowy plik arithmetic.js, bezpośrednio w projekcie VSIX. W praktyce, zalecamy najpierw kompilacji i testowania plików JavaScript i CSS jako aplikację Windows Store — na przykład za pomocą **pusta aplikacja** szablonu — przed wprowadzeniem w projekcie VSIX.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby skorzystać z tego przewodnika, należy zainstalować program Visual Studio SDK. Aby uzyskać więcej informacji, zobacz [programu Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="createSimpleMathVSIX"></a> Aby utworzyć projekt zestawu SDK rozszerzenia SimpleMathVSIX  
  
1. Na pasku menu wybierz **pliku**, **New**, **projektu**.  
  
2. Na liście kategorii szablonu w obszarze **Visual C#**, wybierz opcję **rozszerzalności**, a następnie wybierz pozycję **projekt VSIX** szablonu.  
  
3. W **nazwa** tekstu określ `SimpleMathVSIX` i wybierz polecenie **OK** przycisku.  
  
4. Jeśli **Kreator pakietu Visual Studio** zostanie wyświetlona, wybierz **dalej** znajdujący się na **powitalnej** strony, a następnie na **strona 1 z 7**, wybierz **Zakończ** przycisku.  
  
     Mimo że **Manifest Designer** zostanie otwarta, zachowamy w tym przewodniku prosty, modyfikując plik manifestu bezpośrednio.  
  
5. W **Eksploratora rozwiązań**, otwórz menu skrótów dla pliku source.extension.vsixmanifest, a następnie wybierz **Wyświetl kod**. Użyj tego kodu, aby zastąpić istniejącą zawartość w pliku.  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011">  
      <Metadata>  
        <Identity Id="SimpleMathVSIX" Version="1.0" Language="en-US" Publisher="myname" />  
        <DisplayName>Simple Math</DisplayName>  
        <Description>Does basic arithmetic calculations.</Description>  
      </Metadata>  
      <Installation Scope="Global" AllUsers="true">  
        <InstallationTarget Id="Microsoft.ExtensionSDK" TargetPlatformIdentifier="Windows" TargetPlatformVersion="v8.0" SdkName="SimpleMath" SdkVersion="1.0" />  
      </Installation>  
      <Dependencies>  
        <Dependency Id="Microsoft.Framework.NDP" DisplayName="Microsoft .NET Framework" d:Source="Manual" Version="4.5" />  
      </Dependencies>  
      <Assets>  
        <Asset Type="Microsoft.ExtensionSDK" d:Source="File" Path="SDKManifest.xml" />  
      </Assets>  
    </PackageManifest>  
    ```  
  
6. W **Eksploratora rozwiązań**, otwórz menu skrótów dla projektu SimpleMathVSIX, a następnie wybierz **Dodaj**, **nowy element**.  
  
7. W **danych** kategorii, wybierz opcję **pliku XML**, nadaj plikowi nazwę `SDKManifest.xml`i wybierz polecenie **Dodaj** przycisku.  
  
8. W **Eksploratora rozwiązań**, otwórz menu skrótów dla pliku SDKManifest.xml, a następnie wybierz **Otwórz** do wyświetlenia pliku w **edytora XML**.  
  
9. Dodaj następujący kod do pliku SDKManifest.xml.  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <FileList  
      DisplayName="Simple Math"  
      MinVSVersion="14.0"  
      AppliesTo="JavaScript+WindowsAppContainer"  
      SupportsMultipleVersions="Error"  
      MoreInfo="http://www.msdn.microsoft.com/">  
  
      <!-- JS -->  
      <File Content="js\arithmetic.js" />  
    </FileList>  
  
    ```  
  
10. W **Eksploratora rozwiązań**, w menu skrótów dla pliku SDKManifest.xml wybierz **właściwości**.  
  
11. W **właściwości** oknie **Include w VSIX** właściwości **True**.  
  
12. W **Eksploratora rozwiązań**, w menu skrótów dla projektu SimpleMathVSIX wybierz **Dodaj**, **nowy Folder**, a następnie nadaj mu nazwę `Redist`.  
  
13. Dodaj podfoldery Redist do utworzenia tej struktury folderów:  
  
     \Redist\CommonConfiguration\Neutral\SimpleMath\js\  
  
14. W menu skrótów dla folderu \js\ wybierz **Dodaj**, **nowy element**.  
  
15. W obszarze **elementy Visual C#**, wybierz opcję **Web** kategorii, a następnie wybierz **plik JavaScript** elementu. Nadaj plikowi nazwę `arithmetic.js`, a następnie wybierz **Dodaj** przycisku.  
  
16. Wstaw następujący kod do arithmetic.js:  
  
    ```  
    (function (global) {  
        "use strict";  
        global.Arithmetic = {  
            add: function (firstNumber, secondNumber) {  
                return firstNumber + secondNumber;  
            },  
  
            subtract: function (firstNumber, secondNumber) {  
                return firstNumber - secondNumber;  
            },  
  
            multiply: function (firstNumber, secondNumber) {  
                return firstNumber * secondNumber;  
            },  
  
            divide: function (firstNumber, secondNumber) {  
                return firstNumber / secondNumber;  
            }  
        };  
    })(this);  
  
    ```  
  
17. W **Eksploratora rozwiązań**, w menu skrótów dla pliku arithmetic.js wybierz **właściwości**. Dokonaj następujących zmian właściwości:  
  
    - Ustaw **Include w VSIX** właściwości **True**.  
  
    - Ustaw **Kopiuj do katalogu wyjściowego** właściwości **zawsze Kopiuj**.  
  
18. W **Eksploratora rozwiązań**, w menu skrótów dla projektu SimpleMathVSIX wybierz **kompilacji**.  
  
19. Po kompilacji zakończy się pomyślnie, w menu skrótów dla projektu, wybierz **Otwórz Folder w Eksploratorze plików**. Przejdź do \bin\debug\\i uruchom `SimpleMathVSIX.vsix` go zainstalować.  
  
20. Wybierz **zainstalować** przycisku, dzięki czemu instalacja zakończona.  
  
21. Uruchom ponownie program Visual Studio.  
  
## <a name="createSampleApp"></a> Aby utworzyć przykładową aplikację, która korzysta z zestawu SDK  
  
1. Na pasku menu wybierz **pliku**, **New**, **projektu**.  
  
2. Na liście kategorii szablonu w obszarze **JavaScript**, wybierz opcję **Windows Store**, a następnie wybierz pozycję **pusta aplikacja** szablonu.  
  
3. W **nazwa** określ `ArithmeticUI`. Wybierz **OK** przycisku.  
  
4. W **Eksploratora rozwiązań**, otwórz menu skrótów dla projektu ArithmeticUI, a następnie wybierz **Dodaj**, **odwołania**.  
  
5. W obszarze **Windows**, wybierz **rozszerzenia**i zwróć uwagę, że **proste matematyczne** jest wyświetlana.  
  
6. Wybierz **proste matematyczne** pole wyboru, a następnie wybierz **OK** przycisku.  
  
7. W **Eksploratora rozwiązań**w obszarze **odwołania**, zwróć uwagę, że **proste matematyczne** odwołanie jest wyświetlana. Rozwiń ją, a następnie zwróć uwagę, że jest folderu \js\, który zawiera arithmetic.js. Możesz otworzyć arithmetic.js, aby upewnić się, że kod źródłowy został zainstalowany.  
  
8. Użyj poniższego kodu, aby zastąpić zawartość default.htm.  
  
    ```  
    <!DOCTYPE html>  
    <html>  
    <head>  
        <meta charset="utf-8" />  
        <title>ArithmeticUI</title>  
  
        <!-- WinJS references -->  
        <link href="//Microsoft.WinJS.1.0/css/ui-dark.css" rel="stylesheet" />  
        <script src="//Microsoft.WinJS.1.0/js/base.js"></script>  
        <script src="//Microsoft.WinJS.1.0/js/ui.js"></script>  
  
        <!-- ArithmeticUI references -->  
        <link href="/css/default.css" rel="stylesheet" />  
        <script src="/js/default.js"></script>  
        <script src="/SimpleMath/js/arithmetic.js"></script>  
    </head>  
    <body>  
        <form>  
        <div id="calculator" class="ms-grid">  
            <input name="firstNumber" id="firstNumber" type="number" step="any">  
            <div id="operators">  
                <button class="operator" type="button">+</button>  
                <button class="operator" type="button">-</button>  
                <button class="operator" type="button">*</button>  
                <button class="operator" type="button">/</button>  
            </div>  
            <input id="secondNumber" type="number">  
            <button class="calculate" type="button">=</button>  
            <input id="result" type="number" name="result" disabled="" readonly="">  
        </div>  
        </form>  
    </body>  
    </html>  
    ```  
  
9. Umożliwia zastąpienie zawartości \js\default.js kolejnego kodu.  
  
    ```  
    (function () {  
        "use strict";  
  
        var app = WinJS.Application;  
        var operation = null;  
  
        function calculateResult() {  
            var firstNumber = parseFloat(document.querySelector("#firstNumber").value),  
                secondNumber = parseFloat(document.querySelector("#secondNumber").value),  
                result = 0;  
  
            if (isNaN(firstNumber) || isNaN(secondNumber)) {  
                result = 0;  
            }  
            else {  
                switch (operation) {  
                    case "+":  
                        result = Arithmetic.add(firstNumber, secondNumber);  
                        break;  
                    case "-":  
                        result = Arithmetic.subtract(firstNumber, secondNumber);  
                        break;  
                    case "*":  
                        result = Arithmetic.multiply(firstNumber, secondNumber);  
                        break;  
                    case "/":  
                        result = Arithmetic.divide(firstNumber, secondNumber);  
                        break;  
                    default:  
                }  
            }  
            document.querySelector("#result").value = result.toString();  
        }  
  
        app.onactivated = function (args) {  
            document.querySelector("#calculator").addEventListener("click", function (event) {  
                if (event.target.tagName.toLowerCase() === "button") {  
                    switch (event.target.className) {  
                        case "operator":  
                            operation = event.target.innerText;  
                            break;  
                        case "calculate":  
                            calculateResult();  
                            break;  
                        default:  
                            break;  
                    }  
                }  
            });  
        };  
  
        app.start();  
    })();  
    ```  
  
10. Zastąp zawartość \css\default.css przy użyciu tego kodu:  
  
    ```  
    form {  
        display: -ms-grid;  
        -ms-grid-rows: 1fr auto 1fr;  
        -ms-grid-columns: 1fr auto 1fr;  
        height: 100%;  
        width: 100%;  
    }  
  
    button, input[type=number] {  
        margin-right: 5px;  
        -ms-grid-row-align: center;  
    }  
  
    #calculator {  
        -ms-grid-column: 2;  
        -ms-grid-row: 2;  
        display: -ms-grid;  
        -ms-grid-rows: 1fr;  
        -ms-grid-columns: auto min-content auto auto auto;  
    }  
  
    .ms-grid input {  
        width: 5em;  
    }  
  
    #firstNumber {  
        -ms-grid-column: 1;  
        -ms-grid-row-align: center;  
    }  
  
    #operators {  
        -ms-grid-column: 2;  
        -ms-grid-row-align: center;  
    }  
  
        #operators button.operator {  
            margin-bottom: 5px;  
            height: 40px;  
        }  
  
    #secondNumber {  
        -ms-grid-column: 3;  
    }  
  
    button.calculate {  
        -ms-grid-column: 4;  
        -ms-grid-row-align: center;  
        height: 40px;  
    }  
  
    #result {  
        -ms-grid-column: 5;  
    }  
  
    ```  
  
11. Wybierz klawisz F5, aby skompilować i uruchomić aplikację.  
  
12. W interfejsie użytkownika aplikacji, wprowadź dowolne dwie liczby, umożliwia wybranie operacji, a następnie wybierz **=** przycisku. Zostanie wyświetlony odpowiedni wynik.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie zestawu SDK](../extensibility/creating-a-software-development-kit.md)
