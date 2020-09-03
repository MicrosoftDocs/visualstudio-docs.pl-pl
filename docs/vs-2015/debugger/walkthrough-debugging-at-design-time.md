---
title: 'Przewodnik: debugowanie w czasie projektowania | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], design-time
- breakpoints, design-time debugging
- Immediate window, design-time debugging
- design-time debugging
ms.assetid: 35bfdd2c-6f60-4be1-ba9d-55fce70ee4d8
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 54466cc3561c194199bbad2b35cd00433da2b0f3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149431"
---
# <a name="walkthrough-debugging-at-design-time"></a>Wskazówki: debugowanie w czasie projektowania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz użyć **natychmiastowego** okna programu Visual Studio, aby wykonać funkcję lub procedurę podprocedury, gdy aplikacja nie jest uruchomiona. Jeśli funkcja lub podprocedura zawiera punkt przerwania, program Visual Studio przerywa wykonywanie w odpowiednim punkcie. Można następnie użyć okien debugera do sprawdzenia stanu programu. Ta funkcja jest nazywana debugowaniem w czasie projektowania.  
  
 Poniższa procedura pokazuje, jak można użyć tej funkcji.  
  
### <a name="to-hit-breakpoints-from-the-immediate-window"></a>Aby trafiać punkty przerwania z okna bezpośredniego  
  
1. Wklej następujący kod do Visual Basic aplikacji konsolowej:  
  
    ```  
    Module Module1  
  
        Sub Main()  
            MySub()  
        End Sub  
  
        Function MyFunction() As Decimal  
            Static i As Integer  
            i = i + 1  
            Dim s As String  
  
            s = "Add Breakpoint here"  
            Return 4  
        End Function  
  
        Sub MySub()  
            MyFunction()  
        End Sub  
    End Module  
    ```  
  
2. Ustaw punkt przerwania w wierszu, który odczytuje, `s="Add BreakPoint Here"` .  
  
3. W oknie **bezpośrednim** wpisz następujące elementy: `?MyFunction<enter>`  
  
4. Sprawdź, czy punkt przerwania został trafiony i czy stos wywołań jest prawidłowy.  
  
5. W menu **debugowanie** kliknij przycisk **Kontynuuj**i sprawdź, czy nadal Pracujesz w trybie projektowania.  
  
6. W oknie **bezpośrednim** wpisz następujące elementy: `?MyFunction<enter>`  
  
7. W oknie **bezpośrednim** wpisz następujące elementy: `?MySub<enter>`  
  
8. Sprawdź, czy osiągnięto punkt przerwania, i sprawdź wartość zmiennej statycznej `i` w oknie **zmiennych lokalnych** . Powinna mieć wartość 3.  
  
9. Sprawdź, czy stos wywołań jest prawidłowy.  
  
10. W menu **debugowanie** kliknij przycisk **Kontynuuj**i sprawdź, czy nadal Pracujesz w trybie projektowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia debugera](../debugger/debugger-security.md)   
 [Podstawowe informacje o debugerze](../debugger/debugger-basics.md)
