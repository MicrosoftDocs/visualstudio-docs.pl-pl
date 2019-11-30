---
title: Modyfikowanie programu Visual Studio
titleSuffix: ''
description: Dowiedz się, jak modyfikować program Visual Studio, krok po kroku.
ms.custom: H1Hack27Feb2017,seodec18
ms.date: 08/23/2019
ms.topic: conceptual
helpviewer_keywords:
- modify Visual Studio
- change visual studio
- changing Visual Studio
- customize Visual Studio
ms.assetid: 3399ea7b-a291-4a9e-80a1-b861a21afa1d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 628d8fe5d8374d0cb203e6953f63bd63d77d0c58
ms.sourcegitcommit: 3ba2968a4b44643482aadad4d50e1a55bb36b136
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2019
ms.locfileid: "74566998"
---
# <a name="modify-visual-studio-by-adding-or-removing-workloads-and-components"></a>Modyfikowanie programu Visual Studio przez dodawanie lub usuwanie obciążeń i składników

::: moniker range="vs-2019"

Można łatwo zmodyfikować program Visual Studio tak, aby zawierał tylko to, czego potrzebujesz. Aby to zrobić, Otwórz Instalator programu Visual Studio, aby dodać lub usunąć obciążenia i składniki.

::: moniker-end

::: moniker range="vs-2017"

Nie tylko Ułatwiamy Personalizowanie programu Visual Studio w celu dopasowania do zadań, które mają zostać wykonane, ale również Ułatwiamy dostosowanie programu Visual Studio. Aby to zrobić, uruchom nową Instalator programu Visual Studio i wprowadź odpowiednie zmiany.

::: moniker-end

Oto jak to zrobić.

>[!IMPORTANT]
>Aby zainstalować, zaktualizować lub zmodyfikować program Visual Studio, należy zalogować się przy użyciu konta z uprawnieniami administracyjnymi. Aby uzyskać więcej informacji, zobacz [uprawnienia użytkownika i program Visual Studio](../ide/user-permissions-and-visual-studio.md).

## <a name="modify-workloads"></a>Modyfikuj obciążenia

::: moniker range="vs-2017"

 [Obciążenia](https://visualstudio.microsoft.com/vs/support/selecting-workloads-visual-studio-2017/) zawierają funkcje potrzebne dla używanego języka programowania lub platformy. Użyj obciążeń, aby zmodyfikować program Visual Studio, aby obsługiwał zadania, które chcesz wykonać, gdy chcesz to zrobić.

::: moniker-end

::: moniker range="vs-2019"

 Obciążenia zawierają funkcje potrzebne dla używanego języka programowania lub platformy. Użyj obciążeń, aby zmodyfikować program Visual Studio, aby obsługiwał zadania, które chcesz wykonać, gdy chcesz to zrobić.

::: moniker-end

>[!NOTE]
> W poniższej procedurze przyjęto założenie, że masz połączenie z Internetem.
>
> Aby uzyskać więcej informacji na temat modyfikowania wcześniej utworzonej [instalacji w trybie offline](create-an-offline-installation-of-visual-studio.md) programu Visual Studio, zobacz sekcję [Aktualizowanie instalacji opartej na sieci](update-a-network-installation-of-visual-studio.md) na stronie programu Visual Studio i [aktualizowanie formantów na stronie wdrożenia programu Visual Studio opartej na sieci](controlling-updates-to-visual-studio-deployments.md) .

::: moniker range="vs-2017"

1. Znajdź Instalator programu Visual Studio na komputerze.

     Na przykład na komputerze z systemem Windows 10 Wybierz pozycję **Start**, a następnie przewiń do litery **V**, gdzie jest ona wyświetlana jako **Instalator programu Visual Studio**.

     ![Instalator programu Visual Studio](media/vs2017-locate-the-visual-studio-installer.PNG "Lokalizowanie Instalatora Microsoft Visual Studio")

     >[!TIP]
     >Na niektórych komputerach Instalator programu Visual Studio mogą być wyświetlane pod literą **"M"** jako **Instalator Microsoft Visual Studio**.<br/><br/> Alternatywnie można znaleźć Instalator programu Visual Studio w następującej lokalizacji: `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. Kliknij lub naciśnij, aby uruchomić Instalatora, a następnie wybierz **Modyfikuj**.

     ![Uruchamianie lub modyfikowanie programu Visual Studio](media/modify-visual-studio.png "Modyfikuj program Visual Studio 2017")

     Jeśli masz oczekujące aktualizacje, przycisk Modyfikuj znajduje się w innym miejscu. W ten sposób można zmodyfikować program Visual Studio bez aktualizowania go, aby to zrobić. Kliknij pozycję **więcej**, a następnie wybierz polecenie **Modyfikuj**.

     ![Aktualizowanie lub modyfikowanie programu Visual Studio](media/modify-or-update-visual-studio.png "Aktualizowanie lub modyfikowanie programu Visual Studio 2017")

1. Na ekranie **obciążenia** zaznacz lub usuń zaznaczenie obciążeń, które chcesz zainstalować lub odinstalować.

    ![Okno dialogowe Instalatora programu Visual Studio 2017](media/vs2017-modify-workloads.PNG "Wybieranie obciążenia w programie Visual Studio 2017")

1. Wybierz ponownie przycisk **Modyfikuj** .

1. Po zainstalowaniu nowych obciążeń i składników wybierz pozycję **Uruchom**.

::: moniker-end

::: moniker range="vs-2019"

1. Znajdź Instalator programu Visual Studio na komputerze.

     Na przykład na komputerze z systemem Windows 10 Wybierz pozycję **Start**, a następnie przewiń do litery **V**, gdzie jest ona wyświetlana jako **Instalator programu Visual Studio**.

     ![Otwórz Instalator programu Visual Studio z systemu Windows](media/vs-2019/vs-installer-windows-start.png "Otwórz Instalator programu Visual Studio")

     > [!NOTE]
     > Instalator programu Visual Studio można również znaleźć w następującej lokalizacji:
     >
     > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

    Może być konieczne zaktualizowanie Instalatora przed kontynuowaniem. Jeśli tak, postępuj zgodnie z monitami.

1. W instalatorze zapoznaj się z zainstalowaną wersją programu Visual Studio, a następnie wybierz **Modyfikuj**.

     ![Aktualizowanie lub modyfikowanie programu Visual Studio](media/vs-2019/vs-installer-modify.png "Aktualizowanie lub modyfikowanie programu Visual Studio 2019")

1. Na karcie **obciążenia** wybierz lub Anuluj wybór obciążeń, które chcesz zainstalować lub odinstalować.

    ![Okno dialogowe Instalatora programu Visual Studio 2019](media/vs-2019/vs-installer-modify-workloads.png "Wybieranie obciążenia w programie Visual Studio 2019")

1. Wybierz, czy chcesz zaakceptować domyślną **instalację podczas pobierania** , czy opcję **Pobierz wszystko, a następnie zainstaluj** .

    ![Opcje instalacji programu Visual Studio 2019](media/vs-2019/vs-installer-choose-install-or-download.png "Wybierz, aby zainstalować program podczas pobierania lub najpierw pobrać i zainstalować później")

    Opcja "Pobierz wszystko, a następnie zainstaluj" jest użyteczna, jeśli chcesz najpierw pobrać program, a następnie zainstalować go później.

1. Wybierz **Modyfikuj**.

1. Po zainstalowaniu nowych obciążeń i składników wybierz pozycję **Uruchom** w Instalator programu Visual Studio.

::: moniker-end

## <a name="modify-individual-components"></a>Modyfikuj poszczególne składniki

Jeśli nie chcesz instalować obciążeń w celu dostosowania instalacji programu Visual Studio, wybierz kartę **poszczególne składniki** na Instalator programu Visual Studio, wybierz, co chcesz zrobić, a następnie postępuj zgodnie z monitami.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz także

* [Lista identyfikatorów składników & obciążeń programu Visual Studio](workload-and-component-ids.md)
* [Aktualizowanie programu Visual Studio](update-visual-studio.md)
* [Aktualizowanie instalacji sieciowej programu Visual Studio](update-a-network-installation-of-visual-studio.md)
* [Aktualizowanie programu Visual Studio w punkcie odniesienia obsługi](update-servicing-baseline.md)
* [Sterowanie aktualizacjami wdrożeń programu Visual Studio opartych na sieci](controlling-updates-to-visual-studio-deployments.md)
* [Odinstalowywanie programu Visual Studio](uninstall-visual-studio.md)
