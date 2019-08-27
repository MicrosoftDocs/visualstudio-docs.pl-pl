---
title: Modyfikowanie programu Visual Studio
titleSuffix: ''
description: Dowiedz się, jak modyfikowanie programu Visual Studio krok po kroku.
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
ms.openlocfilehash: a97db7e6b81eb9e807902d1b9bd0ea8ee6efa55e
ms.sourcegitcommit: 0bd63f3bc429ae059b9df6e45c6b8dcae6152940
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/26/2019
ms.locfileid: "70026492"
---
# <a name="modify-visual-studio-by-adding-or-removing-workloads-and-components"></a>Modyfikowanie programu Visual Studio przez dodawanie lub usuwanie obciążeń i składników

::: moniker range="vs-2019"

Można łatwo zmodyfikować program Visual Studio tak, aby zawierał tylko to, czego potrzebujesz. Aby to zrobić, Otwórz Instalator programu Visual Studio, aby dodać lub usunąć obciążenia i składniki.

::: moniker-end

::: moniker range="vs-2017"

Nie tylko mieć ułatwiliśmy umożliwia personalizowanie programu Visual Studio, aby dopasować zadań, należy wykonać, została również ułatwiliśmy zbyt dostosować Visual Studio. Aby to zrobić, uruchom nowy Instalator programu Visual Studio i wprowadzić zmiany, które chcesz.

::: moniker-end

Poniżej przedstawiono sposób.

>[!IMPORTANT]
>Aby zainstalować, zaktualizować lub zmodyfikuj program Visual Studio, musisz zalogować się przy użyciu konta z uprawnieniami administracyjnymi. Aby uzyskać więcej informacji, zobacz [uprawnienia użytkownika i program Visual Studio](../ide/user-permissions-and-visual-studio.md).

## <a name="modify-workloads"></a>Modyfikowanie obciążeń

 [Obciążenia](https://visualstudio.microsoft.com/vs/visual-studio-workloads/) zawierają funkcje potrzebne dla używanego języka programowania lub platformy. Zmodyfikować programu Visual Studio, dzięki czemu obsługuje pracę, którą chcesz zrobić, jeśli chcesz to zrobić za pomocą obciążeń.

>[!NOTE]
> W poniższej procedurze przyjęto założenie, że masz połączenie z Internetem.
>
> Aby uzyskać więcej informacji na temat modyfikowania wcześniej utworzonej [instalacji w trybie offline](create-an-offline-installation-of-visual-studio.md) programu Visual Studio, zobacz sekcję [Aktualizowanie instalacji sieciowej programu Visual Studio](update-a-network-installation-of-visual-studio.md) i aktualizowanie [formantów do programu Visual Studio opartego na sieci Strona wdrożenia](controlling-updates-to-visual-studio-deployments.md) .

::: moniker range="vs-2017"

1. Znajdowanie Instalatora programu Visual Studio na komputerze.

     Na przykład na komputerze z systemem Windows 10, wybierz pozycję **Start**, a następnie przewiń do list **V**, w którym znajduje się w **Instalatora programu Visual Studio**.

     ![Instalator programu Visual Studio](media/vs2017-locate-the-visual-studio-installer.PNG "zlokalizować Instalatora programu Microsoft Visual Studio")

     >[!TIP]
     >Na niektórych komputerach Instalatora programu Visual Studio może zostać wyświetlony w obszarze list **"M"** jako **Instalator programu Microsoft Visual Studio**.<br/><br/> Alternatywnie można znaleźć Instalatora programu Visual Studio w następującej lokalizacji: `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. Kliknij lub naciśnij, aby uruchomić Instalatora a następnie wybierz **Modyfikuj**.

     ![Uruchom lub zmodyfikuj program Visual Studio](media/modify-visual-studio.png "modyfikowanie programu Visual Studio 2017")

     Jeśli masz oczekująca aktualizacja, przycisk Modyfikuj znajduje się w innym miejscu. Dzięki temu można zmodyfikować programu Visual Studio bez aktualizacji, należy wybrać w tym celu. Kliknij przycisk **więcej**, a następnie wybierz **Modyfikuj**.

     ![Aktualizowanie lub modyfikowanie programu Visual Studio](media/modify-or-update-visual-studio.png "aktualizacji lub zmodyfikować programu Visual Studio 2017")

1. Z **obciążeń** ekranu, zaznacz lub odznacz opcję obciążeń, które chcesz zainstalować lub odinstalować.

    ![Okno dialogowe programu Visual Studio 2017 konfiguracji](media/vs2017-modify-workloads.PNG "wybierz obciążenia w programie Visual Studio 2017")

1. Wybierz **Modyfikuj** ponownie.

1. Po zainstalowaniu nowych obciążeń i składników, wybierz **Uruchom**.

::: moniker-end

::: moniker range="vs-2019"

1. Znajdowanie Instalatora programu Visual Studio na komputerze.

     Na przykład na komputerze z systemem Windows 10, wybierz pozycję **Start**, a następnie przewiń do list **V**, w którym znajduje się w **Instalatora programu Visual Studio**.

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

## <a name="modify-individual-components"></a>Zmodyfikować poszczególne składniki

Jeśli nie chcesz instalować [obciążeń](https://visualstudio.microsoft.com/vs/visual-studio-workloads/) w celu dostosowania instalacji programu Visual Studio, wybierz kartę **poszczególne składniki** na Instalator programu Visual Studio, wybierz, co chcesz zrobić, a następnie postępuj zgodnie z monitami.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz także

* [Dowiedz się więcej na temat obciążeń programu Visual Studio](https://visualstudio.microsoft.com/vs/visual-studio-workloads/)
* [Lista identyfikatorów składników & obciążeń programu Visual Studio](workload-and-component-ids.md)
* [Aktualizowanie programu Visual Studio](update-visual-studio.md)
* [Aktualizowanie instalacji sieciowej programu Visual Studio](update-a-network-installation-of-visual-studio.md)
* [Aktualizowanie programu Visual Studio w punkcie odniesienia obsługi](update-servicing-baseline.md)
* [Sterowanie aktualizacjami na potrzeby wdrożenia oparte na sieci programu Visual Studio](controlling-updates-to-visual-studio-deployments.md)
* [Odinstalowywanie programu Visual Studio](uninstall-visual-studio.md)
