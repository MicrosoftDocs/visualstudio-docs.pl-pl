---
title: Wróć do funkcji, która wywołała MFC przy zatrzymaniu | Dokumentacja firmy Microsoft
ms.custom: seodec18
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.mfc
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- functions [C++], debugging
- function calls, returning to calling function
- debugging [MFC], returning to calling function
- debugging [MFC], functions
- Break command
- programs, halting
- functions [debugger]
ms.assetid: d254a5a9-afbd-4923-9d7a-7422d824cabf
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c746fc287435ea6219e0f6052bc9372fc2ae5d25
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53048571"
---
# <a name="how-to-get-back-to-the-function-that-called-mfc-if-halted"></a>Porady: powracanie do funkcji, która wywołała MFC przy zatrzymaniu

> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [zresetować ustawienia](../ide/environment-settings.md#reset-settings).

Jeśli użyto **Przerwij** polecenie **debugowania** menu, aby zatrzymać program zakończył w MFC i wiesz, czy problem jest w kodzie okno stosu wywołań można przejść z powrotem do funkcji. Aby uzyskać więcej informacji, zobacz [porady: Korzystanie z okna stosu wywołań](../debugger/how-to-use-the-call-stack-window.md).

Czasami Twój kod może spowodować przerwanie "pompy komunikatów". W takiej sytuacji istnieje żaden kod użytkownika w stosie wywołań. Aby uniknąć tego problemu, można użyć punktów przerwania (także z warunków i liczniki trafień) zamiast **Przerwij** polecenia. Aby uzyskać więcej informacji, zobacz [punkty przerwania i śledzenia](https://msdn.microsoft.com/library/fe4eedc1-71aa-4928-962f-0912c334d583).

## <a name="navigate-to-the-function-from-which-mfc-was-called"></a>Przejdź do funkcji, z którego wywołano MFC

-   Użyj **stos wywołań** okna.

## <a name="see-also"></a>Zobacz także

- [Debugowanie kodu natywnego — często zadawane pytania](../debugger/debugging-native-code-faqs.md)
- [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)