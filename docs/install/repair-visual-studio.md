---
title: Napraw program Visual Studio
titleSuffix: ''
description: Dowiedz się, jak naprawić instalację programu Visual Studio 2017
ms.date: 06/15/2020
ms.custom: seodec18
ms.topic: how-to
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: fda72206059e5c14c46d332e44ea0de481004296
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85418967"
---
# <a name="repair-visual-studio"></a>Napraw program Visual Studio

Czasami instalacja programu Visual Studio przestała być uszkodzona lub uszkodzona. Naprawa jest przydatna w przypadku rozwiązywania problemów dotyczących czasu instalacji we wszystkich operacjach instalacji, w tym aktualizacji.

## <a name="when-to-use-repair"></a>Kiedy należy używać naprawy
* Jeśli masz problemy z ładunkiem instalacji. Może się tak zdarzyć, gdy zapisanie pliku na dysk nie powiedzie się i nie można go naprawić przez usunięcie uszkodzonego pliku. Naprawa może ponownie pobrać zbędne pliki. 
* Jeśli masz problemy z pobieraniem po stronie klienta. Przy założeniu, że wystąpiły problemy związane z połączeniem lub serwerem proxy, naprawianie może pomóc. 
* Jeśli masz problemy z aktualizacją programu Visual Studio. Naprawa rozwiązuje wiele typowych problemów z aktualizacją. 

> [!TIP] 
> Jeśli problem z instalacją jest spowodowany problemem związanym z usługą systemu Windows, na przykład Instalator Windows, naprawa może wystąpić z tym samym problemem. Problemy systemowe mogą obejmować przerwane Instalator Windows lub niestabilne połączenie internetowe. Aby wyszukać problem systemowy, użyj raportu o błędach wygenerowanego podczas operacji instalacji.

> [!NOTE] 
> Naprawianie programu Visual Studio powoduje zresetowanie ustawień użytkownika i ponowne zainstalowanie już posiadanych zestawów. Jeśli występuje problem z produktem, Utwórz [bilet opinii programu Visual Studio](https://developercommunity.visualstudio.com/content/problem/post.html?space=8), ponieważ naprawa może nie rozwiązać problemu.

## <a name="how-to-repair"></a>Jak naprawić
::: moniker range="vs-2017"

1. Znajdź **Instalator programu Visual Studio** na komputerze.

     Na przykład na komputerze z systemem Windows 10 z rocznicą aktualizacji lub nowszym wybierz pozycję **Start**, a następnie przewiń do litery **V**, gdzie jest ona wyświetlana jako **Instalator programu Visual Studio**.

   > [!NOTE]
   > Na niektórych komputerach Instalator programu Visual Studio mogą być wyświetlane pod literą **"M"** jako **Instalator Microsoft Visual Studio**.
   >
   > Alternatywnie można znaleźć Instalator programu Visual Studio w następującej lokalizacji: `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. Otwórz Instalator, wybierz pozycję **więcej**, a następnie wybierz polecenie **napraw**.

    ![Napraw program Visual Studio z poziomu Instalator programu Visual Studio](media/repair-visual-studio.png "Napraw program Visual Studio z poziomu Instalator programu Visual Studio")

   > [!NOTE]
   > Naprawianie programu Visual Studio spowoduje zresetowanie środowiska. Lokalne dostosowania, takie jak rozszerzenia dla poszczególnych użytkowników zainstalowane bez podniesienia uprawnień, ustawienia użytkownika i profile, zostaną usunięte. Twoje zsynchronizowane ustawienia, takie jak motywy, kolory i kluczowe powiązania, zostaną przywrócone.
   >

   > [!TIP]
   > Opcja **naprawy** jest wyświetlana tylko w przypadku zainstalowanych wystąpień programu Visual Studio. Jeśli nie widzisz opcji **Repair (Naprawa** ), prawdopodobnie wybrano opcję **więcej** w wersji, która jest wymieniona w Instalator programu Visual Studio jako "dostępna", a nie "zainstalowano".

::: moniker-end

::: moniker range="vs-2019"

1. Znajdź **Instalator programu Visual Studio** na komputerze.

     Na przykład na komputerze z systemem Windows 10 Wybierz pozycję **Start**, a następnie przewiń do litery **V**, gdzie jest ona wyświetlana jako **Instalator programu Visual Studio**.

     ![Otwórz Instalator programu Visual Studio](media/vs-2019/vs-installer-windows-start.png "Otwórz Instalator programu Visual Studio")

     > [!NOTE]
     > Instalator programu Visual Studio można również znaleźć w następującej lokalizacji:
     >
     > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

    Może być konieczne zaktualizowanie Instalatora przed kontynuowaniem. Jeśli tak, postępuj zgodnie z monitami.

1. W instalatorze zapoznaj się z zainstalowaną wersją programu Visual Studio. Następnie wybierz pozycję **więcej**, a następnie wybierz pozycję **napraw**.

     ![Napraw program Visual Studio 2019](media/vs-2019/vs-installer-repair.png "Napraw program Visual Studio 2019")

   > [!NOTE]
   > Naprawianie programu Visual Studio spowoduje zresetowanie środowiska. Lokalne dostosowania, takie jak rozszerzenia dla poszczególnych użytkowników zainstalowane bez podniesienia uprawnień, ustawienia użytkownika i profile, zostaną usunięte. Twoje zsynchronizowane ustawienia, takie jak motywy, kolory i kluczowe powiązania, zostaną przywrócone.
   >

   > [!TIP]
   > Opcja **naprawy** jest wyświetlana tylko w przypadku zainstalowanych wystąpień programu Visual Studio. Jeśli nie widzisz opcji **Repair (Naprawa** ), prawdopodobnie wybrano opcję **więcej** w wersji, która jest wymieniona w Instalator programu Visual Studio jako "dostępna", a nie "zainstalowano".

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz też

* [Instalowanie programu Visual Studio](install-visual-studio.md)
* [Aktualizowanie programu Visual Studio](update-visual-studio.md)
* [Odinstalowywanie programu Visual Studio](uninstall-visual-studio.md)
* [Rozwiązywanie problemów z instalacją i uaktualnieniem programu Visual Studio](troubleshooting-installation-issues.md)
