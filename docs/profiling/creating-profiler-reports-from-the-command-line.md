---
title: Tworzenie raportów profilera z wiersza polecenia | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c886f8af-2014-4fec-9b24-d98b68ecafb7
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 7f28d7271fdf33822475a663debed269bb515959
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777780"
---
# <a name="create-profiler-reports-from-the-command-line"></a>Tworzenie raportów profilera z wiersza polecenia
Narzędzie wiersza polecenia **VSPerfReport** umożliwia tworzenie programu . *xml* lub wartość oddzielona przecinkami (.* csv*) raporty z danych profilowania (.* vsp).* Typy raportów VSPerfReport są ściśle zgodne z [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]widokami opartymi na tabelach interfejsu dla programu . Raport można filtrować, aby wyświetlić tylko kod i wyświetlić tylko segment pliku danych profilowania. Aby uzyskać więcej informacji, zobacz [VSPerfReport](../profiling/vsperfreport.md).

 Można również ułatwić udostępnianie plików danych profilowania, osadzając symbole w pliku . *vsp* i tworząc wstępnie przeanalizowany raport (.* vsps*) pliki, które są mniejsze i szybsze do otwarcia.

## <a name="common-tasks"></a>Typowe zadania

|Zadanie|Powiązana zawartość|
|----------|---------------------|
|**Tworzenie raportu podstawowego.** Utwórz cały lub podzbiór typów raportów VSPerfReport.|-   [Tworzenie podstawowych raportów](../profiling/creating-basic-profiling-reports-from-the-command-line.md)|
|**Porównaj dwa pliki danych profilowania.** Utwórz raport "diff", który porównuje dane dotyczące wydajności w dwóch plikach danych profilowania.|-   [Jak: Tworzenie raportu porównania profilera z wiersza polecenia](../profiling/how-to-create-a-profiler-comparison-report-from-a-command-prompt.md)|
|**Wyświetlanie danych śledzenia wywołań i śledzenia zdarzeń dla systemu Windows (ETW).** Utwórz raport śledzenia wywołań, który zawiera informacje o chronometrażu dla każdego punktu wejścia i wyjścia do funkcji aplikacji i każdego wywołania innych funkcji przez funkcję. Możesz też utworzyć szczegółową listę wszystkich zdarzeń ETW, które zostały zebrane w przebiegu profilowania.|-   [Jak: Tworzenie raportu śledzenia połączeń](../profiling/how-to-create-a-profiling-tools-call-trace-report.md)|
|**Filtrowanie raportu.** Ogranicz raport tylko do funkcji w kodzie lub do określonego czasu w pliku danych profilowania.|-   [Jak: Filtrowanie raportów z wiersza polecenia](../profiling/how-to-filter-reports-from-the-command-line.md)|
|**Tworzenie przenośnych plików danych profilowania.** Aby ułatwić udostępnianie danych profilowania, można osadzić symbole profilowania w pliku . *vsp.* Można również utworzyć wstępnie przeanalizowane dane profilowania (.* vsps)* plik, który jest mniejszy i szybszy do otwarcia.|-   [Tworzenie przenośnych plików danych profilowania](../profiling/creating-portable-profiling-data-files-from-the-command-line.md)|
