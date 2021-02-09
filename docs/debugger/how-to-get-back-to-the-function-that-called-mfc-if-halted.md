---
title: Wróć do funkcji, która wywołała MFC, jeśli została zatrzymana | Microsoft Docs
description: Informacje o sposobie powrotu do funkcji o nazwie MFC w przypadku zatrzymania wykonywania w debugerze programu Visual Studio.
ms.custom: SEO-VS-2020, seodec18
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
ms.openlocfilehash: a0b3849653161278dc0f6e9e06a1baca2e8b6e62
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99904242"
---
# <a name="how-to-get-back-to-the-function-that-called-mfc-if-halted"></a>Porady: powracanie do funkcji, która wywołała MFC przy zatrzymaniu

> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Importuj i Eksportuj ustawienia** w menu **Narzędzia** . Aby uzyskać więcej informacji, zobacz [Resetowanie ustawień](../ide/environment-settings.md#reset-settings).

Jeśli użyto polecenia **Break** w menu **Debuguj** , aby zatrzymać program i zakończył się w MFC, i masz pewność, że problem występuje w kodzie, możesz użyć okna stosu wywołań, aby przejść z powrotem do funkcji. Aby uzyskać więcej informacji, zobacz [jak: korzystanie z okna stosu wywołań](../debugger/how-to-use-the-call-stack-window.md).

Czasami kod może ulec przerwaniu w pompie komunikatów. W takim przypadku nie ma kodu użytkownika na stosie wywołań. Aby uniknąć tego problemu, można użyć punktów przerwania (prawdopodobnie z warunkami i liczbami trafień) zamiast polecenia **Break** . Aby uzyskać więcej informacji, zobacz [punkty przerwania i punkty śledzenia](/previous-versions/ktf38f66(v=vs.100)).

## <a name="navigate-to-the-function-from-which-mfc-was-called"></a>Przejdź do funkcji, z której wywołano MFC

- Użyj okna **stosu wywołań** .

## <a name="see-also"></a>Zobacz też

- [Debugowanie często zadawanych pytań dotyczących kodu natywnego](../debugger/debugging-native-code-faqs.md)
- [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)