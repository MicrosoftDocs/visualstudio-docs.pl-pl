---
title: Pisanie kodu JavaScript w programie Visual Studio bez rozwiązania lub projektu
titleSuffix: ''
description: Program Visual Studio zapewnia obsługę tworzenia kodu bez zależności od pliku projektu lub pliku rozwiązania
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
ms.openlocfilehash: ae8b6fd52cd2469cf7562a199b952d388b463089
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "79549930"
---
# <a name="develop-javascript-and-typescript-code-in-visual-studio-without-solutions-or-projects"></a>Tworzenie kodu JavaScript i TypeScript w programie Visual Studio bez rozwiązań i projektów

Począwszy od programu Visual Studio 2017, można [tworzyć kod bez projektów lub rozwiązań](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md), który umożliwia otwarcie folderu kodu i natychmiast rozpocząć pracę z bogatym obsługi edytora, takich jak IntelliSense, wyszukiwanie, refaktoryzacji, debugowania i więcej. Oprócz tych funkcji node.js Tools for Visual Studio dodaje obsługę tworzenia plików TypeScript, zarządzania pakietami npm i uruchamiania skryptów npm.

Aby rozpocząć, wybierz pozycję **Folder** > **otwierania** > **pliku** z paska narzędzi. Eksplorator rozwiązań wyświetla wszystkie pliki w folderze i można otworzyć dowolny plik, aby rozpocząć edycję. W tle visual studio indeksuje pliki, aby włączyć npm, kompilacji i debugowania funkcji.

> [!IMPORTANT]
> Wiele funkcji opisanych w tym artykule, w tym integracji npm, wymagają visual studio 2017 w wersji 15.8 lub nowszych wersjach. Należy zainstalować obciążenie deweloperskie programu Visual Studio **Node.js.**

## <a name="npm-integration"></a>integracja npm

Jeśli otwarty folder zawiera plik *package.json,* możesz kliknąć prawym przyciskiem myszy *package.json,* aby wyświetlić menu kontekstowe (menu skrótów) specyficzne dla npm.

![Menu npm w Eksploratorze rozwiązań](../javascript/media/solution-explorer-npm-ctx.png)

W menu skrótów można zarządzać pakietami zainstalowanymi przez npm w taki sam sposób, w jaki [zarządzasz pakietami npm](npm-package-management.md) podczas korzystania z pliku projektu.

Ponadto menu umożliwia również uruchamianie skryptów zdefiniowanych w elemencie `scripts` w pliku *package.json*. Skrypty te będą używać wersji Node.js `PATH` dostępnej w zmiennej środowiskowej. Skrypty są uruchamiane w nowym oknie. Jest to świetny sposób na wykonanie kompilacji lub uruchamiania skryptów.

## <a name="build-and-debug"></a>Tworzenie i debugowanie

### <a name="packagejson"></a>package.json
Jeśli *package.json* w folderze `main` określa element, polecenie **Debugowanie** będzie dostępne w menu skrótów po kliknięciu prawym przyciskiem myszy *pliku package.json*.
Kliknięcie tego spowoduje uruchomienie *node.exe* z określonym skryptem jako jego argumentem.

### <a name="javascript-files"></a>Pliki JavaScript
Można debugować pliki JavaScript, klikając plik prawym przyciskiem myszy i wybierając **debug** z menu skrótów. Spowoduje to uruchomienie *pliku node.exe* z tym plikiem JavaScript jako argumentem.

### <a name="typescript-files-and-tsconfigjson"></a>Pliki TypeScript i tsconfig.json
Jeśli w folderze nie ma pliku *tsconfig.json,* można kliknąć prawym przyciskiem myszy plik TypeScript, aby wyświetlić polecenia menu skrótów służące do tworzenia i debugowania tego pliku. Korzystając z tych poleceń, należy tworzyć lub debugować przy użyciu *tsc.exe* z opcjami domyślnymi. (Przed debugowaniem należy utworzyć plik).

> [!NOTE]
> Podczas tworzenia kodu TypeScript używamy najnowszej `C:\Program Files (x86)\Microsoft SDKs\TypeScript`wersji zainstalowanej w pliku .

Jeśli w folderze znajduje się plik *tsconfig.json,* można kliknąć prawym przyciskiem myszy plik TypeScript, aby wyświetlić polecenie menu do debugowania tego pliku TypeScript. Opcja pojawia się tylko `outFile` wtedy, gdy nie ma określonego w *tsconfig.json*. Jeśli `outFile` określony jest, można debugować ten plik, klikając prawym przyciskiem myszy *tsconfig.json* i wybierając właściwą opcję. Plik `tsconfig.json` daje również opcję kompilacji, aby umożliwić określenie opcji kompilatora.

> [!NOTE]
> Więcej informacji na temat *tsconfig.json* można znaleźć na [stronie podręcznika tsconfig.json TypeScript](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html).

## <a name="unit-tests"></a>Testy jednostkowe
Integrację testu jednostkowego w programie Visual Studio można włączyć, określając katalog główny testu w pliku *package.json:*

```json
{
    // ...
    "vsTest":{
        "testRoot": "./tests"
    }
    // ...
}
```

Wynik testu wylicza lokalnie zainstalowane pakiety, aby określić, która struktura testów do użycia.
Jeśli żadna z obsługiwanych struktur nie zostanie rozpoznana, domyślnie test runner *na ExportRunner*. Inne obsługiwane struktury to:
* Mocha ([mochajs.org](https://mochajs.org/))
* Jaśmin ([Jasmine.github.io](https://jasmine.github.io/))
* Taśma[(github.com/substack/tape](https://github.com/substack/tape))
* Jest ([jestjs.io](https://jestjs.io/))

Po otwarciu Eksploratora testów (wybierz > **Eksploratora** **Test** > testów**systemu**Windows) program Visual Studio odnajduje i wyświetla testy.

> [!NOTE]
> Test runner będzie tylko wyliczyć pliki JavaScript w katalogu głównym testu, jeśli aplikacja jest napisana w typescript trzeba zbudować te pierwsze.
