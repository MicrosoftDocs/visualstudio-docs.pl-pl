---
title: 'Instrukcje: debugowanie w klastrze o wysokiej wydajności | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- cluster debugging
- high-performance debugging
ms.assetid: a2f0eb07-840e-4f95-a1b1-9509217e5b8f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d95c6eeadfdf1bb90471997712299ae03a945be8
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72733664"
---
# <a name="how-to-debug-on-a-high-performance-cluster-c-visual-basic-c"></a>Instrukcje: debugowanie w klastrze o wysokiej wydajności (C#, Visual Basic,) C++

Debugowanie programu przetwarzania wieloprocesowego w klastrze o wysokiej wydajności jest podobne do debugowania zwykłego programu na komputerze zdalnym. Jednak istnieją pewne dodatkowe zagadnienia. Ogólne wymagania dotyczące instalacji zdalnej można znaleźć w temacie [zdalne debugowanie](../debugger/remote-debugging.md).

 Podczas debugowania w klastrze o wysokiej wydajności można używać wszystkich okien debugowania [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] i technik, które są dostępne do zdalnego debugowania. Ponieważ debugowanie jest przeprowadzane zdalnie, nie jest jednak dostępne okno konsoli zewnętrznej.

 Okno **wątków** okna i **procesy** są szczególnie przydatne w przypadku debugowania aplikacji równoległych. Aby uzyskać porady dotyczące korzystania z tych okien, zobacz [How to: Use the processs Window](/previous-versions/visualstudio/visual-studio-2010/7h8h5sdw(v=vs.100)) and [Instruktaż: Debug using the Threads Window](../debugger/how-to-use-the-threads-window.md).

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

     Aby utworzyć bardziej skomplikowany filtr, można łączyć klauzule przy użyciu `&`, operatora i, `||`, operatora OR, `!`, operatora NOT i nawiasów.

4. Kliknij przycisk **OK**.

### <a name="to-set-a-breakpoint-on-a-specific-process"></a>Aby ustawić punkt przerwania dla określonego procesu

1. Pobierz nazwę procesu lub numer IDENTYFIKACYJNy procesu z okna **procesy** .

2. Wybierz punkt przerwania, a następnie otwórz okno dialogowe **Filtr punktu przerwania** , jak w pierwszej procedurze.

3. W oknie dialogowym **Filtr punktu przerwania** wpisz:

     `ProcessName =`  *yourprocessname*

     —lub—

     `ProcessID =` *yourprocessIDnumber*

     Aby utworzyć bardziej skomplikowany filtr, można łączyć klauzule przy użyciu `&`, operatora i, `||`, operatora OR, `!`, operatora NOT i nawiasów.

4. Kliknij przycisk **OK**.

### <a name="to-set-a-breakpoint-on-a-specific-thread"></a>Aby ustawić punkt przerwania dla określonego wątku

1. Pobierz nazwę wątku lub numer IDENTYFIKACYJNy wątku z okna **wątki** .

2. Wybierz punkt przerwania i Otwórz okno dialogowe **Filtr punktu przerwania** zgodnie z opisem w pierwszej procedurze.

3. W oknie dialogowym **Filtr punktu przerwania** wpisz:

     `ThreadName =` *yourthreadname*

     —lub—

     `ThreadID =` *yourthreadIDnumber*

     Aby utworzyć bardziej skomplikowany filtr, można łączyć klauzule przy użyciu `&`, operatora i, `||`, operatora OR, `!`, operatora NOT i nawiasów.

4. Kliknij przycisk **OK**.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje, jak utworzyć filtr dla punktu przerwania na komputerze o nazwie `marvin` i wątku o nazwie `fourier1`.

`(MachineName = marvin) & (ThreadName = fourier1)`

## <a name="see-also"></a>Zobacz także
- [Debugowanie aplikacji wielowątkowych](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Debugowanie zdalne](../debugger/remote-debugging.md)
- [Instrukcje: korzystanie z okna procesy](/previous-versions/visualstudio/visual-studio-2010/7h8h5sdw(v=vs.100))
- [Rozpocznij debugowanie aplikacji wielowątkowych](../debugger/get-started-debugging-multithreaded-apps.md)
- [Wątki i procesy](/previous-versions/visualstudio/visual-studio-2010/ms164740(v=vs.100))
- [Używanie punktów przerwania](../debugger/using-breakpoints.md)