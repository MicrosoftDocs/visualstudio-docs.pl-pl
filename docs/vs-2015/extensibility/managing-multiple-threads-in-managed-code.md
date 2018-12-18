---
title: Zarządzanie wieloma wątkami w kodzie zarządzanym | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 59730063-cc29-4dae-baff-2234ad8d0c8f
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a33b17ddc0eb2d6169761260905b9bf056a4c55e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51802359"
---
# <a name="managing-multiple-threads-in-managed-code"></a>Zarządzanie wieloma wątkami w kodzie zarządzanym
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jeśli masz zarządzanych rozszerzenia pakietu VSPackage, który wywołuje metody asynchronicznej lub operacji, które są wykonywane w wątkach, innego niż wątek interfejsu użytkownika usługi Visual Studio, należy postępować zgodnie z wytycznymi podanymi poniżej. Wątek interfejsu użytkownika umożliwia zachowanie elastyczny, ponieważ nie trzeba czekać do pracy na inny wątek, aby zakończyć. Użytkownik może uczynić kod bardziej efektywne, ponieważ nie masz dodatkowe wątki, które zajmują miejsce na stosie i możesz przekształcić ją w bardziej niezawodne i łatwiejsze do debugowania, ponieważ uniknięcia zakleszczenia i zawiesza się.  
  
 Ogólnie rzecz biorąc, możesz przełączyć się z wątku interfejsu użytkownika do innego wątku, lub na odwrót. Gdy metoda zwróci wartość, bieżący wątek jest wątek, w którym była pierwotnie używana.  
  
> [!IMPORTANT]
>  Poniższe wskazówki przy użyciu interfejsów API w <xref:Microsoft.VisualStudio.Threading> przestrzeni nazw, w szczególności <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> klasy. Interfejsy API w tej przestrzeni nazw są nowością w programie [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]. Można pobrać wystąpienia <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> z <xref:Microsoft.VisualStudio.Shell.ThreadHelper> właściwość `ThreadHelper.JoinableTaskFactory`.  
  
## <a name="switching-from-the-ui-thread-to-a-background-thread"></a>Przełączenie z wątku interfejsu użytkownika na wątku w tle  
  
1.  Jeśli jesteś w wątku interfejsu użytkownika i chcesz zrobić asynchroniczne działania na wątku w tle, należy użyć Task.Run():  
  
    ```csharp  
    await Task.Run(async delegate{  
        // Now you’re on a separate thread.  
    });  
    // Now you’re back on the UI thread.  
  
    ```  
  
2.  Jeśli jesteś w wątku interfejsu użytkownika i chcesz zablokować synchronicznie, podczas wykonywania pracy na wątku w tle, użyj <xref:System.Threading.Tasks.TaskScheduler> właściwość `TaskScheduler.Default` wewnątrz <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>:  
  
    ```csharp  
    // using Microsoft.VisualStudio.Threading;  
    ThreadHelper.JoinableTaskFactory.Run(async delegate {  
        await TaskScheduler.Default;  
        // You're now on a separate thread.  
        DoSomethingSynchronous();  
        await OrSomethingAsynchronous();  
    });  
    ```  
  
## <a name="switching-from-a-background-thread-to-the-ui-thread"></a>Przełączanie z wątku w tle do wątku interfejsu użytkownika  
  
1.  Jeśli jesteś w wątku tła, i chcesz zrobić coś w wątku interfejsu użytkownika, użyj <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>:  
  
    ```csharp  
    // Switch to main thread  
    await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();  
    ```  
  
     Możesz użyć <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> metodę, aby przełączyć się do wątku interfejsu użytkownika. Ta metoda wysyła komunikat do wątku interfejsu użytkownika o kontynuowanie bieżącej metody asynchronicznej, a także komunikuje się z pozostałą częścią wątkowości platformę, by ustawić priorytet prawidłowe i uniknięcia zakleszczenia.  
  
     Jeśli nie możesz obejrzeć asynchronicznego metodę wątku tła jest asynchroniczne, możesz nadal używać `await` składni, aby przełączyć się do wątku interfejsu użytkownika dzięki zawijaniu pracy przy użyciu <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>, jak w tym przykładzie:  
  
    ```csharp  
    ThreadHelper.JoinableTaskFactory.Run(async delegate {  
        // Switch to main thread  
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();  
        // Do your work on the main thread here.  
    });  
    ```

