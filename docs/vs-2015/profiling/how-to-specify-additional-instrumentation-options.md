---
title: 'Instrukcje: Określanie dodatkowych opcji Instrumentacji | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.property.advanced
helpviewer_keywords:
- instrumentation, options
- profiling tools, session options
- performance sessions, options
ms.assetid: 639afe26-8335-4bd4-8aa5-f2c607b81f07
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d4bc6eeb208ab6d80168431f110f0f6169abbc82
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63442134"
---
# <a name="how-to-specify-additional-instrumentation-options"></a>Instrukcje: Określanie dodatkowych opcji Instrumentacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możliwe jest instrumentowanie plików binarnych z [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] zintegrowanego środowiska programistycznego (IDE) lub za pomocą narzędzia wiersza polecenia. Jeśli Instrumentacji danych binarnych z poziomu środowiska IDE, możesz kontrolować ilość danych zebranych podczas instrumentacji, przez określenie dodatkowych opcji Instrumentacji do [VSInstr](../profiling/vsinstr.md) narzędzia. Te opcje są dostępne na poziomie docelowego lub sesji. Na przykład aby dołączyć lub wykluczyć określone funkcje w procesie instrumentacji, opcja dodatkowe Instrumentacji na poziomie docelowej.  
  
 **Wymagania**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
> [!IMPORTANT]
> Każdy sondowania, który jest wstawiany modyfikuje zachowanie oryginalnej programu nieco. Ta modyfikacja spowoduje, że obciążenie w czasie analizy. Mimo że przybliżeniem to obciążenie jest odejmowany, nadal ma skutki subtelne chronometrażu dla aplikacji wielowątkowych. [VSInstr](../profiling/vsinstr.md) narzędzie Pomoc opcji sterowanie zbieraniem danych podczas profilowania.  
  
### <a name="to-specify-additional-instrumentation-option"></a>Aby określić opcję dodatkowe Instrumentacji  
  
1. W **Eksplorator wydajności**, wybierz opcję **sesji wydajności** a następnie kliknij prawym przyciskiem myszy i wybierz **właściwości**.  
  
2. W **strony właściwości**, kliknij przycisk **zaawansowane** właściwości.  
  
3. Wpisz opcje w **dodatkowych opcji Instrumentacji** pole.  
  
     Na przykład użyć /CONTROL:THREAD, aby określić poziom profilowania. Aby uzyskać pełną listę opcji, zobacz [VSInstr](../profiling/vsinstr.md).  
  
4. Kliknij przycisk **OK**.  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)   
 [Profilowanie z wiersza polecenia](../profiling/using-the-profiling-tools-from-the-command-line.md)
