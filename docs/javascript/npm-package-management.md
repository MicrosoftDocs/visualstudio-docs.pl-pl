---
title: Zarządzanie pakietami npm
description: Program Visual Studio pomaga zarządzać pakietami przy użyciu Menedżera pakietów Node.js (npm)
ms.custom: seodec18
ms.date: 04/16/2020
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 0b4b699c01522878d83e59aadb2c6a54e9d7517f
ms.sourcegitcommit: a7f781d5a089e6aab6b073a07f3d4d2967af8aa6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81760167"
---
# <a name="manage-npm-packages-in-visual-studio"></a>Zarządzanie pakietami npm w programie Visual Studio

npm umożliwia instalowanie i zarządzanie pakietami do użytku w aplikacjach Node.js. Visual Studio ułatwia interakcję z npm i wydawania poleceń npm za pośrednictwem interfejsu użytkownika lub bezpośrednio. Jeśli nie znasz npm i chcesz dowiedzieć się więcej, przejdź do [dokumentacji npm](https://docs.npmjs.com/).

Integracja programu Visual Studio z npm różni się w zależności od typu projektu.
* [Node.js](#nodejs-projects)
* [ASP.NET Core](#aspnet-core-projects)
* [Otwórz folder (Node.js)](../javascript/develop-javascript-code-without-solutions-projects.md)

> [!Important]
> npm oczekuje *node_modules* folderu i *package.json* w katalogu głównym projektu. Jeśli struktura folderów aplikacji jest inna, należy zmodyfikować strukturę folderów, jeśli chcesz zarządzać pakietami npm przy użyciu programu Visual Studio.

## <a name="nodejs-projects"></a>Projekty node.js

W przypadku projektów node.js można wykonywać następujące zadania:
* [Instalowanie pakietów z Eksploratora rozwiązań](#npmInstallWindow)
* [Zarządzanie zainstalowanymi pakietami z Eksploratora rozwiązań](#solutionExplorer)
* [Użyj `.npm` polecenia w oknie interaktywnym Node.js](#interactive)

Te funkcje współpracują ze sobą i synchronizują się z systemem projektu i plikiem *package.json* w projekcie.

### <a name="prerequisites"></a>Wymagania wstępne

Aby dodać obsługę npm do projektu, potrzebne jest obciążenie **deweloperne node.js** i środowisko uruchomieniowe Node.js. Aby uzyskać szczegółowe kroki, zobacz [Tworzenie projektu node.js](/visualstudio/ide/quickstart-nodejs?toc=/visualstudio/javascript/toc.json).

> [!NOTE]
> W przypadku istniejących projektów node.js użyj szablonu rozwiązania **kodu z istniejącego pliku Node.js** lub typu projektu [Otwórz folder (Node.js),](../javascript/develop-javascript-code-without-solutions-projects.md) aby włączyć npm w projekcie.

### <a name="install-packages-from-solution-explorer-nodejs"></a><a name="npmInstallWindow"></a>Instalowanie pakietów z Eksploratora rozwiązań (node.js)

W przypadku projektów Node.js najprostszym sposobem instalowania pakietów npm jest okno instalacji pakietu npm. Aby uzyskać dostęp do tego okna, kliknij prawym przyciskiem myszy węzeł **npm** w projekcie i wybierz polecenie **Zainstaluj nowe pakiety npm**.

:::image type="content" source="../javascript/media/solution-explorer-install-package.png" alt-text="Zainstaluj nowy pakiet npm z Eksploratora rozwiązań" border="true":::

W tym oknie można wyszukać pakiet, określić opcje i zainstalować.

![Szukaj pakietu npm](../javascript/media/search-package.png)

* **Typ zależności** — wybierane między pakietami **Standard,** **Development**i **Optional.** Standard określa, że pakiet jest zależnością środowiska uruchomieniowego, podczas gdy programowanie określa, że pakiet jest wymagany tylko podczas tworzenia.
* **Dodaj do package.json** - Zalecane. Ta opcja konfigurowalna jest przestarzała.
* **Wybrana wersja** — wybierz wersję pakietu, który chcesz zainstalować.
* **Inne argumenty npm** — określanie innych standardowych argumentów npm. Na przykład można wprowadzić wartość wersji, taką jak `@~0.8` zainstalowanie określonej wersji, która nie jest dostępna na liście wersji.

Postęp instalacji można zobaczyć w danych wyjściowych **npm** w oknie **Dane wyjściowe.** Może to potrwać jakiś czas.

![npm wyjście](../javascript/media/npm-output.png)

> [!TIP]
> Można wyszukiwać pakiety o określonym zakresie, dołączając zapytanie wyszukiwania do zakresu, `@types/mocha` który Cię interesuje, na przykład wpisz, aby wyszukać pliki definicji TypeScript dla mokki. Ponadto podczas instalowania definicji typów dla kodu TypeScript można określić docelową wersję kodu TypeScript, dodając `@ts2.6` je w polu argumentu npm.

### <a name="manage-installed-packages-in-solution-explorer-nodejs"></a><a name="solutionExplorer"></a>Zarządzanie zainstalowanymi pakietami w Eksploratorze rozwiązań (node.js)

pakiety npm są wyświetlane w Eksploratorze rozwiązań. Wpisy w węźle **npm** naśladują zależności w pliku *package.json.*

![Szukaj pakietu npm](../javascript/media/solution-explorer-status.png)

### <a name="package-status"></a>Stan pakietu

* ![Zainstalowany pakiet](../javascript/media/installed-npm.png) - Zainstalowany i wymieniony w package.json
* ![Pakiet](../javascript/media/extraneous-npm.png) obce - Zainstalowany, ale nie jawnie wymienione w package.json
* ![Brakujący pakiet](../javascript/media/missing-npm.png) - Nie zainstalowany, ale wymienione w package.json

::: moniker range=">=vs-2019"
Kliknij prawym przyciskiem myszy węzeł **npm,** aby podjąć jedną z następujących czynności:

* **Instalowanie nowych pakietów npm** Otwiera interfejs użytkownika, aby zainstalować nowe pakiety.
* **Instalowanie pakietów npm** Uruchamia polecenie instalacji npm, aby zainstalować wszystkie pakiety wymienione w *pliku package.json*. (Działa.) `npm install`
* **Aktualizowanie pakietów npm** Aktualizuje pakiety do najnowszych wersji, zgodnie z zakresem semver określonym w *package.json*. (Działa `npm update --save`.). Zakresy semver są zazwyczaj określane za pomocą "~" lub "^". Aby uzyskać więcej informacji, [konfiguracja package.json](../javascript/configure-packages-with-package-json.md).

Kliknij prawym przyciskiem myszy węzeł pakietu, aby podjąć jedną z następujących akcji:

* **Instalowanie pakietów npm** Uruchamia polecenie instalacji npm w celu zainstalowania wersji pakietu wymienionej w *pliku package.json*. (Działa.) `npm install`
* **Aktualizacja pakietów npm** Aktualizuje pakiet do najnowszej wersji, zgodnie z zakresem semver określonym w *package.json*. (Uruchom.) `npm update --save` Zakresy semver są zazwyczaj określane za pomocą "~" lub "^".
* **Odinstalowywanie pakietów npm** Odinstalowuje pakiet i usuwa go z *package.json* (uruchamia `npm uninstall --save`.)
::: moniker-end
::: moniker range="vs-2017"
Kliknij prawym przyciskiem myszy węzeł pakietu lub węzeł **npm,** aby podjąć jedną z następujących akcji:
* **Instalowanie brakujących pakietów** wymienionych w *pliku package.json*
* **Aktualizacja pakietów npm** do najnowszej wersji
* **Odinstalowywanie pakietu** i usuwanie z *pliku package.json*
::: moniker-end

>[!NOTE]
> Aby uzyskać pomoc dotyczącą rozwiązywania problemów z pakietami npm, zobacz [Rozwiązywanie problemów](#troubleshooting-npm-packages).

### <a name="use-the-npm-command-in-the-nodejs-interactive-window-nodejs"></a><a name="interactive"></a>Użyj polecenia .npm w oknie interaktywnym Node.js (node.js)

Można również użyć `.npm` polecenia w oknie interaktywnym Node.js do wykonywania poleceń npm. Aby otworzyć okno, kliknij prawym przyciskiem myszy projekt w Eksploratorze rozwiązań i wybierz polecenie **Otwórz okno interaktywne Node.js**.

W oknie można użyć poleceń, takich jak następujące, aby zainstalować pakiet:

`.npm install azure@4.2.3`

 > [!Tip]
 > Domyślnie npm będzie wykonywany w katalogu domowym projektu. Jeśli masz wiele projektów w rozwiązaniu określ nazwę lub ścieżkę projektu w nawiasach.
 > `.npm [MyProjectNameOrPath] install azure@4.2.3`

 > [!Tip]
 > Jeśli projekt nie zawiera pliku package.json, `.npm init -y` użyj do utworzenia nowego pliku package.json z wpisami domyślnymi.

 ## <a name="aspnet-core-projects"></a>ASP.NET Podstawowe projekty

W przypadku projektów takich jak ASP.NET Core można zintegrować obsługę npm w projekcie i użyć npm do zainstalowania pakietów.
* [Dodawanie pomocy technicznej npm do projektu](#npmAdd)
* [Instalowanie pakietów przy użyciu pliku package.json](#npmInstallPackage)

>[!NOTE]
> W przypadku projektów ASP.NET Core można również użyć [Menedżera biblioteki](https://docs.microsoft.com/aspnet/core/client-side/libman/?view=aspnetcore-3.1) lub przędzy zamiast npm, aby zainstalować pliki JavaScript i CSS po stronie klienta.

### <a name="add-npm-support-to-a-project-aspnet-core"></a><a name="npmAdd"></a>Dodawanie obsługi npm do projektu (ASP.NET Core)

Jeśli projekt nie zawiera jeszcze pliku *package.json,* można dodać jeden, aby włączyć obsługę npm, dodając plik *package.json* do projektu.

1. Jeśli nie masz zainstalowanego pliku Node.js, zalecamy zainstalowanie wersji LTS z witryny [node.js](https://nodejs.org/en/download/) w celu zapewnienia najlepszej zgodności z zewnętrznymi strukturami i bibliotekami.

   npm wymaga node.js.

1. Aby dodać plik *package.json,* kliknij prawym przyciskiem myszy projekt w Eksploratorze rozwiązań i wybierz polecenie **Dodaj** > **nowy element**. Wybierz **plik konfiguracji npm**, użyj nazwy domyślnej i kliknij przycisk **Dodaj**.

   ![Dodawanie pliku package.json do projektu](../javascript/media/npm-add-package-json.png)

   Jeśli nie widzisz na liście pliku konfiguracji npm, narzędzia programistyczne Node.js nie są zainstalowane. Instalatora programu Visual Studio można użyć, aby dodać obciążenie **deweloperskie Node.js.** Następnie powtórz poprzedni krok.

1. Uwzględnij jeden lub więcej `dependencies` pakietów npm w sekcji `devDependencies` *package.json*. Na przykład można dodać do pliku następujące elementy:

   ```json
   "devDependencies": {
      "gulp": "4.0.2",
      "@types/jquery": "3.3.33"
   }
   ```

Po zapisaniu pliku program Visual Studio dodaje pakiet w węźle **Zależności / npm** w Eksploratorze rozwiązań. Jeśli nie widzisz węzła, kliknij prawym przyciskiem myszy **package.json** i wybierz polecenie **Przywróć pakiety**.

>[!NOTE]
> W niektórych scenariuszach Eksplorator rozwiązań może nie wykazywać prawidłowego stanu dla zainstalowanych pakietów npm. Aby uzyskać więcej informacji, zobacz temat [Rozwiązywanie problemów](#troubleshooting-npm-packages).

### <a name="install-packages-using-packagejson-aspnet-core"></a><a name="npmInstallPackage"></a>Instalowanie pakietów przy użyciu pliku package.json (ASP.NET Core)

W przypadku projektów z dołączonymi npm można `package.json`skonfigurować pakiety npm za pomocą . Kliknij prawym przyciskiem myszy węzeł npm w Eksploratorze rozwiązań i wybierz polecenie **Otwórz package.json**.

![Szukaj pakietu npm](../javascript/media/npm-add-package.png)

IntelliSense w *package.json* pomaga wybrać konkretną wersję pakietu npm.

:::image type="content" source="../javascript/media/npm-add-package-intellisense.png" alt-text="Wybierz wersję pakietu npm" border="true":::

Po zapisaniu pliku program Visual Studio dodaje pakiet w węźle **Zależności / npm** w Eksploratorze rozwiązań. Jeśli nie widzisz węzła, kliknij prawym przyciskiem myszy **package.json** i wybierz polecenie **Przywróć pakiety**.

Zainstalowanie pakietu może potrwać kilka minut. Sprawdź postęp instalacji pakietu, przełączając się na dane **wyjściowe npm** w oknie **Dane wyjściowe.**

![npm wyjście](../javascript/media/npm-output.png)

## <a name="troubleshooting-npm-packages"></a>Rozwiązywanie problemów z pakietami npm

* npm wymaga Node.js Jeśli nie masz zainstalowanego node.js, zalecamy zainstalowanie wersji LTS z witryny [node.js](https://nodejs.org/en/download/) w celu uzyskania najlepszej zgodności z zewnętrznymi strukturami i bibliotekami.

* W przypadku projektów node.js należy zainstalować obciążenie **deweloperskie Node.js** dla obsługi npm.

* W niektórych scenariuszach Eksplorator rozwiązań może nie wykazywać prawidłowego stanu zainstalowanych pakietów npm z powodu znanego problemu opisanego [w tym miejscu.](https://github.com/aspnet/Tooling/issues/479) Na przykład pakiet może pojawić się jako nie zainstalowany po zainstalowaniu. W większości przypadków można zaktualizować Eksploratora rozwiązań, usuwając *plik package.json*, ponowne uruchomienie programu Visual Studio i ponowne dodanie pliku *package.json* zgodnie z opisem we wcześniejszej części tego artykułu. Lub podczas instalowania pakietów można użyć okna npm Output, aby zweryfikować stan instalacji.

* Jeśli podczas tworzenia aplikacji lub transpilowania kodu TypeScript są widoczne błędy, sprawdź, czy nie ma niezgodności pakietu npm jako potencjalnego źródła błędów. Aby ułatwić identyfikację błędów, sprawdź okno dane wyjściowe npm podczas instalowania pakietów, zgodnie z opisem opisanym wcześniej w tym artykule. Na przykład jeśli jedna lub więcej wersji pakietu npm zostało przestarzałych i powoduje błąd, może być konieczne zainstalowanie nowszej wersji w celu naprawienia błędów. Aby uzyskać informacje na temat *używania pliku package.json* do kontrolowania wersji pakietu npm, zobacz [konfigurację package.json](../javascript/configure-packages-with-package-json.md).

