---
title: Debuguj naruszenia dostępu podczas uruchamiania aplikacji poza programem Visual Studio
titleSuffix: ''
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5bbc129c4f5f4aa4d3ed1c6e346f9f8ab0395230
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852181"
---
# <a name="how-can-i-debug-access-violations-when-running-my-program-outside-the-debugger"></a>W jaki sposób można debugować naruszenia zasad dostępu przy uruchamianiu programu poza debugerem?

## <a name="problem-description"></a>Opis problemu
 Mój program działa prawidłowo w środowisku programu Visual Studio, ale w przypadku uruchomienia go autonomicznego z systemem operacyjnym Windows powoduje naruszenie zasad dostępu. Jak można debugować ten problem?

## <a name="solution"></a>Rozwiązanie
 Ustaw opcję [debugowanie just in Time](../debugger/just-in-time-debugging-in-visual-studio.md) i uruchom program autonomicznie do momentu wystąpienia naruszenia zasad dostępu. Następnie w oknie dialogowym **naruszenie zasad dostępu** można kliknąć przycisk **Anuluj** , aby uruchomić debuger.

## <a name="see-also"></a>Zobacz także
- [Debugowanie kodu natywnego — Często zadawane pytania](../debugger/debugging-native-code-faqs.md)
- [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)