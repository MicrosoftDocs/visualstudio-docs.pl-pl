---
title: Zarządzanie pakietami npm
description: Program Visual Studio pomaga w zakresie zarządzania pakietami przy użyciu Menedżera pakietów środowiska Node.js (npm)
ms.custom: seodec18
ms.date: 06/06/2018
ms.technology: vs-nodejs
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: douge
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 297bad186c7f3412e56a5a59f65b82ab9cd35a03
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53049657"
---
# <a name="manage-npm-packages-in-visual-studio"></a>Zarządzanie pakietami npm w programie Visual Studio

npm pozwala Ci instalować i Zarządzaj pakietami do użytku w aplikacjach Node.js. Jeśli znasz npm i chcesz, aby dowiedzieć się więcej, przejdź do strony [dokumentacji npm](https://docs.npmjs.com/).

Visual Studio można łatwo korzystać z polecenia npm npm i problem za pomocą interfejsu użytkownika lub bezpośrednio. Można użyć następujących metod:
* [Zainstaluj pakiety za pomocą Eksploratora rozwiązań](#npmInstallWindow)
* [Zarządzanie pakietami zainstalowanych za pomocą Eksploratora rozwiązań](#solutionExplorer)
* [Użyj `.npm` polecenia w oknie interaktywne Node.js](#interactive)

Te funkcje współdziałają ze sobą i synchronizować z system projektu i *package.json* pliku w projekcie.

## <a name="npmInstallWindow"></a> Zainstaluj pakiety za pomocą Eksploratora rozwiązań

Jest najprostszym sposobem zainstalowania pakietów npm w oknie instalacji pakietu npm. Aby uzyskać dostęp do tego okna, kliknij prawym przyciskiem myszy **npm** węzeł w projekcie i wybierz **zainstalować nowe pakiety npm**.

![Zainstaluj nowy pakiet npm z Eksploratora rozwiązań](../javascript/media/solution-explorer-install-package.png)

W tym oknie można wyszukać pakietu, określ opcje i zainstalować. 

![Wyszukiwanie pakietów Menedżera npm](../javascript/media/search-package.png)

* **Typ zależności** — wybrać między **standardowa**, **rozwoju**, i **opcjonalnie** pakietów. Standard określa, czy pakiet jest zależnością środowiska uruchomieniowego rozwoju Określa, że pakiet jest tylko wymagane podczas programowania.
* **Dodaj do pliku package.json** — ta opcja jest przestarzały
* **Wybrana wersja** — wybierz wersję pakietu, którą chcesz zainstalować.
* **Inne argumenty pakietu npm** -określ inne argumenty pakietu npm standardowych. Na przykład można wprowadzić wartość wersji takie jak `@~0.8` zainstalować określoną wersję, która nie jest dostępna na liście wersji.

Aby zobaczyć postęp instalacji na karcie npm w oknie danych wyjściowych. Może to potrwać pewien czas.

> [!TIP]
> Można wyszukiwać pakiety o określonym zakresie przez poprzedzenie jej zapytania wyszukiwania z zakresem interesuje Cię, na przykład wpisz `@types/mocha` do wyszukiwania plików definicji TypeScript dla środowiska mocha. Instalując definicje typów TypeScript, możesz również określić wersji TypeScript jest elementem docelowym, dodając `@ts2.6` w polu argumentów npm.

## <a name="solutionExplorer"></a>Zarządzanie pakietów zainstalowanych w Eksploratorze rozwiązań

pakiety npm są wyświetlane w Eksploratorze rozwiązań. Wpisy w obszarze **npm** węzła naśladować zależności w *package.json* pliku.

![Wyszukiwanie pakietów Menedżera npm](../javascript/media/solution-explorer-status.png)

### <a name="package-status"></a>Stan pakietu
* ![Zainstalowany pakiet](../javascript/media/installed-npm.png) -Zainstalowanych i wymienionych w pliku package.json
* ![Nadmiarowe pakietu](../javascript/media/extraneous-npm.png) — zainstalowany, ale nie zostały jawnie wymienione w pliku package.json
* ![Brak pakietu](../javascript/media/missing-npm.png) — Użytkownik nie jest zainstalowany, ale wymienione w pliku package.json

Kliknij prawym przyciskiem myszy węzeł pakietu lub **npm** węzeł, aby wykonać jedną z następujących czynności:
* **Instalowanie brakujących pakietów** wymienione w *pliku package.json*
* **Pakiety aktualizacji** do najnowszej wersji
* **Odinstaluj pakiet** i Usuń z *pliku package.json*

## <a name="interactive"></a>W oknie interaktywne Node.js za pomocą polecenia .npm

Można również użyć `.npm` polecenia w oknie interaktywne Node.js do wykonywania poleceń Menedżera npm. Aby otworzyć okno, kliknij prawym przyciskiem myszy projekt w Eksploratorze rozwiązań, a następnie wybierz **Otwórz okno interaktywne języka Node.js**.

W oknie poleceń, takich jak następujące służy do zainstalowania pakietu:

`.npm install azure@4.2.3`
 
 > [!Tip]
 > Domyślnie npm będą wykonywane w katalogu głównym projektu. Jeśli masz wiele projektów w rozwiązaniu należy określić nazwę lub ścieżkę projektu w nawiasach. 
 > `.npm [MyProjectNameOrPath] install azure@4.2.3`

 > [!Tip]
 > Jeśli projekt nie zawiera pliku package.json, użyj `.npm init -y` Aby utworzyć nowy plik package.json przy użyciu domyślnych wpisów. 