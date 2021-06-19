---
title: Używanie okien debugera podczas debugowania aplikacji pierwszego planu | Microsoft Docs
description: Jeśli debugujesz program, który musi pozostać na pierwszym planie, użyj debugowania zdalnego, aby uniknąć umieszczania go w tle.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fce51a1a28a8e03692faeee3ed723627864f4031
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386829"
---
# <a name="how-can-i-use-debugger-windows-while-debugging-a-foreground-program"></a>Jak można używać okien debugera przy debugowaniu programu pierwszego planu?
## <a name="problem-description"></a>Opis problemu
 Próbuję debugować problem z obrazem ekranu. Aby zaobserwować ten problem, muszę zachować swój program na pierwszym planie, co oznacza, że nie mam dostępu do okien debugowania. Co mogę zrobić?

## <a name="solution"></a>Rozwiązanie
 Jeśli masz drugi komputer, możesz użyć debugowania zdalnego. W przypadku konfiguracji na dwóch komputerach można obejrzeć obraz ekranu na komputerze zdalnym podczas pracy z debugerem na hoście. Aby uzyskać więcej informacji na temat zdalnego debugowania, zobacz [Debugowanie zdalne.](../debugger/remote-debugging.md)

## <a name="see-also"></a>Zobacz też
- [Debugowanie kodu natywnego : często zadawane pytania](../debugger/debugging-native-code-faqs.md)
- [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)
