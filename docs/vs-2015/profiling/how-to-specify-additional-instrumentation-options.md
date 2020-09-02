---
title: 'Instrukcje: Określanie dodatkowych opcji instrumentacji | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64794731"
---
# <a name="how-to-specify-additional-instrumentation-options"></a>Porady: określanie dodatkowych opcji instrumentacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pliki binarne można instrumentować za [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] pomocą zintegrowanego środowiska programistycznego (IDE) lub narzędzia wiersza polecenia. W przypadku Instrumentacji pliku binarnego z poziomu IDE można kontrolować ilość danych zbieranych w ramach usługi Instrumentation, określając dodatkowe opcje Instrumentacji dla narzędzia [VSInstr](../profiling/vsinstr.md) . Te opcje są dostępne w sesji lub na poziomie docelowym. Na przykład aby dołączyć lub wykluczyć określone funkcje podczas procesu instrumentacji, użyj opcji dodatkowe Instrumentacja na poziomie docelowym.  
  
 **Wymagania**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
> [!IMPORTANT]
> Każda sonda, która jest wstawiana modyfikuje zachowanie oryginalnego programu. Ta modyfikacja powoduje obciążenie w czasie analizy. Nawet w przypadku odejmowania zbliżania się tego kosztu, nadal ma delikatne efekty chronometrażu w aplikacjach wielowątkowych. Opcje narzędzia [VSInstr](../profiling/vsinstr.md) ułatwiają kontrolowanie zbierania danych podczas profilowania.  
  
### <a name="to-specify-additional-instrumentation-option"></a>Aby określić dodatkową instrumentację  
  
1. W **Eksplorator wydajności**wybierz **sesję wydajności** , a następnie kliknij prawym przyciskiem myszy i wybierz pozycję **Właściwości**.  
  
2. Na **stronie właściwości**kliknij pozycję **Zaawansowane** właściwości.  
  
3. Wpisz opcje w polu **dodatkowe opcje Instrumentacji** .  
  
     Na przykład użyj/CONTROL: THREAD, aby określić poziom profilowania. Aby uzyskać pełną listę opcji, zobacz [VSInstr](../profiling/vsinstr.md).  
  
4. Kliknij przycisk **OK**.  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)   
 [Profilowanie z wiersza polecenia](../profiling/using-the-profiling-tools-from-the-command-line.md)
