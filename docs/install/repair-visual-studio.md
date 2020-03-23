---
title: Napraw program Visual Studio
titleSuffix: ''
description: Dowiedz się, jak naprawić instalację programu Visual Studio 2017
ms.date: 07/31/2019
ms.custom: seodec18
ms.topic: conceptual
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 368ca6619a2fcff48cc3bcc7eb70913247b631b2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114738"
---
# <a name="repair-visual-studio"></a>Napraw program Visual Studio

::: moniker range="vs-2017"

Czasami instalacja programu Visual Studio ulega uszkodzeniu lub uszkodzeniu. Naprawa może to naprawić.

1. Znajdź **Instalator programu Visual Studio** na komputerze.

     Na przykład na komputerze z systemem Windows 10 Anniversary Update lub nowszym wybierz pozycję **Start**, a następnie przewiń do litery **V**, gdzie jest ona wymieniona jako **Instalator programu Visual Studio**.

   > [!NOTE]
   > Na niektórych komputerach Instalator programu Visual Studio może być wymieniony pod literą **"M"** jako **Instalator programu Microsoft Visual Studio**.
   >
   > Alternatywnie można znaleźć Instalatora programu Visual Studio w następującej lokalizacji:`C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. Otwórz instalatora, wybierz pozycję **Więcej**, a następnie wybierz pozycję **Napraw .**

    ![Naprawianie programu Visual Studio za podstawie instalatora programu Visual Studio](media/repair-visual-studio.png "Naprawianie programu Visual Studio za podstawie instalatora programu Visual Studio")

   > [!NOTE]
   > Naprawianie programu Visual Studio spowoduje zresetowanie środowiska. Modyfikacje lokalne, takie jak rozszerzenia na użytkownika zainstalowane bez podniesienia uprawnień, ustawienia użytkownika i profile zostaną usunięte. Zostaną przywrócone zsynchronizowane ustawienia, takie jak motywy, kolory, powiązania klawiszy.
   >

   > [!TIP]
   > Opcja **Napraw jest** wyświetlana tylko dla zainstalowanych wystąpień programu Visual Studio. Jeśli nie widzisz **opcji Napraw,** są szanse, że wybrano **więcej** w wersji, która jest wymieniona w Instalatorze programu Visual Studio jako "Dostępne", a nie "Zainstalowane".

::: moniker-end

::: moniker range="vs-2019"

1. Znajdź Instalator programu Visual Studio na komputerze.

     Na przykład na komputerze z systemem Windows 10 wybierz pozycję **Start**, a następnie przewiń do litery **V**, gdzie jest ona wymieniona jako **Instalator programu Visual Studio**.

     ![Otwieranie Instalatora programu Visual Studio](media/vs-2019/vs-installer-windows-start.png "Otwieranie Instalatora programu Visual Studio")

     > [!NOTE]
     > Instalator programu Visual Studio można również znaleźć w następującej lokalizacji:
     >
     > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

    Może być trzeba zaktualizować instalatora przed kontynuowaniem. Jeśli tak, postępuj zgodnie z instrukcjami.

1. W instalatorze poszukaj zainstalowanej wersji programu Visual Studio. Następnie wybierz pozycję **Więcej**, a następnie wybierz pozycję **Napraw .**

     ![Naprawa programu Visual Studio 2019](media/vs-2019/vs-installer-repair.png "Naprawa programu Visual Studio 2019")

   > [!NOTE]
   > Naprawianie programu Visual Studio spowoduje zresetowanie środowiska. Modyfikacje lokalne, takie jak rozszerzenia na użytkownika zainstalowane bez podniesienia uprawnień, ustawienia użytkownika i profile zostaną usunięte. Zostaną przywrócone zsynchronizowane ustawienia, takie jak motywy, kolory, powiązania klawiszy.
   >

   > [!TIP]
   > Opcja **Napraw jest** wyświetlana tylko dla zainstalowanych wystąpień programu Visual Studio. Jeśli nie widzisz **opcji Napraw,** są szanse, że wybrano **więcej** w wersji, która jest wymieniona w Instalatorze programu Visual Studio jako "Dostępne", a nie "Zainstalowane".

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz też

* [Instalacja programu Visual Studio](install-visual-studio.md)
* [Aktualizowanie programu Visual Studio](update-visual-studio.md)
* [Odinstalowywanie programu Visual Studio](uninstall-visual-studio.md)
* [Rozwiązywanie problemów z instalacją i uaktualnieniem programu Visual Studio](troubleshooting-installation-issues.md)
