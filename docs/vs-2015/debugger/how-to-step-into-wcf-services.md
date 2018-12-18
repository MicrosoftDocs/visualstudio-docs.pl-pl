---
title: 'Porady: przechodzenie do usług WCF | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: 7474626ccf5310faf5fc22c6323dc388dd20461d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51798082"
---
# <a name="how-to-step-into-wcf-services"></a>Porady: usługi WCF krok po kroku
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], możesz wejść do usługi WCF. Jeśli usługa WCF jest w tej samej [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozwiązania jako klienta, można identyfikować punkty przerwania wewnątrz usługi WCF.  
  
 Do przechodzenia do pracy, konieczne jest posiadanie debugowanie włączone w pliku Web.config lub app.config. Aby uzyskać informacje o tym, jak włączyć debugowanie i ograniczeń dotyczących Przechodzenie do usług WCF, zobacz [ograniczenia debugowania WCF](../debugger/limitations-on-wcf-debugging.md).  
  
### <a name="to-step-into-a-wcf-service"></a>Aby wkraczać do usługi WCF  
  
1.  Utwórz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozwiązanie, które zawiera klienta programu WCF i projekty usługi WCF.  
  
2.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt klienta WCF, a następnie kliknij przycisk **Ustaw jako projekt startowy**.  
  
3.  Włącz debugowanie w pliku app.config lub web.config. Aby uzyskać więcej informacji, zobacz [ograniczenia debugowania WCF](../debugger/limitations-on-wcf-debugging.md).  
  
4.  Ustaw punkt przerwania w lokalizacji w projekt klienta, w którym chcesz rozpocząć przechodzenie krok po kroku. Zazwyczaj są to po prostu przed wywołaniem usługi WCF.  
  
5.  Uruchom do punktu przerwania, a następnie rozpocząć przechodzenie krok po kroku. Debuger przechodzi do usługi automatycznie.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie usług WCF](../debugger/debugging-wcf-services.md)   
 [Ograniczenia debugowania WCF](../debugger/limitations-on-wcf-debugging.md)   
 [Instrukcje: debugowanie hostowanej samodzielnie usługi WCF](../debugger/how-to-debug-a-self-hosted-wcf-service.md)



