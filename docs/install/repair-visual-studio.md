---
title: Napraw program Visual Studio
titleSuffix: ''
description: Dowiedz się, jak naprawić instalację programu Visual Studio 2017
ms.date: 07/31/2019
ms.custom: seodec18
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: ed6b7050d2162fc4e893db6ec4f429fbe3f8eb4f
ms.sourcegitcommit: 5694c5236fa32ba7f5bc1236a853f725ec7557e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/31/2019
ms.locfileid: "68681329"
---
# <a name="repair-visual-studio"></a>Napraw program Visual Studio

::: moniker range="vs-2017"

Czasami instalację programu Visual Studio staje się uszkodzone lub uszkodzony. Naprawa może rozwiązać ten problem.

1. Znajdź **Instalator programu Visual Studio** na komputerze.

     Na przykład na komputerze z systemem Windows 10 rozliczenia aktualizacji lub później, wybierz **Start**, a następnie przewiń do list **V**, w którym znajduje się w **Instalatora programu Visual Studio**.

   > [!NOTE]
   > Na niektórych komputerach Instalatora programu Visual Studio może zostać wyświetlony w obszarze list **"M"** jako **Instalator programu Microsoft Visual Studio**.
   >
   > Alternatywnie można znaleźć Instalatora programu Visual Studio w następującej lokalizacji: `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. Otwórz Instalator, wybierz pozycję **więcej**, a następnie wybierz polecenie **napraw**.

    ![Napraw program Visual Studio z poziomu Instalator programu Visual Studio](media/repair-visual-studio.png "Napraw program Visual Studio z poziomu Instalator programu Visual Studio")

   > [!NOTE]
   > Naprawianie programu Visual Studio spowoduje zresetowanie środowiska. Lokalne dostosowania, takie jak rozszerzenia dla poszczególnych użytkowników zainstalowane bez podniesienia uprawnień, ustawienia użytkownika i profile, zostaną usunięte. Twoje zsynchronizowane ustawienia, takie jak motywy, kolory i kluczowe powiązania, zostaną przywrócone.
   >

   > [!TIP]
   > Opcja **naprawy** jest wyświetlana tylko w przypadku zainstalowanych wystąpień programu Visual Studio. Jeśli nie widzisz opcji **Repair (Naprawa** ), prawdopodobnie wybrano opcję **więcej** w wersji, która jest wymieniona w Instalator programu Visual Studio jako "dostępna", a nie "zainstalowano".

::: moniker-end

::: moniker range="vs-2019"

1. Znajdowanie Instalatora programu Visual Studio na komputerze.

     Na przykład na komputerze z systemem Windows 10, wybierz pozycję **Start**, a następnie przewiń do list **V**, w którym znajduje się w **Instalatora programu Visual Studio**.

     ![Otwórz Instalator programu Visual Studio](media/vs-2019/vs-installer-windows-start.png "Otwórz Instalator programu Visual Studio")

     > [!NOTE]
     > Instalator programu Visual Studio można również znaleźć w następującej lokalizacji:
     >
     > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

    Może być konieczne zaktualizowanie Instalatora przed kontynuowaniem. Jeśli tak, postępuj zgodnie z monitami.

1. W instalatorze zapoznaj się z zainstalowaną wersją programu Visual Studio. Następnie wybierz pozycję **więcej**, a następnie wybierz pozycję **napraw**.

     ![Repair Visual Studio 2019](media/vs-2019/vs-installer-repair.png "Repair Visual Studio 2019")

   > [!NOTE]
   > Naprawianie programu Visual Studio spowoduje zresetowanie środowiska. Lokalne dostosowania, takie jak rozszerzenia dla poszczególnych użytkowników zainstalowane bez podniesienia uprawnień, ustawienia użytkownika i profile, zostaną usunięte. Twoje zsynchronizowane ustawienia, takie jak motywy, kolory i kluczowe powiązania, zostaną przywrócone.
   >

   > [!TIP]
   > Opcja **naprawy** jest wyświetlana tylko w przypadku zainstalowanych wystąpień programu Visual Studio. Jeśli nie widzisz opcji **Repair (Naprawa** ), prawdopodobnie wybrano opcję **więcej** w wersji, która jest wymieniona w Instalator programu Visual Studio jako "dostępna", a nie "zainstalowano".

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz także

* [Instalowanie programu Visual Studio](install-visual-studio.md)
* [Aktualizowanie programu Visual Studio](update-visual-studio.md)
* [Odinstalowywanie programu Visual Studio](uninstall-visual-studio.md)
* [Rozwiązywanie problemów z instalacją i uaktualnieniem programu Visual Studio](troubleshooting-installation-issues.md)
