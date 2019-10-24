---
title: 'Instrukcje: debugowanie samohostowanej usługi WCF | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging, WCF
- WCF, self-hosted service
- WCF, debugging
ms.assetid: 288922be-ba3f-411e-af50-bba39c9529cc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 12654a6aa1abb34c9813e8d29c7608814021a3f0
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72733980"
---
# <a name="how-to-debug-a-self-hosted-wcf-service"></a>Porady: debugowanie hostowania samoobsługowego WCF
*Samoobsługowa usługa* to usługa WCF, która nie działa w ramach usług IIS, hosta usługi WCF ani [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] serwera deweloperskiego. Najprostszym sposobem na Debugowanie samohostowanego programu WCF jest skonfigurowanie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] uruchamiania klienta i serwera w przypadku wybrania opcji **Rozpocznij debugowanie** w menu **Debuguj** .

 Jeśli usługa WCF jest w trakcie samodzielnego hostowania lub proces, którego nie można uruchomić w ten sposób, na przykład usługa NT, nie można użyć tej metody. Zamiast tego można wykonać jedną z następujących czynności:

- Ręcznie Dołącz debuger do procesu hostingu. Aby uzyskać więcej informacji, zobacz [dołączanie do uruchomionych procesów](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

     oraz

- Rozpocznij debugowanie klienta, a następnie przejdź do wywołania usługi. Wymaga to włączenia debugowania w pliku App. config. Aby uzyskać więcej informacji, [ograniczenia dotyczące debugowania WCF](../debugger/limitations-on-wcf-debugging.md).

### <a name="to-start-both-client-and-host-from-visual-studio"></a>Aby uruchomić klienta i hosta z programu Visual Studio

1. Utwórz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] rozwiązanie, które zawiera zarówno projekty klienta, jak i serwera.

2. Skonfiguruj rozwiązanie do uruchamiania procesów klienta i serwera, gdy wybierzesz pozycję **Rozpocznij** w menu **debugowanie** .

   1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy nazwę rozwiązania.

   2. Kliknij pozycję **Ustaw projekty startowe**.

   3. W oknie dialogowym **\<name rozwiązania > właściwości** wybierz **wiele projektów startowych**.

   4. W siatce **wielu projektów startowych** , w wierszu, który odnosi się do projektu serwera, kliknij przycisk **Akcja** , a następnie wybierz pozycję **Uruchom**.

   5. W wierszu, który odpowiada projektowi klienta, kliknij pozycję **Akcja** , a następnie wybierz pozycję **Uruchom**.

   6. Kliknij przycisk **OK**.

## <a name="see-also"></a>Zobacz także
- [Debugowanie usług WCF](../debugger/debugging-wcf-services.md)
- [Ograniczenia dotyczące debugowania usług WCF](../debugger/limitations-on-wcf-debugging.md)
- [Instrukcje: przechodzenie do usług WCF](../debugger/how-to-step-into-wcf-services.md)