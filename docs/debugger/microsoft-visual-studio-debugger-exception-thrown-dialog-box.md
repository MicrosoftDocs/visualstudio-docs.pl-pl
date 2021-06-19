---
title: Microsoft Visual Studio dialogowe Debuger (zgłaszany wyjątek) | Microsoft Docs
titleSuffix: ''
description: 'Dowiedz się, co należy zrobić, gdy wystąpi wyjątek, który musi obsłużyć program. Możesz: 1) włamać się do debugera; 2) kontynuować; lub 3) zignoruj.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c7a4b92a3ec5c6876fae3054b692ff46f26e82cd
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387050"
---
# <a name="microsoft-visual-studio-debugger-exception-thrown-dialog-box"></a>Microsoft Visual Studio Debugger (wystąpienie wyjątku) ― okno dialogowe
Wystąpił wyjątek w programie. To okno dialogowe zgłasza rodzaj zgłoszonego wyjątku. Kod musi obsługiwać ten wyjątek. Do obsługi wyjątku można wybrać jedną z następujących opcji:

 **Przerwij** Umożliwia wykonanie włamanie do debugera. Program obsługi wyjątków nie jest wywoływany przed przerwą. Jeśli będziesz kontynuować pracę po przerwie, zostanie wywołana procedura obsługi wyjątków.

 **Kontynuuj** Umożliwia kontynuowanie wykonywania, dając programowi obsługi wyjątków możliwość obsługi wyjątku. Ta opcja nie jest dostępna dla niektórych typów wyjątków. **Ciąg Kontynuuj** umożliwi aplikacji kontynuowanie. W aplikacji natywnej spowoduje to ponowne zgłoszenie wyjątku. W aplikacji zarządzanej spowoduje to zakończenie działania programu lub obsługę wyjątku przez aplikację hostingu.

> [!NOTE]
> Nie można kontynuować po nieobsługiwanym wyjątku w kodzie zarządzanym. Wybranie **opcji Kontynuuj** po nieobsługiwanym wyjątku w kodzie zarządzanym powoduje zatrzymanie debugowania.

 **Ignoruj** Umożliwia kontynuowanie wykonywania bez wywołania procedury obsługi wyjątków. Ponieważ program obsługi wyjątków nie jest wywoływany, może to prowadzić do dalszych konsekwencji, w tym dodatkowych wyjątków i błędów. Ta opcja nie jest dostępna dla niektórych typów wyjątków.

## <a name="see-also"></a>Zobacz też
- [Zarządzanie wyjątkami za pomocą debugera](../debugger/managing-exceptions-with-the-debugger.md)
- [Najlepsze rozwiązania dotyczące wyjątków](/dotnet/standard/exceptions/best-practices-for-exceptions)
- [Obsługa wyjątków](/cpp/extensions/exception-handling-cpp-component-extensions)