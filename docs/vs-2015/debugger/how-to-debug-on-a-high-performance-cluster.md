---
title: 'Instrukcje: debugowanie w klastrze o wysokiej wydajności | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- cluster debugging
- high-performance debugging
ms.assetid: a2f0eb07-840e-4f95-a1b1-9509217e5b8f
caps.latest.revision: 27
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f4487b168c3d405b2449bcfb9515e60f0ea67ed1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65702689"
---
# <a name="how-to-debug-on-a-high-performance-cluster"></a>Porady: debugowanie w klastrze o wysokiej wydajności
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Debugowanie programu przetwarzania wieloprocesowego w klastrze o wysokiej wydajności jest podobne do debugowania zwykłego programu na komputerze zdalnym. Jednak istnieją pewne dodatkowe zagadnienia. Ogólne wymagania dotyczące instalacji zdalnej można znaleźć w temacie [zdalne debugowanie](../debugger/remote-debugging.md).  
  
 Podczas debugowania w klastrze o wysokiej wydajności można używać wszystkich [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] okien debugowania i technik, które są dostępne do zdalnego debugowania. Ponieważ debugowanie jest przeprowadzane zdalnie, nie jest jednak dostępne okno konsoli zewnętrznej.  
  
 Okno **wątków** okna i **procesy** są szczególnie przydatne w przypadku debugowania aplikacji równoległych. Aby uzyskać porady dotyczące korzystania z tych okien, zobacz [How to: Use the processs Window](https://msdn.microsoft.com/0207ce2f-8ceb-4fe7-b2b5-4dd35b035ed7) i [How to: use Window Threads](../debugger/how-to-use-the-threads-window.md).  
  
 W poniższych procedurach przedstawiono kilka technik, które są szczególnie przydatne podczas debugowania w klastrze o wysokiej wydajności.  
  
 Podczas debugowania aplikacji równoległej można ustawić punkt przerwania dla określonego wątku, procesu lub komputera. Można to zrobić, tworząc normalny punkt przerwania, a następnie dodając filtr punktu przerwania.  
  
### <a name="to-open-the-breakpoint-filter-dialog-box"></a>Aby otworzyć okno dialogowe Filtr punktu przerwania  
  
1. Kliknij prawym przyciskiem myszy symbol punktu przerwania w oknie źródła, oknie **demontażu** , oknie **stos wywołań** lub oknie **punkty przerwania** .  
  
2. W menu skrótów kliknij polecenie **Filtruj**. Ta opcja może pojawić się na najwyższym poziomie lub w podmenu w obszarze **punkty przerwania**.  
  
### <a name="to-set-a-breakpoint-on-a-specific-computer"></a>Aby ustawić punkt przerwania na określonym komputerze  
  
1. Pobierz nazwę komputera z okna **procesy** .  
  
2. Wybierz punkt przerwania, a następnie otwórz okno dialogowe **Filtr punktu przerwania** zgodnie z opisem w poprzedniej procedurze.  
  
3. W oknie dialogowym **Filtr punktu przerwania** wpisz:  
  
     MachineName =*yourmachinename*  
  
     Aby utworzyć bardziej skomplikowany filtr, można łączyć klauzule przy użyciu `&` , operatora i, `||` ,, operatora OR, operatora `!` not i nawiasów.  
  
4. Kliknij przycisk **OK**.  
  
### <a name="to-set-a-breakpoint-on-a-specific-process"></a>Aby ustawić punkt przerwania dla określonego procesu  
  
1. Pobierz nazwę procesu lub numer IDENTYFIKACYJNy procesu z okna **procesy** .  
  
2. Wybierz punkt przerwania, a następnie otwórz okno dialogowe **Filtr punktu przerwania** , jak w pierwszej procedurze.  
  
3. W oknie dialogowym **Filtr punktu przerwania** wpisz:  
  
     `ProcessName =`  *yourprocessname*  
  
     —lub—  
  
     `ProcessID =`*yourprocessIDnumber*  
  
     Aby utworzyć bardziej skomplikowany filtr, można łączyć klauzule przy użyciu `&` , operatora i, `||` ,, operatora OR, operatora `!` not i nawiasów.  
  
4. Kliknij przycisk **OK**.  
  
### <a name="to-set-a-breakpoint-on-a-specific-thread"></a>Aby ustawić punkt przerwania dla określonego wątku  
  
1. Pobierz nazwę wątku lub numer IDENTYFIKACYJNy wątku z okna **wątki** .  
  
2. Wybierz punkt przerwania i Otwórz okno dialogowe **Filtr punktu przerwania** zgodnie z opisem w pierwszej procedurze.  
  
3. W oknie dialogowym **Filtr punktu przerwania** wpisz:  
  
     `ThreadName =`*yourthreadname*  
  
     —lub—  
  
     `ThreadID =`*yourthreadIDnumber*  
  
     Aby utworzyć bardziej skomplikowany filtr, można łączyć klauzule przy użyciu `&` , operatora i, `||` ,, operatora OR, operatora `!` not i nawiasów.  
  
4. Kliknij przycisk **OK**.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak utworzyć filtr dla punktu przerwania na komputerze o nazwie `marvin` i wątku o nazwie `fourier1` .  
  
```  
(MachineName = marvin) & (ThreadName = fourier1)  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Debuguj aplikacje wielowątkowe](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Debugowanie zdalne](../debugger/remote-debugging.md)   
 [Instrukcje: korzystanie z okna procesy](https://msdn.microsoft.com/0207ce2f-8ceb-4fe7-b2b5-4dd35b035ed7)   
 [Instrukcje: korzystanie z okna wątków](../debugger/how-to-use-the-threads-window.md)   
 [Wątki i procesy](https://msdn.microsoft.com/73d87480-9af3-4d1b-baf5-397d5d876ae6)   
 [Używanie punktów przerwania](../debugger/using-breakpoints.md)
