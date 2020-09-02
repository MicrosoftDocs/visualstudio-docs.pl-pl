---
title: Debuger Microsoft Visual Studio (zgłoszony wyjątek) — okno dialogowe | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.exceptions.thrown
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Microsoft Visual Studio Debugger (Exception Thrown) dialog box
- exception handling, during debugging
- debugger, exceptions
- throwing exceptions, during debugging
ms.assetid: 1fe98d10-c8f9-4b39-a920-99169bfd542e
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9062b1f3811b0b2b596cfb7fa016bca00143f332
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "66261068"
---
# <a name="microsoft-visual-studio-debugger-exception-thrown-dialog-box"></a>Microsoft Visual Studio Debugger (wystąpienie wyjątku) ― okno dialogowe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W programie wystąpił wyjątek. To okno dialogowe służy do zgłaszania rodzaju zgłoszonego wyjątku. Kod musi obsłużyć ten wyjątek. Można wybrać jedną z następujących opcji obsługi wyjątku:  
  
 **Przerwij**  
 Zezwala na wykonanie przerwania w debugerze. Procedura obsługi wyjątków nie jest wywoływana przed przerwaniem. W przypadku kontynuowania od przerwy zostanie wywołana procedura obsługi wyjątków.  
  
 **Kontynuuj**  
 Umożliwia kontynuowanie wykonywania, dając programowi obsługi wyjątków szansę obsługi wyjątku. Ta opcja jest niedostępna w przypadku niektórych typów wyjątków. Wartość **Kontynuuj** umożliwi kontynuowanie działania aplikacji. W aplikacji natywnej spowoduje to, że wyjątek zostanie ponownie wygenerowany. W aplikacji zarządzanej spowoduje to przerwanie działania programu lub wyjątek, który ma być obsługiwany przez aplikację hostingu.  
  
> [!NOTE]
> Nie można kontynuować po nieobsługiwanym wyjątku w kodzie zarządzanym. Wybranie opcji **Kontynuuj** po nieobsługiwanym wyjątku w kodzie zarządzanym powoduje zatrzymanie debugowania.  
  
 **Ignoruj**  
 Umożliwia kontynuowanie wykonywania bez wywoływania procedury obsługi wyjątków. Ponieważ program obsługi wyjątków nie jest wywoływany, może to prowadzić do dalszych konsekwencji, w tym dodatkowych wyjątków i błędów. Ta opcja jest niedostępna w przypadku niektórych typów wyjątków.  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie wyjątkami za pomocą debugera](../debugger/managing-exceptions-with-the-debugger.md)   
 [Najlepsze rozwiązania dotyczące wyjątków](https://msdn.microsoft.com/library/f06da765-235b-427a-bfb6-47cd219af539)   
 [Obsługa wyjątków](/cpp/extensions/exception-handling-cpp-component-extensions)
