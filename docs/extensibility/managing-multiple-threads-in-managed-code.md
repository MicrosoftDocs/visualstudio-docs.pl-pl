---
title: 'Jak: Zarządzanie wieloma wątkami w kodzie zarządzanym | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 59730063-cc29-4dae-baff-2234ad8d0c8f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ceaa0af4f57fe374cf9cf4b2dd8b4f40af74a852
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702781"
---
# <a name="how-to-manage-multiple-threads-in-managed-code"></a>Jak: Zarządzanie wieloma wątkami w kodzie zarządzanym
Jeśli masz zarządzane rozszerzenie VSPackage, które wywołuje metody asynchroniczne lub ma operacje, które są wykonywane w wątkach innych niż wątek interfejsu użytkownika programu Visual Studio, należy postępować zgodnie z wytycznymi podanymi poniżej. Można zachować wątek interfejsu użytkownika elastyczne, ponieważ nie trzeba czekać na pracę nad innym wątku, aby zakończyć. Można uczynić kod bardziej wydajne, ponieważ nie masz dodatkowych wątków, które zajmują miejsce w stosie i można uczynić go bardziej niezawodne i łatwiejsze do debugowania, ponieważ można uniknąć zakleszczenia i zawiesza.

 Ogólnie rzecz biorąc można przełączyć się z wątku interfejsu użytkownika do innego wątku lub odwrotnie. Gdy metoda zwraca bieżący wątek jest wątku, z którego został pierwotnie wywołany.

> [!IMPORTANT]
> Poniższe wskazówki używają interfejsów <xref:Microsoft.VisualStudio.Threading> API w obszarze <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> nazw, w szczególności klasy. Interfejsy API w tej przestrzeni [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)]nazw są nowe w pliku . Można uzyskać wystąpienie <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> z <xref:Microsoft.VisualStudio.Shell.ThreadHelper> właściwości `ThreadHelper.JoinableTaskFactory`.

## <a name="switch-from-the-ui-thread-to-a-background-thread"></a>Przełączanie z wątku interfejsu użytkownika na wątek tła

1. Jeśli jesteś w wątku interfejsu użytkownika i chcesz wykonać pracę asynchroniką nad wątkiem w tle, użyj: `Task.Run()`

    ```csharp
    await Task.Run(async delegate{
        // Now you're on a separate thread.
    });
    // Now you're back on the UI thread.

    ```

2. Jeśli jesteś w wątku interfejsu użytkownika i chcesz synchronicznie zablokować podczas wykonywania pracy <xref:System.Threading.Tasks.TaskScheduler> `TaskScheduler.Default` na <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>wątku tła, użyj właściwości wewnątrz:

    ```csharp
    // using Microsoft.VisualStudio.Threading;
    ThreadHelper.JoinableTaskFactory.Run(async delegate {
        await TaskScheduler.Default;
        // You're now on a separate thread.
        DoSomethingSynchronous();
        await OrSomethingAsynchronous();
    });
    ```

## <a name="switch-from-a-background-thread-to-the-ui-thread"></a>Przełączanie z wątku tła do wątku interfejsu użytkownika

1. Jeśli jesteś w wątku w tle i chcesz coś zrobić <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>w wątku interfejsu użytkownika, użyj:

    ```csharp
    // Switch to main thread
    await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();
    ```

     Można użyć <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> metody, aby przełączyć się do wątku interfejsu użytkownika. Ta metoda księguje komunikat do wątku interfejsu użytkownika z kontynuacją bieżącej metody asynchroniczną, a także komunikuje się z resztą struktury wątków, aby ustawić poprawny priorytet i uniknąć zakleszczenia.

     Jeśli metoda wątku tła nie jest asynchroniczne i nie można go asynchroniczne, nadal można użyć `await` składni, aby <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>przełączyć się do wątku interfejsu użytkownika przez zawijanie pracy z , jak w tym przykładzie:

    ```csharp
    ThreadHelper.JoinableTaskFactory.Run(async delegate {
        // Switch to main thread
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();
        // Do your work on the main thread here.
    });
    ```
