---
title: Tworzenie raportów profilera z wiersza polecenia | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: c886f8af-2014-4fec-9b24-d98b68ecafb7
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 475c8da2d10dea4953486fc9c564c5bde7fb0887
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85329074"
---
# <a name="create-profiler-reports-from-the-command-line"></a>Tworzenie raportów profilera z poziomu wiersza polecenia
Narzędzie wiersza polecenia **VSPerfReport** umożliwia tworzenie. wartość w *formacie XML* lub przecinkiem (.* CSV*) raporty z profilowania danych (.* VSP*). Typy raportów VSPerfReport ściśle pasują do widoków opartych na tabelach interfejsu dla [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Raport można filtrować, aby wyświetlić tylko kod i wyświetlić tylko segment pliku danych profilowania. Aby uzyskać więcej informacji, zobacz [VSPerfReport](../profiling/vsperfreport.md).

 Można także ułatwić udostępnianie plików danych profilowania przez osadzanie symboli w. pliki *VSP* i przez utworzenie raportu wstępnie przeanalizowanego (.* vsps*) pliki, które są krótsze i szybsze do otwarcia.

## <a name="common-tasks"></a>Typowe zadania

|Zadanie|Powiązana zawartość|
|----------|---------------------|
|**Utwórz raport podstawowy.** Utwórz wszystkie lub podzbiór typów raportów VSPerfReport.|-   [Tworzenie podstawowych raportów](../profiling/creating-basic-profiling-reports-from-the-command-line.md)|
|**Porównaj dwa pliki danych profilowania.** Utwórz raport "różnica" porównujący dane dotyczące wydajności w dwóch plikach danych profilowania.|-   [Instrukcje: Tworzenie raportu porównania profilera z wiersza polecenia](../profiling/how-to-create-a-profiler-comparison-report-from-a-command-prompt.md)|
|**Wyświetl dane śledzenia wywołań i śledzenie zdarzeń dla systemu Windows (ETW).** Utwórz raport śledzenia wywołań, który wyświetla listę informacji o chronometrażu dla każdego wpisu i punktu wyjścia do funkcji aplikacji oraz każdego wywołania funkcji przez funkcję. Lub utwórz szczegółową listę wszystkich zdarzeń ETW, które zostały zebrane w ramach przebiegu profilowania.|-   [Instrukcje: Tworzenie raportu śledzenia wywołań](../profiling/how-to-create-a-profiling-tools-call-trace-report.md)|
|**Filtrowanie raportu.** Ogranicz raport tylko do funkcji w kodzie lub do określonego czasu w pliku danych profilowania.|-   [Instrukcje: filtrowanie raportów z wiersza polecenia](../profiling/how-to-filter-reports-from-the-command-line.md)|
|**Tworzenie przenośnych plików danych profilowania.** Aby ułatwić udostępnianie danych profilowania, można osadzić symbole dla profilowania przebiegu w. plik *VSP* . Możesz również utworzyć wstępnie przeanalizowane dane profilowania (.* vsps*) plik, który jest krótszy i szybszy do otwarcia.|-   [Tworzenie przenośnych plików danych profilowania](../profiling/creating-portable-profiling-data-files-from-the-command-line.md)|
