---
title: Tworzenie aplikacji Vue.js przy użyciu Node.js
description: Możesz tworzyć Node.js aplikacje w programie Visual Studio przy użyciu struktury Vue.js
ms.custom: seodec18
ms.date: 07/06/2018
ms.topic: how-to
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 52281c403ceb0f2708aa546cbd73559593c419be
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942831"
---
# <a name="create-a-vuejs-application-using-nodejs-tools-for-visual-studio"></a>Tworzenie aplikacji Vue.js przy użyciu narzędzi Node.js Tools for Visual Studio

Program Visual Studio obsługuje programowanie aplikacji za pomocą platformy [Vue.js](https://vuejs.org/) w języku JavaScript lub TypeScript.

Poniższe nowe funkcje obsługują Programowanie aplikacji Vue.js w programie Visual Studio:

* Obsługa skryptów, stylów i bloków szablonów w plikach *. Vue*
* Rozpoznawanie `lang` atrybutu w plikach *. Vue*
* Vue.js szablonów plików i projektów

## <a name="prerequisites"></a>Wymagania wstępne

* Musisz mieć zainstalowany program Visual Studio 2017 w wersji 15,8 lub nowszej orazNode.js obciążenie **programowaniem** .

    > [!IMPORTANT]
    > Ten artykuł wymaga funkcji, które są dostępne tylko w programie Visual Studio 2017 w wersji 15,8.

    ::: moniker range=">=vs-2019"
    Jeśli wymagana wersja nie jest jeszcze zainstalowana, zainstaluj [program Visual Studio 2019](https://visualstudio.microsoft.com/downloads).
    ::: moniker-end
    ::: moniker range="vs-2017"
    Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony [plików do pobrania programu Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) , aby zainstalować ją bezpłatnie.
    ::: moniker-end

    Jeśli musisz zainstalować obciążenie, ale masz już program Visual Studio, przejdź do pozycji **Narzędzia**  >  **Pobierz narzędzia i funkcje..**., co spowoduje otwarcie Instalator programu Visual Studio. Wybierz **Node.js obciążenie programowaniem** , a następnie wybierz **Modyfikuj**.

* Aby utworzyć projekt ASP.NET Core, trzeba mieć zainstalowane ASP.NET i programowanie aplikacji sieci Web oraz platformy .NET Core dla wielu platform.

* Musisz mieć zainstalowane środowisko uruchomieniowe Node.js.

    Jeśli go nie zainstalowano, Zainstaluj wersję LTS z witryny sieci Web [Node.js](https://nodejs.org/en/download/) . Ogólnie rzecz biorąc, program Visual Studio automatycznie wykrywa zainstalowane Node.js środowiska uruchomieniowego. Jeśli nie wykryje zainstalowanego środowiska uruchomieniowego, można skonfigurować projekt tak, aby odwoływała się do zainstalowanego środowiska uruchomieniowego na stronie właściwości. (Po utworzeniu projektu kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Właściwości**).

## <a name="create-a-vuejs-project-using-nodejs"></a>Tworzenie projektu Vue.js przy użyciu Node.js

Aby utworzyć nowy projekt, można użyć nowych szablonów Vue.js. Korzystanie z szablonu jest najprostszym sposobem na rozpoczęcie pracy. Aby uzyskać szczegółowe instrukcje, zobacz [Korzystanie z programu Visual Studio w celu utworzenia pierwszej aplikacji Vue.js](../javascript/quickstart-vuejs-with-nodejs.md).

## <a name="create-a-vuejs-project-with-aspnet-core-and-the-vue-cli"></a>Tworzenie projektu Vue.js za pomocą ASP.NET Core i interfejsu wiersza polecenia Vue

Vue.js udostępnia oficjalnego interfejsu wiersza polecenia do szybkiego tworzenia szkieletów projektów. Jeśli chcesz utworzyć aplikację za pomocą interfejsu wiersza polecenia, wykonaj kroki opisane w tym artykule, aby skonfigurować środowisko deweloperskie.

> [!IMPORTANT]
> W tych krokach przyjęto założenie, że masz już doświadczenie z platformą Vue.js. Jeśli nie, odwiedź stronę [Vue.js](https://vuejs.org/) , aby dowiedzieć się więcej o platformie.

### <a name="create-a-new-aspnet-core-project"></a>Utwórz nowy projekt ASP.NET Core

W tym przykładzie użyto pustej aplikacji ASP.NET Core (C#). Można jednak wybrać jedną z wielu projektów i języków programowania.

#### <a name="create-an-empty-project"></a>Utwórz pusty projekt

1. Otwórz program Visual Studio i Utwórz nowy projekt.

    ::: moniker range=">=vs-2019"
    Naciśnij klawisz **ESC** , aby zamknąć okno uruchamiania. **Naciśnij klawisze CTRL + Q** , aby otworzyć pole wyszukiwania, wpisz **ASP.NET**, a następnie wybierz pozycję **utwórz nową aplikację sieci Web ASP.NET Core**. W wyświetlonym oknie dialogowym wpisz nazwę **Client-App**, a następnie wybierz pozycję Create ( **Utwórz**).
    ::: moniker-end
    ::: moniker range="vs-2017"
    Na górnym pasku menu wybierz pozycję **plik**  >  **Nowy**  >  **projekt**. W lewym okienku okna dialogowego **Nowy projekt** rozwiń pozycję **Visual C#**, a następnie wybierz pozycję **Sieć Web**. W środkowym okienku wybierz pozycję **ASP.NET Core aplikacja sieci Web**, wpisz nazwę **klient-aplikacja**, a następnie wybierz **przycisk OK**.
    ::: moniker-end

    Jeśli nie widzisz szablonu projektu **ASP.NET Core aplikacji sieci Web** , musisz zainstalować obciążenie **ASP.NET i programowanie dla sieci Web** oraz. Najpierw **nasienne programowanie w sieci podstawowej** . Aby zainstalować obciążenia, kliknij link **Otwórz Instalator programu Visual Studio** w lewym okienku okna dialogowego **Nowy projekt** (wybierz pozycję **plik**  >  **Nowy**  >  **projekt**). Zostanie uruchomiona Instalator programu Visual Studio. Wybierz wymagane obciążenia.

1. Wybierz opcję **puste**, a następnie kliknij przycisk **OK**.

    Program Visual Studio tworzy projekt, który zostanie otwarty w Eksplorator rozwiązań (prawego okienka).

#### <a name="configure-the-project-startup-file"></a>Konfigurowanie pliku startowego projektu

* Otwórz plik *./Startup.cs* i Dodaj następujące wiersze do metody Configure:

    ```csharp
    app.UseDefaultFiles(); // Enables default file mapping on the web root.
    app.UseStaticFiles(); // Marks files on the web root as servable.
    ```

### <a name="install-the-vue-cli"></a>Instalowanie interfejsu wiersza polecenia Vue

Aby zainstalować moduł Vue-CLI npm, Otwórz wiersz polecenia i wpisz `npm install --g vue-cli` lub `npm install -g @vue/cli` dla wersji 3,0 (obecnie w wersji beta).

### <a name="scaffold-a-new-client-application-using-the-vue-cli"></a>Tworzenie szkieletu nowej aplikacji klienckiej przy użyciu interfejsu wiersza polecenia Vue

1. Przejdź do wiersza polecenia i Zmień bieżący katalog na folder główny projektu.

1. Wpisz `vue init webpack client-app` i postępuj zgodnie z instrukcjami, gdy zostanie wyświetlony monit o udzielenie odpowiedzi na dodatkowe pytania.

    > [!NOTE]
    > W przypadku plików *. Vue* należy użyć programu WebPack lub podobnej struktury z modułem ładującym w celu wykonania konwersji. Programy TypeScript i Visual Studio nie wiedzą, jak kompilować pliki *. Vue* . Ta sama wartość dotyczy grupowania; Język TypeScript nie wie, jak konwertować moduły ES2015 (to jest `import` i `export` instrukcje) na jeden końcowy plik *. js* do załadowania w przeglądarce. Teraz pakiet WebPack jest najlepszym wyborem. Aby uzyskać ten proces z poziomu programu Visual Studio przy użyciu programu MSBuild, należy zacząć od szablonu programu Visual Studio. Obecnie nie istnieje szablon ASP.NET do tworzenia Vue.js.

#### <a name="modify-the-webpack-configuration-to-output-the-built-files-to-wwwroot"></a>Zmodyfikuj konfigurację pakietu WebPack, aby wyprowadzić skompilowane pliki do pliku wwwroot

* Otwórz plik *./client-app/config/index.js* i Zmień `build.index` ścieżkę i do pliku `build.assetsRoot` wwwroot:

    ```js
    // Template for index.html
    index: path.resolve(__dirname, '../../wwwroot/index.html'),

    // Paths
    assetsRoot: path.resolve(__dirname, '../../wwwroot'),
    ```

#### <a name="indicate-the-project-to-build-the-client-app-each-time-that-a-build-is-triggered"></a>Wskaż projekt, aby skompilować aplikację kliencką za każdym razem, gdy kompilacja jest wyzwalana

1. W programie Visual Studio przejdź do pozycji  >  **Właściwości** projektu  >  **Kompiluj zdarzenia**.

1. W **wierszu polecenia zdarzenia przed kompilacją** wpisz `npm --prefix ./client-app run build` .

#### <a name="configure-webpacks-output-module-names"></a>Skonfiguruj nazwy modułów wyjściowych elementu WebPack

* Otwórz plik *./client-app/build/webpack.base.conf.js* i Dodaj następujące właściwości do właściwości Output:

    ```js
    devtoolModuleFilenameTemplate: '[absolute-resource-path]',
    devtoolFallbackModuleFilenameTemplate: '[absolute-resource-path]?[hash]'
    ```

### <a name="add-typescript-support-with-the-vue-cli"></a>Dodawanie obsługi języka TypeScript przy użyciu interfejsu wiersza polecenia Vue

Te kroki wymagają Vue-CLI 3,0, który jest obecnie w wersji beta.

1. Przejdź do wiersza polecenia i Zmień bieżący katalog na folder główny projektu.

1. Wpisz `vue create client-app` , a następnie wybierz pozycję **ręcznie wybierz funkcje**.

1. Wybierz pozycję **TypeScript**, a następnie wybierz inne żądane opcje.

1. Wykonaj pozostałe kroki i udziel odpowiedzi na pytania.

#### <a name="configure-a-vuejs-project-for-typescript"></a>Skonfiguruj projekt Vue.js dla języka TypeScript

1. Otwórz plik *./client-app/tsconfig.jsna* i Dodaj `noEmit:true` do opcji kompilatora.

    Ustawienie tej opcji pozwala uniknąć powstawania projektu za każdym razem, gdy kompilujesz w programie Visual Studio.

1. Następnie utwórz plik *vue.config.js* w pliku *./Client-App/* i Dodaj następujący kod.

    ```js
    module.exports = {
        outputDir: '../wwwroot',

        configureWebpack: {
            output: {
                devtoolModuleFilenameTemplate: '[absolute-resource-path]',
                devtoolFallbackModuleFilenameTemplate: '[absolute-resource-path]?[hash]'
            }
        }
    };
    ```

    Poprzedni kod konfiguruje pakiet WebPack i ustawia folder wwwroot.

#### <a name="build-with-vue-cli-30"></a>Kompiluj z Vue-CLI 3,0

Nieznany problem z Vue-CLI 3,0 może uniemożliwić automatyzację procesu kompilacji. Za każdym razem, gdy próbujesz odświeżyć folder wwwroot, należy uruchomić polecenie `npm run build` w folderze klient-aplikacja.

Alternatywnie można skompilować projekt Vue-CLI 3,0 jako zdarzenie sprzed kompilacji przy użyciu właściwości projektu ASP.NET. Kliknij prawym przyciskiem myszy projekt, wybierz polecenie **Właściwości** i Dołącz następujące polecenia na karcie **kompilacja** w polu tekstowym **wiersz polecenia zdarzenia przed kompilacją** .

``` cmd
cd ./client-app
npm run build
cd ../
```

## <a name="limitations"></a>Ograniczenia

* `lang` atrybut obsługuje tylko języki JavaScript i TypeScript. Akceptowane są następujące wartości: JS, JSX, TS i TSX.
* `lang` atrybut nie działa z tagami szablonu lub stylu.
* Debugowanie bloków skryptu w plikach *. Vue* nie jest obsługiwane ze względu na jego wstępnie przetworzony charakter.
* Język TypeScript nie rozpoznaje plików *Vue* jako modułów. Potrzebny jest plik, który zawiera kod, taki jak poniżej, aby poinformować program TypeScript, jak wyglądają pliki *. Vue* (szablon Vue-CLI 3,0 zawiera już ten plik).

    ```js
    // ./client-app/vue-shims.d.ts
    declare module "*.vue" {
        import Vue from "vue";
        export default Vue;
    }
    ```

* Uruchomienie polecenia `npm run build` jako zdarzenia sprzed kompilacji we właściwościach projektu nie działa, gdy jest używany Vue-cli 3,0.

## <a name="see-also"></a>Zobacz też

- [Przewodnik wprowadzenie Vue](https://vuejs.org/v2/guide).
- [Projekt interfejsu wiersza polecenia Vue](https://github.com/vuejs/vue-cli).
- [Dokumentacja dotycząca konfiguracji pakietu WebPack](https://webpack.js.org/configuration/).
