---
title: Zbierania śladu ETL za pomocą narzędzia PerfView
ms.date: 06/27/2019
ms.topic: conceptual
helpviewer_keywords:
- perfview
- ETL Trace
author: mikeblome
ms.author: mblome
manager: jillfra
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.description: Use perfview.exe to collect ETL traces for troubleshooting issues with Visual Studio
ms.openlocfilehash: baae89b7bf45a4848c571f75e37c6cc0d203d459
ms.sourcegitcommit: 6f7a740750b2cd17ea2275c3d046caebc9782917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2019
ms.locfileid: "67518236"
---
# <a name="collect-an-etl-trace-with-perfview"></a>Zbierania śladu ETL za pomocą narzędzia PerfView

Narzędzia PerfView to narzędzie, które tworzy pliki ETL (dziennik śledzenia zdarzeń), na podstawie [Event Tracing for Windows](/windows/desktop/ETW/event-tracing-portal) , może być przydatne przy rozwiązywaniu niektórych typów poza problemów z programem Visual Studio. Od czasu do czasu podczas zgłaszania problemu, zespół pracujący nad produktem może poprosić o uruchomienie narzędzia PerfView do zbierania dodatkowych informacji.

## <a name="install-perfview"></a>Zainstaluj narzędzia PerfView

Pobierz narzędzia PerfView z [Centrum pobierania Microsoft](http://www.microsoft.com/download/details.aspx?id=28567).

## <a name="run-perfview"></a>Uruchom narzędzia PerfView

1. Kliknij prawym przyciskiem myszy **PerfView.exe** w Eksploratorze Windows i wybierz polecenie **Uruchom jako administrator** jako administrator
1. Zbieranie menu, wybierz **zbierania**
1. Sprawdź **Zip**, **scalania**, i **Czas wątku**.
1. Zwiększ **cykliczne MB** do 1000.
1. Zmiana **bieżący katalog** zapisanie śladów ETL do określonego folderu i pliku danych, jeśli zamierzasz zbierać więcej niż jeden raz.
1. Aby rozpocząć rejestrowanie danych, wybierz opcję **Rozpocznij zbieranie** przycisku.
1. Aby zatrzymać rejestrowanie danych, wybierz opcję **Zatrzymaj Kolekcjonowanie** przycisku. Plik PrefView.etl.zip zostaną zapisane w określonym katalogu.

Narzędzia PerfView można przechowywać tylko najnowszych danych, która pasuje do jego buforu. W związku z tym spróbuj zatrzymać zbieranie, w jak najszybciej po uruchomieniu programu Visual Studio zablokować lub spowolnić. Nie zbieraj przez więcej niż 30 sekund, trzeba uderzyć problem.

Aby uzyskać więcej informacji, zobacz [narzędzia PerfView samouczek w witrynie Channel9](http://channel9.msdn.com/Series/PerfView-Tutorial/PerfView-Tutorial-1-Collecting-data-with-the-Run-command).
