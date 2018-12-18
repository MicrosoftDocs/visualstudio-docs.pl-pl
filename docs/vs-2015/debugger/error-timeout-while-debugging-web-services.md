---
title: 'Błąd: Przekroczono limit czasu podczas debugowania usług sieci Web | Dokumentacja firmy Microsoft'
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
- debugger, Web application errors
- XML Web services, timeout while debugging
ms.assetid: 4b7df112-788a-4429-9a0c-4c6dac4fb609
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 985082d675da2a56d9880414809d91e92cb1fe0d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51736346"
---
# <a name="error-timeout-while-debugging-web-services"></a>Błąd: przekroczono limit czasu podczas debugowania usług sieci Web
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gdy są Wkraczanie do usługi sieci Web XML, z kodu wywołującego, wywołanie może czasami limit czasu, w wyniku możliwe, że nie można kontynuować debugowanie. Zobaczysz komunikat o błędzie, np. to.  
  
```  
An unhandled exception of type 'System.Net.WebException' occurred in   
system.Web.services.dll  
Additional information: The operation has timed-out.  
```  
  
## <a name="solution"></a>Rozwiązanie  
 Aby uniknąć tego problemu, należy ustawić wartość limitu czasu dla wywołania usługi sieci Web XML na wartość infinite, jak pokazano w poniższym przykładzie:  
  
```  
Service1 obj = new Service1();  
obj.TimeOut = -1; // infinite time out.  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie aplikacji internetowych: błędy i rozwiązywanie problemów](../debugger/debugging-web-applications-errors-and-troubleshooting.md)



