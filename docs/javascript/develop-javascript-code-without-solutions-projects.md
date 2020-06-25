---
title: Pisanie kodu JavaScript w programie Visual Studio bez rozwiązania lub projektu
titleSuffix: ''
description: Program Visual Studio zapewnia obsługę tworzenia kodu bez zależności w pliku projektu lub pliku rozwiązania
ms.custom: seodec18
ms.date: 09/24/2018
ms.topic: how-to
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 187ca5ea0d0232e0ca8b99165e77ee265b81e801
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85285091"
---
# <a name="develop-javascript-and-typescript-code-in-visual-studio-without-solutions-or-projects"></a>Programowanie kodu JavaScript i TypeScript w programie Visual Studio bez rozwiązań i projektów

Począwszy od programu Visual Studio 2017, można [opracowywać kod bez projektów i rozwiązań](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md), dzięki czemu można otwierać foldery kodu i od razu zacząć pracę z zaawansowaną obsługą edytora, taką jak IntelliSense, wyszukiwanie, Refaktoryzacja, debugowanie i nie tylko. Oprócz tych funkcji narzędzie Node.js Tools for Visual Studio dodaje obsługę tworzenia plików TypeScript, zarządzania pakietami npm oraz uruchamiania skryptów npm.

Aby rozpocząć, wybierz pozycję **plik**  >  **Otwórz**  >  **folder** na pasku narzędzi. Eksplorator rozwiązań wyświetla wszystkie pliki w folderze, a wszystkie pliki można otworzyć, aby rozpocząć edycję. W tle program Visual Studio indeksuje pliki w celu włączenia funkcji npm, Build i Debug.

> [!IMPORTANT]
> Wiele funkcji opisanych w tym artykule, łącznie z integracją npm, wymaga programu Visual Studio 2017 w wersji 15,8 lub nowszej. Należy zainstalować program Visual Studio **Node.js obciążenie programowaniem** .

## <a name="npm-integration"></a>Integracja npm

Jeśli otwarty folder zawiera *package.jsw* pliku, możesz kliknąć prawym przyciskiem myszy pozycję *package.json* , aby wyświetlić menu kontekstowe (menu skrótów) specyficzne dla npm.

![menu npm w Eksplorator rozwiązań](../javascript/media/solution-explorer-npm-ctx.png)

W menu skrótów można zarządzać pakietami instalowanymi przez npm w taki sam sposób, jak [w przypadku korzystania](npm-package-management.md) z pliku projektu.

Ponadto menu pozwala także uruchamiać skrypty zdefiniowane w `scripts` elemencie w *package.json*. Te skrypty będą używać wersji Node.js dostępnej w `PATH` zmiennej środowiskowej. Skrypty są uruchamiane w nowym oknie. To świetny sposób na wykonanie kompilacji lub uruchomienie skryptów.

## <a name="build-and-debug"></a>Kompiluj i Debuguj

### <a name="packagejson"></a>package.json
Jeśli *package.js* w folderze określa `main` element, polecenie **Debug** będzie dostępne w menu skrótów kliknij prawym przyciskiem myszy dla *package.jsna*.
Kliknięcie tej opcji spowoduje rozpoczęcie *node.exe* z określonym skryptem jako argumentem.

### <a name="javascript-files"></a>Pliki JavaScript
Aby debugować pliki JavaScript, kliknij prawym przyciskiem myszy plik i wybierz polecenie **Debuguj** z menu skrótów. Spowoduje to uruchomienie *node.exe* z tym plikiem JavaScript jako argumentem.

### <a name="typescript-files-and-tsconfigjson"></a>Pliki TypeScript i tsconfig.jsna
Jeśli w folderze nie ma *tsconfig.js* , możesz kliknąć prawym przyciskiem myszy plik TypeScript, aby wyświetlić polecenia menu skrótów umożliwiające skompilowanie i debugowanie tego pliku. Korzystając z tych poleceń, kompilujesz lub debugujesz przy użyciu *tsc.exe* z opcjami domyślnymi. (Należy skompilować plik przed rozpoczęciem debugowania).

> [!NOTE]
> Podczas kompilowania kodu TypeScript używamy najnowszej wersji zainstalowanej w programie `C:\Program Files (x86)\Microsoft SDKs\TypeScript` .

Jeśli istnieje *tsconfig.js* w pliku znajdującym się w folderze, możesz kliknąć prawym przyciskiem myszy plik TypeScript, aby wyświetlić polecenie menu, aby debugować ten plik TypeScript. Ta opcja jest dostępna tylko wtedy, gdy nie `outFile` określono w *tsconfig.js*. Jeśli `outFile` jest określony, można debugować ten plik przez kliknięcie prawym przyciskiem myszy *tsconfig.jsna* i wybranie odpowiedniej opcji. `tsconfig.json`Plik udostępnia również opcję kompilacji umożliwiającą określenie opcji kompilatora.

> [!NOTE]
> Więcej informacji na temat *tsconfig.js* można znaleźć na [stronietsconfig.jsna podręczniku TypeScript](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html).

## <a name="unit-tests"></a>Testy jednostkowe
Możesz włączyć integrację testu jednostkowego w programie Visual Studio, określając główny test w *package.jsna*:

```json
{
    // ...
    "vsTest":{
        "testRoot": "./tests"
    }
    // ...
}
```

Moduł uruchamiający testy wylicza zainstalowane lokalnie pakiety, aby określić, która Platforma testowa ma być używana.
Jeśli żadna z obsługiwanych struktur nie zostanie rozpoznana, program Test Runner domyślnie *ExportRunner*. Inne obsługiwane struktury to:
* Środowiska Mocha ([mochajs.org](https://mochajs.org/))
* Jasmine ([Jasmine.GitHub.IO](https://jasmine.github.io/))
* Taśma ([GitHub.com/Substack/Tape](https://github.com/substack/tape))
* On ([jestjs.IO](https://jestjs.io/))

Po otwarciu Eksploratora testów (wybierz **test**  >  **Windows**  >  **Eksplorator testów**systemu Windows) program Visual Studio odnajduje i wyświetla testy.

> [!NOTE]
> Moduł uruchamiający testy będzie wyliczał tylko pliki JavaScript w katalogu głównym testu, jeśli aplikacja jest zapisywana w języku TypeScript, należy najpierw ją skompilować.
