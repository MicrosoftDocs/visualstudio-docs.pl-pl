---
title: Przejdź do usług WCF | Microsoft Docs
description: Wkrocz do usługi Windows Communication Foundation (WCF). Jeśli znajduje się w tym samym rozwiązaniu programu Visual Studio, co klient, trafij punkty przerwania wewnątrz usługi WCF.
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
- WCF, debugging
ms.assetid: 9893ad01-54af-499f-85a6-9d1cfe6eb640
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 428f5576b595797605abff2ebc5f4669e2927389
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150733"
---
# <a name="how-to-step-into-wcf-services"></a>Porady: usługi WCF krok po kroku
W programie możesz [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] przejść do usługi WCF. Jeśli usługa WCF jest w tym samym [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] rozwiązaniu co klient, można trafić punkty przerwania wewnątrz usługi WCF.

 Aby przechodzenie do pracy, musisz mieć włączone debugowanie w pliku app.config lub Web.config. Aby uzyskać informacje na temat włączania debugowania i ograniczeń dotyczących przechodzenia do usług WCF, zobacz [ograniczenia dotyczące debugowania WCF](../debugger/limitations-on-wcf-debugging.md).

### <a name="to-step-into-a-wcf-service"></a>Aby przejść do usługi WCF

1. Utwórz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] rozwiązanie, które zawiera zarówno klienta programu WCF, jak i projekty usług WCF.

2. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt klienta WCF, a następnie kliknij pozycję **Ustaw jako projekt startowy**.

3. Włącz debugowanie w pliku app.config lub web.config. Aby uzyskać więcej informacji, zobacz [ograniczenia dotyczące debugowania WCF](../debugger/limitations-on-wcf-debugging.md).

4. Ustaw punkt przerwania w lokalizacji w projekcie klienta, w której chcesz rozpocząć krokowe wykonywanie kroków. Zwykle jest to przed wywołaniem usługi WCF.

5. Uruchom polecenie do punktu przerwania, a następnie zacznij krokowe. Debuger rozpocznie automatyczne przechodzenie do usługi.

## <a name="see-also"></a>Zobacz także
- [Debugowanie usług WCF](../debugger/debugging-wcf-services.md)
- [Ograniczenia dotyczące debugowania WCF](../debugger/limitations-on-wcf-debugging.md)
- [Instrukcje: debugowanie hostowanej samodzielnie usługi WCF](../debugger/how-to-debug-a-self-hosted-wcf-service.md)