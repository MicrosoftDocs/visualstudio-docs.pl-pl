---
title: Napraw program Visual Studio
titleSuffix: ''
description: Dowiedz się, jak naprawić instalację programu Visual Studio 2017
ms.date: 10/12/2020
ms.custom: acquisition
ms.topic: how-to
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 5fd791b035bc99d46f53d499339a9e9f80a42905
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2021
ms.locfileid: "112306946"
---
# <a name="repair-visual-studio"></a>Napraw program Visual Studio

Czasami instalacja Visual Studio uszkodzona lub uszkodzona. Naprawa jest przydatna do rozwiązywania problemów z czasem instalacji we wszystkich operacjach instalacji, w tym aktualizacjach.

## <a name="when-to-use-repair"></a>Kiedy należy używać naprawy
* Jeśli masz problemy z ładunkiem instalacyjnym. Może się to zdarzyć, gdy zapisywanie pliku na dysku nie powiedzie się i nie można go naprawić przez usunięcie uszkodzonego pliku. Naprawa może ponownie uzyskać potrzebne pliki. 
* Jeśli masz problemy z pobieraniem po stronie klienta. Jeśli rozwiązano problemy z połączeniem lub serwerem proxy, naprawa może pomóc. 
* Jeśli masz problemy z aktualizowaniem Visual Studio. Naprawa rozwiązuje wiele typowych problemów z aktualizacjami. 

> [!TIP] 
> Jeśli problem z instalowaniem jest spowodowany przez problem w podstawowej usłudze systemu Windows, na przykład Instalator Windows, naprawa może spowodować ten sam problem. Problemy systemowe mogą obejmować przerwane Instalator Windows niestabilne połączenie internetowe. Aby sprawdzić problem systemowy, użyj raportu o błędzie wygenerowanego podczas operacji instalacji.

> [!NOTE] 
> Naprawianie Visual Studio resetuje ustawienia użytkownika i ponownie instaluje już posiadane zestawy. Jeśli występuje problem z produktem, utwórz bilet Visual Studio [opinii,](https://aka.ms/feedback/suggest?space=8)ponieważ naprawa może nie rozwiązać problemu.

## <a name="how-to-repair"></a>Jak naprawić
::: moniker range="vs-2017"

1. Znajdź **Instalator programu Visual Studio** na komputerze.

     Na przykład na komputerze z systemem Rocznicowa aktualizacja systemu Windows 10 lub nowszym wybierz pozycję **Uruchom,** a następnie przewiń do litery **V,** gdzie jest ona wymieniona jako **Instalator programu Visual Studio**.

   > [!NOTE]
   > Na niektórych komputerach Instalator programu Visual Studio być wyświetlane pod literą **"M"** jako Microsoft Visual Studio **Instalatora** programu .
   >
   > Alternatywnie możesz znaleźć Instalator programu Visual Studio w następującej lokalizacji: `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. Otwórz instalatora, wybierz **pozycję Więcej,** a następnie wybierz pozycję **Napraw.**

    ![Napraw Visual Studio z Instalator programu Visual Studio](media/repair-visual-studio.png "Napraw Visual Studio z Instalator programu Visual Studio")

   > [!NOTE]
   > Naprawienie Visual Studio spowoduje zresetowanie środowiska. Dostosowania lokalne, takie jak rozszerzenia dla per-user zainstalowane bez podniesienia uprawnień, ustawień użytkownika i profilów, zostaną usunięte. Zsynchronizowane ustawienia, takie jak motywy, kolory i powiązania kluczy, zostaną przywrócone.
   >

   > [!TIP]
   > Opcja **Napraw** jest dostępna tylko dla zainstalowanych wystąpień Visual Studio. Jeśli nie widzisz  opcji Napraw, istnieje prawdopodobieństwo,  że wybrano opcję Więcej w wersji, która jest wymieniona na liście Instalator programu Visual Studio jako "Dostępne", a nie "Zainstalowane".

::: moniker-end

::: moniker range=">=vs-2019"

1. Znajdź **Instalator programu Visual Studio** na komputerze.

     Na stronie menu Start Windows możesz wyszukać "instalatora".

     ![Instalator programu Visual Studio](media/vs-2019/visual-studio-installer.png "Wyszukaj Instalator programu Visual Studio")

     > [!NOTE]
     > Możesz również znaleźć Instalator programu Visual Studio w następującej lokalizacji:
     >
     > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

    Przed kontynuowaniem może być konieczne zaktualizowanie instalatora. Jeśli tak, postępuj zgodnie z monitami.

1. W instalatorze poszukaj zainstalowanej wersji Visual Studio programu . Następnie wybierz pozycję **Więcej,** a następnie wybierz pozycję **Napraw.**

     ![Repair Visual Studio 2019](media/vs-2019/vs-installer-repair.png "Repair Visual Studio 2019")

   > [!NOTE]
   > Naprawienie Visual Studio spowoduje zresetowanie środowiska. Dostosowania lokalne, takie jak rozszerzenia dla per-user zainstalowane bez podniesienia uprawnień, ustawień użytkownika i profilów, zostaną usunięte. Zsynchronizowane ustawienia, takie jak motywy, kolory i powiązania kluczy, zostaną przywrócone.
   >

   > [!TIP]
   > Opcja **Napraw** jest dostępna tylko dla zainstalowanych wystąpień Visual Studio. Jeśli nie widzisz  opcji Napraw, istnieje prawdopodobieństwo,  że wybrano opcję Więcej w wersji, która jest wymieniona na liście Instalator programu Visual Studio jako "Dostępne", a nie "Zainstalowane".

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz też

* [Instalowanie programu Visual Studio](install-visual-studio.md)
* [Aktualizowanie programu Visual Studio](update-visual-studio.md)
* [Odinstalowywanie programu Visual Studio](uninstall-visual-studio.md)
* [Rozwiązywanie problemów Visual Studio instalacji i uaktualniania](troubleshooting-installation-issues.md)
