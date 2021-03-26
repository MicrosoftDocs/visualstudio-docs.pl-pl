---
title: 'Przewodnik: Tworzenie zestawu SDK przy użyciu języka JavaScript | Microsoft Docs'
description: Dowiedz się, jak używać języka JavaScript do tworzenia prostego zestawu SDK matematycznego jako rozszerzenia programu Visual Studio za pomocą tego przewodnika.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: a8c89d5d-5b78-4435-817f-c5f25ca6d715
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 3b9a3d9e84731fe0c2526b69f60cdda1b1487583
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105080388"
---
# <a name="walkthrough-create-an-sdk-using-javascript"></a>Przewodnik: Tworzenie zestawu SDK przy użyciu języka JavaScript
W tym instruktażu przedstawiono sposób użycia języka JavaScript w celu utworzenia prostego zestawu Math SDK jako rozszerzenia programu Visual Studio (VSIX).  Przewodnik jest podzielony na te części:

- [Aby utworzyć projekt zestawu SDK rozszerzenia SimpleMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSimpleMathVSIX)

- [Aby utworzyć przykładową aplikację korzystającą z zestawu SDK](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSampleApp)

  W przypadku języka JavaScript nie istnieje typ projektu biblioteki klas. W tym instruktażu przykładowy plik *arithmetic.js* jest tworzony bezpośrednio w projekcie VSIX. W programie zaleca się, aby najpierw skompilować i przetestować pliki JavaScript i CSS jako aplikację ze sklepu Windows — na przykład przy użyciu szablonu **pustej aplikacji** — przed umieszczeniem ich w projekcie VSIX.

## <a name="prerequisites"></a>Wymagania wstępne
 Aby wykonać czynności opisane w tym przewodniku, należy zainstalować Visual Studio SDK. Aby uzyskać więcej informacji, zobacz [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="to-create-the-simplemathvsix-extension-sdk-project"></a><a name="createSimpleMathVSIX"></a> Aby utworzyć projekt zestawu SDK rozszerzenia SimpleMathVSIX

1. Na pasku menu wybierz pozycję **plik**  >  **Nowy**  >  **projekt**.

2. Na liście kategorii szablonów w obszarze **Visual C#** wybierz pozycję **rozszerzalność**, a następnie wybierz szablon **projektu VSIX** .

3. W polu tekstowym **Nazwa** Określ `SimpleMathVSIX` i wybierz przycisk **OK** .

4. Jeśli zostanie wyświetlony **Kreator pakietu programu Visual Studio** , wybierz przycisk **dalej** na stronie **powitalnej** , a następnie na **stronie 1.7** wybierz przycisk **Zakończ** .

     Mimo że **projektant manifestu** zostanie otwarty, utrzymujemy ten Instruktaż, modyfikując plik manifestu bezpośrednio.

5. W **Eksplorator rozwiązań** Otwórz menu skrótów dla pliku **source. Extension. vsixmanifest** , a następnie wybierz polecenie **Wyświetl kod**. Użyj tego kodu, aby zastąpić istniejącą zawartość pliku.

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

6. W **Eksplorator rozwiązań** Otwórz menu skrótów dla projektu **SimpleMathVSIX** , a następnie wybierz polecenie **Dodaj**  >  **nowy element**.

7. W kategorii **dane** wybierz pozycję **plik XML**, Nazwij plik `SDKManifest.xml` , a następnie wybierz przycisk **Dodaj** .

8. W **Eksplorator rozwiązań** Otwórz menu skrótów dla pliku **SDKManifest.xml** , a następnie wybierz **Otwórz** , aby wyświetlić plik w **edytorze XML**.

9. Dodaj następujący kod do pliku **SDKManifest.xml** .

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

10. W **Eksplorator rozwiązań**, w menu skrótów dla pliku **SDKManifest.xml** , wybierz **Właściwości**.

11. W oknie **Właściwości** ustaw właściwość **include in VSIX** na **wartość true**.

12. W **Eksplorator rozwiązań**, w menu skrótów dla projektu **SimpleMathVSIX** , wybierz polecenie **Dodaj**  >  **Nowy folder**, a następnie Nazwij folder `Redist` .

13. Dodaj podfoldery w ramach Redist, aby utworzyć tę strukturę folderów:

     *\Redist\CommonConfiguration\Neutral\SimpleMath\js\\*

14. W menu skrótów dla folderu **\js \\** wybierz pozycję **Dodaj**  >  **nowy element**.

15. W obszarze **elementy Visual C#** wybierz kategorię **Sieć Web** , a następnie wybierz element **plik JavaScript** . Nazwij plik `arithmetic.js` , a następnie wybierz przycisk **Dodaj** .

16. Wstaw następujący kod do *arithmetic.js*:

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

17. W **Eksplorator rozwiązań**, w menu skrótów dla pliku **arithmetic.js** , wybierz **Właściwości**. Wprowadź te zmiany właściwości:

    - Ustaw właściwość **include in VSIX** na **wartość true**.

    - Ustaw wartość właściwości **Kopiuj do katalogu wyjściowego** na **zawsze Kopiuj**.

18. W **Eksplorator rozwiązań**, w menu skrótów dla projektu **SimpleMathVSIX** , wybierz polecenie **Kompiluj**.

19. Po pomyślnym zakończeniu kompilacji w menu skrótów projektu wybierz polecenie **Otwórz folder w Eksploratorze plików**. Przejdź do **\bin\debug \\**, a następnie uruchom polecenie, `SimpleMathVSIX.vsix` Aby go zainstalować.

20. Wybierz przycisk **Instaluj** i pozwól na ukończenie instalacji.

21. Uruchom ponownie program Visual Studio.

## <a name="to-create-a-sample-app-that-uses-the-sdk"></a><a name="createSampleApp"></a> Aby utworzyć przykładową aplikację korzystającą z zestawu SDK

1. Na pasku menu wybierz pozycję **plik**  >  **Nowy**  >  **projekt**.

2. Na liście kategorii szablonów w obszarze **JavaScript** wybierz pozycję **Sklep Windows**, a następnie wybierz szablon **pustej aplikacji** .

3. W polu **Nazwa** Określ `ArithmeticUI` . Wybierz przycisk **OK** .

4. W **Eksplorator rozwiązań** Otwórz menu skrótów dla projektu **ArithmeticUI** , a następnie wybierz **Dodaj**  >  **odwołanie**.

5. W obszarze **Windows** wybierz **rozszerzenia** i Zauważ, że jest wyświetlana **prosta matematyczna** .

6. Zaznacz pole wyboru **proste wyrażenie matematyczne** , a następnie wybierz przycisk **OK** .

7. W **Eksplorator rozwiązań** w obszarze **odwołania** należy zauważyć, że jest wyświetlane **proste odwołanie matematyczne** . Rozwiń go i zwróć uwagę na to, że istnieje folder **\js \\** , który zawiera **arithmetic.js**. Możesz otworzyć **arithmetic.js** , aby upewnić się, że kod źródłowy został zainstalowany.

8. Użyj poniższego kodu, aby zamienić zawartość *default.htm*.

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

9. Użyj poniższego kodu, aby zamienić zawartość *\js\default.js*.

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

10. Zastąp zawartość *\css\default.css* tym kodem:

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

11. Wybierz klawisz **F5** , aby skompilować i uruchomić aplikację.

12. W interfejsie użytkownika aplikacji wprowadź dwie liczby, wybierz operację, a następnie wybierz **=** przycisk. Zostanie wyświetlony prawidłowy wynik.

## <a name="see-also"></a>Zobacz też
- [Tworzenie zestawu SDK](../extensibility/creating-a-software-development-kit.md)
