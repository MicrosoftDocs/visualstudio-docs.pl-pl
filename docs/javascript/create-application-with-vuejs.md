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
ms.openlocfilehash: 2fd172de3791006688c5d9542a7d8c353bc4831e
ms.sourcegitcommit: d4bea2867a4f0c3b044fd334a54407c0fe87f9e8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58789569"
---
# <a name="create-a-vuejs-application-using-nodejs-tools-for-visual-studio"></a>Tworzenie aplikacji Vue.js przy użyciu narzędzia Node.js dla programu Visual Studio

Program Visual Studio 2017 zapewnia lepszą obsługę [Vue.js](https://vuejs.org/) struktury, która ulepsza środowisko projektowania, podczas tworzenia aplikacji przy użyciu Vue.js, JavaScript i TypeScript.

Następujące nowe funkcje obsługi opracowywania aplikacji Vue.js w programie Visual Studio:

* Obsługa bloków skryptu, styl i szablonu w *.vue* plików
* Rozpoznawanie `lang` atrybutu na *.vue* plików
* VUE.js szablonów projektów i plików

## <a name="prerequisites"></a>Wymagania wstępne

* Konieczne jest posiadanie programu Visual Studio 2017 wersji Preview należy zachować 15,8 3 lub nowszym i **programowania Node.js** obciążenia.

    > [!IMPORTANT]
    > W tym artykule wymaga funkcji, które są tylko dostępne począwszy od programu Visual Studio 2017 w wersji Preview należy zachować 15,8 3.

    Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [program Visual Studio pobiera](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) strony, aby zainstalować go za darmo.

    Jeśli musisz zainstalować obciążenie, ale już program Visual Studio, przejdź do strony **narzędzia** > **Pobierz narzędzia i funkcje...** , która otwiera Instalatora programu Visual Studio. Wybierz **programowania Node.js** obciążenia, wybierz **Modyfikuj**.

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
    Naciśnij klawisz **Esc** aby zamknąć okno rozpoczęcia. Typ **Ctrl + Q** aby otworzyć pole wyszukiwania, wpisz **asp.net**, następnie wybierz **Tworzenie nowej aplikacji sieci Web platformy ASP.NET Core**. W oknie dialogowym wybierz **Utwórz**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Na pasku menu u góry wybierz **pliku** > **New** > **projektu**. W okienku po lewej stronie **nowy projekt** okna dialogowego rozwiń **Visual C#** , następnie wybierz **Web**. W środkowym okienku wybierz **aplikacji sieci Web programu ASP.NET Core**, następnie wybierz **OK**.
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

1. Typ `vue init webpack ClientApp` i wykonaj kroki po wyświetleniu monitu o odpowiedzieć dodatkowe pytania.

#### <a name="modify-the-webpack-configuration-to-output-the-built-files-to-wwwroot"></a>Modyfikowanie konfiguracji webpack do utworzonych plików wyjściowych do wwwroot

* Otwórz plik *./ClientApp/config/index.js*i zmień `build.index` i `build.assetsRoot` wwwroot ścieżki:

    ```js
    // Template for index.html
    index: path.resolve(__dirname, '../../wwwroot/index.html'),

    // Paths
    assetsRoot: path.resolve(__dirname, '../../wwwroot'),
    ```

#### <a name="indicate-the-project-to-build-the-clientapp-each-time-that-a-build-is-triggered"></a>Projekt do kompilacji ClientApp wskazują za każdym razem, kompilacja zostaje wyzwolona

1. W programie Visual Studio, przejdź do **projektu** > **właściwości** > **zdarzenia kompilacji**.

1. Na **wiersz polecenia zdarzenia sprzed kompilacji**, typ `npm --prefix ./ClientApp run build`.

#### <a name="configure-webpacks-output-module-names"></a>Konfigurowanie nazwy modułów dane wyjściowe webpack firmy

* Otwórz plik *./ClientApp/build/webpack.base.conf.js*i dodaj następujące właściwości dla właściwości danych wyjściowych:

    ```js
    devtoolModuleFilenameTemplate: '[absolute-resource-path]',
    devtoolFallbackModuleFilenameTemplate: '[absolute-resource-path]?[hash]'
    ```

### <a name="add-typescript-support-with-the-vue-cli"></a>Dodanie obsługi TypeScript za pomocą interfejsu wiersza polecenia Vue

Te kroki wymagają vue-cli 3.0, która jest obecnie dostępna w wersji beta.

1. Przejdź do wiersza polecenia i zmień bieżący katalog na folder główny projektu.

1. Typ `vue create ClientApp`, a następnie wybierz **ręcznie wybrać funkcje**.

1. Wybierz **Typescript**, a następnie wybierz inne żądane opcje.

1. Wykonaj pozostałe kroki i odpowiadać na pytania.

#### <a name="configure-a-vuejs-project-for-typescript"></a>Konfigurowanie projektu Vue.js dla TypeScript

1. Otwórz plik *./ClientApp/tsconfig.json* i Dodaj `noEmit:true` w opcjach kompilatora.

    To ustawienie pozwala uniknąć zaśmiecania projektu za każdym razem, gdy kompilujesz w programie Visual Studio.

1. Następnie należy utworzyć *vue.config.js* w pliku *./ClientApp/* i Dodaj następujący kod.

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

Wystąpił nieznany problem z vue — interfejs wiersza polecenia 3.0 zapobiega Automatyzowanie procesu kompilacji. Za każdym razem, spróbuj odświeżyć folderu wwwroot, musisz uruchomić polecenie `npm run build` w folderze ClientApp.

## <a name="limitations"></a>Ograniczenia

* `lang` atrybut tylko obsługuje języki JavaScript i TypeScript. Akceptowane wartości to: node.js, jsx, ts i tsx.
* `lang` atrybut nie działa z tagami stylu lub szablonu.
* Debugowanie skryptu bloków w *.vue* plików nie jest obsługiwane ze względu na charakter wstępnie przetworzony.
* TypeScript nie rozpoznaje *.vue* pliki modułów. Potrzebujesz pliku, który zawiera kod, takich jak co mówić TypeScript *.vue* wyglądać plików (szablon vue-cli 3.0 zawiera już ten plik).

    ```js
    // ./ClientApp/vue-shims.d.ts
    declare module "*.vue" {
        import Vue from "vue";
        export default Vue;
    }
    ```

* Uruchomienie polecenia `npm run build` jako zdarzenie sprzed kompilacji, we właściwościach projektu nie rozwiąże problemu, korzystając z vue-cli 3.0.

## <a name="see-also"></a>Zobacz także

- [Przewodnik Wprowadzenie dla VUE get](https://vuejs.org/v2/guide).
- [Projekt interfejsu wiersza polecenia VUE](https://github.com/vuejs/vue-cli).
- [Dokumentacja konfiguracji Webpack](https://webpack.js.org/configuration/).
