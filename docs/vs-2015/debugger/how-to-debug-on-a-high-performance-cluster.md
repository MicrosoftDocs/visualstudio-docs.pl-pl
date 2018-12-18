---
title: 'Porady: debugowanie w klastrze o wysokiej wydajności | Dokumentacja firmy Microsoft'
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
helpviewer_keywords:
- cluster debugging
- high-perfomance debugging
ms.assetid: a2f0eb07-840e-4f95-a1b1-9509217e5b8f
caps.latest.revision: 27
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 75f2a96df18137f04b8b7637940c70378842e23d
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51747733"
---
# <a name="how-to-debug-on-a-high-performance-cluster"></a>Porady: debugowanie w klastrze o wysokiej wydajności
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Debugowanie programu przetwarzania wieloprocesowego w klastrze o wysokiej wydajności jest podobne do debugowania zwykłego programu na komputerze zdalnym. Istnieją jednak pewne dodatkowe zagadnienia. Aby uzyskać wymagania ogólne instalacji zdalnej, zobacz [zdalne debugowanie](../debugger/remote-debugging.md).  
  
 Podczas debugowania w klastrze o wysokiej wydajności, można używać wszystkich [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] debugowania systemu windows i technik, które są dostępne dla zdalnego debugowania. Ponieważ przeprowadzasz debugowanie zdalne, jednak zewnętrzne okno konsoli nie jest dostępna.  
  
 **Wątków** okna i **procesy** są szczególnie przydatne podczas debugowania aplikacji równoległych. Aby uzyskać porady na temat sposobu korzystania z tych okien, zobacz [porady: Korzystanie z okna procesów](http://msdn.microsoft.com/en-us/0207ce2f-8ceb-4fe7-b2b5-4dd35b035ed7) i [porady: Korzystanie z okna wątków](../debugger/how-to-use-the-threads-window.md).  
  
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
  
```  
(MachineName = marvin) & (ThreadName = fourier1)  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie aplikacji wielowątkowych](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Debugowanie zdalne](../debugger/remote-debugging.md)   
 [Porady: Korzystanie z okna procesów](http://msdn.microsoft.com/en-us/0207ce2f-8ceb-4fe7-b2b5-4dd35b035ed7)   
 [Porady: Korzystanie z okna wątków](../debugger/how-to-use-the-threads-window.md)   
 [Wątków i procesów](http://msdn.microsoft.com/en-us/73d87480-9af3-4d1b-baf5-397d5d876ae6)   
 [Używanie punktów przerwania](../debugger/using-breakpoints.md)



