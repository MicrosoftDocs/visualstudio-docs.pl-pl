---
title: 'Instrukcje: debugowanie samohostowanej usługi WCF | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185179"
---
# <a name="how-to-debug-a-self-hosted-wcf-service"></a>Porady: debugowanie hostowania samoobsługowego WCF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*Samoobsługowa usługa* to usługa WCF, która nie działa w ramach usług IIS, hosta usługi WCF ani [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] serwera deweloperskiego. Najprostszym sposobem na Debugowanie samoobsługowego programu WCF jest skonfigurowanie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] uruchamiania klienta i serwera w przypadku wybrania opcji **Rozpocznij debugowanie** w menu **Debuguj** .  
  
 Jeśli usługa WCF jest w trakcie samodzielnego hostowania lub proces, którego nie można uruchomić w ten sposób, na przykład usługa NT, nie można użyć tej metody. Zamiast tego można wykonać jedną z następujących czynności:  
  
- Ręcznie Dołącz debuger do procesu hostingu. Aby uzyskać więcej informacji, zobacz [dołączanie do uruchomionych procesów](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
     oraz  
  
- Rozpocznij debugowanie klienta, a następnie przejdź do wywołania usługi. Wymaga to włączenia debugowania w pliku app.config. Aby uzyskać więcej informacji, [ograniczenia dotyczące debugowania WCF](../debugger/limitations-on-wcf-debugging.md).  
  
### <a name="to-start-both-client-and-host-from-visual-studio"></a>Aby uruchomić klienta i hosta z programu Visual Studio  
  
1. Utwórz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozwiązanie, które zawiera projekty klienta i serwera.  
  
2. Skonfiguruj rozwiązanie do uruchamiania procesów klienta i serwera, gdy wybierzesz pozycję **Rozpocznij** w menu **debugowanie** .  
  
    1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy nazwę rozwiązania.  
  
    2. Kliknij pozycję **Ustaw projekty startowe**.  
  
    3. W oknie **dialogowym \<name> Właściwości rozwiązania** wybierz **wiele projektów startowych**.  
  
    4. W siatce **wielu projektów startowych** , w wierszu, który odnosi się do projektu serwera, kliknij przycisk **Akcja** , a następnie wybierz pozycję **Uruchom**.  
  
    5. W wierszu, który odpowiada projektowi klienta, kliknij pozycję **Akcja** , a następnie wybierz pozycję **Uruchom**.  
  
    6. Kliknij przycisk **OK**.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie usług WCF](../debugger/debugging-wcf-services.md)   
 [Ograniczenia dotyczące debugowania WCF](../debugger/limitations-on-wcf-debugging.md)   
 [Instrukcje: przechodzenie do usług WCF](../debugger/how-to-step-into-wcf-services.md)
