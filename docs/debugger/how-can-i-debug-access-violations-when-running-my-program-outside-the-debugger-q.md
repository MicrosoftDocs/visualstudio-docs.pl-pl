---
title: Debuguj naruszenia dostępu podczas uruchamiania aplikacji poza programem Visual Studio
titleSuffix: ''
description: Debuger just in Time umożliwia debugowanie naruszenia zasad dostępu, które występuje poza środowiskiem programu Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.debug.access
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- access violation debugging
- debugging [Visual Studio], access violations
ms.assetid: 780a298a-132e-4245-8370-8c82ca27c6c1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: dd4709807b176806d8a7ca56de4adda8cdfe13ec
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99904318"
---
# <a name="how-can-i-debug-access-violations-when-running-my-program-outside-the-debugger"></a>W jaki sposób można debugować naruszenia zasad dostępu przy uruchamianiu programu poza debugerem?

## <a name="problem-description"></a>Opis problemu
 Mój program działa prawidłowo w środowisku programu Visual Studio, ale w przypadku uruchomienia go autonomicznego z systemem operacyjnym Windows powoduje naruszenie zasad dostępu. Jak można debugować ten problem?

## <a name="solution"></a>Rozwiązanie
 Ustaw opcję [debugowanie just in Time](../debugger/just-in-time-debugging-in-visual-studio.md) i uruchom program autonomicznie do momentu wystąpienia naruszenia zasad dostępu. Następnie w oknie dialogowym **naruszenie zasad dostępu** można kliknąć przycisk **Anuluj** , aby uruchomić debuger.

## <a name="see-also"></a>Zobacz też
- [Debugowanie często zadawanych pytań dotyczących kodu natywnego](../debugger/debugging-native-code-faqs.md)
- [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)