---
title: Korzystanie z pliku Node.js REPL
description: Program Visual Studio zapewnia obsługę interakcji ze środowiska uruchomieniowego Node.js
ms.date: 12/04/2018
ms.topic: conceptual
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jillfra
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: faed930c60869010f740cf0a1e118a40299ce782
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "62840675"
---
# <a name="work-with-the-nodejs-interactive-window"></a>Praca z interakcyjnym oknem Node.js

Node.js Tools for Visual Studio zawiera interaktywne okno dla zainstalowanego środowiska wykonawczego Node.js. To okno umożliwia wprowadzenie kodu JavaScript i natychmiastowe wyświetlenie wyników, a także wykonanie poleceń npm w celu interakcji z bieżącym projektem. Interaktywne okno jest również znane jako REPL (**R**ead/**E**valuate/**P**rint **L**oop).

## <a name="open-the-interactive-window"></a>Otwieranie okna interaktywnego

Okno interaktywne można otworzyć, klikając prawym przyciskiem myszy węzeł projektu Node.js w Eksploratorze rozwiązań i wybierając **polecenie Otwórz okno interaktywne Node.js**.

![Interakcyjne okno Node.js w menu kontekstowym projektu](../javascript/media/interactivewindow-open-from-project.png)

Domyślnymi skrótami klawiszowymi do otwierania interaktywnego okna Node.js są **[CTRL] + K, N**. Można też otworzyć okno na pasku narzędzi, wybierając **polecenie Wyświetl** > okno interaktywne**Windows** > **Node.js**.

## <a name="use-the-repl"></a>Użyj repl

Po otwarciu można wprowadzić polecenia.

![Okno interaktywne Node.js](../javascript/media/interactivewindow.png)

Okno interaktywne ma kilka wbudowanych poleceń, które zaczynają się od prefiksu kropki, aby odróżnić je od dowolnej deklarowaną funkcji JavaScript. Obsługiwane są następujące polecenia:

**.cls, .clear** Czyści zawartość okna edytora, pozostawiając kontekst historii i wykonywania nienaruszone.

**.help (pomoc)** Wyświetla pomoc w określonym poleceniu lub na wszystkich dostępnych poleceniach i powiązaniach klawiszy, jeśli nie określono żadnych.

**.info (informacje)** Pokazuje informacje o bieżącym używanym pliku wykonywalnym Node.js.

**.npm** Uruchamia polecenie npm. Jeśli rozwiązanie zawiera więcej niż jeden projekt, `.npm [projectname] <npm arguments>`określ projekt docelowy za pomocą .

**.reset (reset)** Resetuje środowisko wykonywania do stanu początkowego, zachowaj historię.

**.save (zapisz)** Zapisuje bieżącą sesję REPL w pliku.