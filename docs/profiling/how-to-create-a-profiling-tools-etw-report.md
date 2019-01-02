---
title: 'Instrukcje: Tworzenie raportu ETW narzędzi profilowania | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: bf5547b3-f6c7-4989-9d47-2fe4f1261444
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 304cc9b65ed876e2348a6b96dc1f50e9a6934a4a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53950978"
---
# <a name="how-to-create-a-profiling-tools-etw-report"></a>Instrukcje: Tworzenie raportu ETW narzędzi profilowania
Raport śledzenie zdarzeń dla Windows (ETW) zawiera listę zdarzeń funkcji ETW, które są rejestrowane w sesji pomiaru wydajności [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Profiling Tools. Dane funkcji ETW są zbierane w pliku binarnym (. *etl*) pliku. Aby uzyskać więcej informacji na temat tego raportu, zobacz [raportu śledzenie zdarzeń dla Windows (ETW)](../profiling/event-tracing-for-windows-etw-report.md).  
  
> [!NOTE]
>  Nie można wyświetlić raporty ETW w interfejsie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
- Aby uzyskać informacje dotyczące zbierania danych ETW przy użyciu interfejsu dla [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], zobacz [jak: Zbieraj dane zdarzenia śledzenia dla Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md).  
  
- Aby dowiedzieć się, jak zbierać dane funkcji ETW z poziomu wiersza polecenia, zobacz [VSPerfCmd](../profiling/vsperfcmd.md) i [zdarzenia](../profiling/events-vsperfcmd.md).  
  
  Generowanie raportu ETW za pomocą **VSReport / summary: etw** polecenia. . *etl* zawierający ETW dane muszą być w tym samym katalogu co danych profilowania (. *Vsp* lub. *vsps*) pliku. Domyślnie raport jest generowany jako wartość rozdzielaną przecinkami (. *CSV*) pliku. Aby uzyskać więcej informacji, zobacz [VSPerfReport](../profiling/vsperfreport.md).  
  
### <a name="to-generate-an-etw-report"></a>Aby wygenerować raport ETW  
  
-   W **polecenia** oknie wpisz następujące polecenie w wierszu:  
  
     *ToolsPath* **VSPerfReport** *Plik_vsp* **/Summary: ETW [podsumowań w plikach]**  
  
    |||  
    |-|-|  
    |*ToolsPath*|Ścieżka narzędzia Profiling Tools. Aby uzyskać więcej informacji, zobacz [Określ ścieżkę do narzędzia wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|  
    |*Plik_vsp*|Dane profilowania (. *Vsp* lub. *vsps*) pliku. Akceptowane są pełne i częściowe ścieżki.|  
    |Xml|Generuje raport, który jest sformatowany w języku XML.|
