---
title: 'Instrukcje: Tworzenie raportu śledzenia wywołań narzędzi profilowania | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, viewing ETW data
- ETW [Visual Studio ALM], viewing data
ms.assetid: 7640520a-7d3c-456c-b184-872a5d2f82f3
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c92f5cd8f268b249e8f29ddd706860ff18b2f87c
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60117827"
---
# <a name="how-to-create-a-profiling-tools-call-trace-report"></a>Instrukcje: Tworzenie raportu śledzenia wywołań narzędzi profilowania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*Raport śledzenia wywołań* dla [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Profiling Tools Wyświetla listę informacji chronometrażu dla każdego punktu wejścia i wyjścia do funkcji w aplikacji oraz dla każdego wywołania innych funkcji przez funkcję. Raporty śledzenia wywołań są dostępne dla danych profilowania, tylko wtedy, gdy zostały one pobrane metodą instrumentacji.  
  
> [!NOTE]
>  Nie można wyświetlić raportów śledzenia wywołań w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Należy użyć **VSPerfReport** narzędzie wiersza polecenia do generowania wartości rozdzielanych przecinkami (.csv) lub plik Xml. Aby uzyskać więcej informacji o tym narzędziu, zobacz [VSPerfReport](../profiling/vsperfreport.md).  
  
### <a name="to-create-a-call-trace-report"></a>Aby utworzyć raport śledzenia wywołań  
  
1. Otwórz **polecenia**okno.  
  
2. W wierszu polecenia wpisz następujące polecenie:  
  
     *ToolsPath* **VSPerfReport** *VSPFile*  **/CallTrace [/Xml]**  
  
    |||  
    |-|-|  
    |*ToolsPath*|Ścieżka narzędzi wiersza polecenia Profiling Tools. Aby uzyskać więcej informacji, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|  
    |*VSPFile*|Plik danych profilowania (.vsp lub .vsps). Akceptowane są pełne i częściowe ścieżki.|  
    |Xml|Generuje raport w formacie Xml.|  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: Zbieraj zdarzenia śledzenia dla Windows (ETW) danych](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)   
 [Interfejsy API narzędzi profilowania](../profiling/profiling-tools-apis.md)
