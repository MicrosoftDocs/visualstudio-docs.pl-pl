---
title: 'Instrukcje: Zarządzanie wieloma wątkami w kodzie zarządzanym | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 59730063-cc29-4dae-baff-2234ad8d0c8f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b5c3f8995d5bfbbbfe890100b0ec1a1230450bb6
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63431318"
---
# <a name="how-to-manage-multiple-threads-in-managed-code"></a>Instrukcje: Zarządzanie wieloma wątkami w kodzie zarządzanym
Jeśli masz zarządzanych rozszerzenia pakietu VSPackage, który wywołuje metody asynchronicznej lub operacji, które są wykonywane w wątkach, innego niż wątek interfejsu użytkownika usługi Visual Studio, należy postępować zgodnie z wytycznymi podanymi poniżej. Wątek interfejsu użytkownika umożliwia zachowanie elastyczny, ponieważ nie trzeba czekać do pracy na inny wątek, aby zakończyć. Użytkownik może uczynić kod bardziej efektywne, ponieważ nie masz dodatkowe wątki, które zajmują miejsce na stosie i możesz przekształcić ją w bardziej niezawodne i łatwiejsze do debugowania, ponieważ uniknięcia zakleszczenia i zawiesza się.

 Ogólnie rzecz biorąc, możesz przełączyć się z wątku interfejsu użytkownika do innego wątku, lub na odwrót. Gdy metoda zwróci wartość, bieżący wątek jest wątek, w którym była pierwotnie używana.

> [!IMPORTANT]
> Poniższe wskazówki przy użyciu interfejsów API w <xref:Microsoft.VisualStudio.Threading> przestrzeni nazw, w szczególności <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> klasy. Interfejsy API w tej przestrzeni nazw są nowością w programie [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)]. Można pobrać wystąpienia <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> z <xref:Microsoft.VisualStudio.Shell.ThreadHelper> właściwość `ThreadHelper.JoinableTaskFactory`.

## <a name="switch-from-the-ui-thread-to-a-background-thread"></a>Przełącz z wątku interfejsu użytkownika do wątku w tle

1. Jeśli korzystasz z wątku interfejsu użytkownika, a co chcesz zrobić asynchroniczne działania na wątku w tle, użyj `Task.Run()`:

    ```csharp
    await Task.Run(async delegate{
        // Now you're on a separate thread.
    });
    // Now you're back on the UI thread.

    ```

2. Jeśli jesteś w wątku interfejsu użytkownika i chcesz zablokować synchronicznie, podczas wykonywania pracy na wątku w tle, użyj <xref:System.Threading.Tasks.TaskScheduler> właściwość `TaskScheduler.Default` wewnątrz <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>:

    ```csharp
    // using Microsoft.VisualStudio.Threading;
    ThreadHelper.JoinableTaskFactory.Run(async delegate {
        await TaskScheduler.Default;
        // You're now on a separate thread.
        DoSomethingSynchronous();
        await OrSomethingAsynchronous();
    });
    ```

## <a name="switch-from-a-background-thread-to-the-ui-thread"></a>Przełącz z wątku w tle do wątku interfejsu użytkownika

1. Jeśli jesteś w wątku tła, i chcesz zrobić coś w wątku interfejsu użytkownika, użyj <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>:

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