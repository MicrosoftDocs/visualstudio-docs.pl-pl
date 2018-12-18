---
title: 'Wskazówki: Debugowanie w czasie projektowania | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: 4b6660bc4d9cf0073f1e18b0960c3fa9c0ae9c13
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51737765"
---
# <a name="walkthrough-debugging-at-design-time"></a>Wskazówki: debugowanie w czasie projektowania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz użyć programu Visual Studio **bezpośrednie** okna do wykonania funkcji lub podprocedury, gdy aplikacja nie jest uruchomiona. Jeśli funkcja lub podprocedura zawiera punkt przerwania, program Visual Studio spowoduje przerwanie wykonywania we właściwym miejscu. Można następnie użyć okien debugera do sprawdzenia stanu programu. Ta funkcja jest wywoływana, debugowanie w czasie projektowania.  
  
 Poniższa procedura pokazuje, jak można użyć tej funkcji.  
  
### <a name="to-hit-breakpoints-from-the-immediate-window"></a>Aby identyfikować punkty przerwania w oknie bezpośrednim  
  
1.  Wklej następujący kod do aplikacji konsoli Visual Basic:  
  
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
  
2.  Ustaw punkt przerwania w wierszu, który odczytuje, `s="Add BreakPoint Here"`.  
  
3.  Wpisz następujące polecenie w **bezpośrednie** okna: `?MyFunction<enter>`  
  
4.  Sprawdź, czy punkt przerwania został trafiony i że stos wywołań jest prawidłowo wprowadzony.  
  
5.  Na **debugowania** menu, kliknij przycisk **Kontynuuj**i sprawdź, że jesteś nadal w trybie projektowania.  
  
6.  Wpisz następujące polecenie w **bezpośrednie** okna: `?MyFunction<enter>`  
  
7.  Wpisz następujące polecenie w **bezpośrednie** okna: `?MySub<enter>`  
  
8.  Sprawdź, czy trafiony punkt przerwania i sprawdzić wartość zmiennej statycznej `i` w **lokalne** okna. Powinien mieć wartość 3.  
  
9. Sprawdź, czy wywołanie stosu jest prawidłowa.  
  
10. Na **debugowania** menu, kliknij przycisk **Kontynuuj**i sprawdź, że jesteś nadal w trybie projektowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczenia debugera](../debugger/debugger-security.md)   
 [Podstawowe informacje o debugerze](../debugger/debugger-basics.md)



