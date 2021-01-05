---
title: Zarządzanie pakietami npm
description: Program Visual Studio ułatwia zarządzanie pakietami za pomocą Menedżera pakietów Node.js (npm)
ms.custom: seodec18
ms.date: 04/16/2020
ms.topic: how-to
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: d2c7ec425767e432105bfcec493599197e2fd5ec
ms.sourcegitcommit: 105e7b5a486262bc92939980383ceee068098a11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/30/2020
ms.locfileid: "97815688"
---
# <a name="manage-npm-packages-in-visual-studio"></a>Zarządzanie pakietami npm w programie Visual Studio

npm umożliwia instalowanie pakietów i zarządzanie nimi do użytku w aplikacjach Node.js. Program Visual Studio ułatwia współpracę z npm i wydawanie poleceń npm za pomocą interfejsu użytkownika lub bezpośrednio. Jeśli nie znasz npm i chcesz dowiedzieć się więcej, przejdź do [dokumentacji npm](https://docs.npmjs.com/).

Integracja programu Visual Studio z usługą npm różni się w zależności od typu projektu.
* [Node.js](#nodejs-projects)
* [ASP.NET Core](#aspnet-core-projects)
* [Otwórz folder (Node.js)](../javascript/develop-javascript-code-without-solutions-projects.md)

> [!Important]
> npm oczekuje folderu *node_modules* ipackage.jsw *elemencie* głównym projektu. Jeśli struktura folderów aplikacji jest inna, należy zmodyfikować strukturę folderów, jeśli chcesz zarządzać pakietami npm za pomocą programu Visual Studio.

## <a name="nodejs-projects"></a>Projekty Node.js

W przypadku projektów Node.js można wykonać następujące zadania:
* [Zainstaluj pakiety z Eksplorator rozwiązań](#npmInstallWindow)
* [Zarządzaj zainstalowanymi pakietami z Eksplorator rozwiązań](#solutionExplorer)
* [Użyj `.npm` polecenia w oknie Node.js Interactive](#interactive)

Te funkcje współpracują i synchronizują z systemem projektu oraz *package.jsna* pliku w projekcie.

### <a name="prerequisites"></a>Wymagania wstępne

PotrzebujeszNode.js obciążenie **programowaniem** i zainstalowanym środowiskiem uruchomieniowym Node.js, aby dodać obsługę npm do projektu. Aby uzyskać szczegółowe instrukcje, zobacz [Tworzenie projektu Node.js](../ide/quickstart-nodejs.md?toc=%252fvisualstudio%252fjavascript%252ftoc.json).

> [!NOTE]
> W przypadku istniejących projektów Node.js Użyj szablonu **z istniejącego Node.js kod** rozwiązania lub typu projektu [otwórz folder (Node.js)](../javascript/develop-javascript-code-without-solutions-projects.md) , aby włączyć npm w projekcie.

### <a name="install-packages-from-solution-explorer-nodejs"></a><a name="npmInstallWindow"></a> Zainstaluj pakiety z Eksplorator rozwiązań (Node.js)

W przypadku projektów Node.js Najprostszym sposobem instalowania pakietów npm jest użycie okna instalacji pakietu npm. Aby uzyskać dostęp do tego okna, kliknij prawym przyciskiem myszy węzeł **npm** w projekcie i wybierz polecenie **Instaluj nowe pakiety npm**.

:::image type="content" source="../javascript/media/solution-explorer-install-package.png" alt-text="Zainstaluj nowy pakiet npm z Eksploratora rozwiązań" border="true":::

W tym oknie można wyszukać pakiet, określić opcje i zainstalować.

![Zrzut ekranu przedstawiający okno dialogowe instalowanie nowych pakietów npm. Wybrano pakiet Azure 2.2.1 — wersja zapoznawcza, a szczegóły i opcje dla tego pakietu są wyświetlane.](../javascript/media/search-package.png)

* **Typ zależności** — wybierany między pakietami **Standard**, **Development** i **Optional** . Standard określa, że pakiet jest zależnością czasu wykonywania, podczas gdy programowanie określa, że pakiet jest wymagany tylko podczas tworzenia.
* **Dodaj do package.js** — zalecane. Ta konfigurowalna opcja jest przestarzała.
* **Wybrana wersja** — wybierz wersję pakietu do zainstalowania.
* **Inne argumenty npm** — Określ inne standardowe argumenty npm. Można na przykład wprowadzić wartość wersji `@~0.8` , na przykład w celu zainstalowania określonej wersji, która nie jest dostępna na liście wersje.

Postęp instalacji można zobaczyć w danych wyjściowych **npm** w oknie **danych wyjściowych** . Może to potrwać jakiś czas.

![npm dane wyjściowe](../javascript/media/npm-output.png)

> [!TIP]
> Możesz wyszukać pakiety z zakresem, oczekując na zapytanie wyszukiwania z interesującym zakresem, na przykład wpisz, `@types/mocha` Aby wyszukać pliki definicji TypeScript dla środowiska Mocha. Ponadto podczas instalowania definicji typów dla języka TypeScript można określić wersję języka TypeScript, dodając `@ts2.6` w polu argument npm.

### <a name="manage-installed-packages-in-solution-explorer-nodejs"></a><a name="solutionExplorer"></a>Zarządzaj zainstalowanymi pakietami w Eksplorator rozwiązań (Node.js)

pakiety npm są wyświetlane w Eksplorator rozwiązań. Wpisy w węźle **npm** powodują naśladowanie zależności w *package.js* pliku.

![Zrzut ekranu węzła npm w Eksplorator rozwiązań pokazujący stan instalacji pakietów npm.](../javascript/media/solution-explorer-status.png)

### <a name="package-status"></a>Stan pakietu

* ![Zainstalowany pakiet](../javascript/media/installed-npm.png) -Zainstalowane i wymienione w package.jsna
* ![Niezależny pakiet ](../javascript/media/extraneous-npm.png) instalowany przez program, ale nie jest jawnie wymieniony w package.jsna
* ![Brak pakietu](../javascript/media/missing-npm.png) — Nie zainstalowane, ale wymienione w package.jsna

::: moniker range=">=vs-2019"
Kliknij prawym przyciskiem myszy węzeł **npm** , aby wykonać jedną z następujących czynności:

* **Instalowanie nowych pakietów npm** Otwiera interfejs użytkownika, aby zainstalować nowe pakiety.
* **Zainstaluj pakiety npm** Uruchamia polecenie instalacji npm, aby zainstalować wszystkie pakiety wymienione w *package.jsna*. (Działa `npm install` ).
* **Aktualizowanie pakietów npm** Aktualizuje pakiety do najnowszych wersji, zgodnie z zakresem wersji semantycznej (SemVer) określonym w *package.json*. (Działa `npm update --save` .). Zakresy SemVer są zwykle określane przy użyciu "~" lub "^". Aby uzyskać więcej informacji, [package.jsw konfiguracji](../javascript/configure-packages-with-package-json.md).

Kliknij prawym przyciskiem myszy węzeł pakietu, aby wykonać jedną z następujących czynności:

* **Zainstaluj pakiety npm** Uruchamia polecenie instalacji npm w celu zainstalowania wersji pakietu wymienionej w *package.js*. (Działa `npm install` ).
* **Aktualizowanie pakietów npm** Aktualizuje pakiet do najnowszej wersji, zgodnie z zakresem SemVer określonym w *package.js*. (Uruchom `npm update --save` ). Zakresy SemVer są zwykle określane przy użyciu "~" lub "^".
* **Odinstaluj pakiety npm** Odinstalowuje pakiet i usuwa go z *package.json* (działa `npm uninstall --save` ).
::: moniker-end
::: moniker range="vs-2017"
Kliknij prawym przyciskiem myszy węzeł pakietu lub węzeł **npm** , aby wykonać jedną z następujących czynności:
* **Zainstaluj brakujące pakiety** , które są wymienione w *package.jsna*
* **Aktualizowanie pakietów npm** do najnowszej wersji
* **Odinstaluj pakiet** i usuń z *package.jsna*
::: moniker-end

>[!NOTE]
> Aby uzyskać pomoc w rozwiązywaniu problemów z pakietami npm, zobacz [Rozwiązywanie problemów](#troubleshooting-npm-packages).

### <a name="use-the-npm-command-in-the-nodejs-interactive-window-nodejs"></a><a name="interactive"></a>Użyj polecenia. npm w oknie interaktywnym Node.js (Node.js)

Możesz również użyć `.npm` polecenia w oknie Node.js Interactive, aby wykonać polecenia npm. Aby otworzyć okno, kliknij prawym przyciskiem myszy projekt w Eksplorator rozwiązań i wybierz polecenie **otwórz Node.js okno interaktywne**.

W oknie można użyć poleceń, takich jak następujące, aby zainstalować pakiet:

`.npm install azure@4.2.3`

 > [!Tip]
 > Domyślnie npm będzie wykonywany w katalogu głównym projektu. Jeśli masz wiele projektów w rozwiązaniu, określ nazwę lub ścieżkę projektu w nawiasach.
 > `.npm [MyProjectNameOrPath] install azure@4.2.3`

 > [!Tip]
 > Jeśli projekt nie zawiera package.jsw pliku, użyj, `.npm init -y` Aby utworzyć nowy package.jsdla pliku z wpisami domyślnymi.

 ## <a name="aspnet-core-projects"></a>Projekty ASP.NET Core

W przypadku projektów takich jak projekty ASP.NET Core można zintegrować obsługę npm w projekcie i używać npm do instalowania pakietów.
* [Dodawanie obsługi npm do projektu](#npmAdd)
* [Zainstaluj pakiety przy użyciu package.jsna](#npmInstallPackage)

>[!NOTE]
> W przypadku projektów ASP.NET Core można także użyć [Menedżera bibliotek](/aspnet/core/client-side/libman/?view=aspnetcore-3.1&preserve-view=true) lub przędzy zamiast npm do instalowania plików JavaScript i CSS po stronie klienta.

### <a name="add-npm-support-to-a-project-aspnet-core"></a><a name="npmAdd"></a> Dodawanie obsługi npm do projektu (ASP.NET Core)

Jeśli projekt nie zawiera jeszcze *package.jsw* pliku, można dodać jeden, aby włączyć obsługę npm przez dodanie *package.js* do pliku do projektu.

1. Jeśli nie masz zainstalowanego Node.js, zalecamy zainstalowanie wersji LTS z witryny internetowej [Node.js](https://nodejs.org/en/download/) w celu uzyskania najlepszej zgodności z zewnętrznymi platformami i bibliotekami.

   npm wymaga Node.js.

1. Aby dodać *package.js* do pliku, kliknij prawym przyciskiem myszy projekt w Eksplorator rozwiązań i wybierz polecenie **Dodaj**  >  **nowy element**. Wybierz **plik konfiguracji npm**, użyj nazwy domyślnej, a następnie kliknij przycisk **Dodaj**.

   ![Dodawanie package.jsdo projektu](../javascript/media/npm-add-package-json.png)

   Jeśli nie widzisz na liście pliku konfiguracji npm, narzędzia programistyczne nie są zainstalowane Node.js. Za pomocą Instalator programu Visual Studio można dodać **Node.js obciążenie programowaniem** . Następnie Powtórz poprzedni krok.

1. Uwzględnij co najmniej jeden pakiet npm w `dependencies` `devDependencies` sekcji lub *package.jsna*. Można na przykład dodać do pliku następujący plik:

   ```json
   "devDependencies": {
      "gulp": "4.0.2",
      "@types/jquery": "3.3.33"
   }
   ```

Po zapisaniu pliku program Visual Studio dodaje pakiet w węźle **zależności/npm** w Eksplorator rozwiązań. Jeśli węzeł nie jest widoczny, kliknij prawym przyciskiem myszy pozycję **package.jsna** i wybierz polecenie **Przywróć pakiety**.

>[!NOTE]
> W niektórych scenariuszach Eksplorator rozwiązań mogą nie wyświetlać poprawnych Stanów zainstalowanych pakietów npm. Aby uzyskać więcej informacji, zobacz temat [Rozwiązywanie problemów](#troubleshooting-npm-packages).

### <a name="install-packages-using-packagejson-aspnet-core"></a><a name="npmInstallPackage"></a>Instalowanie pakietów przy użyciu package.jsna (ASP.NET Core)

W przypadku projektów z dołączoną npm można skonfigurować pakiety npm przy użyciu programu `package.json` . Kliknij prawym przyciskiem myszy węzeł npm w Eksplorator rozwiązań i wybierz polecenie **otwórz package.jsna**.

![Zrzut ekranu przedstawiający Eksplorator rozwiązań z wybranym węzłem npm. Menu kontekstowe kliknij prawym przyciskiem myszy jest otwarte i otwarte package.jsna jest zaznaczone.](../javascript/media/npm-add-package.png)

Funkcja IntelliSense w *package.js* jest pomocna w przypadku wybrania konkretnej wersji pakietu npm.

:::image type="content" source="../javascript/media/npm-add-package-intellisense.png" alt-text="Wybierz wersję pakietu npm" border="true":::

Po zapisaniu pliku program Visual Studio dodaje pakiet w węźle **zależności/npm** w Eksplorator rozwiązań. Jeśli węzeł nie jest widoczny, kliknij prawym przyciskiem myszy pozycję **package.jsna** i wybierz polecenie **Przywróć pakiety**.

Zainstalowanie pakietu może potrwać kilka minut. Sprawdź postęp instalacji pakietu, przełączając się do **npm** danych wyjściowych w oknie **danych wyjściowych** .

![npm dane wyjściowe](../javascript/media/npm-output.png)

## <a name="troubleshooting-npm-packages"></a>Rozwiązywanie problemów z pakietami npm

* npm wymaga Node.js Jeśli nie masz Node.js zainstalowanych, zalecamy zainstalowanie wersji LTS z witryny internetowej [Node.js](https://nodejs.org/en/download/) w celu uzyskania najlepszej zgodności z zewnętrznymi strukturami i bibliotekami.

* W przypadku projektów Node.js należy mieć zainstalowaną **Node.js obciążenie programowaniem** na potrzeby obsługi npm.

* W niektórych scenariuszach Eksplorator rozwiązań mogą nie wyświetlać poprawnego stanu zainstalowanych pakietów npm z powodu znanego [tutaj](https://github.com/aspnet/Tooling/issues/479)problemu. Na przykład pakiet może być wyświetlany jako niezainstalowany podczas instalacji. W większości przypadków można zaktualizować Eksplorator rozwiązań przez usunięcie *package.jsna*, ponowne uruchomienie programu Visual Studio i ponowne dodanie *package.js* do pliku zgodnie z opisem we wcześniejszej części tego artykułu. Lub, podczas instalowania pakietów, można użyć okna danych wyjściowych npm do sprawdzenia stanu instalacji.

* Jeśli podczas kompilowania aplikacji lub transpiling kodu TypeScript wystąpią jakieś błędy, sprawdź, czy nie ma niezgodności pakietów npm jako potencjalne źródło błędów. Aby ułatwić identyfikację błędów, Sprawdź okno danych wyjściowych npm podczas instalowania pakietów, jak opisano wcześniej w tym artykule. Na przykład jeśli co najmniej jedna wersja pakietu npm jest przestarzała i spowoduje błąd, może być konieczne zainstalowanie nowszej wersji w celu rozwiązania błędów. Aby uzyskać informacje na temat korzystania z *package.jsw* celu kontrolowania wersji pakietu npm, zobacz [package.json Configuration](../javascript/configure-packages-with-package-json.md).
