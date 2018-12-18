---
title: 'Porady: Tworzenie raportu śledzenia wywołań narzędzi profilowania | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
ms.openlocfilehash: a363554dfab8463ed91a82ffae9dea4f52d435d4
ms.sourcegitcommit: 1b9c1e333c2f096d35cfc77e846116f8e5054557
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2018
ms.locfileid: "34815733"
---
# <a name="how-to-create-a-profiling-tools-call-trace-report"></a>Porady: Tworzenie raportu śledzenia wywołań narzędzi profilowania
*Raportu śledzenia wywołań* dla [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzia profilowania Wyświetla informacje o chronometrażu dla każdego punktu wejścia i wyjścia funkcji aplikacji i każde wywołanie innych funkcji w funkcji. Wywołanie śledzenia raporty są dostępne dla danych profilowania tylko wtedy, gdy został zebrany przy użyciu metody instrumentacji.  
  
> [!NOTE]
>  Nie można wyświetlić raportów śledzenia wywołań w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Należy użyć **VSPerfReport** narzędzia wiersza polecenia do generowania wartości rozdzielanych przecinkami (. *CSV*) lub. *xml* pliku. Aby uzyskać więcej informacji o tym narzędziu, zobacz [VSPerfReport](../profiling/vsperfreport.md).  
  
### <a name="to-create-a-call-trace-report"></a>Aby utworzyć raportu śledzenia wywołań  
  
1.  Otwórz **wiersza polecenia** okna.  
  
2.  W wierszu polecenia wpisz następujące polecenie:  
  
     *ToolsPath* **VSPerfReport** *Plik_vsp*  **/calltrace [XML]**  
  
    |||  
    |-|-|  
    |*ToolsPath*|Ścieżka narzędzia wiersza polecenia narzędzi profilowania. Aby uzyskać więcej informacji, zobacz [Określ ścieżkę do narzędzia wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|  
    |*Plik_vsp*|Dane profilowania (. *Vsp* lub. *vsps*) pliku. Ścieżki pełne i częściowe są akceptowane.|  
    |Xml|Generuje raport w formacie XML.|  

  
## <a name="see-also"></a>Zobacz także  
 [Porady: zbieranie danych funkcji Śledzenie zdarzeń systemu Windows ()](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)   
 [Interfejsy API narzędzi profilowania](../profiling/profiling-tools-apis.md)
