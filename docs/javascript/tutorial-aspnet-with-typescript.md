---
title: Tworzenie aplikacji ASP.NET Core przy użyciu języka TypeScript
description: W tym samouczku utworzysz aplikację przy użyciu ASP.NET Core i języka TypeScript
ms.date: 01/03/2020
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 8d733c41e2833eeca2a8bf8c68f5e329f0af723c
ms.sourcegitcommit: 0d8488329263cc0743a89d43f6de863028e982ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/06/2020
ms.locfileid: "75685308"
---
# <a name="tutorial-create-an-aspnet-core-app-with-typescript-in-visual-studio"></a>Samouczek: Tworzenie aplikacji ASP.NET Core przy użyciu języka TypeScript w programie Visual Studio

W tym samouczku dla programu Visual Studio Development ASP.NET Core i języka TypeScript utworzysz prostą aplikację sieci Web, dodamy kod TypeScript, a następnie uruchomisz aplikację. 

::: moniker range="vs-2017"

Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [program Visual Studio pobiera](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) strony, aby zainstalować go za darmo.

::: moniker-end

::: moniker range="vs-2019"

Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [program Visual Studio pobiera](https://visualstudio.microsoft.com/downloads) strony, aby zainstalować go za darmo.

::: moniker-end

Z tego samouczka dowiesz się, jak wykonywać następujące czynności:
> [!div class="checklist"]
> * Tworzenie projektu ASP.NET Core
> * Dodaj pakiet NuGet dla obsługi języka TypeScript
> * Dodaj jakiś kod TypeScript
> * Uruchamianie aplikacji

## <a name="prerequisites"></a>Wymagania wstępne

* Musisz mieć zainstalowany program Visual Studio i obciążenie Programowanie aplikacji sieci Web ASP.NET.

    ::: moniker range=">=vs-2019"
    Jeśli program Visual Studio 2019 nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/downloads/) , aby zainstalować ją bezpłatnie.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Jeśli program Visual Studio 2017 nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/downloads/) , aby zainstalować ją bezpłatnie.
    ::: moniker-end

    Jeśli musisz zainstalować obciążenie, ale masz już program Visual Studio, przejdź do pozycji **narzędzia** > **Pobierz narzędzia i funkcje..** ., co spowoduje otwarcie Instalator programu Visual Studio. Wybierz obciążenie **ASP.NET i projektowanie sieci Web** , a następnie wybierz **Modyfikuj**.

## <a name="create-a-new-aspnet-core-mvc-project"></a>Utwórz nowy projekt ASP.NET Core MVC

Program Visual Studio zarządza plikami dla pojedynczej aplikacji w *projekcie*. Projekt zawiera kod źródłowy, zasoby i pliki konfiguracji.

W tym samouczku rozpocznie się Tworzenie prostego projektu zawierającego kod dla aplikacji ASP.NET Core MVC.

1. Otwórz program Visual Studio.

1. Utwórz nowy projekt.

    ::: moniker range=">=vs-2019"
    Naciśnij klawisz **ESC** , aby zamknąć okno uruchamiania. **Naciśnij klawisze CTRL + Q** , aby otworzyć pole wyszukiwania, wpisz **ASP.NET**, a następnie wybierz **ASP.NET Core aplikacji C#sieci Web —** . W wyświetlonym oknie dialogowym wybierz pozycję **Utwórz**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Na pasku menu u góry wybierz **pliku** > **New** > **projektu**. W lewym okienku okna dialogowego **Nowy projekt** rozwiń węzeł **JavaScript**, a następnie wybierz polecenie **Node. js**. W środkowym okienku wybierz pozycję **ASP.NET Core aplikacja C#sieci Web** , a następnie wybierz przycisk **OK**.
    ::: moniker-end
    Jeśli nie widzisz szablonu projektu **ASP.NET Core aplikacji sieci Web** , musisz dodać obciążenie **ASP.NET i programowanie dla sieci Web** . Aby uzyskać szczegółowe instrukcje, zobacz [wymagania wstępne](#prerequisites).

1. Po wybraniu opcji **Utwórz**wybierz pozycję **aplikacja sieci Web (Model-View-Controller)** w oknie dialogowym, a następnie wybierz pozycję **Utwórz**.

   ![Wybierz szablon MVC](../javascript/media/aspnet-core-ts-mvc-template.png)

    Program Visual Studio tworzy nowe rozwiązanie i otwiera projekt w okienku po prawej stronie.

## <a name="add-some-code"></a>Dodaj kod

1. W Eksplorator rozwiązań (okienko po prawej). Kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Zarządzaj pakietami NuGet**. Na karcie **Przeglądaj** Wyszukaj pozycję **Microsoft. TypeScript. MSBuild**, a następnie kliknij pozycję **Zainstaluj** po prawej stronie, aby zainstalować pakiet.

   ![Dodaj pakiet NuGet](../javascript/media/aspnet-core-ts-nuget.png)

   Program Visual Studio dodaje pakiet NuGet w węźle **zależności** w Eksplorator rozwiązań.

   > [!NOTE]
   > Ten samouczek wymaga pakietu NuGet. Alternatywnie, w własnych aplikacjach, możesz chcieć użyć [pakietu npm języka TypeScript](https://www.npmjs.com/package/typescript).

1. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **dodaj > nowy folder**. Użyj nazwy *skryptów* dla nowego folderu.

1. Kliknij prawym przyciskiem myszy folder *skrypty* i wybierz polecenie **Dodaj > nowy element**. Wybierz **plik konfiguracji języka TYPESCRIPT JSON**, a następnie kliknij przycisk **Dodaj**.

   Program Visual Studio dodaje plik *tsconfig. JSON* do folderu *scripts* . Tego pliku można użyć do [skonfigurowania opcji](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html) kompilatora języka TypeScript.

1. Otwórz plik *tsconfig. JSON* i Zastąp domyślny kod następującym kodem:

   ```json
   {
     "compilerOptions": {
       "noImplicitAny": false,
       "noEmitOnError": true,
       "removeComments": false,
       "sourceMap": true,
       "target": "es5",
       "outDir": "../wwwroot/js"
     },
     "exclude": [
       "node_modules",
       "wwwroot"
     ]
   }
   ```

   Opcja *outDir* określa folder wyjściowy dla plików języka JavaScript, które są transstertne przez kompilator TypeScript.

   Ta konfiguracja zawiera podstawowe wprowadzenie do korzystania z języka TypeScript. W innych scenariuszach, na przykład w przypadku korzystania z programu [Gulp lub WebPack](https://www.typescriptlang.org/docs/handbook/asp-net-core.html), może być potrzebna inna pośrednia lokalizacja dla plików JavaScript o niestosie, w zależności od narzędzi i preferencji konfiguracji, a nie *. /wwwroot/js*.

1. Kliknij prawym przyciskiem myszy folder *skrypty* i wybierz polecenie **Dodaj > nowy element**. Wybierz **plik TypeScript**, wpisz nazwę *App. TS* dla nazwy pliku, a następnie kliknij przycisk **Dodaj**.

   Program Visual Studio dodaje *aplikację App. TS* do folderu *scripts* .

1. Otwórz *aplikację App. TS* i Dodaj następujący kod języka TypeScript.

    ```ts
    function TSButton() {
       let name: string = "Fred";
       document.getElementById("ts-example").innerHTML = greeter(user);
    }

    class Student {
       fullName: string;
       constructor(public firstName: string, public middleInitial: string, public lastName: string) {
           this.fullName = firstName + " " + middleInitial + " " + lastName;
       }
    }

    interface Person {
       firstName: string;
       lastName: string;
    }

    function greeter(person: Person) {
       return "Hello, " + person.firstName + " " + person.lastName;
    }

    let user = new Student("Fred", "M.", "Smith");
    ```

    Program Visual Studio zapewnia obsługę technologii IntelliSense dla kodu języka TypeScript.

    Aby to przetestować, Usuń `.lastName` z funkcji `greeter`, a następnie wpisz ponownie ".", a zobaczysz funkcję IntelliSense.

    ![Wyświetlanie funkcji IntelliSense](../javascript/media/aspnet-core-ts-intellisense.png)

    Wybierz `lastName`, aby dodać ostatnią nazwę z powrotem do kodu.

1. Otwórz *Widok/folder macierzysty* , a następnie otwórz *plik index. html*.

1. Dodaj następujący kod HTML na końcu pliku.

    ```html
    <div id="ts-example">
        <br />
        <button type="button" class="btn btn-primary btn-md" onclick="TSButton()">
            Click Me
        </button>
    </div>
    ```

1. Otwórz *Widok/folder udostępniony* , a następnie otwórz *_Layout. cshtml*.

1. Dodaj następujące odwołanie do skryptu przed wywołaniem do `@RenderSection("Scripts", required: false)`:

    ```js
    <script src="~/js/app.js"></script>
    ````

## <a name="build-the-application"></a>Kompilowanie aplikacji

1. Wybierz **kompiluj > Kompiluj rozwiązanie**.

   Mimo że aplikacja automatycznie kompiluje się po uruchomieniu, chcemy obejrzeć coś, co się dzieje w trakcie procesu kompilacji.

1. Otwórz folder *wwwroot/js* i Znajdź dwa nowe pliki, *App. js* i plik mapy źródłowej *App. js. map*. Te pliki są generowane przez kompilator języka TypeScript.

   Pliki mapy źródłowej są wymagane do debugowania.

## <a name="run-the-application"></a>Uruchamianie aplikacji

1. Naciśnij klawisz **F5** (**Debuguj** > **Rozpocznij debugowanie**), aby uruchomić aplikację.

    Aplikacja zostanie otwarta w przeglądarce.

    W oknie przeglądarki zobaczysz nagłówek **powitalny** i przycisk **kliknij mnie** .

    ![ASP.NET Core przy użyciu języka TypeScript](../javascript/media/aspnet-core-ts-running-app.png)

1. Kliknij przycisk, aby wyświetlić komunikat, który został określony w pliku TypeScript.

## <a name="debug-the-application"></a>Debugowanie aplikacji

1. Ustaw punkt przerwania w funkcji `greeter` w `app.ts`, klikając na lewym marginesie w edytorze kodu.

    ![Ustaw punkt przerwania](../javascript/media/aspnet-core-ts-set-breakpoint.png)

1. Naciśnij klawisz **F5**, aby uruchomić aplikację.

   Aby włączyć debugowanie skryptów, może być konieczne udzielenie odpowiedzi na wiadomość.

   Aplikacja wstrzymuje się w punkcie przerwania. Teraz można sprawdzić zmienne i korzystać z funkcji debugera.

## <a name="next-steps"></a>Następne kroki

Warto dowiedzieć się więcej na temat używania języka TypeScript z ASP.NET Core.

> [!div class="nextstepaction"]
> [ASP.NET Core i TypeScript](https://www.typescriptlang.org/docs/handbook/asp-net-core.html)
