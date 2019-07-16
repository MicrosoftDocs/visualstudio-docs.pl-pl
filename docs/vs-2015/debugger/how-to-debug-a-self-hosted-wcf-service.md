---
title: 'Instrukcje: Debugowanie hostowania samoobsługowego WCF usługi | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging, WCF
- WCF, self-hosted service
- WCF, debugging
ms.assetid: 288922be-ba3f-411e-af50-bba39c9529cc
caps.latest.revision: 28
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e58acc6323f396f9b0755e84b369ce0fdf413c08
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68185179"
---
# <a name="how-to-debug-a-self-hosted-wcf-service"></a>Instrukcje: Debugowanie samodzielnie hostowanej usługi WCF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A *usługi hosta samodzielnego* to usługa WCF, która nie jest uruchamiane w usługach IIS, Host usługi WCF, lub [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] serwera projektowego. Najprostszym sposobem na debugowanie hostowania samoobsługowego WCF jest skonfigurowanie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] do uruchomienia klienta i serwera, po wybraniu **Rozpocznij debugowanie** na **debugowania** menu.  
  
 Jeśli usługa WCF jest hostingu samodzielnego wewnątrz, czy Proces, który nie można uruchomić w ten sposób, takich jak usługa NT nie można użyć tej metody. Zamiast tego możesz wykonać jedną z następujących czynności:  
  
- Ręcznie dołączyć debuger do procesu hostingu. Aby uzyskać więcej informacji, zobacz [dołączenia do uruchamiania procesów](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
     — lub —  
  
- Rozpocznij debugowanie klienta, a następnie wejdź do wywołań do usługi. Ta migracja wymaga włączenia debugowania w pliku app.config. Aby uzyskać więcej informacji [ograniczenia debugowania WCF](../debugger/limitations-on-wcf-debugging.md).  
  
### <a name="to-start-both-client-and-host-from-visual-studio"></a>Można uruchomić zarówno klient, jak i hosta w programie Visual Studio  
  
1. Utwórz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozwiązania zawierającego projekty zarówno klient, jak i serwera.  
  
2. Konfigurowanie rozwiązania do uruchamiania procesów klienta i serwera, po wybraniu **Start** na **debugowania** menu.  
  
    1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nazwę rozwiązania.  
  
    2. Kliknij przycisk **Ustaw projekty startowe**.  
  
    3. W **rozwiązania \<name > właściwości** okno dialogowe, wybierz opcję **wiele projektów startowych**.  
  
    4. W **wiele projektów startowych** siatki w wierszu, który odnosi się do projektu serwera, kliknij przycisk **akcji** i wybierz polecenie **Start**.  
  
    5. W wierszu, który odnosi się do projektu klienta, kliknij przycisk **akcji** i wybierz polecenie **Start**.  
  
    6. Kliknij przycisk **OK**.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie usług WCF](../debugger/debugging-wcf-services.md)   
 [Ograniczenia debugowania WCF](../debugger/limitations-on-wcf-debugging.md)   
 [Instrukcje: Przechodzenie do usług WCF](../debugger/how-to-step-into-wcf-services.md)
