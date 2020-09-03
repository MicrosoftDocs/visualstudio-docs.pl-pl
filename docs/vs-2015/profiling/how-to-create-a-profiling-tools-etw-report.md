---
title: 'Instrukcje: Tworzenie raportu ETW narzędzia profilowania | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: bf5547b3-f6c7-4989-9d47-2fe4f1261444
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7dc74f0486ac7196cf406994ee603bc6c0cf4c25
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85548008"
---
# <a name="how-to-create-a-profiling-tools-etw-report"></a>Porady: tworzenie raportu ETW narzędzi profilowania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Raport śledzenie zdarzeń systemu Windows (ETW) zawiera listę zdarzeń ETW, które są rejestrowane w sesji wydajności [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] narzędzia profilowania. Dane ETW są zbierane w pliku binarnym (. etl). Aby uzyskać więcej informacji na temat tego raportu, zobacz [raport śledzenia zdarzeń dla systemu Windows (ETW)](../profiling/event-tracing-for-windows-etw-report.md).  
  
> [!NOTE]
> W interfejsie nie można wyświetlać raportów ETW [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
- Informacje o sposobie zbierania danych ETW przy użyciu interfejsu dla programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] znajdują się w temacie [How to: zbierać dane śledzenia zdarzeń dla systemu Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md).  
  
- Informacje o sposobie zbierania danych ETW z wiersza polecenia można znaleźć w temacie [VSPerfCmd](../profiling/vsperfcmd.md) and [Events (zdarzenia](../profiling/events-vsperfcmd.md)).  
  
  Raport ETW jest generowany przy użyciu polecenia **VSReport/Summary: ETW** . Plik. etl, który zawiera dane funkcji ETW, musi znajdować się w tym samym katalogu, który jest plikiem danych profilowania (. vsp lub. vsps). Domyślnie raport jest generowany jako plik z wartościami rozdzielanymi przecinkami (CSV). Aby uzyskać więcej informacji, zobacz [VSPerfReport](../profiling/vsperfreport.md).  
  
### <a name="to-generate-an-etw-report"></a>Aby wygenerować raport ETW  
  
- W oknie **wiersza polecenia** wpisz w wierszu polecenia następujący tekst:  
  
     *ToolsPath* **VSPerfReport** *VSPFile*  **/Summary: ETW [/XML]**  
  
    |Element polecenia|Opis|  
    |-|-|  
    |*ToolsPath*|Ścieżka narzędzia narzędzia profilowania. Aby uzyskać więcej informacji, zobacz [Określanie ścieżki do narzędzi wiersza polecenia](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).|  
    |*VSPFile*|Plik danych profilowania (. vsp lub. vsps). Akceptowane są pełne i częściowe ścieżki.|  
    |Xml|Generuje raport sformatowany w formacie XML.|
