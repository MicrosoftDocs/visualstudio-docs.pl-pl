---
title: Tworzenie aplikacji Vue.js przy użyciu środowiska Node.js
description: W programie Visual Studio przy użyciu Vue.js framework można tworzyć aplikacje Node.js
ms.custom: seodec18
ms.date: 07/06/2018
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: af781f5735a3539d8b0e2d098bb9252bc60193fc
ms.sourcegitcommit: 44e9b1d9230fcbbd081ee81be9d4be8a485d8502
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/30/2019
ms.locfileid: "70180270"
---
# <a name="create-a-vuejs-application-using-nodejs-tools-for-visual-studio"></a>Tworzenie aplikacji Vue.js przy użyciu narzędzia Node.js dla programu Visual Studio

Program Visual Studio obsługuje programowanie aplikacji za pomocą platformy [Vue. js](https://vuejs.org/) w języku JavaScript lub TypeScript.

Następujące nowe funkcje obsługi opracowywania aplikacji Vue.js w programie Visual Studio:

* Obsługa bloków skryptu, styl i szablonu w *.vue* plików
* Rozpoznawanie `lang` atrybutu na *.vue* plików
* VUE.js szablonów projektów i plików

## <a name="prerequisites"></a>Wymagania wstępne

* Wymagany jest program Visual Studio 2017 w wersji 15,8 lub nowszej oraz obciążenie programowaniem **Node. js** .

    > [!IMPORTANT]
    > Ten artykuł wymaga funkcji, które są dostępne tylko w programie Visual Studio 2017 w wersji 15,8.

    ::: moniker range=">=vs-2019"
    Jeśli wymagana wersja nie jest jeszcze zainstalowana, zainstaluj [program Visual Studio 2019](https://visualstudio.microsoft.com/downloads).
    ::: moniker-end
    ::: moniker range="vs-2017"
    Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [program Visual Studio pobiera](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) strony, aby zainstalować go za darmo.
    ::: moniker-end

    Jeśli musisz zainstalować obciążenie, ale masz już program Visual Studio, przejdź do pozycji **Narzędzia** > **Pobierz narzędzia i funkcje..** ., co spowoduje otwarcie Instalator programu Visual Studio. Wybierz **programowania Node.js** obciążenia, wybierz **Modyfikuj**.

* Aby utworzyć projekt platformy ASP.NET Core, konieczne jest posiadanie programu ASP.NET i tworzenie aplikacji sieci web oraz zainstalowanych obciążeń programowanie dla wielu platform .NET Core.

* Konieczne jest posiadanie zainstalowanego środowiska uruchomieniowego Node.js.

    Jeśli nie jest ona zainstalowana, zainstaluj wersję LTS z [Node.js](https://nodejs.org/en/download/) witryny sieci Web. Ogólnie rzecz biorąc program Visual Studio automatycznie wykrywa zainstalowane środowisko uruchomieniowe Node.js. Jeśli nie zostanie wykryta zainstalowanego środowiska uruchomieniowego, można skonfigurować projekt, aby odwoływać się do zainstalowanego środowiska uruchomieniowego na stronie właściwości. (Po utworzeniu projektu, kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **właściwości**).

## <a name="create-a-vuejs-project-using-a-template"></a>Utwórz projekt Vue.js przy użyciu szablonu

Nowe szablony Vue.js można użyć, aby utworzyć nowy projekt. Korzystanie z tego szablonu jest najprostszym sposobem na rozpoczęcie pracy. Aby uzyskać szczegółowe instrukcje, zobacz [za pomocą Visual Studio Utwórz swoją pierwszą aplikację Vue.js](../javascript/quickstart-vuejs-with-nodejs.md).

## <a name="create-a-vuejs-project-with-aspnet-core-and-the-vue-cli"></a>Utwórz projekt Vue.js za pomocą platformy ASP.NET Core i Vue interfejsu wiersza polecenia

VUE.js zapewnia oficjalny interfejs wiersza polecenia szybkiego tworzenia szkieletów projektów. Jeśli chcesz używać interfejsu wiersza polecenia do tworzenia aplikacji, wykonaj kroki opisane w tym artykule, aby skonfigurować swoje Środowisko deweloperskie.

> [!IMPORTANT]
> Tych krokach założono, że masz już pewne doświadczenie w zakresie Vue.js framework. Jeśli nie, odwiedź stronę [Vue.js](https://vuejs.org/) dowiedzieć się więcej o strukturze.

### <a name="create-a-new-aspnet-core-project"></a>Utwórz nowy projekt ASP.NET Core

W tym przykładzie należy użyć pustą aplikację ASP.NET Core (C#). Możesz z różnych projektów i języków programowania.

#### <a name="create-an-empty-project"></a>Utwórz pusty projekt

1. Otwórz program Visual Studio i Utwórz nowy projekt.

    ::: moniker range=">=vs-2019"
    Naciśnij klawisz **ESC** , aby zamknąć okno uruchamiania. **Naciśnij klawisze CTRL + Q** , aby otworzyć pole wyszukiwania, wpisz **ASP.NET**, a następnie wybierz pozycję **utwórz nową aplikację sieci Web ASP.NET Core**. W wyświetlonym oknie dialogowym wpisz nazwę **Client-App**, a następnie wybierz pozycję Create ( **Utwórz**).
    ::: moniker-end
    ::: moniker range="vs-2017"
    Na pasku menu u góry wybierz **pliku** > **New** > **projektu**. W lewym okienku okna dialogowego **Nowy projekt** rozwiń pozycję **C#Wizualizacja**, a następnie wybierz pozycję **Sieć Web**. W środkowym okienku wybierz pozycję **ASP.NET Core aplikacja sieci Web**, wpisz nazwę **klient-aplikacja**, a następnie wybierz **przycisk OK**.
    ::: moniker-end

    Jeśli nie widzisz **aplikacji sieci Web programu ASP.NET Core** szablonu projektu należy zainstalować **ASP.NET i tworzenie aplikacji internetowych** obciążenia i. **.NET Core** pakietu roboczego programowanie na pierwszym. Aby zainstalować workload(s), kliknij przycisk **Otwórz Instalator programu Visual Studio** łącze w okienku po lewej stronie **nowy projekt** okno dialogowe (wybierz **pliku**  >  **Nowe** > **projektu**). Uruchamia Instalatora programu Visual Studio. Wybierz wymagane obciążenia.

1. Wybierz **pusty**, a następnie kliknij przycisk **OK**.

    Program Visual Studio tworzy projekt, który zostanie otwarty w oknie Eksploratora rozwiązań (w okienku po prawej stronie).

#### <a name="configure-the-project-startup-file"></a>Konfigurowanie projektu plik startowy

* Otwórz plik *./Startup.cs*i dodaj następujące wiersze do metody konfiguracji:

    ```csharp
    app.UseDefaultFiles(); // Enables default file mapping on the web root.
    app.UseStaticFiles(); // Marks files on the web root as servable.
    ```

### <a name="install-the-vue-cli"></a>Zainstaluj vue interfejsu wiersza polecenia

Aby zainstalować moduł npm vue — interfejs wiersza polecenia, otwórz wiersz polecenia i wpisz `npm install --g vue-cli` lub `npm install -g @vue/cli` w wersji 3.0 (obecnie dostępna w wersji beta).

### <a name="scaffold-a-new-client-application-using-the-vue-cli"></a>Tworzenie szkieletu nową aplikację klienta, za pomocą vue interfejsu wiersza polecenia

1. Przejdź do wiersza polecenia i zmień bieżący katalog na folder główny projektu.

1. Typ `vue init webpack client-app` i wykonaj kroki po wyświetleniu monitu o odpowiedzieć dodatkowe pytania.

    > [!NOTE]
    > W przypadku plików *. Vue* należy użyć programu WebPack lub podobnej struktury z modułem ładującym w celu wykonania konwersji. Programy TypeScript i Visual Studio nie wiedzą, jak kompilować pliki *. Vue* . Ta sama wartość dotyczy grupowania; Język TypeScript nie wie, jak konwertować moduły ES2015 (to jest `import` i `export` instrukcje) na jeden końcowy plik *. js* do załadowania w przeglądarce. Teraz pakiet WebPack jest najlepszym wyborem. Aby uzyskać ten proces z poziomu programu Visual Studio przy użyciu programu MSBuild, należy zacząć od szablonu programu Visual Studio. Obecnie nie istnieje szablon ASP.NET do tworzenia aplikacji Vue. js.

#### <a name="modify-the-webpack-configuration-to-output-the-built-files-to-wwwroot"></a>Modyfikowanie konfiguracji webpack do utworzonych plików wyjściowych do wwwroot

* Otwórz plik *./Client-App/config/index.js*i Zmień `build.index` ścieżkę i `build.assetsRoot` do pliku wwwroot:

    ```js
    // Template for index.html
    index: path.resolve(__dirname, '../../wwwroot/index.html'),

    // Paths
    assetsRoot: path.resolve(__dirname, '../../wwwroot'),
    ```

#### <a name="indicate-the-project-to-build-the-client-app-each-time-that-a-build-is-triggered"></a>Wskaż projekt, aby skompilować aplikację kliencką za każdym razem, gdy kompilacja jest wyzwalana

1. W programie Visual Studio, przejdź do **projektu** > **właściwości** > **zdarzenia kompilacji**.

1. Na **wiersz polecenia zdarzenia sprzed kompilacji**, typ `npm --prefix ./client-app run build`.

#### <a name="configure-webpacks-output-module-names"></a>Konfigurowanie nazwy modułów dane wyjściowe webpack firmy

* Otwórz plik *./Client-App/Build/WebPack.Base.conf.js*i Dodaj następujące właściwości do właściwości Output:

    ```js
    devtoolModuleFilenameTemplate: '[absolute-resource-path]',
    devtoolFallbackModuleFilenameTemplate: '[absolute-resource-path]?[hash]'
    ```

### <a name="add-typescript-support-with-the-vue-cli"></a>Dodanie obsługi TypeScript za pomocą interfejsu wiersza polecenia Vue

Te kroki wymagają vue-cli 3.0, która jest obecnie dostępna w wersji beta.

1. Przejdź do wiersza polecenia i zmień bieżący katalog na folder główny projektu.

1. Typ `vue create client-app`, a następnie wybierz **ręcznie wybrać funkcje**.

1. Wybierz **Typescript**, a następnie wybierz inne żądane opcje.

1. Wykonaj pozostałe kroki i odpowiadać na pytania.

#### <a name="configure-a-vuejs-project-for-typescript"></a>Konfigurowanie projektu Vue.js dla TypeScript

1. Otwórz plik *./Client-App/tsconfig.JSON* i Dodaj `noEmit:true` do opcji kompilatora.

    To ustawienie pozwala uniknąć zaśmiecania projektu za każdym razem, gdy kompilujesz w programie Visual Studio.

1. Następnie utwórz plik *Vue. config. js* w *./Client-App/* i Dodaj następujący kod.

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

    Powyższy kod konfiguruje webpack i ustawia folderze wwwroot.

#### <a name="build-with-vue-cli-30"></a>Tworzenie za pomocą vue-cli 3.0

Nieznany problem z Vue-CLI 3,0 może uniemożliwić automatyzację procesu kompilacji. Za każdym razem, gdy próbujesz odświeżyć folder wwwroot, należy uruchomić polecenie `npm run build` w folderze klient-aplikacja.

Alternatywnie można skompilować projekt Vue-CLI 3,0 jako zdarzenie sprzed kompilacji przy użyciu właściwości projektu ASP.NET. Kliknij prawym przyciskiem myszy projekt, wybierz polecenie **Właściwości**i Dołącz następujące polecenia na karcie **kompilacja** w polu tekstowym **wiersz polecenia zdarzenia przed kompilacją** .

``` cmd
cd ./client-app
npm run build
cd ../
```

## <a name="limitations"></a>Ograniczenia

* `lang` atrybut tylko obsługuje języki JavaScript i TypeScript. Akceptowane wartości to: node.js, jsx, ts i tsx.
* `lang` atrybut nie działa z tagami stylu lub szablonu.
* Debugowanie skryptu bloków w *.vue* plików nie jest obsługiwane ze względu na charakter wstępnie przetworzony.
* TypeScript nie rozpoznaje *.vue* pliki modułów. Potrzebujesz pliku, który zawiera kod, takich jak co mówić TypeScript *.vue* wyglądać plików (szablon vue-cli 3.0 zawiera już ten plik).

    ```js
    // ./client-app/vue-shims.d.ts
    declare module "*.vue" {
        import Vue from "vue";
        export default Vue;
    }
    ```

* Uruchomienie polecenia `npm run build` jako zdarzenie sprzed kompilacji, we właściwościach projektu nie rozwiąże problemu, korzystając z vue-cli 3.0.

## <a name="see-also"></a>Zobacz także

- [Przewodnik wprowadzenie Vue](https://vuejs.org/v2/guide).
- [Projekt interfejsu wiersza polecenia Vue](https://github.com/vuejs/vue-cli).
- [Dokumentacja dotycząca konfiguracji pakietu WebPack](https://webpack.js.org/configuration/).
