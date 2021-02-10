---
title: Użyj Node.js REPL
description: Program Visual Studio zapewnia obsługę współdziałania z Node.js środowiska uruchomieniowego
ms.date: 12/04/2018
ms.topic: how-to
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jmartens
dev_langs:
- JavaScript
ms.workload:
- nodejs
ms.openlocfilehash: 9f13128bc552ffdb31b3f4a9315a3f9aa3543b0f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99962694"
---
# <a name="work-with-the-nodejs-interactive-window"></a>Pracuj z oknem interaktywnym Node.js

Narzędzia Node.js Tools for Visual Studio obejmują okno interaktywne dla zainstalowanego Node.js środowiska uruchomieniowego. To okno umożliwia wprowadzanie kodu JavaScript i natychmiastowe wyświetlanie wyników, a także wykonywanie poleceń npm w celu współdziałania z bieżącym projektem. Okno interaktywne jest również znane jako REPL (**R** Eczytaj/**E** Valuate/**P** rukuj **L** OOP).

## <a name="open-the-interactive-window"></a>Otwórz okno interaktywne

Okno interaktywne można otworzyć, klikając prawym przyciskiem myszy węzeł projektu Node.js w Eksplorator rozwiązań i wybierając polecenie **otwórz Node.js okno interaktywne**.

![Okno interaktywne Node.js w menu kontekstowym projektu](../javascript/media/interactivewindow-open-from-project.png)

Domyślne krótkie klucze służące do otwierania okna interaktywnego Node.js są **[Ctrl] + K, N**. Możesz również otworzyć okno z poziomu paska narzędzi, wybierając opcję **Wyświetl**  >    >  **okno WindowsNode.js Interactive**.

## <a name="use-the-repl"></a>Korzystanie z REPL

Po otwarciu można wprowadzać polecenia.

![Okno interaktywne Node.js](../javascript/media/interactivewindow.png)

Okno interaktywne zawiera kilka wbudowanych poleceń, które zaczynają się od prefiksu kropki, aby odróżnić je od dowolnej funkcji języka JavaScript, która została zadeklarowana. Obsługiwane są następujące polecenia:

**. CLS,. Clear** Czyści zawartość okna edytora, pozostawiając historię i kontekst wykonywania bez zmian.

**. Pomoc** Wyświetla pomoc dotyczącą określonego polecenia lub we wszystkich dostępnych poleceniach i powiązaniach kluczy, jeśli nie została określona.

**. info** Pokazuje informacje o aktualnie używanym pliku wykonywalnym Node.js.

**. npm** Uruchamia polecenie npm. Jeśli rozwiązanie zawiera więcej niż jeden projekt, określ projekt docelowy za pomocą `.npm [projectname] <npm arguments>` .

**. Zresetuj** Resetuje środowisko wykonawcze do stanu początkowego, Zachowaj historię.

**. Save** Zapisuje bieżącą sesję REPL do pliku.