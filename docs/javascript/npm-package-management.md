---
title: Zarządzanie pakietami npm
description: Program Visual Studio pomaga w zakresie zarządzania pakietami przy użyciu Menedżera pakietów środowiska Node.js (npm)
ms.custom: seodec18
ms.date: 06/06/2018
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: de92c3f1f0d0e29d1ba2dfaf5d536a42e636be2c
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409453"
---
# <a name="manage-npm-packages-in-visual-studio"></a>Zarządzanie pakietami npm w programie Visual Studio

npm pozwala Ci instalować i Zarządzaj pakietami do użytku w aplikacjach Node.js. Jeśli nie znasz npm i chcesz dowiedzieć się więcej, przejdź do [dokumentacji npm](https://docs.npmjs.com/).

Visual Studio można łatwo korzystać z polecenia npm npm i problem za pomocą interfejsu użytkownika lub bezpośrednio. Można użyć następujących metod:
* [Zainstaluj pakiety z Eksplorator rozwiązań](#npmInstallWindow)
* [Zarządzaj zainstalowanymi pakietami z Eksplorator rozwiązań](#solutionExplorer)
* [Używanie `.npm` polecenia w oknie interaktywnym środowiska Node. js](#interactive)

Te funkcje współpracują i synchronizują z systemem projektu i plikiem *Package. JSON* w projekcie.

> [!Important]
> NPM oczekuje folderu *node_modules* i pliku *Package. JSON* w katalogu głównym projektu. Jeśli struktura folderów aplikacji jest inna, należy zaktualizować strukturę folderów, jeśli chcesz zarządzać pakietami npm za pomocą programu Visual Studio.

> [!NOTE]
> W przypadku istniejących projektów NPM Użyj szablonu **z istniejącego rozwiązania kodu Node. js** .

## <a name="npmInstallWindow"></a>Zainstaluj pakiety z Eksplorator rozwiązań

Jest najprostszym sposobem zainstalowania pakietów npm w oknie instalacji pakietu npm. Aby uzyskać dostęp do tego okna, kliknij prawym przyciskiem myszy węzeł **npm** w projekcie i wybierz polecenie **Instaluj nowe pakiety npm**.

![Zainstaluj nowy pakiet npm z Eksploratora rozwiązań](../javascript/media/solution-explorer-install-package.png)

W tym oknie można wyszukać pakietu, określ opcje i zainstalować.

![Wyszukiwanie pakietów Menedżera npm](../javascript/media/search-package.png)

* **Typ zależności** — wybierany między pakietami **Standard**, **Development**i **Optional** . Standard określa, czy pakiet jest zależnością środowiska uruchomieniowego rozwoju Określa, że pakiet jest tylko wymagane podczas programowania.
* **Dodaj do pliku Package. JSON** — ta opcja jest przestarzała
* **Wybrana wersja** — wybierz wersję pakietu do zainstalowania.
* **Inne argumenty npm** — Określ inne standardowe argumenty npm. Na przykład możesz wprowadzić wartość wersji, taką jak `@~0.8`, aby zainstalować określoną wersję, która nie jest dostępna na liście wersje.

Aby zobaczyć postęp instalacji na karcie npm w oknie danych wyjściowych. Może to potrwać jakiś czas.

> [!TIP]
> Możesz wyszukać pakiety z zakresem, oczekując na zapytanie wyszukiwania z interesującym zakresem, na przykład wpisz `@types/mocha`, aby wyszukać pliki definicji TypeScript dla środowiska Mocha. Ponadto podczas instalowania definicji typów dla języka TypeScript można określić wersję języka TypeScript, którą odwołujących, dodając `@ts2.6` w polu argumentu npm.

## <a name="solutionExplorer"></a>Zarządzaj zainstalowanymi pakietami w Eksplorator rozwiązań

pakiety npm są wyświetlane w Eksploratorze rozwiązań. Wpisy w węźle **npm** powodują naśladowanie zależności w pliku *Package. JSON* .

![Wyszukiwanie pakietów Menedżera npm](../javascript/media/solution-explorer-status.png)

### <a name="package-status"></a>Stan pakietu
* ![Zainstalowany pakiet](../javascript/media/installed-npm.png) -Zainstalowanych i wymienionych w pliku package.json
* ![pakiet niezależny](../javascript/media/extraneous-npm.png)-zainstalowany, ale nie jest jawnie wymieniony w pliku Package. JSON
* ![Brak pakietu](../javascript/media/missing-npm.png) — Użytkownik nie jest zainstalowany, ale wymienione w pliku package.json

Kliknij prawym przyciskiem myszy węzeł pakietu lub węzeł **npm** , aby wykonać jedną z następujących czynności:
* **Zainstaluj brakujące pakiety** , które są wymienione w pliku *Package. JSON*
* **Aktualizuj pakiety** do najnowszej wersji
* **Odinstalowywanie pakietu** i usuwanie z pliku *Package. JSON*

## <a name="interactive"></a>Użyj polecenia. npm w oknie interaktywnym środowiska Node. js

Możesz również użyć `.npm` polecenie w oknie interaktywnym środowiska Node. js, aby wykonać polecenia npm. Aby otworzyć okno, kliknij prawym przyciskiem myszy projekt w Eksplorator rozwiązań i wybierz polecenie **Otwórz okno interaktywne środowiska Node. js**.

W oknie poleceń, takich jak następujące służy do zainstalowania pakietu:

`.npm install azure@4.2.3`

 > [!Tip]
 > Domyślnie npm będą wykonywane w katalogu głównym projektu. Jeśli masz wiele projektów w rozwiązaniu należy określić nazwę lub ścieżkę projektu w nawiasach.
 > `.npm [MyProjectNameOrPath] install azure@4.2.3`

 > [!Tip]
 > Jeśli projekt nie zawiera pliku Package. JSON, użyj `.npm init -y`, aby utworzyć nowy plik Package. JSON z wpisami domyślnymi.
