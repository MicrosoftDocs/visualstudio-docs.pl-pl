---
title: 'Instrukcje: Zarządzanie wieloma wątkami w kodzie zarządzanym | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 59730063-cc29-4dae-baff-2234ad8d0c8f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1fe5cef9f7aebcbfc93ffd057a109647e45b5967
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "86387073"
---
# <a name="how-to-manage-multiple-threads-in-managed-code"></a>Instrukcje: Zarządzanie wieloma wątkami w kodzie zarządzanym
Jeśli masz zarządzane rozszerzenie pakietu VSPackage, które wywołuje metody asynchroniczne lub zawiera operacje wykonywane w wątkach innych niż wątek interfejsu użytkownika programu Visual Studio, należy postępować zgodnie z wytycznymi podanymi poniżej. Wątek interfejsu użytkownika można zachować, ponieważ nie musi czekać na zakończenie pracy w innym wątku. Kod można zwiększyć wydajnie, ponieważ nie masz dodatkowych wątków, które zajmują miejsce na stosie, i możesz być bardziej niezawodny i łatwiejszy do debugowania, ponieważ uniemożliwiasz zakleszczenie i nieodpowiadający kod.

 Ogólnie rzecz biorąc, można przełączać się z wątku interfejsu użytkownika do innego wątku lub odwrotnie. Gdy metoda zwraca, bieżący wątek jest wątkiem, z którego pierwotnie został wywołany.

> [!IMPORTANT]
> Poniższe wskazówki używają interfejsów API w <xref:Microsoft.VisualStudio.Threading> przestrzeni nazw, w szczególności <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> klasy. Interfejsy API w tym obszarze nazw są nowością w programie [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)] . Można uzyskać wystąpienie elementu z <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> <xref:Microsoft.VisualStudio.Shell.ThreadHelper> właściwości `ThreadHelper.JoinableTaskFactory` .

## <a name="switch-from-the-ui-thread-to-a-background-thread"></a>Przełączanie z wątku interfejsu użytkownika do wątku w tle

1. Jeśli jesteś w wątku interfejsu użytkownika i chcesz wykonać asynchroniczne prace w wątku w tle, użyj `Task.Run()` :

    ```csharp
    await Task.Run(async delegate{
        // Now you're on a separate thread.
    });
    // Now you're back on the UI thread.

    ```

2. Jeśli jesteś w wątku interfejsu użytkownika i chcesz synchronicznie blokować podczas wykonywania pracy w wątku w tle, użyj <xref:System.Threading.Tasks.TaskScheduler> właściwości `TaskScheduler.Default` wewnątrz <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A> :

    ```csharp
    // using Microsoft.VisualStudio.Threading;
    ThreadHelper.JoinableTaskFactory.Run(async delegate {
        await TaskScheduler.Default;
        // You're now on a separate thread.
        DoSomethingSynchronous();
        await OrSomethingAsynchronous();
    });
    ```

## <a name="switch-from-a-background-thread-to-the-ui-thread"></a>Przełączanie z wątku w tle do wątku interfejsu użytkownika

1. Jeśli jesteś w wątku w tle i chcesz wykonać coś w wątku interfejsu użytkownika, użyj <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> :

    ```csharp
    // Switch to main thread
    await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();
    ```

     Możesz użyć metody, <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> Aby przełączyć się do wątku interfejsu użytkownika. Ta metoda wysyła komunikat do wątku interfejsu użytkownika z kontynuacją bieżącej metody asynchronicznej, a także komunikuje się z pozostałą częścią środowiska wątkowego, aby ustawić prawidłowy priorytet i uniknąć zakleszczeń.

     Jeśli metoda wątku w tle nie jest asynchroniczna i nie można jej asynchronicznie, nadal można użyć `await` składni do przełączenia do wątku interfejsu użytkownika, zawijając swoją służbę <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A> , tak jak w poniższym przykładzie:

    ```csharp
    ThreadHelper.JoinableTaskFactory.Run(async delegate {
        // Switch to main thread
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();
        // Do your work on the main thread here.
    });
    ```
