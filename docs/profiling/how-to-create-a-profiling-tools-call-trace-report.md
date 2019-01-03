---
title: 'Instrukcje: Tworzenie raportu śledzenia wywołań narzędzi profilowania | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- performance tools, viewing ETW data
- ETW [Visual Studio ALM], viewing data
ms.assetid: 7640520a-7d3c-456c-b184-872a5d2f82f3
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c2d48b266108a053fa24da517d2367fe85b2b6a6
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53985868"
---
# <a name="how-to-create-a-profiling-tools-call-trace-report"></a>Instrukcje: Tworzenie raportu śledzenia wywołań narzędzi profilowania
*Raport śledzenia wywołań* dla [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Profiling Tools Wyświetla listę informacji chronometrażu dla każdego punktu wejścia i wyjścia do funkcji w aplikacji oraz dla każdego wywołania innych funkcji przez funkcję. Raporty śledzenia wywołań są dostępne dla danych profilowania, tylko wtedy, gdy zostały one pobrane metodą instrumentacji.  
  
> [!NOTE]
>  Nie można wyświetlić raportów śledzenia wywołań w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Należy użyć **VSPerfReport** narzędzie wiersza polecenia do generowania wartości rozdzielanych przecinkami (. *CSV*) lub. *xml* pliku. Aby uzyskać więcej informacji o tym narzędziu, zobacz [VSPerfReport](../profiling/vsperfreport.md).  
  
### <a name="to-create-a-call-trace-report"></a>Aby utworzyć raport śledzenia wywołań  
  
1.  Otwórz **polecenia** okna.  
  
2.  W wierszu polecenia wpisz następujące polecenie:  
  
     *ToolsPath* **VSPerfReport** *Plik_vsp* **/calltrace [podsumowań w plikach]**  
  
    |||  
    |-|-|  
    |*ToolsPath*|Ścieżka narzędzi wiersza poleceń Profiling Tools. Aby uzyskać więcej informacji, zobacz [Określ ścieżkę do narzędzia wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|  
    |*Plik_vsp*|Dane profilowania (. *Vsp* lub. *vsps*) pliku. Akceptowane są pełne i częściowe ścieżki.|  
    |Xml|Generuje raport w formacie XML.|  

  
## <a name="see-also"></a>Zobacz także  
 [Instrukcje: Zbieraj dane zdarzenia śledzenia dla Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)   
 [Interfejsy API narzędzi profilowania](../profiling/profiling-tools-apis.md)
