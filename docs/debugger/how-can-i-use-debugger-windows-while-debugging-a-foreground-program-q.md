---
title: Używaj okien debugera podczas debugowania aplikacji pierwszego planu | Microsoft Docs
Description: Jeśli debugujesz program, który musi pozostać na pierwszym planie, użyj debugowania zdalnego, aby uniknąć umieszczania go w tle.
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.debug.background
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- foreground program debugging
- remote debugging, debugging foreground programs
- debugging [Visual Studio], while observing foreground programs
- focus, debugging while observing foreground programs
- debugging [Visual Studio], foreground programs
ms.assetid: 9e67a308-1c81-42ab-966b-7fc3c1d2bf7a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f39f7dfbd463c48675f4b8c98612dfab3f33de3c
ms.sourcegitcommit: 40d758f779d42c66cb02ae7face8a62763a8662b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/14/2020
ms.locfileid: "97398743"
---
# <a name="how-can-i-use-debugger-windows-while-debugging-a-foreground-program"></a>Jak można używać okien debugera przy debugowaniu programu pierwszego planu?
## <a name="problem-description"></a>Opis problemu
 Próbuję debugować problem z narysowaniem ekranu. Aby obsłużyć ten problem, muszę zachować mój program na pierwszym planie, co oznacza, że nie ma dostępu do okien debugowania. Co mogę zrobić?

## <a name="solution"></a>Rozwiązanie
 Jeśli używasz drugiego komputera, możesz użyć zdalnego debugowania. W przypadku konfiguracji z dwoma komputerami można obejrzeć malowanie ekranu na komputerze zdalnym podczas korzystania z debugera na hoście. Aby uzyskać więcej informacji na temat debugowania zdalnego, zobacz [zdalne debugowanie](../debugger/remote-debugging.md).

## <a name="see-also"></a>Zobacz także
- [Debugowanie często zadawanych pytań dotyczących kodu natywnego](../debugger/debugging-native-code-faqs.md)
- [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)