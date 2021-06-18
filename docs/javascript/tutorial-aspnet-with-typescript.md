---
title: Tworzenie aplikacji ASP.NET Core w języku TypeScript
description: W tym samouczku utworzysz aplikację przy użyciu języka ASP.NET Core i TypeScript
ms.date: 03/25/2021
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 0728011c05d47996a313c11a18f31a196ec08e10
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2021
ms.locfileid: "112306502"
---
# <a name="tutorial-create-an-aspnet-core-app-with-typescript-in-visual-studio"></a>Samouczek: tworzenie aplikacji ASP.NET Core przy użyciu języka TypeScript w języku Visual Studio

W tym samouczku Visual Studio tworzenia aplikacji ASP.NET Core i TypeScript utworzysz prostą aplikację internetową, dodasz kod TypeScript, a następnie uruchom aplikację.

::: moniker range="vs-2017"

Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [pobierania](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) Visual Studio, aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range=">=vs-2019"

Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [pobierania](https://visualstudio.microsoft.com/downloads) Visual Studio, aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range="vs-2022"

Jeśli jeszcze nie zainstalowano programu Visual Studio 2022 (wersja zapoznawcza), przejdź do strony pobierania programu [Visual Studio 2022 Preview,](https://visualstudio.microsoft.com/vs/preview/vs2022) aby zainstalować ją bezpłatnie.

::: moniker-end

Ten samouczek zawiera informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
> * Tworzenie projektu platformy ASP.NET Core
> * Dodawanie pakietu NuGet dla obsługi języka TypeScript
> * Dodawanie kodu TypeScript
> * Uruchamianie aplikacji
> * Dodawanie biblioteki innej firmy przy użyciu narzędzia npm

## <a name="prerequisites"></a>Wymagania wstępne

* Musisz mieć zainstalowany Visual Studio i ASP.NET tworzenia aplikacji internetowych.

    ::: moniker range=">=vs-2019"
    Jeśli jeszcze nie zainstalowano programu Visual Studio 2019, [](https://visualstudio.microsoft.com/downloads/) przejdź do strony pobierania Visual Studio, aby zainstalować ją bezpłatnie.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Jeśli jeszcze nie zainstalowano programu Visual Studio 2017, [](https://visualstudio.microsoft.com/downloads/) przejdź do strony pobierania Visual Studio, aby zainstalować ją bezpłatnie.
    ::: moniker-end

    Jeśli musisz zainstalować obciążenie, ale masz już Visual Studio, przejdź do tematu Narzędzia Pobierz narzędzia i  >  **funkcje...,** co spowoduje otwarcie Instalator programu Visual Studio. Wybierz obciążenie **tworzenie aplikacji ASP.NET sieci Web,** a następnie wybierz pozycję **Modyfikuj.**

## <a name="create-a-new-aspnet-core-mvc-project"></a>Tworzenie nowego projektu ASP.NET Core MVC

Visual Studio zarządza plikami dla jednej aplikacji w *projekcie*. Projekt zawiera kod źródłowy, zasoby i pliki konfiguracji.

>[!NOTE]
> Aby rozpocząć od pustego projektu ASP.NET Core i dodać frontonie języka TypeScript, zobacz ASP.NET Core with TypeScript (Podstawowe funkcje w języku [TypeScript).](https://www.typescriptlang.org/docs/handbook/asp-net-core.html)

W tym samouczku rozpoczniesz od prostego projektu zawierającego kod dla ASP.NET Core MVC.

1. Otwórz program Visual Studio.

1. Tworzenie nowego projektu.

    ::: moniker range=">=vs-2019"
    W Visual Studio 2019 r. wybierz pozycję **Utwórz nowy projekt** w oknie uruchamiania. Jeśli okno uruchamiania nie jest otwarte, wybierz pozycję  >  **Okno uruchamiania pliku.** Wpisz **aplikację internetową,** wybierz **język C#,** a następnie wybierz pozycję **ASP.NET Core Web Application (Model-View-Controller),** a następnie wybierz **pozycję Dalej.** Na następnym ekranie nadaj projektowi nazwę, a następnie wybierz pozycję **Dalej.**

    Wybierz zalecaną platformę docelową (.NET Core 3.1) lub .NET 5, a następnie wybierz **pozycję Utwórz.**
    ::: moniker-end
    ::: moniker range="vs-2017"
    Na górnym pasku menu wybierz pozycję **File** New Project  >  **(Plik nowy**  >  **projekt).** W lewym okienku okna **dialogowego Nowy** projekt rozwiń pozycję **Visual C#,** a następnie wybierz **pozycję .NET Core.** W środkowym okienku wybierz pozycję **ASP.NET Core Web Application — C#, a** następnie wybierz przycisk **OK.**

    W wyświetlonym oknie dialogowym wybierz pozycję **Aplikacja internetowa (Model-View-Controller)** w oknie dialogowym, a następnie wybierz pozycję **Utwórz** (lub **OK).**

    ![Wybieranie szablonu MVC](../javascript/media/aspnet-core-ts-mvc-template.png)
    ::: moniker-end
    Jeśli nie widzisz szablonu projektu **ASP.NET Core Web Application,** musisz dodać obciążenie tworzenie aplikacji ASP.NET **tworzenie aplikacji** internetowych. Aby uzyskać szczegółowe instrukcje, zobacz [Wymagania wstępne.](#prerequisites)

    Visual Studio tworzy nowe rozwiązanie i otwiera projekt w okienku po prawej stronie.

## <a name="add-some-code"></a>Dodawanie kodu

1. W Eksplorator rozwiązań (okienko po prawej stronie). Kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Zarządzaj pakietami NuGet.** Na karcie **Przeglądaj** wyszukaj pozycję **Microsoft.TypeScript.MSBuild,** a następnie kliknij przycisk **Zainstaluj** po prawej stronie, aby zainstalować pakiet.

   ![Dodawanie pakietu NuGet](../javascript/media/aspnet-core-ts-nuget.png)

   Visual Studio dodaje pakiet NuGet w **węźle Zależności** w Eksplorator rozwiązań.

1. Kliknij prawym przyciskiem myszy węzeł projektu i wybierz **polecenie Dodaj > nowy element**. Wybierz plik **konfiguracji TypeScript JSON,** a następnie kliknij przycisk **Dodaj**.

   Visual Studio dodajetsconfig.js *pliku* do katalogu głównego projektu. Ten plik umożliwia [skonfigurowanie opcji](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html) kompilatora języka TypeScript.

1. Otwórz *tsconfig.jsi* zastąp kod domyślny następującym kodem:

   ```json
   {
     "compileOnSave": true,
     "compilerOptions": {
       "noImplicitAny": false,
       "noEmitOnError": true,
       "removeComments": false,
       "sourceMap": true,
       "target": "es5",
       "outDir": "wwwroot/js"
     },
     "include": [
       "scripts/**/*"
     ]
   }
   ```

   Opcja *outDir* określa folder wyjściowy dla zwykłych plików JavaScript, które są transpilowane przez kompilator Języka TypeScript.

   Ta konfiguracja zawiera podstawowe wprowadzenie do korzystania z języka TypeScript. W innych scenariuszach, na przykład w przypadku korzystania z narzędzia gulp lub [webpack,](https://www.typescriptlang.org/docs/handbook/asp-net-core.html)możesz chcieć uzyskać inną pośrednią lokalizację transpilowanych plików JavaScript, w zależności od narzędzi i preferencji konfiguracji, zamiast *wwwroot/js.*

1. W Eksplorator rozwiązań prawym przyciskiem myszy węzeł projektu i wybierz polecenie Dodaj > **Nowy folder.** Użyj *skryptów nazw* dla nowego folderu.

1. Kliknij prawym przyciskiem myszy folder *scripts* i wybierz **polecenie Dodaj > nowy element.** Wybierz plik **TypeScript,** wpisz nazwę *app.ts* dla nazwy pliku, a następnie kliknij przycisk **Dodaj**.

   Visual Studio dodaje *plik app.ts* do folderu *scripts.*

1. Otwórz *app.ts* i dodaj następujący kod TypeScript.

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

    Visual Studio zapewnia obsługę funkcji IntelliSense dla kodu TypeScript.

    Aby to przetestować, `.lastName` usuń z funkcji , wpisz ponownie `greeter` "." i zobaczysz funkcję IntelliSense.

    ![Wyświetlanie funkcji IntelliSense](../javascript/media/aspnet-core-ts-intellisense.png)

    Wybierz, `lastName` aby dodać nazwisko z powrotem do kodu.

1. Otwórz folder *Views/Home,* a następnie otwórz *plik Index.cshtml.*

1. Dodaj następujący kod HTML na końcu pliku.

    ```html
    <div id="ts-example">
        <br />
        <button type="button" class="btn btn-primary btn-md" onclick="TSButton()">
            Click Me
        </button>
    </div>
    ```

1. Otwórz folder *Views/Shared,* a następnie otwórz *plik _Layout.cshtml.*

1. Dodaj następujące odwołanie do skryptu przed wywołaniem polecenia `@RenderSection("Scripts", required: false)` :

    ```js
    <script src="~/js/app.js"></script>
    ````

## <a name="build-the-application"></a>Kompilowanie aplikacji

1. Wybierz **pozycję > kompilacji.**

   Mimo że aplikacja jest kompilowana automatycznie po uruchomieniu, chcemy przyjrzeć się coś, co dzieje się podczas procesu kompilacji.

1. Otwórz *folder wwwroot/js* i znajdź dwa nowe pliki, *app.js* i źródłowy plik mapy, *app.js.map.* Te pliki są generowane przez kompilator języka TypeScript.

   Źródłowe pliki mapy są wymagane do debugowania.

## <a name="run-the-application"></a>Uruchamianie aplikacji

1. Naciśnij **klawisz F5** **(Debuguj**  >  **rozpocznij debugowanie),** aby uruchomić aplikację.

    Aplikacja zostanie otwarta w przeglądarce.

    W oknie przeglądarki zobaczysz nagłówek **Welcome (Powitanie)** i **przycisk Click Me (Kliknij** mnie).

    ![ASP.NET Core z typeScript](../javascript/media/aspnet-core-ts-running-app.png)

1. Kliknij przycisk , aby wyświetlić komunikat określony w pliku TypeScript.

## <a name="debug-the-application"></a>Debugowanie aplikacji

1. Ustaw punkt przerwania w funkcji w `greeter` programie `app.ts` , klikając lewy margines w edytorze kodu.

    ![Ustawianie punktu przerwania](../javascript/media/aspnet-core-ts-set-breakpoint.png)

1. Naciśnij **klawisz F5,** aby uruchomić aplikację.

   Może być konieczne odpowiedzieć na komunikat, aby włączyć debugowanie skryptu.

   Aplikacja jest wstrzymywana w punkcie przerwania. Teraz możesz sprawdzać zmienne i używać funkcji debugera.

## <a name="add-typescript-support-for-a-third-party-library"></a>Dodawanie obsługi języka TypeScript dla biblioteki innej firmy

1. Postępuj zgodnie z [instrukcjami dotyczącymi zarządzania pakietami npm,](../javascript/npm-package-management.md#aspnet-core-projects) aby `package.json` dodać plik do projektu. Powoduje to dodanie obsługi npm do projektu.

   >[!NOTE]
   > W ASP.NET Core można również użyć [](/aspnet/core/client-side/libman/) Menedżera bibliotek lub yarn zamiast menedżera npm, aby zainstalować pliki JavaScript i CSS po stronie klienta.

1. W tym przykładzie dodaj plik definicji TypeScript dla jQuery do projektu. Uwzględnij następujące elementy *wpackage.jspliku.*

   ```json
   "devDependencies": {
      "@types/jquery": "3.3.33"
   }
   ```

   Powoduje to dodanie obsługi języka TypeScript dla zapytań jQuery. Sama biblioteka jQuery jest już uwzględniona w szablonie projektu MVC (w obszarze wwwroot/lib w Eksplorator rozwiązań). Jeśli używasz innego szablonu, może być konieczne dołącz również pakiet npm jquery.

1. Jeśli pakiet w Eksplorator rozwiązań nie jest zainstalowany, kliknij prawym przyciskiem myszy węzeł npm i wybierz polecenie **Przywróć pakiety**.

   >[!NOTE]
   > W niektórych scenariuszach Eksplorator rozwiązań, że pakiet npm nie *jest* zsynchronizowany z programempackage.jsz powodu znanego problemu opisanego [tutaj.](https://github.com/aspnet/Tooling/issues/479) Na przykład pakiet może być wyświetlany jako nieinstalowany podczas instalacji. W większości przypadków można zaktualizować Eksplorator rozwiązań, usuwającpackage.jsna *stronie*, ponownie uruchamiając Visual Studio  i ponownie dodającpackage.jsdo pliku zgodnie z opisem we wcześniejszej wersji tego artykułu.

1. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy folder scripts i wybierz polecenie **Dodaj**  >  **nowy element.**

1. Wybierz **pozycję Plik TypeScript,** wpisz *library.ts* i wybierz pozycję **Dodaj.**

1. W *bibliotece library.ts* dodaj następujący kod.

   ```ts
   var jqtest = {
      showMsg: function (): void {
         let v: any = jQuery.fn.jquery.toString();
         let content: any = $("#ts-example-2")[0].innerHTML;
         alert(content.toString() + " " + v + "!!");
         $("#ts-example-2")[0].innerHTML = content + " " + v + "!!";
      }
   };

   jqtest.showMsg();
   ```

   Dla uproszczenia ten kod wyświetla komunikat przy użyciu narzędzia jQuery i alertu.

   Po dodaniu definicji typów języka TypeScript dla języka jQuery można uzyskać obsługę funkcji IntelliSense dla obiektów jQuery po wpisaniu "." po obiekcie jQuery, jak pokazano poniżej.

   ![jquery IntelliSense](../javascript/media/aspnet-core-ts-jquery-intellisense.png)

1. W pliku _Layout.cshtml zaktualizuj odwołania do skryptu, aby uwzględnić `library.js` .

   ```html
   <script src="~/js/app.js"></script>
   <script src="~/js/library.js"></script>
   ```

1. W pliku Index.cshtml dodaj następujący kod HTML na końcu pliku.

   ```html
   <div>
      <p id="ts-example-2">jQuery version is:</p>
   </div>
   ```

1. Naciśnij **klawisz F5** **(Debuguj**  >  **rozpocznij debugowanie),** aby uruchomić aplikację.

    Aplikacja zostanie otwarta w przeglądarce.

    Kliknij **przycisk OK** w alercie, aby wyświetlić stronę zaktualizowaną do wersji **jQuery: 3.3.1??**.

    ![Przykład jquery](../javascript/media/aspnet-core-ts-jquery-example.png)

## <a name="next-steps"></a>Następne kroki

Możesz dowiedzieć się więcej na temat używania języka TypeScript z ASP.NET Core. Jeśli interesuje Cię programowanie AngularJS w usłudze Visual Studio, możesz użyć rozszerzenia usługi językowej [AngularJS](https://devblogs.microsoft.com/visualstudio/angular-language-service-for-visual-studio) na Visual Studio.

> [!div class="nextstepaction"]
> [ASP.NET Core i TypeScript](https://www.typescriptlang.org/docs/handbook/asp-net-core.html)

> [!div class="nextstepaction"]
> [Rozszerzenie usługi językowej AngularJS](https://devblogs.microsoft.com/visualstudio/angular-language-service-for-visual-studio)
