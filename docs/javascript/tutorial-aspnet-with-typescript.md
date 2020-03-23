---
title: Tworzenie aplikacji ASP.NET Core w języku TypeScript
description: W tym samouczku utworzysz aplikację przy użyciu ASP.NET Core i TypeScript
ms.date: 03/16/2020
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: e212aec6d2d3aa7e20cb0ca08c9ea604f32bb08c
ms.sourcegitcommit: f8e3715c64255b476520bfa9267ceaf766bde3b0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2020
ms.locfileid: "79988546"
---
# <a name="tutorial-create-an-aspnet-core-app-with-typescript-in-visual-studio"></a>Samouczek: Tworzenie aplikacji ASP.NET Core za pomocą kodu TypeScript w programie Visual Studio

W tym samouczku dla programu Visual Studio rozwoju ASP.NET Core i TypeScript, można utworzyć prostą aplikację sieci web, dodać kod TypeScript, a następnie uruchomić aplikację. 

::: moniker range="vs-2017"

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [pobierania programu Visual Studio,](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range="vs-2019"

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [pobierania programu Visual Studio,](https://visualstudio.microsoft.com/downloads) aby zainstalować ją bezpłatnie.

::: moniker-end

Niniejszy samouczek zawiera informacje na temat wykonywania następujących czynności:
> [!div class="checklist"]
> * Tworzenie projektu ASP.NET Core
> * Dodawanie pakietu NuGet dla obsługi języka TypeScript
> * Dodaj kod TypeScript
> * Uruchomienie aplikacji
> * Dodawanie biblioteki innej firmy przy użyciu npm

## <a name="prerequisites"></a>Wymagania wstępne

* Musi być zainstalowany program Visual Studio i ASP.NET obciążenia tworzenia sieci Web.

    ::: moniker range=">=vs-2019"
    Jeśli program Visual Studio 2019 nie został jeszcze zainstalowany, przejdź do strony pobierania programu Visual [Studio,](https://visualstudio.microsoft.com/downloads/)aby zainstalować ją bezpłatnie.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Jeśli program Visual Studio 2017 nie został jeszcze zainstalowany, przejdź do strony pobierania programu Visual [Studio,](https://visualstudio.microsoft.com/downloads/)aby zainstalować ją bezpłatnie.
    ::: moniker-end

    Jeśli chcesz zainstalować obciążenie, ale masz już program Visual Studio, przejdź do **narzędzia** > **Pobierz narzędzia i funkcje...**, który otwiera Instalator programu Visual Studio. Wybierz ASP.NET i obciążenia **tworzenia stron internetowych,** a następnie wybierz pozycję **Modyfikuj**.

## <a name="create-a-new-aspnet-core-mvc-project"></a>Tworzenie nowego projektu ASP.NET Core MVC

Program Visual Studio zarządza plikami dla pojedynczej aplikacji w *projekcie*. Projekt zawiera kod źródłowy, zasoby i pliki konfiguracyjne.

>[!NOTE]
> Aby rozpocząć od pustego projektu ASP.NET Core i dodać fronton TypeScript, zobacz [ASP.NET Core z typescriptem.](https://www.typescriptlang.org/docs/handbook/asp-net-core.html)

W tym samouczku należy rozpocząć od prostego projektu zawierającego kod aplikacji ASP.NET Core MVC.

1. Otwórz program Visual Studio.

1. Tworzenie nowego projektu.

    ::: moniker range=">=vs-2019"
    Jeśli okno startowe nie jest otwarte, wybierz polecenie**Okno startowe** **pliku** > . W oknie początkowym wybierz pozycję **Utwórz nowy projekt**. Z listy rozwijanej języka wybierz pozycję **C#**. W polu wyszukiwania wpisz **ASP.NET**, a następnie wybierz **ASP.NET Core Web Application**. Wybierz pozycję **Dalej**.

    Wpisz nazwę projektu i wybierz pozycję **Utwórz**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Na górnym pasku menu wybierz pozycję **Plik** > **nowego** > **projektu**. W lewym okienku okna dialogowego **Nowy projekt** rozwiń węzeł **Visual C#**, a następnie wybierz pozycję **.NET Core**. W środkowym okienku wybierz pozycję **ASP.NET Core Web Application — C#,** a następnie choose **OK**.
    ::: moniker-end
    Jeśli nie widzisz szablonu projektu **ASP.NET Core Web Application,** należy dodać ASP.NET i obciążenia **tworzenia sieci Web.** Aby uzyskać szczegółowe instrukcje, zobacz [Wymagania wstępne](#prerequisites).

1. W wyświetlonym oknie dialogowym wybierz pozycję **Aplikacja sieci Web (kontroler widoku modelu)** w oknie dialogowym, a następnie wybierz pozycję **Utwórz** (lub **OK**).

   ![Wybieranie szablonu MVC](../javascript/media/aspnet-core-ts-mvc-template.png)

    Visual Studio tworzy nowe rozwiązanie i otwiera projekt w prawym okienku.

## <a name="add-some-code"></a>Dodaj kod

1. W Eksploratorze rozwiązań (prawe okienko). kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Zarządzaj pakietami NuGet**. Na karcie **Przeglądaj** wyszukaj pozycję **Microsoft.TypeScript.MSBuild**, a następnie kliknij pozycję **Zainstaluj** po prawej stronie, aby zainstalować pakiet.

   ![Dodaj pakiet NuGet](../javascript/media/aspnet-core-ts-nuget.png)

   Visual Studio dodaje pakiet NuGet w węźle **Zależności** w Eksploratorze rozwiązań.

   > [!NOTE]
   > Ten samouczek wymaga pakietu NuGet. Alternatywnie, we własnych aplikacjach, można użyć [pakietu NpM TypeScript](https://www.npmjs.com/package/typescript).

1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Dodaj > Nowy folder**. Użyj *skryptów* nazw dla nowego folderu.

1. Kliknij prawym przyciskiem myszy folder *skryptów* i wybierz polecenie **Dodaj > Nowy element**. Wybierz **plik konfiguracyjny Języka JSON w języku TypeScript,** a następnie kliknij przycisk **Dodaj**.

   Program Visual Studio dodaje plik *tsconfig.json* do folderu *skryptów.* Za pomocą tego pliku można [skonfigurować opcje](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html) kompilatora TypeScript.

1. Otwórz *plik tsconfig.json* i zastąp domyślny kod następującym kodem:

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

   Opcja *outDir* określa folder wyjściowy dla plików JavaScript planu, które są transpilowane przez kompilator TypeScript.

   Ta konfiguracja zawiera podstawowe wprowadzenie do korzystania z języka TypeScript. W innych scenariuszach, na przykład podczas korzystania z [łyka lub webpacka,](https://www.typescriptlang.org/docs/handbook/asp-net-core.html)możesz chcieć innej pośredniej lokalizacji dla przesiedlonych plików JavaScript, w zależności od narzędzi i preferencji konfiguracyjnych, zamiast *.. /wwwroot/js*.

1. Kliknij prawym przyciskiem myszy folder *skryptów* i wybierz polecenie **Dodaj > Nowy element**. Wybierz **plik TypeScript**, wpisz nazwę *app.ts* dla nazwy pliku, a następnie kliknij przycisk **Dodaj**.

   Program Visual Studio dodaje *plik app.ts* do folderu *skryptów.*

1. Otwórz *plik app.ts* i dodaj następujący kod TypeScript.

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

    Program Visual Studio zapewnia obsługę intellisense dla kodu TypeScript.

    Aby to sprawdzić, `.lastName` `greeter` usuń z funkcji, a następnie wpisz ponownie ".", a zobaczysz IntelliSense.

    ![Zobacz IntelliSense](../javascript/media/aspnet-core-ts-intellisense.png)

    Wybierz, `lastName` aby dodać nazwisko z powrotem do kodu.

1. Otwórz folder *Widoki / Strona główna,* a następnie otwórz *plik index.html*.

1. Dodaj następujący kod HTML na końcu pliku.

    ```html
    <div id="ts-example">
        <br />
        <button type="button" class="btn btn-primary btn-md" onclick="TSButton()">
            Click Me
        </button>
    </div>
    ```

1. Otwórz folder *Widoki/Udostępnione,* a następnie otwórz *_Layout.cshtml*.

1. Dodaj następujące odwołanie do skryptu przed wywołaniem do: `@RenderSection("Scripts", required: false)`

    ```js
    <script src="~/js/app.js"></script>
    ````

## <a name="build-the-application"></a>Kompilowanie aplikacji

1. Wybierz **pozycję Kompilacja > Rozwiązanie kompilacji**.

   Mimo że aplikacja tworzy automatycznie po uruchomieniu go, chcemy przyjrzeć się coś, co dzieje się podczas procesu kompilacji.

1. Otwórz folder *wwwroot / js,* a znajdziesz dwa nowe pliki, *app.js* i plik mapy źródłowej, *app.js.map*. Pliki te są generowane przez kompilator TypeScript.

   Pliki mapy źródłowe są wymagane do debugowania.

## <a name="run-the-application"></a>Uruchamianie aplikacji

1. Naciśnij **klawisz F5** **(Debugowanie** > **startowe),** aby uruchomić aplikację.

    Aplikacja zostanie otwarta w przeglądarce.

    W oknie przeglądarki zobaczysz nagłówek **Powitanie** i przycisk **Kliknij mnie.**

    ![ASP.NET rdzeń z typescriptem](../javascript/media/aspnet-core-ts-running-app.png)

1. Kliknij przycisk, aby wyświetlić komunikat określony w pliku TypeScript.

## <a name="debug-the-application"></a>Debugowanie aplikacji

1. Ustaw punkt przerwania `greeter` w `app.ts` funkcji, klikając lewy margines w edytorze kodu.

    ![Ustawianie punktu przerwania](../javascript/media/aspnet-core-ts-set-breakpoint.png)

1. Naciśnij **klawisz F5,** aby uruchomić aplikację.

   Może być konieczne udzielenie odpowiedzi na komunikat, aby włączyć debugowanie skryptów.

   Aplikacja wstrzymuje się w punkcie przerwania. Teraz można sprawdzić zmienne i użyć funkcji debugera.

## <a name="add-typescript-support-for-a-third-party-library"></a>Dodawanie obsługi języka TypeScript dla biblioteki innej firmy

1. Postępuj zgodnie z instrukcjami w `package.json` [zarządzaniu pakietami npm,](../javascript/npm-package-management.md#aspnet-core-projects) aby dodać plik do projektu. Spowoduje to dodanie wsparcia npm do projektu.

   >[!NOTE]
   > W przypadku projektów ASP.NET Core można również użyć [Menedżera biblioteki](https://docs.microsoft.com/aspnet/core/client-side/libman/?view=aspnetcore-3.1) lub przędzy zamiast npm, aby zainstalować pliki JavaScript i CSS po stronie klienta.

1. W tym przykładzie dodaj plik definicji TypeScript dla jQuery do projektu. Dołącz następujące elementy w pliku *package.json.*

   ```json
   "devDependencies": {
      "@types/jquery": "3.3.33"
   }
   ```

   Spowoduje to dodanie obsługi języka TypeScript dla języka jQuery. Sama biblioteka jQuery jest już uwzględniona w szablonie projektu MVC (patrz wwwroot/lib w Eksploratorze rozwiązań). Jeśli używasz innego szablonu, może być konieczne dołączenie pakietu jquery npm, jak również.

1. Jeśli pakiet w Eksploratorze rozwiązań nie jest zainstalowany, kliknij prawym przyciskiem myszy węzeł npm i wybierz polecenie **Przywróć pakiety**.

   >[!NOTE]
   > W niektórych scenariuszach Eksplorator rozwiązań może wskazywać, że pakiet npm jest niezsynchronizowany z *package.json* z powodu znanego problemu opisanego [tutaj](https://github.com/aspnet/Tooling/issues/479). Na przykład pakiet może pojawić się jako nie zainstalowany po zainstalowaniu. W większości przypadków można zaktualizować Eksploratora rozwiązań, usuwając *plik package.json*, ponowne uruchomienie programu Visual Studio i ponowne dodanie pliku *package.json* zgodnie z opisem we wcześniejszej części tego artykułu.

1. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy folder skryptów i wybierz polecenie **Dodaj** > **nowy element**.

1. Wybierz **pozycję Plik TypuScript**, wpisz *polecenie library.ts*i wybierz pozycję **Dodaj**.

1. W *library.ts*dodaj następujący kod.

   ```ts
   var jqtest = {
      showMsg: function (): void {
         let v: any = jQuery.fn.jquery.toString();
         let content: any = $("#ts-example-2")[0].innerHTML;
         alert(content.toString());
         $("#ts-example-2")[0].innerHTML = content + " " + v + "!!";
      }
   };

   jqtest.showMsg();
   ```

   Dla uproszczenia ten kod wyświetla komunikat za pomocą jQuery i alertu.

   Z definicji typu TypeScript dla jQuery dodał, otrzymasz obsługę IntelliSense na jQuery obiektów po wpisaniu "." po jQuery obiektu, jak pokazano tutaj.

   ![jquery IntelliSense](../javascript/media/aspnet-core-ts-jquery-intellisense.png)

1. W _Layout.cshtml zaktualizuj odwołania do `library.js`skryptu, aby uwzględnić .

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

1. Naciśnij **klawisz F5** **(Debugowanie** > **startowe),** aby uruchomić aplikację.

    Aplikacja zostanie otwarta w przeglądarce.

    Kliknij **przycisk OK** w alercie, aby zobaczyć stronę zaktualizowaną do wersji **jQuery jest: 3.3.1!!**.

    ![jquery przykład](../javascript/media/aspnet-core-ts-jquery-example.png)

## <a name="next-steps"></a>Następne kroki

Więcej informacji na temat używania kodu TypeScript z ASP.NET Core.

> [!div class="nextstepaction"]
> [ASP.NET rdzeń i kod maszynowy](https://www.typescriptlang.org/docs/handbook/asp-net-core.html)
