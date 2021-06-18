---
title: Odinstalowywanie programu Visual Studio
titleSuffix: ''
description: Dowiedz się, Visual Studio odinstalować aplikację krok po kroku.
ms.date: 10/12/2020
ms.custom: seodec18
ms.topic: how-to
f1_keywords:
- uninstall
- uninstall Visual Studio
ms.assetid: 0e445255-b796-426d-ad93-a4d8e36da2c5
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 7d34a5be9598682982c3918aafec7725e59d6f92
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2021
ms.locfileid: "112306790"
---
# <a name="uninstall-visual-studio"></a>Odinstalowywanie programu Visual Studio

Ta strona zawiera omówienie odinstalowywania Visual Studio, naszego zintegrowanego zestawu narzędzi zwiększających produktywność dla deweloperów.

> [!NOTE]
> Ten temat dotyczy Visual Studio systemie Windows. Aby uzyskać Visual Studio dla komputerów Mac temat Uninstall [Visual Studio dla komputerów Mac (Odinstalowywanie Visual Studio dla komputerów Mac](/visualstudio/mac/uninstall)).

> [!TIP]
> Jeśli masz problemy z wystąpieniem usługi Visual Studio, spróbuj **użyć narzędzia do naprawy.** Aby uzyskać więcej informacji, zobacz [Repair Visual Studio](../install/repair-visual-studio.md). 
>
> Jeśli chcesz zmienić lokalizację niektórych plików Visual Studio, możesz to zrobić bez odinstalowywania bieżącego wystąpienia. Aby uzyskać więcej informacji, [zobacz Wybieranie lokalizacji instalacji w programie Visual Studio](../install/change-installation-locations.md).
>
> Aby uzyskać ogólne porady dotyczące rozwiązywania problemów, zobacz [Rozwiązywanie Visual Studio problemów z instalacją i uaktualnieniem.](../install/troubleshooting-installation-issues.md)

::: moniker range="vs-2017"

1. Znajdź Instalator programu Visual Studio na komputerze.

     Na przykład na komputerze z systemem Rocznicowa aktualizacja systemu Windows 10 lub nowszym wybierz pozycję **Uruchom** i przewiń do litery **V,** gdzie jest ona wymieniona jako **Instalator programu Visual Studio**.

     ![Instalator programu Visual Studio](media/locate-the-visual-studio-installer.png "Lokalizowanie Microsoft Visual Studio instalatora")

   > [!NOTE]
   > Na niektórych komputerach Instalator programu Visual Studio być wyświetlane pod literą **"M"** jako Microsoft Visual Studio **Instalatora** programu .<br/><br/> Alternatywnie możesz znaleźć Instalator programu Visual Studio w następującej lokalizacji: `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. W instalatorze poszukaj zainstalowanej wersji Visual Studio programu . Następnie wybierz pozycję **Więcej,** a następnie wybierz pozycję **Odinstaluj.**

     ![Odinstalowywanie Visual Studio 2017 r.](media/uninstall-visual-studio.png "Odinstalowywanie Visual Studio 2017 r.")

1. Kliknij **przycisk OK,** aby potwierdzić wybór.

Jeśli później zmienisz zdanie i chcesz ponownie zainstalować program Visual Studio 2017, uruchom ponownie  Instalator programu Visual Studio, a następnie wybierz pozycję Zainstaluj na ekranie wyboru.

## <a name="uninstall-visual-studio-installer"></a>Odinstalowywanie Instalator programu Visual Studio

Aby całkowicie usunąć wszystkie instalacje programu Visual Studio 2017 i Instalator programu Visual Studio z komputera, odinstaluj je z programu Apps & Features.

1. W Windows 10 wpisz **Aplikacje i** funkcje w polu "Wpisz tutaj, aby wyszukać".
1. Znajdź **Microsoft Visual Studio 2017** (lub **Visual Studio 2017).**
1. Wybierz pozycję **Odinstaluj.**
1. Następnie znajdź pozycję **Microsoft Visual Studio Instalatora**.
1. Wybierz pozycję **Odinstaluj.**

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

1. W instalatorze poszukaj zainstalowanej wersji Visual Studio programu . Następnie wybierz pozycję **Więcej,** a następnie wybierz pozycję **Odinstaluj.**

     ![Odinstalowywanie Visual Studio 2019 r.](media/vs-2019/vs-installer-uninstall.png "Odinstalowywanie Visual Studio 2019 r.")

1. Kliknij **przycisk OK,** aby potwierdzić wybór.

     ![Odinstalowywanie Visual Studio potwierdzenia](media/vs-2019/uninstall-visualstudio-confirm.png "Potwierdź, że chcesz odinstalować program Visual Studio 2019")

Jeśli później zmienisz zdanie i chcesz ponownie zainstalować program Visual Studio 2019 lub 2022,  ponownie uruchom program Instalator programu Visual Studio, wybierz kartę Dostępne, wybierz wersję programu Visual Studio, którą chcesz zainstalować, a następnie wybierz pozycję **Zainstaluj.**

## <a name="uninstall-visual-studio-installer"></a>Odinstalowywanie Instalator programu Visual Studio

Aby usunąć wszystkie instalacje programu Visual Studio 2019, Visual Studio 2022 i Instalator programu Visual Studio z komputera, odinstaluj je z programu Apps & Features.

1. W Windows 10 wpisz **Aplikacje i** funkcje w polu "Wpisz tutaj, aby wyszukać".
1. Znajdź **Visual Studio 2019** **r. lub Visual Studio 2022 r.**
1. Wybierz pozycję **Odinstaluj.**
1. Następnie znajdź pozycję **Microsoft Visual Studio Instalatora**.
1. Wybierz pozycję **Odinstaluj.**

::: moniker-end

## <a name="remove-all-files"></a>Usuń wszystkie pliki

Jeśli wystąpi katastrofalny błąd i nie można odinstalować usługi Visual Studio za pomocą poprzednich instrukcji, możesz rozważyć użycie opcji "w ostateczności". Aby uzyskać więcej informacji na temat całkowitego usuwania Visual Studio plików instalacyjnych i informacji o produkcie, zobacz [stronę Visual Studio](remove-visual-studio.md) instalacji.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz też

* [Modyfikowanie programu Visual Studio](modify-visual-studio.md)
* [Aktualizowanie programu Visual Studio](update-visual-studio.md)
