---
title: Tworzenie raportów Profiler z poziomu wiersza polecenia | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c886f8af-2014-4fec-9b24-d98b68ecafb7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e6a6d31d15f7f7ed533d73683a3c12d152bd7046
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56598885"
---
# <a name="create-profiler-reports-from-the-command-line"></a>Tworzenie raportów profilera z wiersza polecenia
**VSPerfReport** narzędzie wiersza polecenia umożliwia utworzenie. *XML* lub wartości rozdzielanych przecinkami (. *CSV*) raportów z danych profilowania (. *Vsp*) plików. Typy raportów VSPerfReport pasować widoków opartych na tabelach interfejsu dla [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Możesz filtrować raport, aby wyświetlić tylko Twój kod i aby pokazać tylko jeden segment plik danych profilowania. Aby uzyskać więcej informacji, zobacz [VSPerfReport](../profiling/vsperfreport.md).

 Można również ustawić jako pliki danych profilowania łatwiej można udostępnić, osadzając symboli. *vsp* pliki i tworząc wstępnie przeanalizowany raport (. *vsps*) plików, które są mniejsze i szybsze do otwarcia.

## <a name="common-tasks"></a>Wspólne zadania

|Zadanie|Powiązana zawartość|
|----------|---------------------|
|**Tworzenie podstawowych raportów.** Utwórz wszystkie lub podzbiór VSPerfReport typów raportów.|-   [Tworzenie podstawowych raportów](../profiling/creating-basic-profiling-reports-from-the-command-line.md)|
|**Porównanie dwóch plików danych profilowania.** Utwórz raport "diff", który porównuje dane dotyczące wydajności w dwóch plików danych profilowania.|-   [Jak: Tworzenie raportu porównania profilera z wiersza polecenia](../profiling/how-to-create-a-profiler-comparison-report-from-a-command-prompt.md)|
|**Wyświetl ślad wywołania i dane zdarzeń śledzenia dla Windows (ETW).** Tworzenie raportu śledzenia wywołań, który wyświetla listę informacji chronometrażu dla każdego punktu wejścia i wyjścia do funkcji w aplikacji oraz dla każdego wywołania innych funkcji przez funkcję. Lub Utwórz uzyskać szczegółową listę wszystkich zdarzeń ETW, które zostały zebrane podczas uruchomienia profilowania.|-   [Jak: Tworzenie raportu śledzenia wywołań](../profiling/how-to-create-a-profiling-tools-call-trace-report.md)|
|**Filtrowanie raportu.** Ogranicz raport tylko z funkcjami w kodzie lub się w określonym czasie w pliku danych profilowania.|-   [Jak: Filtrować raporty z wiersza polecenia](../profiling/how-to-filter-reports-from-the-command-line.md)|
|**Tworzenie przenośnych plików danych profilowania.** Aby upewnić się, udostępnianie danych ułatwia profilowania, można osadzić symbole dla przebiegu do profilowania. *vsp* pliku. Możesz również utworzyć wstępnie analizowanych danych profilowania (. *vsps*) plik, który jest mniejszy i szybciej otworzyć.|-   [Tworzenie przenośnych plików danych profilowania](../profiling/creating-portable-profiling-data-files-from-the-command-line.md)|