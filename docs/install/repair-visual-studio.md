---
title: Napraw program Visual Studio
titleSuffix: ''
description: Dowiedz się, jak naprawić instalację programu Visual Studio 2017
ms.date: 03/30/2019
ms.custom: seodec18
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 690fe29373e80d9dfc560a616d0e914731d9b6cf
ms.sourcegitcommit: 0a2fdc23faee77187e10a1c19665ba5a1ac68e72
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/10/2019
ms.locfileid: "59477529"
---
# <a name="repair-visual-studio"></a>Napraw program Visual Studio

::: moniker range="vs-2017"

Czasami instalację programu Visual Studio staje się uszkodzone lub uszkodzony. Naprawa może rozwiązać ten problem.

1. Znajdź **Instalatora programu Visual Studio** na tym komputerze.

     Na przykład na komputerze z systemem Windows 10 rozliczenia aktualizacji lub później, wybierz **Start**, a następnie przewiń do list **V**, w którym znajduje się w **Instalatora programu Visual Studio**.

   > [!NOTE]
   > Na niektórych komputerach Instalatora programu Visual Studio może zostać wyświetlony w obszarze list **"M"** jako **Instalator programu Microsoft Visual Studio**.
   >
   > Alternatywnie można znaleźć Instalatora programu Visual Studio w następującej lokalizacji: `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. Otwórz Instalator, wybierz polecenie **więcej**, a następnie wybierz **naprawy**.

    ![Napraw program Visual Studio z poziomu Instalatora programu Visual Studio](media/repair-visual-studio.png "naprawić program Visual Studio z poziomu Instalatora programu Visual Studio")
    
   > [!NOTE]
   > Naprawa programu Visual Studio spowoduje zresetowanie środowiska. Lokalne dostosowania, takie jak rozszerzenia poszczególnych użytkowników zainstalowane bez podniesienia uprawnień, ustawienia użytkownika i profile zostaną usunięte. Zsynchronizowane ustawienia takie jak motywy, kolory, klawiszy zostaną przywrócone.
   >

   > [!TIP]
   > **Naprawy** opcja jest dostępna tylko w przypadku zainstalowanych wystąpień programu Visual Studio. Jeśli nie widzisz **naprawy** opcji jest szansa, że wybrano **więcej** w wersji, który jest wymieniony w Instalatorze programu Visual Studio jako "Dostępne" zamiast "Zainstalowano".

::: moniker-end

::: moniker range="vs-2019"

1. Znajdowanie Instalatora programu Visual Studio na komputerze.

     Na przykład na komputerze z systemem Windows 10, wybierz pozycję **Start**, a następnie przewiń do list **V**, w którym znajduje się w **Instalatora programu Visual Studio**.

     ![Otwórz Instalator programu Visual Studio](media/vs2019-visual-studio-installer.png "Otwórz Instalatora programu Visual Studio")

     > [!NOTE]
     > Instalator programu Visual Studio można również znaleźć w następującej lokalizacji:
     >
     > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

    Trzeba zaktualizować Instalatora przed kontynuowaniem. Jeśli tak, postępuj zgodnie z monitami.

1. W oknie Instalatora poszukaj wersji programu Visual Studio, który został zainstalowany. Następnie wybierz pozycję **więcej**, a następnie wybierz **naprawy**.

     ![Repair Visual Studio 2019](media/vs-2019/vs-installer-repair.png "Repair Visual Studio 2019")

   > [!NOTE]
   > Naprawa programu Visual Studio spowoduje zresetowanie środowiska. Lokalne dostosowania, takie jak rozszerzenia poszczególnych użytkowników zainstalowane bez podniesienia uprawnień, ustawienia użytkownika i profile zostaną usunięte. Zsynchronizowane ustawienia takie jak motywy, kolory, klawiszy zostaną przywrócone.
   >

   > [!TIP]
   > **Naprawy** opcja jest dostępna tylko w przypadku zainstalowanych wystąpień programu Visual Studio. Jeśli nie widzisz **naprawy** opcji jest szansa, że wybrano **więcej** w wersji, który jest wymieniony w Instalatorze programu Visual Studio jako "Dostępne" zamiast "Zainstalowano".

::: moniker-end


[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz także

* [Instalowanie programu Visual Studio](install-visual-studio.md)
* [Aktualizowanie programu Visual Studio](update-visual-studio.md)
* [Odinstalowywanie programu Visual Studio](uninstall-visual-studio.md)
* [Rozwiązywanie problemów instalacji i uaktualniania programu Visual Studio](troubleshooting-installation-issues.md)
