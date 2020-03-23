---
title: Zbieranie śladu ETL za pomocą narzędzia PerfView
ms.date: 09/27/2019
ms.topic: conceptual
helpviewer_keywords:
- perfview
- ETL Trace
author: corob-msft
ms.author: corob
manager: jillfra
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.description: Use perfview.exe to collect ETL traces for troubleshooting issues with Visual Studio
ms.openlocfilehash: 24d72e9630506ecc3d25fcc75e51eeb84f619e53
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77271166"
---
# <a name="collect-an-etl-trace-with-perfview"></a>Zbieranie śladu ETL za pomocą narzędzia PerfView

PerfView to narzędzie, które tworzy pliki ETL (dziennik śledzenia zdarzeń) na podstawie [śledzenia zdarzeń dla systemu Windows,](/windows/desktop/ETW/event-tracing-portal) które mogą być przydatne w rozwiązywaniu niektórych rodzajów problemów z programem Visual Studio. Od czasu do czasu, gdy zgłaszasz problem, zespół produktu może poprosić o uruchomienie programu PerfView w celu zebrania dodatkowych informacji.

## <a name="install-perfview"></a>Instalowanie programu PerfView

Pobierz PerfView z [GitHub](https://github.com/Microsoft/perfview/blob/master/documentation/Downloading.md).

## <a name="run-perfview"></a>Uruchamianie widoku PerfView

1. Kliknij prawym przyciskiem myszy **plik PerfView.exe** w Eksploratorze Windows i wybierz pozycję **Uruchom jako administrator** jako administrator
1. W menu Zbieraj wybierz polecenie **Zbierz**
1. Sprawdź **Zip**, **Merge**i **ThreadTime**.
1. Zwiększ **okrągły MB** do 1000.
1. Zmień **bieżący reż.**
1. Aby rozpocząć nagrywanie danych, wybierz przycisk **Rozpocznij zbieranie danych.**
1. Aby zatrzymać rejestrowanie danych, wybierz przycisk **Zatrzymaj zbieranie** danych. Plik PrefView.etl.zip zostanie zapisany w określonym katalogu.

PerfView można przechowywać tylko najnowsze dane, które pasuje do jego buforu. W związku z tym spróbuj zatrzymać kolekcję tak szybko, jak to możliwe po programie Visual Studio zaczyna zamrażać lub spowolnić. Nie zbieraj więcej niż 30 sekund po trafieniu problemu.

Aby uzyskać więcej informacji, zobacz [PerfView Samouczek na Channel9](https://channel9.msdn.com/Series/PerfView-Tutorial/PerfView-Tutorial-1-Collecting-data-with-the-Run-command).
