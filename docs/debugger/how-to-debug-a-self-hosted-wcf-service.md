---
title: Debugowanie Self-Hosted usługi WCF | Microsoft Docs
Description: Dowiedz się, jak debugować samodzielną usługę WCF. Najprostszym sposobem (ale nie zawsze jest możliwe) jest skonfigurowanie programu Visual Studio do uruchamiania klienta i serwera.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2edcf359bd54774647ff1a5957d741fec25b60a9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99915809"
---
# <a name="how-to-debug-a-self-hosted-wcf-service"></a>Porady: debugowanie hostowania samoobsługowego WCF
*Samoobsługowa usługa* to usługa WCF, która nie działa w ramach usług IIS, hosta usługi WCF ani [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] serwera deweloperskiego. Najprostszym sposobem na Debugowanie samoobsługowego programu WCF jest skonfigurowanie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] uruchamiania klienta i serwera w przypadku wybrania opcji **Rozpocznij debugowanie** w menu **Debuguj** .

 Jeśli usługa WCF jest w trakcie samodzielnego hostowania lub proces, którego nie można uruchomić w ten sposób, na przykład usługa NT, nie można użyć tej metody. Zamiast tego można wykonać jedną z następujących czynności:

- Ręcznie Dołącz debuger do procesu hostingu. Aby uzyskać więcej informacji, zobacz [dołączanie do uruchomionych procesów](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

     oraz

- Rozpocznij debugowanie klienta, a następnie przejdź do wywołania usługi. Wymaga to włączenia debugowania w pliku app.config. Aby uzyskać więcej informacji, [ograniczenia dotyczące debugowania WCF](../debugger/limitations-on-wcf-debugging.md).

### <a name="to-start-both-client-and-host-from-visual-studio"></a>Aby uruchomić klienta i hosta z programu Visual Studio

1. Utwórz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] rozwiązanie, które zawiera projekty klienta i serwera.

2. Skonfiguruj rozwiązanie do uruchamiania procesów klienta i serwera, gdy wybierzesz pozycję **Rozpocznij** w menu **debugowanie** .

   1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy nazwę rozwiązania.

   2. Kliknij pozycję **Ustaw projekty startowe**.

   3. W oknie **dialogowym \<name> Właściwości rozwiązania** wybierz **wiele projektów startowych**.

   4. W siatce **wielu projektów startowych** , w wierszu, który odnosi się do projektu serwera, kliknij przycisk **Akcja** , a następnie wybierz pozycję **Uruchom**.

   5. W wierszu, który odpowiada projektowi klienta, kliknij pozycję **Akcja** , a następnie wybierz pozycję **Uruchom**.

   6. Kliknij przycisk **OK**.

## <a name="see-also"></a>Zobacz też
- [Debugowanie usług WCF](../debugger/debugging-wcf-services.md)
- [Ograniczenia dotyczące debugowania WCF](../debugger/limitations-on-wcf-debugging.md)
- [Instrukcje: przechodzenie do usług WCF](../debugger/how-to-step-into-wcf-services.md)