---
title: Debuger Microsoft Visual Studio (zgłoszony wyjątek) — okno dialogowe | Microsoft Docs
titleSuffix: ''
description: 'Dowiedz się, co należy zrobić, gdy wystąpi wyjątek, że program musi obsłużyć. Możesz: 1) przerwanie w debugerze; 2) Kontynuuj; lub 3) Ignoruj.'
ms.custom: SEO-VS-2020, seodec18
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1c86c765ad8ebfbe36dcaca484f7da4121b7e297
ms.sourcegitcommit: c67dece5ded82a5867148e1f94396954c1ec4398
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2021
ms.locfileid: "97975280"
---
# <a name="microsoft-visual-studio-debugger-exception-thrown-dialog-box"></a>Microsoft Visual Studio Debugger (wystąpienie wyjątku) ― okno dialogowe
W programie wystąpił wyjątek. To okno dialogowe służy do zgłaszania rodzaju zgłoszonego wyjątku. Kod musi obsłużyć ten wyjątek. Można wybrać jedną z następujących opcji obsługi wyjątku:

 **Przerwij** Zezwala na wykonanie przerwania w debugerze. Procedura obsługi wyjątków nie jest wywoływana przed przerwaniem. W przypadku kontynuowania od przerwy zostanie wywołana procedura obsługi wyjątków.

 **Kontynuuj** Umożliwia kontynuowanie wykonywania, dając programowi obsługi wyjątków szansę obsługi wyjątku. Ta opcja jest niedostępna w przypadku niektórych typów wyjątków. Wartość **Kontynuuj** umożliwi kontynuowanie działania aplikacji. W aplikacji natywnej spowoduje to, że wyjątek zostanie ponownie wygenerowany. W aplikacji zarządzanej spowoduje to przerwanie działania programu lub wyjątek, który ma być obsługiwany przez aplikację hostingu.

> [!NOTE]
> Nie można kontynuować po nieobsługiwanym wyjątku w kodzie zarządzanym. Wybranie opcji **Kontynuuj** po nieobsługiwanym wyjątku w kodzie zarządzanym powoduje zatrzymanie debugowania.

 **Ignoruj** Umożliwia kontynuowanie wykonywania bez wywoływania procedury obsługi wyjątków. Ponieważ program obsługi wyjątków nie jest wywoływany, może to prowadzić do dalszych konsekwencji, w tym dodatkowych wyjątków i błędów. Ta opcja jest niedostępna w przypadku niektórych typów wyjątków.

## <a name="see-also"></a>Zobacz też
- [Zarządzanie wyjątkami za pomocą debugera](../debugger/managing-exceptions-with-the-debugger.md)
- [Najlepsze rozwiązania dotyczące wyjątków](/dotnet/standard/exceptions/best-practices-for-exceptions)
- [Obsługa wyjątków](/cpp/extensions/exception-handling-cpp-component-extensions)