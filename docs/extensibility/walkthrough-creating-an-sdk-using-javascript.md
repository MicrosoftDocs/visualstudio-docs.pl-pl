---
title: 'Przewodnik: Tworzenie sdk przy użyciu języka JavaScript | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: a8c89d5d-5b78-4435-817f-c5f25ca6d715
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f3a3fa110bd6521443521449898474299dd267d6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697505"
---
# <a name="walkthrough-create-an-sdk-using-javascript"></a>Instruktaż: tworzenie sdk przy użyciu języka JavaScript
W tym przewodniku uczy się, jak używać javascript do tworzenia prostego sdk matematycznych jako rozszerzenia programu Visual Studio (VSIX).  Instruktaż jest podzielony na następujące części:

- [Aby utworzyć projekt SDK rozszerzenia SimpleMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSimpleMathVSIX)

- [Aby utworzyć przykładową aplikację, która używa sdk](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSampleApp)

  W przypadku języka JavaScript nie ma typu projektu biblioteki klas. W tym instruktażu przykładowy plik *arithmetic.js* jest tworzony bezpośrednio w projekcie VSIX. W praktyce zaleca się najpierw skompilować i przetestować pliki JavaScript i CSS jako aplikację ze Sklepu Windows — na przykład przy użyciu szablonu **pustej aplikacji** — zanim umieścisz je w projekcie VSIX.

## <a name="prerequisites"></a>Wymagania wstępne
 Aby wykonać ten przewodnik, należy zainstalować visual studio SDK. Aby uzyskać więcej informacji, zobacz [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="to-create-the-simplemathvsix-extension-sdk-project"></a><a name="createSimpleMathVSIX"></a>Aby utworzyć projekt SDK rozszerzenia SimpleMathVSIX

1. Na pasku menu wybierz pozycję **Plik** > **nowego** > **projektu**.

2. Na liście kategorii szablonów w obszarze **Visual C#** wybierz pozycję **Rozszerzalność**, a następnie wybierz szablon **projektu VSIX.**

3. W **Name** polu tekstowym `SimpleMathVSIX` Nazwa określ i wybierz przycisk **OK.**

4. Jeśli pojawi się **Kreator pakietów programu Visual Studio,** wybierz przycisk **Dalej** na stronie **powitalnej,** a następnie na **stronie 1 z 7**wybierz przycisk **Zakończ.**

     Mimo że **projektant manifestu** otwiera, będziemy zachować ten przewodnik proste, modyfikując plik manifestu bezpośrednio.

5. W **Eksploratorze rozwiązań**otwórz menu skrótów dla pliku **source.extension.vsixmanifest,** a następnie wybierz polecenie **Wyświetl kod**. Ten kod służy do zastępowania istniejącej zawartości w pliku.

    ```xml
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

6. W **Eksploratorze rozwiązań**otwórz menu skrótów dla projektu **SimpleMathVSIX,** a następnie wybierz pozycję **Dodaj** > **nowy element**.

7. W kategorii **Dane** wybierz **plik XML**, `SDKManifest.xml`nazwij plik i wybierz przycisk **Dodaj.**

8. W **Eksploratorze rozwiązań**otwórz menu skrótów dla pliku **SDKManifest.xml,** a następnie wybierz pozycję **Otwórz,** aby wyświetlić plik w **Edytorze XML**.

9. Dodaj następujący kod do pliku **SDKManifest.xml.**

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <FileList
      DisplayName="Simple Math"
      MinVSVersion="14.0"
      AppliesTo="JavaScript+WindowsAppContainer"
      SupportsMultipleVersions="Error"
      MoreInfo="https://msdn.microsoft.com/">

      <!-- JS -->
      <File Content="js\arithmetic.js" />
    </FileList>

    ```

10. W **Eksploratorze rozwiązań**w menu skrótów dla pliku **SDKManifest.xml** wybierz polecenie **Właściwości**.

11. W oknie **Właściwości** ustaw właściwość **Uwzględnij w VSIX** na **True**.

12. W **Eksploratorze rozwiązań**w menu skrótów dla projektu **SimpleMathVSIX** `Redist`wybierz pozycję **Dodaj** > nowy**folder,** a następnie nazwij folder .

13. Dodaj podfoldery w obszarze Redist, aby utworzyć tę strukturę folderów:

     *\Redist\CommonConfiguration\Neutral\SimpleMath\js\\*

14. W menu skrótów w folderze **\js\\ ** wybierz polecenie **Dodaj** > **nowy element**.

15. W obszarze **Elementy programu Visual C#** wybierz kategorię **Sieć Web,** a następnie wybierz element **Plik JavaScript.** Nazwij `arithmetic.js`plik , a następnie wybierz przycisk **Dodaj.**

16. Wstaw następujący kod do *pliku arithmetic.js:*

    ```csharp
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

17. W **Eksploratorze rozwiązań**w menu skrótów pliku **arithmetic.js** wybierz polecenie **Właściwości**. Wprowadzać następujące zmiany właściwości:

    - Ustaw właściwość **Uwzględnij w VSIX** na **True**.

    - Ustaw właściwość **Kopiuj na Katalog wyjściowy** na **Kopiuj zawsze**.

18. W **Eksploratorze rozwiązań**w menu skrótów dla projektu **SimpleMathVSIX** wybierz polecenie **Buduj**.

19. Po pomyślnym zakończeniu kompilacji w menu skrótów dla projektu wybierz polecenie **Otwórz folder w Eksploratorze plików**. Przejdź do **\bin\debug\\** `SimpleMathVSIX.vsix` i uruchom, aby go zainstalować.

20. Wybierz przycisk **Zainstaluj** i pozwól na zakończenie instalacji.

21. Uruchom ponownie program Visual Studio.

## <a name="to-create-a-sample-app-that-uses-the-sdk"></a><a name="createSampleApp"></a>Aby utworzyć przykładową aplikację, która używa sdk

1. Na pasku menu wybierz pozycję **Plik** > **nowego** > **projektu**.

2. Na liście kategorii szablonów w obszarze **JavaScript**wybierz pozycję **Sklep Windows**, a następnie wybierz szablon **Pusta aplikacja.**

3. W polu **Nazwa** `ArithmeticUI`określ . Wybierz przycisk **OK.**

4. W **Eksploratorze rozwiązań**otwórz menu skrótów dla projektu **ArithmeticUI,** a następnie wybierz pozycję **Dodaj** > **odwołanie**.

5. W obszarze **Windows**wybierz pozycję **Rozszerzenia**i zwróć uwagę, że wyświetlana jest **prosta matematyka.**

6. Zaznacz pole wyboru **Prosta matematyka,** a następnie wybierz przycisk **OK.**

7. W **Eksploratorze rozwiązań**w obszarze **Odwołania**zwróć uwagę, że jest wyświetlane odwołanie **do prostej matematyki.** Rozwiń go i zwróć uwagę, że istnieje folder **\js,\\ ** który zawiera **plik arithmetic.js**. Można otworzyć **plik arithmetic.js,** aby potwierdzić, że kod źródłowy został zainstalowany.

8. Użyj następującego kodu, aby zastąpić zawartość *pliku default.htm*.

   ```html
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

9. Użyj następującego kodu, aby zastąpić zawartość *pliku \js\default.js*.

    ```csharp
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

10. Zastąp zawartość *\css\default.css* za pomocą tego kodu:

    ```xml
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

11. Wybierz klawisz **F5,** aby utworzyć i uruchomić aplikację.

12. W interfejsie użytkownika aplikacji wprowadź dowolne dwie liczby, **=** wybierz operację, a następnie wybierz przycisk. Pojawi się poprawny wynik.

## <a name="see-also"></a>Zobacz też
- [Tworzenie zestawu SDK](../extensibility/creating-a-software-development-kit.md)
