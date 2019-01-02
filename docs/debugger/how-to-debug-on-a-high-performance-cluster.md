---
title: 'Instrukcje: Debugowanie w klastrze o wysokiej wydajności | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- cluster debugging
- high-perfomance debugging
ms.assetid: a2f0eb07-840e-4f95-a1b1-9509217e5b8f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f2d551387b0b784d896ab435f61f9366663e6219
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53966459"
---
# <a name="how-to-debug-on-a-high-performance-cluster"></a>Instrukcje: Debugowanie w klastrze o wysokiej wydajności
Debugowanie programu przetwarzania wieloprocesowego w klastrze o wysokiej wydajności jest podobne do debugowania zwykłego programu na komputerze zdalnym. Istnieją jednak pewne dodatkowe zagadnienia. Aby uzyskać wymagania ogólne instalacji zdalnej, zobacz [zdalne debugowanie](../debugger/remote-debugging.md).  
  
 Podczas debugowania w klastrze o wysokiej wydajności, można używać wszystkich [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] debugowania systemu windows i technik, które są dostępne dla zdalnego debugowania. Ponieważ przeprowadzasz debugowanie zdalne, jednak zewnętrzne okno konsoli nie jest dostępna.  
  
 **Wątków** okna i **procesy** są szczególnie przydatne podczas debugowania aplikacji równoległych. Aby uzyskać porady na temat sposobu korzystania z tych okien, zobacz [jak: Korzystanie z okna procesów](/previous-versions/visualstudio/visual-studio-2010/7h8h5sdw(v=vs.100)) i [instruktażu: Debugowanie za pomocą okna wątki](../debugger/how-to-use-the-threads-window.md).  
  
 W poniższych procedurach przedstawiono kilka technik, które są szczególnie przydatne podczas debugowania w klastrze o wysokiej wydajności.  
  
 Podczas debugowania aplikacji równoległej, można ustawić punkt przerwania w określonym wątku, proces lub komputer. Można to zrobić, tworząc normalny punkt przerwania, a następnie dodając filtr punktu przerwania.  
  
### <a name="to-open-the-breakpoint-filter-dialog-box"></a>Aby otworzyć okno dialogowe Filtr punktów przerwania  
  
1.  Kliknij prawym przyciskiem myszy symbol punktu przerwania w oknie źródła, **dezasemblacji** oknie **stos wywołań** oknie lub **punktów przerwania** okna.  
  
2.  W menu skrótów kliknij **filtru**. Ta opcja może pojawić się u góry poziomie lub w podmenu w obszarze **punktów przerwania**.  
  
### <a name="to-set-a-breakpoint-on-a-specific-computer"></a>Aby ustawić punkt przerwania na określonym komputerze  
  
1.  Pobierz nazwę komputera z **procesy** okna.  
  
2.  Zaznacz punkt przerwania, a następnie otwórz **filtr punktów przerwania** okno dialogowe, zgodnie z opisem w poprzedniej procedurze.  
  
3.  W **filtr punktów przerwania** okno dialogowe, typ:  
  
     MachineName =*yourmachinename*  
  
     Aby utworzyć bardziej złożony filtr, można połączyć klauzule za pomocą `&`, operator i `||`, operatora OR `!`, operatora NOT i nawiasów.  
  
4.  Kliknij przycisk **OK**.  
  
### <a name="to-set-a-breakpoint-on-a-specific-process"></a>Aby ustawić punkt przerwania w określonym procesie  
  
1.  Pobierz nazwę procesu lub numer identyfikacyjny procesu z **procesy** okna.  
  
2.  Zaznacz punkt przerwania, a następnie otwórz **filtr punktów przerwania** okno dialogowe, jak w pierwszej procedurze.  
  
3.  W **filtr punktów przerwania** okno dialogowe, typ:  
  
     `ProcessName =`  *yourprocessname*  
  
     —lub—  
  
     `ProcessID =` *yourprocessIDnumber*  
  
     Aby utworzyć bardziej złożony filtr, można połączyć klauzule za pomocą `&`, operator i `||`, operatora OR `!`, operatora NOT i nawiasów.  
  
4.  Kliknij przycisk **OK**.  
  
### <a name="to-set-a-breakpoint-on-a-specific-thread"></a>Aby ustawić punkt przerwania w określonym wątku  
  
1.  Pobierz nazwę wątku lub numer identyfikacyjny wątku z **wątków** okna.  
  
2.  Zaznacz punkt przerwania, a następnie otwórz **filtr punktów przerwania** okno dialogowe, zgodnie z opisem w pierwszej procedurze.  
  
3.  W **filtr punktów przerwania** okno dialogowe, typ:  
  
     `ThreadName =` *yourthreadname*  
  
     —lub—  
  
     `ThreadID =` *yourthreadIDnumber*  
  
     Aby utworzyć bardziej złożony filtr, można połączyć klauzule za pomocą `&`, operator i `||`, operatora OR `!`, operatora NOT i nawiasów.  
  
4.  Kliknij przycisk **OK**.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak utworzyć filtr dla punktu przerwania na komputerze o nazwie `marvin` i wątek o nazwie `fourier1`.  
  
`(MachineName = marvin) & (ThreadName = fourier1)`  

  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie aplikacji wielowątkowych](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Debugowanie zdalne](../debugger/remote-debugging.md)   
 [Instrukcje: Korzystanie z okna procesów](/previous-versions/visualstudio/visual-studio-2010/7h8h5sdw(v=vs.100))   
 [Rozpoczynanie debugowania aplikacji wielowątkowych](../debugger/get-started-debugging-multithreaded-apps.md)   
 [Wątków i procesów](/previous-versions/visualstudio/visual-studio-2010/ms164740(v=vs.100))   
 [Używanie punktów przerwania](../debugger/using-breakpoints.md)