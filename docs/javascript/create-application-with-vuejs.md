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
ms.openlocfilehash: a83e19f808a3f3ab7e1bf9f4fb58f5ddd7a218b7
ms.sourcegitcommit: 91c7f1b525e0c22d938bc4080ba4ceac2483474f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2019
ms.locfileid: "67033142"
---
# <a name="create-a-vuejs-application-using-nodejs-tools-for-visual-studio"></a>Tworzenie aplikacji Vue.js przy użyciu narzędzia Node.js dla programu Visual Studio

Program Visual Studio obsługuje tworzenie aplikacji za pomocą [Vue.js](https://vuejs.org/) framework w JavaScript i TypeScript.

Następujące nowe funkcje obsługi opracowywania aplikacji Vue.js w programie Visual Studio:

* Obsługa bloków skryptu, styl i szablonu w *.vue* plików
* Rozpoznawanie `lang` atrybutu na *.vue* plików
* VUE.js szablonów projektów i plików

## <a name="prerequisites"></a>Wymagania wstępne

* Konieczne jest posiadanie programu Visual Studio 2017 w wersji 15.8 lub nowszy i **programowania Node.js** obciążenia.

    > [!IMPORTANT]
    > W tym artykule wymaga funkcji, które są dostępne, począwszy od programu Visual Studio 2017 w wersji 15.8 tylko.

    ::: moniker range=">=vs-2019"
    Jeśli wymagana wersja nie jest już zainstalowana, zainstaluj [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019).
    ::: moniker-end
    ::: moniker range="vs-2017"
    Jeśli jeszcze nie zainstalowano programu Visual Studio, przejdź do strony [program Visual Studio pobiera](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) strony, aby zainstalować go za darmo.
    ::: moniker-end

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
    Naciśnij klawisz **Esc** aby zamknąć okno rozpoczęcia. Typ **Ctrl + Q** aby otworzyć pole wyszukiwania, wpisz **asp.net**, następnie wybierz **Tworzenie nowej aplikacji sieci Web platformy ASP.NET Core**. W oknie dialogowym wpisz nazwę **aplikację kliencką**, a następnie wybierz **Utwórz**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Na pasku menu u góry wybierz **pliku** > **New** > **projektu**. W okienku po lewej stronie **nowy projekt** okna dialogowego rozwiń **Visual C#** , następnie wybierz **Web**. W środkowym okienku wybierz **aplikacji sieci Web programu ASP.NET Core**, wpisz nazwę **aplikację kliencką**, a następnie wybierz **OK**.
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
    > Aby uzyskać *.vue* plików, należy użyć WebPack lub podobne struktury przy użyciu modułu ładującego, aby wykonać konwersję. TypeScript i programu Visual Studio nie wiedzieć, jak skompilować *.vue* plików. Dotyczy to także tworzenie pakietów; TypeScript nie wie, jak konwertować ES2015 modułów (oznacza to, że `import` i `export` instrukcji) do pojedynczego final *js* plik do załadowania w przeglądarce. Ponownie WebPack jest najlepszym wyborem. Można dostarczać ten proces z poziomu programu Visual Studio, korzystając z programu MSBuild, należy uruchomić z szablonu programu Visual Studio. Obecnie nie ma ASP.NET szablonu dla Vue.js rozwoju w pakiecie.

#### <a name="modify-the-webpack-configuration-to-output-the-built-files-to-wwwroot"></a>Modyfikowanie konfiguracji webpack do utworzonych plików wyjściowych do wwwroot

* Otwórz plik *./client-app/config/index.js*i zmień `build.index` i `build.assetsRoot` wwwroot ścieżki:

    ```js
    // Template for index.html
    index: path.resolve(__dirname, '../../wwwroot/index.html'),

    // Paths
    assetsRoot: path.resolve(__dirname, '../../wwwroot'),
    ```

#### <a name="indicate-the-project-to-build-the-client-app-each-time-that-a-build-is-triggered"></a>Wskazuje projekt, aby utworzyć aplikację klienta, za każdym razem, kompilacja zostaje wyzwolona

1. W programie Visual Studio, przejdź do **projektu** > **właściwości** > **zdarzenia kompilacji**.

1. Na **wiersz polecenia zdarzenia sprzed kompilacji**, typ `npm --prefix ./client-app run build`.

#### <a name="configure-webpacks-output-module-names"></a>Konfigurowanie nazwy modułów dane wyjściowe webpack firmy

* Otwórz plik *./client-app/build/webpack.base.conf.js*i dodaj następujące właściwości dla właściwości danych wyjściowych:

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

1. Otwórz plik *./client-app/tsconfig.json* i Dodaj `noEmit:true` w opcjach kompilatora.

    To ustawienie pozwala uniknąć zaśmiecania projektu za każdym razem, gdy kompilujesz w programie Visual Studio.

1. Następnie należy utworzyć *vue.config.js* w pliku *./client-app/* i Dodaj następujący kod.

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

Wystąpił nieznany problem z vue — interfejs wiersza polecenia 3.0 może uniemożliwić Automatyzowanie procesu kompilacji. Za każdym razem, spróbuj odświeżyć folderu wwwroot, musisz uruchomić polecenie `npm run build` w folderze aplikacji klienckiej.

Alternatywnie można utworzyć projektu vue-cli 3.0 jako zdarzenie sprzed kompilacji za pomocą właściwości projektu programu ASP.NET. Kliknij prawym przyciskiem myszy projekt, wybierz polecenie **właściwości**i zawiera następujące polecenia w **kompilacji** na karcie **wiersz polecenia zdarzenia sprzed kompilacji** pola tekstowego.

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

- [Przewodnik Wprowadzenie dla VUE get](https://vuejs.org/v2/guide).
- [Projekt interfejsu wiersza polecenia VUE](https://github.com/vuejs/vue-cli).
- [Dokumentacja konfiguracji Webpack](https://webpack.js.org/configuration/).
