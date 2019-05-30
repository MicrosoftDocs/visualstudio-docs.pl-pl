---
title: Microsoft Visual Studio Debugger (wystąpienie wyjątku), okno dialogowe | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/28/2019
ms.locfileid: "66261068"
---
# <a name="microsoft-visual-studio-debugger-exception-thrown-dialog-box"></a>Microsoft Visual Studio Debugger (wystąpienie wyjątku) ― okno dialogowe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wystąpił wyjątek w programach. To okno dialogowe Raporty rodzaj zgłaszanego wyjątku. Twój kod musi do obsługi tego wyjątku. Można wybrać jedną z następujących opcji do obsługi wyjątku:  
  
 **BREAK**  
 Zezwala na wykonywanie przerwać działanie debugera. Obsługa wyjątków nie jest wywoływany przed przerwy. Jeśli będziesz kontynuować z przerwy, zostanie wywołany program obsługi wyjątków.  
  
 **Continue**  
 Umożliwia wykonywanie kontynuować, dzięki czemu program obsługi wyjątków szansę, aby obsłużyć wyjątek. Ta opcja nie jest dostępna dla niektórych rodzajów wyjątków. **Kontynuuj** umożliwi aplikacji, aby kontynuować. W aplikacji macierzystej spowoduje wyjątek jest zgłaszany ponownie. W zarządzanej aplikacji albo spowoduje się program, aby zakończyć lub wyjątku, które mają być obsługiwane przez hostingu aplikacji.  
  
> [!NOTE]
> Nie możesz kontynuować po wystąpieniu nieobsługiwanego wyjątku w kodzie zarządzanym. Wybieranie **Kontynuuj** po nieobsługiwany wyjątek w kodzie zarządzanym powoduje zatrzymanie debugowania.  
  
 **Ignoruj**  
 Zezwala na wykonywanie kontynuować bez wywoływania programu obsługi wyjątków. Ponieważ nie zostanie wywołany program obsługi wyjątków, może to prowadzić do dalsze konsekwencje, uwzględniając dodatkowe wyjątki i błędy. Ta opcja nie jest dostępna dla niektórych rodzajów wyjątków.  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie wyjątkami za pomocą debugera](../debugger/managing-exceptions-with-the-debugger.md)   
 [Najlepsze praktyki dotyczące wyjątków](https://msdn.microsoft.com/library/f06da765-235b-427a-bfb6-47cd219af539)   
 [Obsługa wyjątków](/cpp/extensions/exception-handling-cpp-component-extensions)
