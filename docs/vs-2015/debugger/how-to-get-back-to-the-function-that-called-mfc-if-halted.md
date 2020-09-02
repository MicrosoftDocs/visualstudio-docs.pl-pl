---
title: 'Instrukcje: przewracanie do funkcji o nazwie MFC, jeśli została zatrzymana | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.mfc
dev_langs:
- FSharp
- VB
- CSharp
- C++
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
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c19cbf6e892ba8b35f2b92ad9b86aa0b74a64810
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65685880"
---
# <a name="how-to-get-back-to-the-function-that-called-mfc-if-halted"></a>Porady: powracanie do funkcji, która wywołała MFC przy zatrzymaniu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

KORYGUJĄC
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz Importuj i Eksportuj ustawienia w menu Narzędzia. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień deweloperskich w programie Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Jeśli użyto polecenia **Break** w menu **Debuguj** , aby zatrzymać program i zakończył się w MFC, i masz pewność, że problem występuje w kodzie, możesz użyć okna stosu wywołań, aby przejść z powrotem do funkcji. Aby uzyskać więcej informacji, zobacz [jak: korzystanie z okna stosu wywołań](../debugger/how-to-use-the-call-stack-window.md).  
  
 Czasami kod może ulec przerwaniu w pompie komunikatów. W takim przypadku nie ma kodu użytkownika na stosie wywołań. Aby uniknąć tego problemu, można użyć punktów przerwania (prawdopodobnie z warunkami i liczbami trafień) zamiast polecenia **Break** . Aby uzyskać więcej informacji, zobacz [punkty przerwania i punkty śledzenia](https://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583)).  
  
### <a name="to-navigate-to-the-function-from-which-mfc-was-called"></a>Aby przejść do funkcji, z której wywołano MFC  
  
- Użyj okna **stosu wywołań** .  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie często zadawanych pytań dotyczących kodu natywnego](../debugger/debugging-native-code-faqs.md)   
 [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)
