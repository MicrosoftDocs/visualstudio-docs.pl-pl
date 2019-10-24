---
title: Kontynuowanie wykonania po wystąpieniu wyjątku | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- managed exceptions, continuing execution after
- exceptions, continuing execution after
- debugger, exceptions
- managed code, exception handling
- exception handling, continuing execution after
- execution, continuing after an exception
- program execution
- threading [Visual Studio], continuing execution after exceptions
- Exceptions dialog box
- programs, executing
ms.assetid: 6fe97aac-2131-4615-bd92-d3afee741558
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e7be214a950c8cc93d986f97834a848bd9ab824e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745646"
---
# <a name="continuing-execution-after-an-exception"></a>Kontynuowanie wykonania po wyjątkach
Gdy debuger przerywa wykonywanie z powodu wyjątku, domyślnie zobaczysz **pomocnika wyjątków**. Jeśli w oknie dialogowym **Opcje** wyłączono **pomocnika wyjątków** , zobaczysz **asystenta wyjątków** (C# lub Visual Basic) lub okno dialogowe **wyjątku** (C++).

 Po wyświetleniu **pomocnika wyjątków** można spróbować rozwiązać problem, który spowodował wyjątek.

## <a name="managed-and-native-code"></a>Kod zarządzany i natywny
 W kodzie zarządzanym i natywnym można kontynuować wykonywanie w tym samym wątku po wystąpieniu nieobsłużonego wyjątku. **Pomocnik wyjątku** rozwinięcia stos wywołań do punktu, w którym został zgłoszony wyjątek.

## <a name="mixed-code"></a>Kod mieszany
 Jeśli wystąpił nieobsługiwany wyjątek podczas debugowania kodu natywnego i zarządzanego, ograniczenia systemu operacyjnego uniemożliwiają rozwinięcia stosu wywołań. Jeśli spróbujesz odwinąć stos wywołań za pomocą menu skrótów, komunikat o błędzie wyjaśnia, że debuger nie może wycofać się z nieobsłużonego elementu, z wyjątkiem debugowania kodu mieszanego.

## <a name="see-also"></a>Zobacz także

- [Zarządzanie wyjątkami za pomocą debugera](../debugger/managing-exceptions-with-the-debugger.md)