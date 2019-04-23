---
title: Pisanie kodu JavaScript w programie Visual Studio bez rozwiązania lub projektu
titleSuffix: ''
description: Program Visual Studio zapewnia obsługę tworzenia kodu bez zależności w pliku projektu lub pliku rozwiązania
ms.custom: seodec18
ms.date: 09/24/2018
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 3d6e3479fe27c5d88b58f096ab5405d75c6c98e3
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60102773"
---
# <a name="develop-javascript-and-typescript-code-in-visual-studio-without-solutions-or-projects"></a>Tworzenie kodu JavaScript i TypeScript w programie Visual Studio bez rozwiązań lub projektów

Począwszy od programu Visual Studio 2017 możesz [tworzenie kodu bez projektów ani rozwiązań](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md), która umożliwia otwieranie folderu kodu i od razu zacząć korzystać z pomocy technicznej Zaawansowany edytor, takie jak IntelliSense, wyszukiwanie, Refaktoryzacja, debugowania i innych. Poza tymi funkcjami Node.js Tools for Visual Studio dodaje obsługę tworzenia plików TypeScript, Zarządzanie pakietami npm i uruchamiania skryptów npm.

Aby rozpocząć, wybierz **pliku** > **Otwórz** > **folderu** na pasku narzędzi. Eksplorator rozwiązań zawiera wszystkie pliki w folderze, a następnie można otworzyć dowolne pliki, aby rozpocząć edycję. W tle programu Visual Studio indeksuje pliki, aby włączyć npm, kompilacji i funkcji debugowania.

> [!IMPORTANT]
> Wiele funkcji opisanych w tym artykule, w tym Integracja z menedżerem npm wymaga programu Visual Studio 2017 w wersji należy zachować 15,8 lub nowszej wersji.

## <a name="npm-integration"></a>Integracja z menedżerem npm

Możesz otworzyć zawiera *package.json* pliku, możesz kliknąć prawym przyciskiem myszy *package.json* do wyświetlenia menu kontekstowego (menu skrótów) specyficzne dla Menedżera npm.

![menu npm w oknie Eksploratora rozwiązań](../javascript/media/solution-explorer-npm-ctx.png)

W menu skrótów, można zarządzać pakiety instalowane przez pakiety npm w taki sam sposób, jak [Zarządzanie pakietami npm](npm-package-management.md) podczas korzystania z pliku projektu.

Ponadto menu umożliwia również uruchamiać skrypty zdefiniowane w `scripts` element *package.json*. Te skrypty będą używać wersji środowiska node.js jest dostępny na `PATH` zmiennej środowiskowej. Skrypty uruchamiane w nowym oknie. Jest to doskonały sposób na wykonanie kompilacji lub uruchamiania skryptów.

## <a name="build-and-debug"></a>Kompilowanie i debugowanie

### <a name="packagejson"></a>pliku Package.JSON
Jeśli *package.json* w folderze Określa `main` elementu **debugowania** polecenia będą dostępne w menu skrótów kliknij prawym przyciskiem myszy *package.json*.
Kliknięcie rozpocznie *node.exe* przy użyciu określonego skryptu jako argumentem.

### <a name="javascript-files"></a>Pliki JavaScript
Pliki JavaScript można debugować, kliknij plik prawym przyciskiem myszy i wybierając **debugowania** z menu skrótów. Spowoduje to uruchomienie *node.exe* razem z tym plikiem języka JavaScript jako argumentem.

### <a name="typescript-files-and-tsconfigjson"></a>Pliki TypeScript i plik tsconfig.json
W przypadku nie *tsconfig.json* istnieje w folderze, kliknąć prawym przyciskiem myszy plik TypeScript, aby wyświetlić polecenia menu skrótów, aby kompilować i debugować tego pliku. Korzystając z tych poleceń kompilacji lub debugowania za pomocą *tsc.exe* z użyciem opcji domyślnych. (Potrzebne do tworzenia pliku, zanim można było debugować).

> [!NOTE]
> Podczas kompilowania kodu TypeScript, korzystamy z najnowszej wersji, które są zainstalowane w `C:\Program Files (x86)\Microsoft SDKs\TypeScript`.

W przypadku *tsconfig.json* plików w folderze, możesz kliknąć prawym przyciskiem myszy plik TypeScript, aby wyświetlić polecenia menu, aby debugować ten plik TypeScript. Opcja jest wyświetlana tylko wtedy, gdy nie `outFile` określonych w *tsconfig.json*. Jeśli `outFile` jest określony, ten plik można debugować, klikając prawym przyciskiem myszy *tsconfig.json* i wybranie opcji jest poprawne. `tsconfig.json` Pliku oferuje również możliwość kompilacji pozwala użytkownikowi na określenie opcji kompilatora.

> [!NOTE]
> Więcej informacji można znaleźć o *tsconfig.json* w [tsconfig.json TypeScript Handbook strony](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html).

## <a name="unit-tests"></a>Testy jednostkowe
Aby umożliwić integrację testu jednostkowego w programie Visual Studio, określając katalog główny testu, w swojej *package.json*:

```json
{
    // ...
    "vsTest":{
        "testRoot": "./tests"
    }
    // ...
}
```

Narzędzie test runner wylicza lokalnie zainstalowane pakiety, aby określić, które struktury testów do użycia.
Jeśli żaden z obsługiwanych platform są rozpoznawane, narzędzia test runner domyślnie *ExportRunner*. Inne obsługiwane platformy to:
* Mocha ([mochajs.org](http://mochajs.org/))
* Jasmine ([Jasmine.github.io](https://jasmine.github.io/))
* Taśmy ([github.com/substack/tape](https://github.com/substack/tape))

Po otwarciu Eksploratora testów (wybierz **testu** > **Windows** > **Eksplorator testów**), Visual Studio wykrywa i wyświetla testów.

> [!NOTE]
> Narzędzie test runner wyliczą tylko pliki JavaScript, w katalogu głównym testu, jeśli aplikacja została napisana TypeScript, musisz utworzyć je w pierwszej kolejności.
