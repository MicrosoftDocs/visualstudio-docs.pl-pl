---
title: Tworzenie raportów profilera z wiersza polecenia | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: c886f8af-2014-4fec-9b24-d98b68ecafb7
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 489ebd4e5aff3ef9b93ef0d8fe18f9ae8cc85011
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62537205"
---
# <a name="creating-profiler-reports-from-the-command-line"></a>Tworzenie raportów profilera z wiersza polecenia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Za pomocą narzędzia wiersza polecenia **VSPerfReport** można tworzyć raporty XML lub wartości rozdzielane przecinkami (CSV) z plików danych profilowania (. vsp). Typy raportów VSPerfReport ściśle pasują do widoków opartych na tabelach interfejsu dla [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Raport można filtrować, aby wyświetlić tylko kod i wyświetlić tylko segment pliku danych profilowania. Aby uzyskać więcej informacji, zobacz [VSPerfReport](../profiling/vsperfreport.md).  
  
 Można także ułatwić udostępnianie plików danych profilowania przez osadzanie symboli w plikach. vsp oraz Tworzenie wstępnie przeanalizowanych plików raportu (. vsps), które są krótsze i szybsze do otwarcia.  
  
## <a name="common-tasks"></a>Typowe zadania  
  
|Zadanie|Powiązana zawartość|  
|----------|---------------------|  
|**Utwórz raport podstawowy.** Utwórz wszystkie lub podzbiór typów raportów VSPerfReport.|-   [Tworzenie podstawowych raportów](../profiling/creating-basic-profiling-reports-from-the-command-line.md)|  
|**Porównaj dwa pliki danych profilowania.** Utwórz raport "różnica" porównujący dane dotyczące wydajności w dwóch plikach danych profilowania.|-   [Instrukcje: Tworzenie raportu porównania profilera z wiersza polecenia](../profiling/how-to-create-a-profiler-comparison-report-from-a-command-prompt.md)|  
|**Wyświetl dane śledzenia wywołań i śledzenie zdarzeń dla systemu Windows (ETW).** Utwórz raport śledzenia wywołań, który wyświetla listę informacji o chronometrażu dla każdego wpisu i punktu wyjścia do funkcji aplikacji oraz każdego wywołania funkcji przez funkcję. Lub utwórz szczegółową listę wszystkich zdarzeń ETW, które zostały zebrane w ramach przebiegu profilowania.|-   [Instrukcje: Tworzenie raportu śledzenia wywołań](../profiling/how-to-create-a-profiling-tools-call-trace-report.md)|  
|**Filtrowanie raportu.** Ogranicz raport tylko do funkcji w kodzie lub do określonego czasu w pliku danych profilowania.|-   [Instrukcje: filtrowanie raportów z wiersza polecenia](../profiling/how-to-filter-reports-from-the-command-line.md)|  
|**Tworzenie przenośnych plików danych profilowania.** Aby ułatwić udostępnianie danych profilowania, można osadzić symbole dla uruchomienia profilowania w pliku. vsp. Możesz również utworzyć wstępnie przeanalizowany plik danych profilowania (vsps), który jest krótszy i szybszy do otwarcia.|-   [Tworzenie przenośnych plików danych profilowania](../profiling/creating-portable-profiling-data-files-from-the-command-line.md)|
