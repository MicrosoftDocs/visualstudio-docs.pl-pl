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
ms.openlocfilehash: 288cb11d3e6ae3917f5fcc6ec9ed242549908576
ms.sourcegitcommit: 978df2feb5e64228d2e3dd430b299a5c234cda17
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2019
ms.locfileid: "72888641"
---
# <a name="develop-javascript-and-typescript-code-in-visual-studio-without-solutions-or-projects"></a>Programowanie kodu JavaScript i TypeScript w programie Visual Studio bez rozwiązań i projektów

Począwszy od programu Visual Studio 2017, można [opracowywać kod bez projektów i rozwiązań](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md), dzięki czemu można otwierać foldery kodu i od razu zacząć pracę z zaawansowaną obsługą edytora, taką jak IntelliSense, wyszukiwanie, Refaktoryzacja, debugowanie i nie tylko. Oprócz tych funkcji Node.js Tools for Visual Studio dodaje obsługę tworzenia plików TypeScript, zarządzania pakietami npm oraz uruchamiania skryptów npm.

Aby rozpocząć, wybierz pozycję **plik** > **Otwórz** **folder** > z paska narzędzi. Eksplorator rozwiązań wyświetla wszystkie pliki w folderze, a wszystkie pliki można otworzyć, aby rozpocząć edycję. W tle program Visual Studio indeksuje pliki w celu włączenia funkcji npm, Build i Debug.

> [!IMPORTANT]
> Wiele funkcji opisanych w tym artykule, łącznie z integracją npm, wymaga programu Visual Studio 2017 w wersji 15,8 lub nowszej.

## <a name="npm-integration"></a>Integracja npm

Jeśli otwarty folder zawiera plik *Package. JSON* , możesz kliknąć prawym przyciskiem myszy element *Package. JSON* , aby wyświetlić menu kontekstowe (menu skrótów) specyficzne dla npm.

![menu npm w Eksplorator rozwiązań](../javascript/media/solution-explorer-npm-ctx.png)

W menu skrótów można zarządzać pakietami instalowanymi przez npm w taki sam sposób, jak [w przypadku korzystania](npm-package-management.md) z pliku projektu.

Ponadto menu pozwala także uruchamiać skrypty zdefiniowane w `scripts` elementu w pliku *Package. JSON*. Te skrypty będą używać wersji środowiska Node. js dostępnej w zmiennej środowiskowej `PATH`. Skrypty są uruchamiane w nowym oknie. To świetny sposób na wykonanie kompilacji lub uruchomienie skryptów.

## <a name="build-and-debug"></a>Kompiluj i Debuguj

### <a name="packagejson"></a>plik Package. JSON
Jeśli plik *Package. JSON* w folderze określa `main` element, polecenie **Debug** będzie dostępne w menu skrótów kliknij prawym przyciskiem myszy pliku *Package. JSON*.
Kliknięcie tej opcji spowoduje uruchomienie programu *Node. exe* z określonym skryptem jako argumentem.

### <a name="javascript-files"></a>Pliki JavaScript
Aby debugować pliki JavaScript, kliknij prawym przyciskiem myszy plik i wybierz polecenie **Debuguj** z menu skrótów. Spowoduje to uruchomienie programu *Node. exe* z tym plikiem JavaScript jako argumentem.

### <a name="typescript-files-and-tsconfigjson"></a>Pliki TypeScript i tsconfig. JSON
Jeśli w folderze nie ma pliku *tsconfig. JSON* , można kliknąć prawym przyciskiem myszy plik TypeScript, aby wyświetlić polecenia menu skrótów, które umożliwiają kompilowanie i debugowanie tego pliku. Korzystając z tych poleceń, można skompilować lub debugować przy użyciu programu *TSC. exe* z opcjami domyślnymi. (Należy skompilować plik przed rozpoczęciem debugowania).

> [!NOTE]
> Podczas kompilowania kodu TypeScript używamy najnowszej wersji zainstalowanej w `C:\Program Files (x86)\Microsoft SDKs\TypeScript`.

Jeśli istnieje plik *tsconfig. JSON* znajdujący się w folderze, można kliknąć prawym przyciskiem myszy plik TypeScript, aby wyświetlić polecenie menu, aby debugować ten plik TypeScript. Ta opcja jest dostępna tylko wtedy, gdy nie określono `outFile` w pliku *tsconfig. JSON*. Jeśli określono `outFile`, można debugować ten plik przez kliknięcie prawym przyciskiem myszy *tsconfig. JSON* i wybranie odpowiedniej opcji. Plik `tsconfig.json` udostępnia również opcję kompilacji umożliwiającą określenie opcji kompilatora.

> [!NOTE]
> Więcej informacji na temat pliku *tsconfig. JSON* można znaleźć na [stronie podręcznika języka TypeScript tsconfig. JSON](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html).

## <a name="unit-tests"></a>Testy jednostkowe
Możesz włączyć integrację testu jednostkowego w programie Visual Studio, określając główny test w pliku *Package. JSON*:

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

Po otwarciu Eksploratora testów (wybierz **Test** > **Windows** > **Test Explorer**) program Visual Studio odnajduje i wyświetla testy.

> [!NOTE]
> Moduł uruchamiający testy będzie wyliczał tylko pliki JavaScript w katalogu głównym testu, jeśli aplikacja jest zapisywana w języku TypeScript, należy najpierw ją skompilować.
