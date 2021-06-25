---
title: 'How to: Managing Multiple Threads in Managed Code | (Jak zarządzać wieloma wątkami w zarządzanych plikach | Microsoft Docs'
description: Dowiedz się, jak zarządzać wieloma wątkami w kodzie, jeśli zarządzane rozszerzenie vspackage wywołuje metody asynchroniczne lub ma operacje poza Visual Studio interfejsu użytkownika.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 59730063-cc29-4dae-baff-2234ad8d0c8f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 39319b748dd41c6936e7b70e20243202452fae67
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903089"
---
# <a name="how-to-manage-multiple-threads-in-managed-code"></a>Jak zarządzać wieloma wątkami w kodzie zarządzanym
Jeśli masz zarządzane rozszerzenie VSPackage, które wywołuje metody asynchroniczne lub wykonuje operacje na wątkach innych niż Visual Studio wątku interfejsu użytkownika, postępuj zgodnie z poniższymi wskazówkami. Wątek interfejsu użytkownika może być dynamiczny, ponieważ nie musi czekać na zakończenie pracy nad innym wątkiem. Możesz sprawić, że kod będzie bardziej wydajny, ponieważ nie masz dodatkowych wątków, które zabrały miejsce na stosie, i sprawić, że będzie bardziej niezawodny i łatwiejszy do debugowania, ponieważ unikniesz zakleszczeń i nieosiągalnego kodu.

 Ogólnie rzecz biorąc, możesz przełączyć się z wątku interfejsu użytkownika na inny wątek lub na odwrót. Gdy metoda zwraca wartość , bieżący wątek jest wątkiem, z którego pierwotnie został wywołany.

> [!IMPORTANT]
> Poniższe wskazówki korzystają z interfejsów API w przestrzeni <xref:Microsoft.VisualStudio.Threading> nazw , a w szczególności w klasie <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> . Interfejsy API w tej przestrzeni nazw są nowe w programie [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)] . Wystąpienie obiektu można pobrać <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> z <xref:Microsoft.VisualStudio.Shell.ThreadHelper> właściwości `ThreadHelper.JoinableTaskFactory` .

## <a name="switch-from-the-ui-thread-to-a-background-thread"></a>Przełączanie z wątku interfejsu użytkownika na wątek w tle

1. Jeśli jesteś w wątku interfejsu użytkownika i chcesz wykonać asynchroniczną pracę w wątku w tle, użyj metody `Task.Run()` :

    ```csharp
    await Task.Run(async delegate{
        // Now you're on a separate thread.
    });
    // Now you're back on the UI thread.

    ```

2. Jeśli jesteś w wątku interfejsu użytkownika i chcesz synchronicznie blokować podczas wykonywania pracy w wątku w tle, użyj <xref:System.Threading.Tasks.TaskScheduler> właściwości `TaskScheduler.Default` wewnątrz obiektu <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A> :

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

1. Jeśli jesteś w wątku w tle i chcesz coś zrobić w wątku interfejsu użytkownika, użyj funkcji <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> :

    ```csharp
    // Switch to main thread
    await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();
    ```

     Możesz użyć metody <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> , aby przełączyć się do wątku interfejsu użytkownika. Ta metoda publikuje komunikat w wątku interfejsu użytkownika z kontynuacją bieżącej metody asynchronicznej, a także komunikuje się z resztą struktury wątkowej w celu ustawienia poprawnego priorytetu i uniknięcia zakleszczeń.

     Jeśli metoda wątku w tle nie jest asynchroniczna i nie można jej ustawić jako asynchroniczną, nadal możesz użyć składni , aby przełączyć się do wątku interfejsu użytkownika, opakowując swoją pracę za pomocą funkcji , jak w poniższym `await` <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A> przykładzie:

    ```csharp
    ThreadHelper.JoinableTaskFactory.Run(async delegate {
        // Switch to main thread
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();
        // Do your work on the main thread here.
    });
    ```
