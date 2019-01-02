---
title: Debugowanie naruszenia zasad dostępu w przypadku uruchamiania aplikacji poza debugerem | Dokumentacja firmy Microsoft
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8b65c10b07b93e657a9e3cb9da5f94d5c9b14362
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53854025"
---
# <a name="how-can-i-debug-access-violations-when-running-my-program-outside-the-debugger"></a>W jaki sposób można debugować naruszenia zasad dostępu przy uruchamianiu programu poza debugerem?

## <a name="problem-description"></a>Opis problemu  
 Program działa poprawnie w środowisku Visual Studio, ale gdy uruchamiam go autonomicznego w systemie operacyjnym Windows, generuje naruszenie zasad dostępu. W jaki sposób można debugować ten problem?  
  
## <a name="solution"></a>Rozwiązanie  
 Ustaw [Just-in-time debugging](../debugger/just-in-time-debugging-in-visual-studio.md) opcji, a następnie uruchom program autonomiczny, dopóki nie nastąpi naruszenie zasad dostępu. Następnie w **naruszenie zasad dostępu** okno dialogowe, możesz kliknąć pozycję **anulować** można uruchomić debugera.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie kodu natywnego — często zadawane pytania](../debugger/debugging-native-code-faqs.md)   
 [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)