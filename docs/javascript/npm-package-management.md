---
title: Zarządzanie pakietami npm
description: Program Visual Studio pomaga zarządzać pakietami przy użyciu Menedżera pakietów Node.js (npm)
ms.custom: seodec18
ms.date: 03/12/2020
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: dba657d30eedef26337c708e7ede6c5ab85ed4cc
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "79549954"
---
# <a name="manage-npm-packages-in-visual-studio"></a>Zarządzanie pakietami npm w programie Visual Studio

npm umożliwia instalowanie i zarządzanie pakietami do użytku w aplikacjach Node.js. Visual Studio ułatwia interakcję z npm i wydawania poleceń npm za pośrednictwem interfejsu użytkownika lub bezpośrednio. Jeśli nie znasz npm i chcesz dowiedzieć się więcej, przejdź do [dokumentacji npm](https://docs.npmjs.com/).

Integracja programu Visual Studio z npm różni się w zależności od typu projektu.
* [Node.js](#nodejs-projects)
* [ASP.NET Core](#aspnet-core-projects)
* [Otwórz folder (Node.js)](../javascript/develop-javascript-code-without-solutions-projects.md)

> [!Important]
> npm oczekuje *node_modules* folderu i *package.json* w katalogu głównym projektu. Jeśli struktura folderów aplikacji jest inna, należy zmodyfikować strukturę folderów, jeśli chcesz zarządzać pakietami npm przy użyciu programu Visual Studio.

> [!NOTE]
> W przypadku istniejących projektów Node.js użyj szablonu rozwiązania **kodu Istniejący node.js,** aby włączyć npm w projekcie.

## <a name="nodejs-projects"></a>Projekty node.js

W przypadku projektów node.js należy użyć jednej z następujących metod:
* [Instalowanie pakietów z Eksploratora rozwiązań](#npmInstallWindow)
* [Zarządzanie zainstalowanymi pakietami z Eksploratora rozwiązań](#solutionExplorer)
* [Użyj `.npm` polecenia w oknie interaktywnym Node.js](#interactive)

Te funkcje współpracują ze sobą i synchronizują się z systemem projektu i plikiem *package.json* w projekcie.

### <a name="install-packages-from-solution-explorer-nodejs"></a><a name="npmInstallWindow"></a>Instalowanie pakietów z Eksploratora rozwiązań (node.js)

W przypadku projektów Node.js najprostszym sposobem instalowania pakietów npm jest okno instalacji pakietu npm. Aby uzyskać dostęp do tego okna, kliknij prawym przyciskiem myszy węzeł **npm** w projekcie i wybierz polecenie **Zainstaluj nowe pakiety npm**.

![Zainstaluj nowy pakiet npm z Eksploratora rozwiązań](../javascript/media/solution-explorer-install-package.png)

W tym oknie można wyszukać pakiet, określić opcje i zainstalować.

![Szukaj pakietu npm](../javascript/media/search-package.png)

* **Typ zależności** — wybierane między pakietami **Standard,** **Development**i **Optional.** Standard określa, że pakiet jest zależnością środowiska uruchomieniowego, podczas gdy programowanie określa, że pakiet jest wymagany tylko podczas tworzenia.
* **Dodaj do package.json** — ta opcja jest przestarzała
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

Kliknij prawym przyciskiem myszy węzeł pakietu lub węzeł **npm,** aby podjąć jedną z następujących akcji:
* **Instalowanie brakujących pakietów** wymienionych w *pliku package.json*
* **Aktualizowanie pakietów** do najnowszej wersji
* **Odinstalowywanie pakietu** i usuwanie z *pliku package.json*

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

Jeśli projekt nie zawiera jeszcze pliku *package.json,* można dodać jedną włącz obsługę npm, dodając plik package.json do projektu.

1. Aby dodać plik, kliknij prawym przyciskiem myszy projekt w Eksploratorze rozwiązań i wybierz polecenie **Dodaj** > **nowy element**. Wybierz **plik konfiguracji npm**, użyj nazwy domyślnej i kliknij przycisk **Dodaj**.

   ![Dodawanie pliku package.json do projektu](../javascript/media/npm-add-package-json.png)

1. Uwzględnij jeden lub więcej `dependencies` pakietów npm w sekcji `devDependencies` *package.json*. Na przykład można dodać do pliku następujące elementy:

   ```json
   "devDependencies": {
      "gulp": "4.0.2",
      "@types/jquery": "3.3.33"
   }
   ```

Po zapisaniu pliku program Visual Studio dodaje pakiet w węźle **Zależności / npm** w Eksploratorze rozwiązań. Jeśli nie widzisz węzła, kliknij prawym przyciskiem myszy **package.json** i wybierz polecenie **Przywróć pakiety**.

>[!NOTE]
> W niektórych scenariuszach Eksplorator rozwiązań może wskazywać, że pakiet npm jest niezsynchronizowany z *package.json* z powodu znanego problemu opisanego [tutaj](https://github.com/aspnet/Tooling/issues/479). Na przykład pakiet może pojawić się jako nie zainstalowany po zainstalowaniu. W większości przypadków można zaktualizować Eksploratora rozwiązań, usuwając *plik package.json*, ponowne uruchomienie programu Visual Studio i ponowne dodanie pliku *package.json* zgodnie z opisem we wcześniejszej części tego artykułu.

### <a name="install-packages-using-packagejson-aspnet-core"></a><a name="npmInstallPackage"></a>Instalowanie pakietów przy użyciu pliku package.json (ASP.NET Core)

W przypadku projektów z dołączonymi npm można `package.json`skonfigurować pakiety npm za pomocą . Kliknij prawym przyciskiem myszy węzeł npm w Eksploratorze rozwiązań i wybierz polecenie **Otwórz package.json**.

![Szukaj pakietu npm](../javascript/media/npm-add-package.png)

IntelliSense w *package.json* pomaga wybrać konkretną wersję pakietu npm.

![Szukaj pakietu npm](../javascript/media/npm-add-package-intellisense.png)

Po zapisaniu pliku program Visual Studio dodaje pakiet w węźle **Zależności / npm** w Eksploratorze rozwiązań. Jeśli nie widzisz węzła, kliknij prawym przyciskiem myszy **package.json** i wybierz polecenie **Przywróć pakiety**.

Zainstalowanie pakietu może potrwać kilka minut. Sprawdź postęp instalacji pakietu, przełączając się na dane **wyjściowe npm** w oknie **Dane wyjściowe.**

![npm wyjście](../javascript/media/npm-output.png)

