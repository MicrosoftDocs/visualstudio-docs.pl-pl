---
title: 'Instrukcje: przechodzenie do usług WCF | Microsoft Docs'
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
- WCF, debugging
ms.assetid: 9893ad01-54af-499f-85a6-9d1cfe6eb640
caps.latest.revision: 27
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 951d5f39fbf3929d094cc18de5fe108b46753b09
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68176528"
---
# <a name="how-to-step-into-wcf-services"></a>Porady: usługi WCF krok po kroku
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W programie możesz [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] przejść do usługi WCF. Jeśli usługa WCF jest w tym samym [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozwiązaniu co klient, można trafić punkty przerwania wewnątrz usługi WCF.  
  
 Aby przechodzenie do pracy, musisz mieć włączone debugowanie w pliku app.config lub Web.config. Aby uzyskać informacje na temat włączania debugowania i ograniczeń dotyczących przechodzenia do usług WCF, zobacz [ograniczenia dotyczące debugowania WCF](../debugger/limitations-on-wcf-debugging.md).  
  
### <a name="to-step-into-a-wcf-service"></a>Aby przejść do usługi WCF  
  
1. Utwórz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozwiązanie, które zawiera zarówno klienta programu WCF, jak i projekty usług WCF.  
  
2. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt klienta WCF, a następnie kliknij pozycję **Ustaw jako projekt startowy**.  
  
3. Włącz debugowanie w pliku app.config lub web.config. Aby uzyskać więcej informacji, zobacz [ograniczenia dotyczące debugowania WCF](../debugger/limitations-on-wcf-debugging.md).  
  
4. Ustaw punkt przerwania w lokalizacji w projekcie klienta, w której chcesz rozpocząć krokowe wykonywanie kroków. Zwykle jest to przed wywołaniem usługi WCF.  
  
5. Uruchom polecenie do punktu przerwania, a następnie zacznij krokowe. Debuger rozpocznie automatyczne przechodzenie do usługi.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie usług WCF](../debugger/debugging-wcf-services.md)   
 [Ograniczenia dotyczące debugowania WCF](../debugger/limitations-on-wcf-debugging.md)   
 [Instrukcje: debugowanie hostowanej samodzielnie usługi WCF](../debugger/how-to-debug-a-self-hosted-wcf-service.md)
