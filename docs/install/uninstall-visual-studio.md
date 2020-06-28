---
title: Odinstalowywanie programu Visual Studio
titleSuffix: ''
description: Dowiedz się, jak odinstalować program Visual Studio, krok po kroku.
ms.date: 05/06/2020
ms.custom: seodec18
ms.topic: how-to
f1_keywords:
- uninstall
- uninstall Visual Studio
ms.assetid: 0e445255-b796-426d-ad93-a4d8e36da2c5
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 9d1412d6e015ec7d05e700370c7a379ada9a57b0
ms.sourcegitcommit: 9e15138a34532b222e80f6b42b1a9de7b2fe0175
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2020
ms.locfileid: "85419097"
---
# <a name="uninstall-visual-studio"></a>Odinstalowywanie programu Visual Studio

Ta strona przeprowadzi Cię przez proces odinstalowywania programu Visual Studio — naszego zintegrowanego pakietu narzędzi zwiększających produktywność dla deweloperów.

> [!NOTE]
> Ten temat ma zastosowanie do programu Visual Studio w systemie Windows. Aby uzyskać Visual Studio dla komputerów Mac, zobacz [odinstalowywanie Visual Studio dla komputerów Mac](/visualstudio/mac/uninstall).

> [!TIP]
> Jeśli masz problemy z wystąpieniem programu Visual Studio, wypróbuj narzędzie do **naprawy** . Aby uzyskać więcej informacji, zobacz temat [Naprawa programu Visual Studio](../install/repair-visual-studio.md). 
>
> Jeśli chcesz zmienić lokalizację niektórych plików programu Visual Studio, możesz to zrobić bez odinstalowywania bieżącego wystąpienia. Aby uzyskać więcej informacji, zobacz [Wybieranie lokalizacji instalacji w programie Visual Studio](../install/change-installation-locations.md).
>
> Ogólne porady dotyczące rozwiązywania problemów znajdują się w temacie [Rozwiązywanie problemów z instalacją i uaktualnianiem programu Visual Studio](../install/troubleshooting-installation-issues.md).

::: moniker range="vs-2017"

1. Znajdź Instalator programu Visual Studio na komputerze.

     Na przykład na komputerze z systemem Windows 10 z rocznicą aktualizacji lub nowszym wybierz pozycję **Rozpocznij** i przewiń do litery **V**, gdzie jest ona wyświetlana jako **Instalator programu Visual Studio**.

     ![Instalator programu Visual Studio](media/locate-the-visual-studio-installer.png "Lokalizowanie Instalatora Microsoft Visual Studio")

   > [!NOTE]
   > Na niektórych komputerach Instalator programu Visual Studio mogą być wyświetlane pod literą **"M"** jako **Instalator Microsoft Visual Studio**.<br/><br/> Alternatywnie można znaleźć Instalator programu Visual Studio w następującej lokalizacji:`C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. W instalatorze zapoznaj się z zainstalowaną wersją programu Visual Studio. Następnie wybierz pozycję **więcej**, a następnie wybierz pozycję **Odinstaluj**.

     ![Odinstaluj program Visual Studio 2017](media/uninstall-visual-studio.png "Odinstaluj program Visual Studio 2017")

1. Kliknij przycisk **OK** , aby potwierdzić wybór.

Jeśli zmienisz zdanie później i chcesz ponownie zainstalować program Visual Studio 2017, uruchom Instalator programu Visual Studio ponownie, a następnie wybierz opcję **Zainstaluj** z ekranu wyboru.

## <a name="uninstall-visual-studio-installer"></a>Odinstaluj Instalator programu Visual Studio

Aby całkowicie usunąć wszystkie instalacje programu Visual Studio 2017 i Instalator programu Visual Studio z komputera, odinstaluj je z poziomu aplikacji & funkcje.

1. W systemie Windows 10 wpisz **aplikacje i funkcje** w polu "Wpisz tutaj, aby wyszukać".
1. Znajdź **Microsoft Visual Studio 2017** (lub **Visual Studio 2017**).
1. Wybierz **Odinstaluj**.
1. Następnie Znajdź **Microsoft Visual Studio Instalatora**.
1. Wybierz **Odinstaluj**.

::: moniker-end

::: moniker range="vs-2019"

1. Znajdź Instalator programu Visual Studio na komputerze.

     Na przykład na komputerze z systemem Windows 10 Wybierz pozycję **Start**, a następnie przewiń do litery **V**, gdzie jest ona wyświetlana jako **Instalator programu Visual Studio**.

     ![Otwórz Instalator programu Visual Studio](media/vs-2019/vs-installer-windows-start.png "Otwórz Instalator programu Visual Studio")

     > [!NOTE]
     > Instalator programu Visual Studio można również znaleźć w następującej lokalizacji:
     >
     > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

    Może być konieczne zaktualizowanie Instalatora przed kontynuowaniem. Jeśli tak, postępuj zgodnie z monitami.

1. W instalatorze zapoznaj się z zainstalowaną wersją programu Visual Studio. Następnie wybierz pozycję **więcej**, a następnie wybierz pozycję **Odinstaluj**.

     ![Odinstaluj program Visual Studio 2019](media/vs-2019/vs-installer-uninstall.png "Odinstaluj program Visual Studio 2019")

1. Kliknij przycisk **OK** , aby potwierdzić wybór.

     ![Potwierdzenie odinstalowania programu Visual Studio](media/vs-2019/uninstall-visualstudio-confirm.png "Potwierdź, że chcesz odinstalować program Visual Studio 2019")

Jeśli zmienisz zdanie później i chcesz ponownie zainstalować program Visual Studio 2019, uruchom Instalator programu Visual Studio ponownie, wybierz kartę **dostępne** , wybierz wersję programu Visual Studio, którą chcesz zainstalować, a następnie wybierz pozycję **Zainstaluj**.

## <a name="uninstall-visual-studio-installer"></a>Odinstaluj Instalator programu Visual Studio

Aby usunąć wszystkie instalacje programu Visual Studio 2019 i Instalator programu Visual Studio z komputera, odinstaluj je z poziomu aplikacji & funkcje.

1. W systemie Windows 10 wpisz **aplikacje i funkcje** w polu "Wpisz tutaj, aby wyszukać".
1. Znajdź **program Visual Studio 2019**.
1. Wybierz **Odinstaluj**.
1. Następnie Znajdź **Microsoft Visual Studio Instalatora**.
1. Wybierz **Odinstaluj**.

::: moniker-end

## <a name="remove-all-files"></a>Usuń wszystkie pliki

Jeśli wystąpił błąd krytyczny i nie można odinstalować programu Visual Studio przy użyciu poprzednich instrukcji, jest dostępna opcja "Ostatnia możliwość", którą można rozważyć przy użyciu polecenia. Aby uzyskać więcej informacji o tym, jak całkowicie usunąć wszystkie pliki instalacyjne i informacje o produkcie programu Visual Studio, zobacz stronę [usuwanie programu Visual Studio](remove-visual-studio.md) .

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz też

* [Modyfikowanie programu Visual Studio](modify-visual-studio.md)
* [Aktualizowanie programu Visual Studio](update-visual-studio.md)
