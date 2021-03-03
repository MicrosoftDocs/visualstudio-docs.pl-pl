---
title: Tworzenie aplikacji ASP.NET Core w języku TypeScript
description: W tym samouczku utworzysz aplikację przy użyciu ASP.NET Core i języka TypeScript
ms.date: 03/16/2020
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 411fbd757eb063202136eba5c1e5fbec27f56523
ms.sourcegitcommit: 5654b7a57a9af111a6f29239212d76086bc745c9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/03/2021
ms.locfileid: "101683638"
---
# <a name="tutorial-create-an-aspnet-core-app-with-typescript-in-visual-studio"></a>Samouczek: Tworzenie aplikacji ASP.NET Core przy użyciu języka TypeScript w programie Visual Studio

W tym samouczku dla programu Visual Studio Development ASP.NET Core i języka TypeScript utworzysz prostą aplikację sieci Web, dodamy kod TypeScript, a następnie uruchomisz aplikację.

::: moniker range="vs-2017"

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) , aby zainstalować ją bezpłatnie.

::: moniker-end

::: moniker range="vs-2019"

Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/downloads) , aby zainstalować ją bezpłatnie.

::: moniker-end

Z tego samouczka dowiesz się, jak wykonywać następujące czynności:
> [!div class="checklist"]
> * Tworzenie projektu platformy ASP.NET Core
> * Dodaj pakiet NuGet dla obsługi języka TypeScript
> * Dodaj jakiś kod TypeScript
> * Uruchamianie aplikacji
> * Dodawanie biblioteki innej firmy przy użyciu usługi npm

## <a name="prerequisites"></a>Wymagania wstępne

* Musisz mieć zainstalowany program Visual Studio i obciążenie Programowanie aplikacji sieci Web ASP.NET.

    ::: moniker range=">=vs-2019"
    Jeśli program Visual Studio 2019 nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/downloads/) , aby zainstalować ją bezpłatnie.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Jeśli program Visual Studio 2017 nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/downloads/) , aby zainstalować ją bezpłatnie.
    ::: moniker-end

    Jeśli musisz zainstalować obciążenie, ale masz już program Visual Studio, przejdź do pozycji **Narzędzia**  >  **Pobierz narzędzia i funkcje..**., co spowoduje otwarcie Instalator programu Visual Studio. Wybierz obciążenie **ASP.NET i projektowanie sieci Web** , a następnie wybierz **Modyfikuj**.

## <a name="create-a-new-aspnet-core-mvc-project"></a>Utwórz nowy projekt ASP.NET Core MVC

Program Visual Studio zarządza plikami dla pojedynczej aplikacji w *projekcie*. Projekt zawiera kod źródłowy, zasoby i pliki konfiguracji.

>[!NOTE]
> Aby rozpocząć od pustego projektu ASP.NET Core i dodać fronton języka TypeScript, zobacz [ASP.NET Core z użyciem języka TypeScript](https://www.typescriptlang.org/docs/handbook/asp-net-core.html) .

W tym samouczku rozpocznie się Tworzenie prostego projektu zawierającego kod dla aplikacji ASP.NET Core MVC.

1. Otwórz program Visual Studio.

1. Tworzenie nowego projektu.

    ::: moniker range=">=vs-2019"
    W programie Visual Studio 2019 wybierz pozycję **Utwórz nowy projekt** w oknie uruchamiania. Jeśli okno startowe nie jest otwarte, wybierz pozycję **plik**  >  **startowy**. Wpisz **aplikacja sieci Web**, wybierz **C#** jako język, a następnie wybierz **ASP.NET Core aplikacji sieci Web (Model-View-Controller)**, a następnie wybierz **dalej**. Na następnym ekranie Nazwij projekt, a następnie wybierz **dalej**.

    Wybierz zalecaną platformę docelową (.NET Core 3,1) lub .NET 5, a następnie wybierz pozycję **Utwórz**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Na górnym pasku menu wybierz pozycję **plik**  >  **Nowy**  >  **projekt**. W lewym okienku okna dialogowego **Nowy projekt** rozwiń pozycję **Visual C#**, a następnie wybierz pozycję **.NET Core**. W środkowym okienku wybierz pozycję **ASP.NET Core aplikacja sieci Web — C#**, a następnie wybierz przycisk **OK**.

    W wyświetlonym oknie dialogowym wybierz pozycję **aplikacja sieci Web (Model-View-Controller)** w oknie dialogowym, a następnie wybierz pozycję **Utwórz** (lub **OK**).

    ![Wybierz szablon MVC](../javascript/media/aspnet-core-ts-mvc-template.png)
    ::: moniker-end
    Jeśli nie widzisz szablonu projektu **ASP.NET Core aplikacji sieci Web** , musisz dodać obciążenie **ASP.NET i programowanie dla sieci Web** . Aby uzyskać szczegółowe instrukcje, zobacz [wymagania wstępne](#prerequisites).

    Program Visual Studio tworzy nowe rozwiązanie i otwiera projekt w okienku po prawej stronie.

## <a name="add-some-code"></a>Dodaj kod

1. W Eksplorator rozwiązań (okienko po prawej). Kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Zarządzaj pakietami NuGet**. Na karcie **Przeglądaj** Wyszukaj pozycję **Microsoft. TypeScript. MSBuild**, a następnie kliknij pozycję **Zainstaluj** po prawej stronie, aby zainstalować pakiet.

   ![Dodaj pakiet NuGet](../javascript/media/aspnet-core-ts-nuget.png)

   Program Visual Studio dodaje pakiet NuGet w węźle **zależności** w Eksplorator rozwiązań.

1. Kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **dodaj > nowy element**. Wybierz **plik konfiguracji języka TYPESCRIPT JSON**, a następnie kliknij przycisk **Dodaj**.

   Program Visual Studio dodaje *tsconfig.js* do pliku w katalogu głównym projektu. Tego pliku można użyć do [skonfigurowania opcji](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html) kompilatora języka TypeScript.

1. Otwórz *tsconfig.jsna* i Zastąp domyślny kod następującym kodem:

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

   Opcja *outDir* określa folder wyjściowy dla zwykłych plików JavaScript, które są transstertne przez kompilator języka TypeScript.

   Ta konfiguracja zawiera podstawowe wprowadzenie do korzystania z języka TypeScript. W innych scenariuszach, na przykład w przypadku korzystania z programu [Gulp lub WebPack](https://www.typescriptlang.org/docs/handbook/asp-net-core.html), może być potrzebna inna pośrednia lokalizacja dla plików JavaScript o transstosie, w zależności od narzędzi i preferencji konfiguracyjnych zamiast pliku *wwwroot/js*.

1. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **dodaj > nowy folder**. Użyj nazwy *skryptów* dla nowego folderu.

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

    Aby to przetestować, Usuń `.lastName` z `greeter` funkcji, a następnie wpisz ponownie ".", a zobaczysz funkcję IntelliSense.

    ![Wyświetlanie funkcji IntelliSense](../javascript/media/aspnet-core-ts-intellisense.png)

    Wybierz `lastName` , aby dodać ostatnią nazwę z powrotem do kodu.

1. Otwórz *Widok/folder macierzysty* , a następnie otwórz *index. cshtml*.

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

1. Dodaj następujące odwołanie do skryptu przed wywołaniem do `@RenderSection("Scripts", required: false)` :

    ```js
    <script src="~/js/app.js"></script>
    ````

## <a name="build-the-application"></a>Kompilowanie aplikacji

1. Wybierz **kompiluj > Kompiluj rozwiązanie**.

   Mimo że aplikacja automatycznie kompiluje się po uruchomieniu, chcemy obejrzeć coś, co się dzieje w trakcie procesu kompilacji.

1. Otwórz folder *wwwroot/js* i Znajdź dwa nowe pliki, *app.js* i plik mapy źródłowej, *app.js. map*. Te pliki są generowane przez kompilator języka TypeScript.

   Pliki mapy źródłowej są wymagane do debugowania.

## <a name="run-the-application"></a>Uruchamianie aplikacji

1. Naciśnij klawisz **F5** (**Debuguj**  >  **Rozpocznij debugowanie**), aby uruchomić aplikację.

    Aplikacja zostanie otwarta w przeglądarce.

    W oknie przeglądarki zobaczysz nagłówek **powitalny** i przycisk **kliknij mnie** .

    ![ASP.NET Core przy użyciu języka TypeScript](../javascript/media/aspnet-core-ts-running-app.png)

1. Kliknij przycisk, aby wyświetlić komunikat, który został określony w pliku TypeScript.

## <a name="debug-the-application"></a>Debugowanie aplikacji

1. Ustaw punkt przerwania w `greeter` funkcji w programie `app.ts` , klikając na lewym marginesie w edytorze kodu.

    ![Ustawianie punktu przerwania](../javascript/media/aspnet-core-ts-set-breakpoint.png)

1. Naciśnij klawisz **F5** , aby uruchomić aplikację.

   Aby włączyć debugowanie skryptów, może być konieczne udzielenie odpowiedzi na wiadomość.

   Aplikacja wstrzymuje się w punkcie przerwania. Teraz można sprawdzić zmienne i korzystać z funkcji debugera.

## <a name="add-typescript-support-for-a-third-party-library"></a>Dodawanie obsługi języka TypeScript dla biblioteki innej firmy

1. Aby dodać plik do projektu, postępuj zgodnie z instrukcjami w temacie [Zarządzanie pakietami npm](../javascript/npm-package-management.md#aspnet-core-projects) `package.json` . Spowoduje to dodanie obsługi npm do projektu.

   >[!NOTE]
   > W przypadku projektów ASP.NET Core można także użyć [Menedżera bibliotek](https://docs.microsoft.com/aspnet/core/client-side/libman/?view=aspnetcore-3.1&preserve-view=true) lub przędzy zamiast npm do instalowania plików JavaScript i CSS po stronie klienta.

1. W tym przykładzie Dodaj plik definicji TypeScript dla platformy jQuery do projektu. W *package.js* pliku należy uwzględnić następujące elementy.

   ```json
   "devDependencies": {
      "@types/jquery": "3.3.33"
   }
   ```

   Spowoduje to dodanie obsługi języka TypeScript dla platformy jQuery. Sama Biblioteka jQuery jest już dołączona do szablonu projektu MVC (poszukaj w katalogu wwwroot/lib w Eksplorator rozwiązań). Jeśli używasz innego szablonu, może być konieczne również dołączenie pakietu jQuery npm.

1. Jeśli pakiet w Eksplorator rozwiązań nie jest zainstalowany, kliknij prawym przyciskiem myszy węzeł npm i wybierz polecenie **Przywróć pakiety**.

   >[!NOTE]
   > W niektórych scenariuszach Eksplorator rozwiązań może wskazywać, że pakiet npm nie jest zsynchronizowany z *package.jsna* skutek znanego problemu opisanego w [tym miejscu](https://github.com/aspnet/Tooling/issues/479). Na przykład pakiet może być wyświetlany jako niezainstalowany podczas instalacji. W większości przypadków można zaktualizować Eksplorator rozwiązań przez usunięcie *package.jsna*, ponowne uruchomienie programu Visual Studio i ponowne dodanie *package.js* do pliku zgodnie z opisem we wcześniejszej części tego artykułu.

1. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy folder skrypty i wybierz polecenie **Dodaj**  >  **nowy element**.

1. Wybierz pozycję **plik TypeScript**, typ *Biblioteka. TS*, a następnie wybierz pozycję **Dodaj**.

1. W obszarze *Biblioteka. TS* Dodaj następujący kod.

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

   Dla uproszczenia ten kod wyświetla komunikat przy użyciu platformy jQuery i alertu.

   W przypadku dodania definicji typu TypeScript dla programu jQuery do obsługi technologii IntelliSense w obiektach jQuery jest pobierana obsługa środowiska, która jest pokazana poniżej.

   ![Technologia IntelliSense technologii jQuery](../javascript/media/aspnet-core-ts-jquery-intellisense.png)

1. W _Layout. cshtml zaktualizuj odwołania do skryptów, aby uwzględnić `library.js` .

   ```html
   <script src="~/js/app.js"></script>
   <script src="~/js/library.js"></script>
   ```

1. Na stronie index. cshtml Dodaj następujący kod HTML na końcu pliku.

   ```html
   <div>
      <p id="ts-example-2">jQuery version is:</p>
   </div>
   ```

1. Naciśnij klawisz **F5** (**Debuguj**  >  **Rozpocznij debugowanie**), aby uruchomić aplikację.

    Aplikacja zostanie otwarta w przeglądarce.

    Kliknij przycisk **OK** w alercie, aby zobaczyć, że strona zaktualizowana do **wersji jQuery ma wartość: 3.3.1!**.

    ![przykład jQuery](../javascript/media/aspnet-core-ts-jquery-example.png)

## <a name="next-steps"></a>Następne kroki

Warto dowiedzieć się więcej na temat używania języka TypeScript z ASP.NET Core.

> [!div class="nextstepaction"]
> [ASP.NET Core i TypeScript](https://www.typescriptlang.org/docs/handbook/asp-net-core.html)
