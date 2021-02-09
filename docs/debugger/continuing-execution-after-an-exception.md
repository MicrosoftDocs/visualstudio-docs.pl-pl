---
title: Kontynuowanie wykonania po wystąpieniu wyjątku | Microsoft Docs
description: Dowiedz się, co się dzieje, gdy debuger przerywa wykonywanie z powodu nieobsługiwanego wyjątku. Możesz kontynuować wykonywanie w tym samym wątku.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9af71aba1b26c3d8160af229d8c050038800106a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99865816"
---
# <a name="continuing-execution-after-an-exception"></a>Kontynuowanie wykonania po wyjątkach
Gdy debuger przerywa wykonywanie z powodu wyjątku, domyślnie zobaczysz **pomocnika wyjątków**. Jeśli w oknie dialogowym **Opcje** wyłączono **pomocnika wyjątków** , zobaczysz **asystenta wyjątków** (C# lub Visual Basic) lub okno dialogowe **wyjątek** (C++).

 Po wyświetleniu **pomocnika wyjątków** można spróbować rozwiązać problem, który spowodował wyjątek.

## <a name="managed-and-native-code"></a>Kod zarządzany i natywny
 W kodzie zarządzanym i natywnym można kontynuować wykonywanie w tym samym wątku po wystąpieniu nieobsłużonego wyjątku. **Pomocnik wyjątku** rozwinięcia stos wywołań do punktu, w którym został zgłoszony wyjątek.

## <a name="mixed-code"></a>Kod mieszany
 Jeśli wystąpił nieobsługiwany wyjątek podczas debugowania kodu natywnego i zarządzanego, ograniczenia systemu operacyjnego uniemożliwiają rozwinięcia stosu wywołań. Jeśli spróbujesz odwinąć stos wywołań za pomocą menu skrótów, komunikat o błędzie wyjaśnia, że debuger nie może wycofać się z nieobsłużonego elementu, z wyjątkiem debugowania kodu mieszanego.

## <a name="see-also"></a>Zobacz też

- [Zarządzanie wyjątkami za pomocą debugera](../debugger/managing-exceptions-with-the-debugger.md)