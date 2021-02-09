---
title: Zachowaj fokus podczas przechodzenia przez moją aplikację | Microsoft Docs
Description: Używaj debugowania zdalnego, aby zapobiec utracie fokusu przez program podczas debugowania problemu z aktywacją okna.
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.debug.stepping
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], stepping
- focus, keeping
- stepping, focus
- windows, troubleshooting activation
ms.assetid: 11a30580-3a1a-4be8-a241-0abdc758302e
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b821c374a87983ab8cb2667b434b1509e8449f31
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99911438"
---
# <a name="how-can-i-keep-focus-when-stepping-through-my-app"></a>Jak zachować fokus podczas przechodzenia przez aplikację?
## <a name="description"></a>Opis
 Mój program ma problem z aktywacją okna. Przechodzenie przez program za pomocą debugera zakłóca moją możliwość odtworzenia problemu, ponieważ mój program utrzymuje fokus. Czy istnieje sposób, aby to uniknąć?

## <a name="solution"></a>Rozwiązanie
 Jeśli używasz drugiego komputera, Użyj zdalnego debugowania. Program można obsługiwać na komputerze zdalnym podczas uruchamiania debugera na hoście. Aby uzyskać więcej informacji, zobacz [How to: Select a Remote Computer](/previous-versions/visualstudio/visual-studio-2010/w8wtw2f3(v=vs.100)).

## <a name="see-also"></a>Zobacz też
- [Debugowanie często zadawanych pytań dotyczących kodu natywnego](../debugger/debugging-native-code-faqs.md)
- [Dołączanie do uruchomionych procesów](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)