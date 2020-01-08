---
title: Modyfikowanie programu Visual Studio
titleSuffix: ''
description: Dowiedz się, jak modyfikowanie programu Visual Studio krok po kroku.
ms.custom: H1Hack27Feb2017,seodec18
ms.date: 12/19/2019
ms.topic: conceptual
helpviewer_keywords:
- modify Visual Studio
- change visual studio
- changing Visual Studio
- customize Visual Studio
ms.assetid: 3399ea7b-a291-4a9e-80a1-b861a21afa1d
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 554b7a01ee4a7a8834c86c8a2c7e15b9cf331cf5
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75565841"
---
# <a name="modify-visual-studio-by-adding-or-removing-workloads-and-components"></a>Modyfikowanie programu Visual Studio przez dodawanie lub usuwanie obciążeń i składników

::: moniker range="vs-2019"

Można łatwo zmodyfikować program Visual Studio tak, aby zawierał tylko to, czego potrzebujesz. Aby to zrobić, Otwórz Instalator programu Visual Studio, aby dodać lub usunąć obciążenia i składniki.

::: moniker-end

::: moniker range="vs-2017"

Nie tylko mieć ułatwiliśmy umożliwia personalizowanie programu Visual Studio, aby dopasować zadań, należy wykonać, została również ułatwiliśmy zbyt dostosować Visual Studio. Aby to zrobić, Otwórz Nowy Instalator programu Visual Studio i wprowadź żądane zmiany.

::: moniker-end

Poniżej przedstawiono sposób.

>[!IMPORTANT]
>Aby zainstalować, zaktualizować lub zmodyfikuj program Visual Studio, musisz zalogować się przy użyciu konta z uprawnieniami administracyjnymi. Aby uzyskać więcej informacji, zobacz [uprawnienia użytkownika i program Visual Studio](../ide/user-permissions-and-visual-studio.md).

>[!NOTE]
> W poniższych procedurach przyjęto założenie, że masz połączenie z Internetem.
>
> Aby uzyskać więcej informacji na temat modyfikowania wcześniej utworzonej [instalacji w trybie offline](create-an-offline-installation-of-visual-studio.md) programu Visual Studio, zobacz sekcję [Aktualizowanie instalacji opartej na sieci](update-a-network-installation-of-visual-studio.md) na stronie programu Visual Studio i [aktualizowanie formantów na stronie wdrożenia programu Visual Studio opartej na sieci](controlling-updates-to-visual-studio-deployments.md) .

## <a name="open-the-visual-studio-installer"></a>Otwórz Instalator programu Visual Studio

::: moniker range="vs-2017"

1. Znajdowanie Instalatora programu Visual Studio na komputerze.

     Na przykład na komputerze z systemem Windows 10, wybierz pozycję **Start**, a następnie przewiń do list **V**, w którym znajduje się w **Instalatora programu Visual Studio**.

     ![Instalator programu Visual Studio](media/locate-the-visual-studio-installer.png "Lokalizowanie Instalatora Microsoft Visual Studio")

     >[!TIP]
     >Na niektórych komputerach Instalatora programu Visual Studio może zostać wyświetlony w obszarze list **"M"** jako **Instalator programu Microsoft Visual Studio**.<br/><br/> Alternatywnie można znaleźć Instalatora programu Visual Studio w następującej lokalizacji: `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. Otwórz instalatora, a następnie wybierz **Modyfikuj**.

     ![Uruchamianie lub modyfikowanie programu Visual Studio](media/modify-visual-studio.png "Modyfikuj program Visual Studio 2017")

     > [!IMPORTANT]
     > Jeśli masz oczekująca aktualizacja, przycisk Modyfikuj znajduje się w innym miejscu. Dzięki temu można zmodyfikować programu Visual Studio bez aktualizacji, należy wybrać w tym celu. Kliknij przycisk **więcej**, a następnie wybierz **Modyfikuj**.
     >
     > ![Aktualizowanie lub modyfikowanie programu Visual Studio](media/modify-or-update-visual-studio.png "Aktualizowanie lub modyfikowanie programu Visual Studio 2017")

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

     > [!IMPORTANT]
     > Jeśli masz oczekująca aktualizacja, przycisk Modyfikuj znajduje się w innym miejscu. W ten sposób można zmodyfikować program Visual Studio bez aktualizowania go, jeśli chcesz. Wybierz pozycję **więcej**, a następnie wybierz polecenie **Modyfikuj**.
     >
     > ![Aktualizowanie lub modyfikowanie programu Visual Studio](media/vs-2019/modify-update-visual-studio.png "Aktualizowanie lub modyfikowanie programu Visual Studio 2019")

::: moniker-end

## <a name="modify-workloads"></a>Modyfikowanie obciążeń

::: moniker range="vs-2017"

 [Obciążenia](https://visualstudio.microsoft.com/vs/support/selecting-workloads-visual-studio-2017/) zawierają funkcje potrzebne dla używanego języka programowania lub platformy. Zmodyfikować programu Visual Studio, dzięki czemu obsługuje pracę, którą chcesz zrobić, jeśli chcesz to zrobić za pomocą obciążeń.

1. W Instalator programu Visual Studio wybierz kartę **obciążenia** , a następnie wybierz lub usuń zaznaczenie żądanych obciążeń.

    ![Okno dialogowe Instalatora programu Visual Studio 2017](media/modify-workloads.png "Wybieranie obciążenia w programie Visual Studio 2019")

1. Wybierz, czy chcesz zaakceptować domyślną **instalację podczas pobierania** , czy opcję **Pobierz wszystko, a następnie zainstaluj** .

    ![Opcje instalacji programu Visual Studio 2017](media/vs-2019/vs-installer-choose-install-or-download.png "Wybierz, aby zainstalować program podczas pobierania lub najpierw pobrać i zainstalować później")

    Opcja "Pobierz wszystko, a następnie zainstaluj" jest użyteczna, jeśli chcesz najpierw pobrać program, a następnie zainstalować go później.

1. Wybierz **Modyfikuj**.

1. Po zainstalowaniu nowych obciążeń wybierz pozycję **Uruchom** w Instalator programu Visual Studio, aby otworzyć program Visual Studio.

::: moniker-end

::: moniker range="vs-2019"

 Obciążenia zawierają funkcje potrzebne dla używanego języka programowania lub platformy. Zmodyfikować programu Visual Studio, dzięki czemu obsługuje pracę, którą chcesz zrobić, jeśli chcesz to zrobić za pomocą obciążeń.

1. W Instalator programu Visual Studio wybierz kartę **obciążenia** , a następnie wybierz lub usuń zaznaczenie żądanych obciążeń.

    ![Okno dialogowe Instalatora programu Visual Studio 2019](media/vs-2019/vs-installer-modify-workloads.png "Wybieranie obciążenia w programie Visual Studio 2019")

1. Wybierz, czy chcesz zaakceptować domyślną **instalację podczas pobierania** , czy opcję **Pobierz wszystko, a następnie zainstaluj** .

    ![Opcje instalacji programu Visual Studio 2019](media/vs-2019/vs-installer-choose-install-or-download.png "Wybierz, aby zainstalować program podczas pobierania lub najpierw pobrać i zainstalować później")

    Opcja "Pobierz wszystko, a następnie zainstaluj" jest użyteczna, jeśli chcesz najpierw pobrać program, a następnie zainstalować go później.

1. Wybierz **Modyfikuj**.

1. Po zainstalowaniu nowych obciążeń wybierz pozycję **Uruchom** w Instalator programu Visual Studio, aby otworzyć program Visual Studio.

::: moniker-end

## <a name="modify-individual-components"></a>Zmodyfikować poszczególne składniki

Jeśli nie chcesz używać obciążeń do dostosowywania instalacji programu Visual Studio, wybierz kartę **poszczególne składniki** w Instalator programu Visual Studio, wybierz odpowiednie składniki, a następnie postępuj zgodnie z monitami.

## <a name="modify-language-packs"></a>Modyfikuj pakiety językowe

Domyślnie Instalator jest zgodny z językiem systemu operacyjnego, gdy jest uruchamiany po raz pierwszy. Można jednak zmienić język w dowolnym momencie. Aby to zrobić, wybierz kartę **pakiety językowe** w Instalator programu Visual Studio wybierz preferowany język, a następnie postępuj zgodnie z instrukcjami.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz także

* [Lista identyfikatorów składników & obciążeń programu Visual Studio](workload-and-component-ids.md)
* [Aktualizowanie programu Visual Studio](update-visual-studio.md)
* [Aktualizowanie instalacji sieciowej programu Visual Studio](update-a-network-installation-of-visual-studio.md)
* [Aktualizowanie programu Visual Studio w punkcie odniesienia obsługi](update-servicing-baseline.md)
* [Sterowanie aktualizacjami na potrzeby wdrożenia oparte na sieci programu Visual Studio](controlling-updates-to-visual-studio-deployments.md)
* [Odinstalowywanie programu Visual Studio](uninstall-visual-studio.md)
