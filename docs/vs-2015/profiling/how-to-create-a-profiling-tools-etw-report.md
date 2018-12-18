---
title: 'Porady: Tworzenie raportu ETW narzędzi profilowania | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bf5547b3-f6c7-4989-9d47-2fe4f1261444
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1901cf0800483ee4ce8ba0bce26fe3cf7ac073e6
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51761602"
---
# <a name="how-to-create-a-profiling-tools-etw-report"></a>Porady: tworzenie raportu ETW narzędzi profilowania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Raport śledzenie zdarzeń dla Windows (ETW) zawiera listę zdarzeń funkcji ETW, które są rejestrowane w sesji pomiaru wydajności [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Profiling Tools. Dane ETW są zbierane w pliku danych binarnych (ETL). Aby uzyskać więcej informacji na temat tego raportu, zobacz [raportu śledzenie zdarzeń dla Windows (ETW)](../profiling/event-tracing-for-windows-etw-report.md).  
  
> [!NOTE]
>  Nie można wyświetlić raporty ETW w interfejsie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
- Aby uzyskać informacje dotyczące zbierania danych ETW przy użyciu interfejsu dla [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], zobacz [jak: danych zbierania zdarzeń śledzenia dla Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md).  
  
- Aby dowiedzieć się, jak zbierać dane funkcji ETW z poziomu wiersza polecenia, zobacz [VSPerfCmd](../profiling/vsperfcmd.md) i [zdarzenia](../profiling/events-vsperfcmd.md).  
  
  Generowanie raportu ETW za pomocą **VSReport / summary: etw** polecenia. .Etl, który zawiera dane funkcji ETW muszą być w tym samym katalogu co plik danych profilowania (.vsp lub .vsps). Domyślnie raport jest generowany w formacie wartości rozdzielanych przecinkami (CSV). Aby uzyskać więcej informacji, zobacz [VSPerfReport](../profiling/vsperfreport.md).  
  
### <a name="to-generate-an-etw-report"></a>Aby wygenerować raport ETW  
  
-   W **polecenia** oknie wpisz następujące polecenie w wierszu:  
  
     *ToolsPath* **VSPerfReport** *Plik_vsp* **/Summary: ETW [podsumowań w plikach]**  
  
    |||  
    |-|-|  
    |*ToolsPath*|Ścieżka narzędzia Profiling Tools. Aby uzyskać więcej informacji, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|  
    |*Plik_vsp*|Plik danych profilowania (.vsp lub .vsps). Akceptowane są pełne i częściowe ścieżki.|  
    |Xml|Generuje raport, który jest sformatowany w języku XML.|



