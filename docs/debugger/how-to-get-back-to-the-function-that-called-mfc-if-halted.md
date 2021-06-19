---
title: Wróć do funkcji, która wywołała MFC w przypadku zatrzymania | Microsoft Docs
description: Dowiedz się, jak wrócić do funkcji, która wywołała MFC, jeśli wykonywanie zostanie zatrzymane w Visual Studio debugerze.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 31bbb064aad5a43738b2f345cf31a20767c55e69
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112384684"
---
# <a name="how-to-get-back-to-the-function-that-called-mfc-if-halted"></a>Porady: powracanie do funkcji, która wywołała MFC przy zatrzymaniu

> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **pozycję Importuj i eksportuj ustawienia** **w** menu Narzędzia. Aby uzyskać więcej informacji, zobacz [Resetowanie ustawień](../ide/environment-settings.md#reset-settings).

Jeśli używasz polecenia **Break** w **menu** Debugowanie, aby zatrzymać program i zakończyło się w MFC, i masz pewność, że problem znajduje się w kodzie, możesz użyć okna stosu wywołań, aby wrócić do funkcji. Aby uzyskać więcej informacji, [zobacz Jak używać okna stosu wywołań](../debugger/how-to-use-the-call-stack-window.md).

Czasami kod może spowodować przerwę w pompie komunikatów. W takim przypadku nie ma kodu użytkownika w stosie wywołań. Aby uniknąć tego problemu, można użyć punktów przerwania (prawdopodobnie z warunkami i liczbami trafień) zamiast **break** polecenia. Aby uzyskać więcej informacji, zobacz [Punkty przerwania i punkty śledzenia](/previous-versions/ktf38f66(v=vs.100)).

## <a name="navigate-to-the-function-from-which-mfc-was-called"></a>Przejdź do funkcji, z której wywołano MFC

- Użyj okna **Stos wywołań.**

## <a name="see-also"></a>Zobacz też

- [Debugowanie kodu natywnego : często zadawane pytania](../debugger/debugging-native-code-faqs.md)
- [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)