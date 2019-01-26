---
title: Kontynuowanie wykonania po wystąpieniu wyjątku | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 48e0cf526d6fadcb1b91206d6e1958d89d3bdfe5
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54949968"
---
# <a name="continuing-execution-after-an-exception"></a>Kontynuowanie wykonania po wyjątkach
Kiedy debuger przerywa wykonywanie z powodu wyjątku, zobaczysz **pomocnika wyjątków**, domyślnie. Jeśli wyłączono **pomocnika wyjątków** w **opcje** zobaczysz okno dialogowe **Asystenta wyjątków** (C# lub Visual Basic) lub  **Wyjątek** okno dialogowe (C++).  
  
 Gdy **pomocnika wyjątków** zostanie wyświetlony, możesz spróbować rozwiązać ten problem, który spowodował wyjątek.
  
## <a name="managed-and-native-code"></a>Kodu zarządzanego i natywnego  
 W kodu zarządzanego i natywnego można kontynuować wykonywania w tym samym wątku, po wystąpieniu nieobsługiwanego wyjątku. **Pomocnika wyjątków** rozwija stos wywołań do punktu, w którym został zgłoszony wyjątek.
  
## <a name="mixed-code"></a>Kod mieszany  
 Jeśli napotkasz nieobsługiwany wyjątek podczas debugowania mieszane kodu natywnego i zarządzanego, ograniczenia systemu operacyjnego uniemożliwiają odwijanie stosu wywołań. Jeśli spróbujesz przewijanie stosu wywołań, za pomocą menu skrótów, komunikat o błędzie wyjaśniono, że debuger nie może wykonać odwinięcia z nieobsługiwanego z wyjątkiem podczas debugowania kodu mieszanego.  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie wyjątkami za pomocą debugera](../debugger/managing-exceptions-with-the-debugger.md)