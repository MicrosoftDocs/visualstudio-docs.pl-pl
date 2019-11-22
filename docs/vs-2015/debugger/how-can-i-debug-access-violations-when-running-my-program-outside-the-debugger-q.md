---
title: W jaki sposób można debugować naruszenia zasad dostępu przy uruchamianiu programu poza debugerem? | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.access
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- access violation debugging
- debugging [Visual Studio], access violations
ms.assetid: 780a298a-132e-4245-8370-8c82ca27c6c1
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ce5b21f92eecf2e8929c142bc1ee32e20d386335
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299260"
---
# <a name="how-can-i-debug-access-violations-when-running-my-program-outside-the-debugger"></a>W jaki sposób można debugować naruszenia zasad dostępu przy uruchamianiu programu poza debugerem?
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Opis problemu  
 Program działa poprawnie w środowisku Visual Studio, ale gdy uruchamiam go autonomicznego w systemie operacyjnym Windows, generuje naruszenie zasad dostępu. W jaki sposób można debugować ten problem?  
  
## <a name="solution"></a>Rozwiązanie  
 Ustaw [Just-in-time debugging](../debugger/just-in-time-debugging-in-visual-studio.md) opcji, a następnie uruchom program autonomiczny, dopóki nie nastąpi naruszenie zasad dostępu. Następnie w **naruszenie zasad dostępu** okno dialogowe, możesz kliknąć pozycję **anulować** można uruchomić debugera.  
  
 Zobacz także artykuł z bazy wiedzy Q133174, "Jak zlokalizować miejsce wystąpienia błędu ochrony ogólnej (GP)". Artykuły bazy wiedzy można znaleźć na dysku CD biblioteki MSDN lub przeszukać [http://support.microsoft.com/](https://support.microsoft.com/).  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie kodu natywnego — często zadawane pytania](../debugger/debugging-native-code-faqs.md)   
 [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)
