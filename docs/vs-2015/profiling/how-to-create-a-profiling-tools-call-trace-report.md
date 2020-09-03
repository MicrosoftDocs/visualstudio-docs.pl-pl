---
title: 'Instrukcje: Tworzenie raportu śledzenia wywołań narzędzia profilowania | Microsoft Docs'
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
ms.openlocfilehash: fbf92b38f9408455e10048fbd4a5e84fdf822ea2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547995"
---
# <a name="how-to-create-a-profiling-tools-call-trace-report"></a>Porady: tworzenie raportu śledzenia wywołań narzędzi profilowania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*Raport śledzenia wywołań* dla [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] narzędzia profilowania wyświetla informacje o chronometrażu dla każdego wpisu i punktu wyjścia do funkcji aplikacji oraz każde wywołanie funkcji przez funkcję. Raporty śledzenia wywołań są dostępne do profilowania danych tylko wtedy, gdy zostały zebrane przy użyciu metody instrumentacji.  
  
> [!NOTE]
> Nie można wyświetlić raportów śledzenia wywołań w programie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Aby wygenerować plik z wartościami rozdzielanymi przecinkami (CSV) lub XML, należy użyć narzędzia wiersza polecenia **VSPerfReport** . Aby uzyskać więcej informacji na temat tego narzędzia, zobacz [VSPerfReport](../profiling/vsperfreport.md).  
  
### <a name="to-create-a-call-trace-report"></a>Aby utworzyć raport śledzenia wywołań  
  
1. Otwórz okno **wiersza polecenia**iersz.  
  
2. W wierszu polecenia wpisz następujące polecenie:  
  
     *ToolsPath* **VSPerfReport** *VSPFile*  **/CallTrace [/XML]**  
  
    |Element polecenia|Opis|
    |-|-|  
    |*ToolsPath*|Ścieżka narzędzia profilowania narzędzi wiersza polecenia. Aby uzyskać więcej informacji, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|  
    |*VSPFile*|Plik danych profilowania (. vsp lub. vsps). Akceptowane są pełne i częściowe ścieżki.|  
    |Xml|Generuje raport w formacie XML.|  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: zbieranie danych śledzenia zdarzeń dla systemu Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)   
 [Interfejsy API narzędzi profilowania](../profiling/profiling-tools-apis.md)
