---
title: W jaki sposób można debugować naruszenia zasad dostępu przy uruchamianiu programu poza debugerem? | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: 5e0ed8025986c92cd4c809ea8b04f0109fb010c5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51816293"
---
# <a name="how-can-i-debug-access-violations-when-running-my-program-outside-the-debugger"></a>W jaki sposób można debugować naruszenia zasad dostępu przy uruchamianiu programu poza debugerem?
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Opis problemu  
 Program działa poprawnie w środowisku Visual Studio, ale gdy uruchamiam go autonomicznego w systemie operacyjnym Windows, generuje naruszenie zasad dostępu. W jaki sposób można debugować ten problem?  
  
## <a name="solution"></a>Rozwiązanie  
 Ustaw [Just-in-time debugging](../debugger/just-in-time-debugging-in-visual-studio.md) opcji, a następnie uruchom program autonomiczny, dopóki nie nastąpi naruszenie zasad dostępu. Następnie w **naruszenie zasad dostępu** okno dialogowe, możesz kliknąć pozycję **anulować** można uruchomić debugera.  
  
 Zobacz też artykuł bazy wiedzy Knowledge Base Q133174, "Jak do lokalizacji, w którym występuje ogólny błąd ochrony (GP)". Można znaleźć artykuły bazy wiedzy na dysku CD z biblioteki MSDN lub przeszukując [ http://support.microsoft.com/ ](http://support.microsoft.com/).  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie kodu natywnego — często zadawane pytania](../debugger/debugging-native-code-faqs.md)   
 [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)



