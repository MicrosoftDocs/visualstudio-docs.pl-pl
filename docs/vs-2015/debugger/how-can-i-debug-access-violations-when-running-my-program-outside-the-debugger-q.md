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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "74299260"
---
# <a name="how-can-i-debug-access-violations-when-running-my-program-outside-the-debugger"></a>W jaki sposób można debugować naruszenia zasad dostępu przy uruchamianiu programu poza debugerem?
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Opis problemu  
 Mój program działa prawidłowo w środowisku programu Visual Studio, ale w przypadku uruchomienia go autonomicznego z systemem operacyjnym Windows powoduje naruszenie zasad dostępu. Jak można debugować ten problem?  
  
## <a name="solution"></a>Rozwiązanie  
 Ustaw opcję [debugowanie just in Time](../debugger/just-in-time-debugging-in-visual-studio.md) i uruchom program autonomicznie do momentu wystąpienia naruszenia zasad dostępu. Następnie w oknie dialogowym **naruszenie zasad dostępu** można kliknąć przycisk **Anuluj** , aby uruchomić debuger.  
  
 Zobacz także artykuł z bazy wiedzy Q133174, "Jak zlokalizować miejsce wystąpienia błędu ochrony ogólnej (GP)". Artykuły bazy wiedzy można znaleźć na dysku CD biblioteki MSDN lub przez wyszukiwanie [http://support.microsoft.com/](https://support.microsoft.com/) .  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie często zadawanych pytań dotyczących kodu natywnego](../debugger/debugging-native-code-faqs.md)   
 [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)
