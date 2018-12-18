---
title: Microsoft Visual Studio Debugger (wystąpienie wyjątku), okno dialogowe | Dokumentacja firmy Microsoft
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.exceptions.thrown
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Microsoft Visual Studio Debugger (Exception Thrown) dialog box
- exception handling, during debugging
- debugger, exceptions
- throwing exceptions, during debugging
ms.assetid: 1fe98d10-c8f9-4b39-a920-99169bfd542e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5609f87063d3b2852b6a45f7174cfd3db90a1ccd
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53062735"
---
# <a name="microsoft-visual-studio-debugger-exception-thrown-dialog-box"></a>Microsoft Visual Studio Debugger (wystąpienie wyjątku) ― okno dialogowe
Wystąpił wyjątek w programach. To okno dialogowe Raporty rodzaj zgłaszanego wyjątku. Twój kod musi do obsługi tego wyjątku. Można wybrać jedną z następujących opcji do obsługi wyjątku:  
  
 **BREAK**  
 Zezwala na wykonywanie przerwać działanie debugera. Obsługa wyjątków nie jest wywoływany przed przerwy. Jeśli będziesz kontynuować z przerwy, zostanie wywołany program obsługi wyjątków.  
  
 **Continue**  
 Umożliwia wykonywanie kontynuować, dzięki czemu program obsługi wyjątków szansę, aby obsłużyć wyjątek. Ta opcja nie jest dostępna dla niektórych rodzajów wyjątków. **Kontynuuj** umożliwi aplikacji, aby kontynuować. W aplikacji macierzystej spowoduje wyjątek jest zgłaszany ponownie. W zarządzanej aplikacji albo spowoduje się program, aby zakończyć lub wyjątku, które mają być obsługiwane przez hostingu aplikacji.  
  
> [!NOTE]
>  Nie możesz kontynuować po wystąpieniu nieobsługiwanego wyjątku w kodzie zarządzanym. Wybieranie **Kontynuuj** po nieobsługiwany wyjątek w kodzie zarządzanym powoduje zatrzymanie debugowania.  
  
 **Ignoruj**  
 Zezwala na wykonywanie kontynuować bez wywoływania programu obsługi wyjątków. Ponieważ nie zostanie wywołany program obsługi wyjątków, może to prowadzić do dalsze konsekwencje, uwzględniając dodatkowe wyjątki i błędy. Ta opcja nie jest dostępna dla niektórych rodzajów wyjątków.  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie wyjątkami za pomocą debugera](../debugger/managing-exceptions-with-the-debugger.md)   
 [Najlepsze praktyki dotyczące wyjątków](/dotnet/standard/exceptions/best-practices-for-exceptions)   
 [Obsługa wyjątków](/cpp/windows/exception-handling-cpp-component-extensions)