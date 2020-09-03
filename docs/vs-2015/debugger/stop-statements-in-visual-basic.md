---
title: Instrukcje zatrzymania w Visual Basic | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
helpviewer_keywords:
- End statements
- breakpoints, Stop statements
- debugging managed code, Stop statements vs breakpoints
- Stop statements, about Stop statements
- debugging [Visual Basic], Stop statements vs. breakpoints
ms.assetid: 4ad3fe5c-3dfb-4913-b2eb-a0b635751c18
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8f2749ef9a6cfd310da5da832a283b55b6af59a6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198889"
---
# <a name="stop-statements-in-visual-basic"></a>Instrukcje stop w Visual Basic
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Instrukcja Visual Basic Stop zawiera programistyczną alternatywę do ustawiania punktu przerwania. Gdy debuger napotka instrukcję stop, przerywa wykonywanie programu (przejdzie do trybu przerwania). Programiści języka C# mogą osiągać ten sam efekt przy użyciu wywołania metody System. Diagnostics. Debugger. Break.  
  
 Możesz ustawić lub usunąć instrukcję zatrzymania, edytując kod źródłowy. Nie można ustawiać lub czyścić instrukcji zatrzymania przy użyciu poleceń debugera, tak jak w przypadku punktu przerwania.  
  
 W przeciwieństwie do instrukcji End, instrukcja Stop nie resetuje zmiennych ani nie zwraca do trybu projektowania. Aby kontynuować działanie aplikacji, możesz wybrać pozycję Kontynuuj z menu Debuguj.  
  
 Po uruchomieniu aplikacji Visual Basic poza debugerem instrukcja Stop uruchomi debuger, jeśli jest włączone debugowanie just in Time. Jeśli debugowanie just in Time nie jest włączone, instrukcja stop zachowuje się tak, jakby była instrukcją End, kończąc wykonywanie. Nie wystąpi zdarzenie QueryUnload ani Unload, dlatego należy usunąć wszystkie instrukcje zatrzymania z wersji aplikacji Visual Basic. Aby uzyskać więcej informacji, zobacz [debugowanie just in Time](../debugger/just-in-time-debugging-in-visual-studio.md).  
  
 Aby uniknąć konieczności usuwania instrukcji zatrzymania, można użyć kompilacji warunkowej:  
  
```  
#If DEBUG Then  
   Stop  
#Else  
   ' Don't stop  
#End If  
```  
  
 Kolejną alternatywą jest użycie instrukcji Assert zamiast instrukcji Stop. Instrukcja Debug. Assert przerywa wykonywanie tylko wtedy, gdy określony warunek nie jest spełniony i jest automatycznie usuwany podczas tworzenia wersji. Aby uzyskać więcej informacji, zobacz [potwierdzenia w kodzie zarządzanym](../debugger/assertions-in-managed-code.md). Jeśli potrzebujesz instrukcji Assert, która zawsze przerywa wykonywanie w wersji debugowania, możesz to zrobić:  
  
```  
Debug.Assert(false)  
```  
  
 Jeszcze kolejną alternatywą jest użycie metody Debug. Fail:  
  
```  
Debug.Fail("a clever output string goes here")  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia debugera](../debugger/debugger-security.md)   
 [Typy projektów C#, F # i Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Debugowanie zarządzanego kodu](../debugger/debugging-managed-code.md)
