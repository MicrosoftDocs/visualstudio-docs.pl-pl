---
title: Tworzenie aplikacji Vue.js przy użyciu pliku Node.js
description: Aplikacje Node.js można tworzyć w programie Visual Studio przy użyciu struktury Vue.js
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
ms.openlocfilehash: edf5307984b4efc00a7c83c84fe5cb87954a93dd
ms.sourcegitcommit: 5c804c42d24d35dcf2ba195aba9ce07031743f62
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81744916"
---
# <a name="create-a-vuejs-application-using-nodejs-tools-for-visual-studio"></a>Tworzenie aplikacji Vue.js przy użyciu narzędzia Node.js dla programu Visual Studio

Program Visual Studio obsługuje tworzenie aplikacji za pomocą struktury [Vue.js](https://vuejs.org/) w języku JavaScript lub TypeScript.

Następujące nowe funkcje obsługują tworzenie aplikacji Vue.js w programie Visual Studio:

* Obsługa bloków skryptów, stylów i szablonów w plikach *.vue*
* Rozpoznawanie `lang` atrybutu w plikach *.vue*
* Szablony projektów i plików Vue.js

## <a name="prerequisites"></a>Wymagania wstępne

* Musi być zainstalowany program Visual Studio 2017 w wersji 15.8 lub nowszej wersji oraz obciążenie **deweloperskie node.js.**

    > [!IMPORTANT]
    > Ten artykuł wymaga funkcji, które są dostępne tylko począwszy od programu Visual Studio 2017 w wersji 15.8.

    ::: moniker range=">=vs-2019"
    Jeśli wymagana wersja nie jest jeszcze zainstalowana, zainstaluj [program Visual Studio 2019](https://visualstudio.microsoft.com/downloads).
    ::: moniker-end
    ::: moniker range="vs-2017"
    Jeśli program Visual Studio nie został jeszcze zainstalowany, przejdź do strony pobierania programu Visual [Studio,](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)aby zainstalować ją bezpłatnie.
    ::: moniker-end

    Jeśli chcesz zainstalować obciążenie, ale masz już program Visual Studio, przejdź do **narzędzia** > **Pobierz narzędzia i funkcje...**, który otwiera Instalator programu Visual Studio. Wybierz obciążenie **deweloperne node.js,** a następnie wybierz pozycję **Modyfikuj**.

* Aby utworzyć projekt ASP.NET Core, musisz mieć zainstalowane ASP.NET i tworzenia sieci Web oraz obciążeń deweloperskich .NET Core.

* Musi być zainstalowany środowisko uruchomieniowe Node.js.

    Jeśli nie masz go zainstalowanego, zainstaluj wersję LTS z [witryny node.js.](https://nodejs.org/en/download/) Ogólnie rzecz biorąc program Visual Studio automatycznie wykrywa zainstalowane środowisko uruchomieniowe Node.js. Jeśli nie wykryje zainstalowanego środowiska uruchomieniowego, można skonfigurować projekt, aby odwoływać się do zainstalowanego środowiska uruchomieniowego na stronie właściwości. (Po utworzeniu projektu kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Właściwości).**

## <a name="create-a-vuejs-project-using-nodejs"></a>Tworzenie projektu Vue.js przy użyciu pliku Node.js

Możesz użyć nowych szablonów Vue.js, aby utworzyć nowy projekt. Korzystanie z szablonu jest najprostszym sposobem rozpoczęcia pracy. Aby uzyskać szczegółowe kroki, zobacz [Tworzenie pierwszej aplikacji Vue.js za pomocą programu Visual Studio.](../javascript/quickstart-vuejs-with-nodejs.md)

## <a name="create-a-vuejs-project-with-aspnet-core-and-the-vue-cli"></a>Tworzenie projektu Vue.js z ASP.NET Core i Vue CLI

Vue.js zapewnia oficjalny cli dla projektów szybko rusztowania. Jeśli chcesz użyć interfejsu wiersza polecenia do utworzenia aplikacji, wykonaj kroki opisane w tym artykule, aby skonfigurować środowisko programistyczne.

> [!IMPORTANT]
> W tych krokach założono, że masz już pewne doświadczenie z platformą Vue.js. Jeśli nie, odwiedź [Stronę Vue.js,](https://vuejs.org/) aby dowiedzieć się więcej o ramach.

### <a name="create-a-new-aspnet-core-project"></a>Tworzenie nowego projektu ASP.NET Core

W tym przykładzie należy użyć pustej ASP.NET podstawowej aplikacji (C#). Można jednak wybierać spośród różnych projektów i języków programowania.

#### <a name="create-an-empty-project"></a>Tworzenie pustego projektu

1. Otwórz program Visual Studio i utwórz nowy projekt.

    ::: moniker range=">=vs-2019"
    Naciśnij **klawisz Esc,** aby zamknąć okno początkowe. Wpisz **Ctrl + Q,** aby otworzyć pole wyszukiwania, wpisz **asp.net**, a następnie wybierz pozycję **Utwórz nową ASP.NET podstawową aplikację sieci Web**. W wyświetlonym oknie dialogowym wpisz nazwę **klient-aplikacja**, a następnie wybierz pozycję **Utwórz**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Na górnym pasku menu wybierz pozycję **Plik** > **nowego** > **projektu**. W lewym okienku okna dialogowego **Nowy projekt** rozwiń węzeł **Visual C#**, a następnie wybierz pozycję **Sieć Web**. W środkowym okienku wybierz pozycję **ASP.NET Core Web Application**, wpisz nazwę **client-app**, a następnie wybierz przycisk **OK**.
    ::: moniker-end

    Jeśli nie widzisz szablonu projektu **ASP.NET Core Web Application,** musisz zainstalować ASP.NET i obciążenia **tworzenia stron internetowych** oraz . Najpierw podstawowe obciążenie **programistyczne NET.** Aby zainstalować obciążenia, kliknij łącze **Otwórz Instalator programu Visual Studio** w lewym okienku okna dialogowego Nowy **projekt** (wybierz **opcję Plik** > **nowego** > **projektu**). Uruchamia instalator programu Visual Studio. Wybierz wymagane obciążenia.

1. Wybierz **pozycję Puste**, a następnie kliknij przycisk **OK**.

    Visual Studio tworzy projekt, który otwiera się w Eksploratorze rozwiązań (prawe okienko).

#### <a name="configure-the-project-startup-file"></a>Konfigurowanie pliku uruchamiania projektu

* Otwórz plik *./Startup.cs*i dodaj następujące wiersze do metody Konfiguruj:

    ```csharp
    app.UseDefaultFiles(); // Enables default file mapping on the web root.
    app.UseStaticFiles(); // Marks files on the web root as servable.
    ```

### <a name="install-the-vue-cli"></a>Zainstaluj vue CLI

Aby zainstalować moduł vue-cli npm, otwórz `npm install --g vue-cli` wiersz `npm install -g @vue/cli` polecenia i wpisz lub w wersji 3.0 (obecnie w wersji beta).

### <a name="scaffold-a-new-client-application-using-the-vue-cli"></a>Rusztowanie nowej aplikacji klienckiej przy użyciu interfejsu wiersza polecenia vue

1. Przejdź do wiersza polecenia i zmień bieżący katalog na folder główny projektu.

1. Wpisz `vue init webpack client-app` i wykonaj kroki po wyświetleniu monitu o udzielenie odpowiedzi na dodatkowe pytania.

    > [!NOTE]
    > W przypadku plików *.vue* musisz użyć webpacku lub podobnej struktury z programem ładującego, aby wykonać konwersję. TypeScript i Visual Studio nie wiedzą, jak skompilować pliki *.vue.* To samo dotyczy sprzedaży pakietowej; TypeScript nie wie, jak przekonwertować moduły ES2015 (czyli `import` i `export` instrukcje) na jeden końcowy plik *.js* do załadowania w przeglądarce. Ponownie, WebPack jest najlepszym wyborem tutaj. Aby napędzać ten proces z poziomu programu Visual Studio przy użyciu programu MSBuild, należy rozpocząć od szablonu programu Visual Studio. Obecnie nie ma ASP.NET szablonu dla rozwoju Vue.js in-the-box.

#### <a name="modify-the-webpack-configuration-to-output-the-built-files-to-wwwroot"></a>Zmodyfikuj konfigurację webpacku, aby wyprowadzić wbudowane pliki do wwwroot

* Otwórz plik *./client-app/config/index.js*i `build.index` zmień `build.assetsRoot` ścieżkę i na wwwroot:

    ```js
    // Template for index.html
    index: path.resolve(__dirname, '../../wwwroot/index.html'),

    // Paths
    assetsRoot: path.resolve(__dirname, '../../wwwroot'),
    ```

#### <a name="indicate-the-project-to-build-the-client-app-each-time-that-a-build-is-triggered"></a>Wskaż projekt do utworzenia aplikacji klienckiej za każdym razem, gdy zostanie wyzwolona kompilacja

1. W programie Visual Studio przejdź do zdarzenia > **kompilacji** > **Build Events**właściwości **projektu.**

1. W **wierszu polecenia zdarzenia przed kompilacją**wpisz `npm --prefix ./client-app run build`.

#### <a name="configure-webpacks-output-module-names"></a>Konfigurowanie nazw modułów wyjściowych pakietu wwwpack

* Otwórz plik *./client-app/build/webpack.base.conf.js*i dodaj następujące właściwości do właściwości wyjściowej:

    ```js
    devtoolModuleFilenameTemplate: '[absolute-resource-path]',
    devtoolFallbackModuleFilenameTemplate: '[absolute-resource-path]?[hash]'
    ```

### <a name="add-typescript-support-with-the-vue-cli"></a>Dodawanie obsługi języka TypeScript za pomocą interfejsu wiersza polecenia Vue

Te kroki wymagają vue-cli 3.0, który jest obecnie w wersji beta.

1. Przejdź do wiersza polecenia i zmień bieżący katalog na folder główny projektu.

1. Wpisz `vue create client-app`, a następnie wybierz pozycję **Ręcznie wybierz operacje**.

1. Wybierz **pozycję Typescript**, a następnie wybierz inne żądane opcje.

1. Wykonaj pozostałe kroki i odpowiedz na pytania.

#### <a name="configure-a-vuejs-project-for-typescript"></a>Konfigurowanie projektu Vue.js dla języka TypeScript

1. Otwórz plik *./client-app/tsconfig.json* `noEmit:true` i dodaj do opcji kompilatora.

    Ustawiając tę opcję, można uniknąć zaśmiecania projektu za każdym razem, gdy tworzysz w programie Visual Studio.

1. Następnie utwórz plik *vue.config.js* w *./client-app/* i dodaj następujący kod.

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

    Poprzedni kod konfiguruje webpack i ustawia folder wwwroot.

#### <a name="build-with-vue-cli-30"></a>Zbuduj z vue-cli 3.0

Nieznany problem z vue-cli 3.0 może uniemożliwić automatyzację procesu kompilacji. Za każdym razem, gdy próbujesz odświeżyć folder wwwroot, musisz uruchomić polecenie `npm run build` w folderze klient-aplikacja.

Alternatywnie można utworzyć projekt vue-cli 3.0 jako zdarzenie przed kompilacją przy użyciu właściwości projektu ASP.NET. Kliknij prawym przyciskiem myszy projekt, wybierz polecenie **Właściwości**i dołącz następujące polecenia na karcie **Kompilacja** w polu **tekstowym wiersza polecenia Zdarzenia przed kompilacją.**

``` cmd
cd ./client-app
npm run build
cd ../
```

## <a name="limitations"></a>Ograniczenia

* `lang`atrybut obsługuje tylko języki JavaScript i TypeScript. Akceptowane wartości to: js, jsx, ts i tsx.
* `lang`atrybut nie działa z tagami szablonów lub stylów.
* Debugowanie bloków skryptów w plikach *.vue* nie jest obsługiwane ze względu na jego wstępnie przetworzony charakter.
* TypeScript nie rozpoznaje plików *.vue* jako modułów. Potrzebny jest plik zawierający kod, taki jak *poniższy,* aby poinformować TypeScript, jak wyglądają pliki .vue (szablon vue-cli 3.0 zawiera już ten plik).

    ```js
    // ./client-app/vue-shims.d.ts
    declare module "*.vue" {
        import Vue from "vue";
        export default Vue;
    }
    ```

* Uruchamianie `npm run build` polecenia jako zdarzenia przed kompilacją we właściwościach projektu nie działa podczas korzystania z vue-cli 3.0.

## <a name="see-also"></a>Zobacz też

- [Vue rozpocząć przewodnik](https://vuejs.org/v2/guide).
- [Projekt Vue CLI](https://github.com/vuejs/vue-cli).
- [Dokumentacja konfiguracji pakietu Webpack](https://webpack.js.org/configuration/).
