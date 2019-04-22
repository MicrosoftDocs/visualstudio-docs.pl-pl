---
title: Modyfikowanie programu Visual Studio
titleSuffix: ''
description: Dowiedz się, jak modyfikowanie programu Visual Studio krok po kroku.
ms.custom: H1Hack27Feb2017,seodec18
ms.date: 03/30/2018
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
ms.openlocfilehash: a08a14d8d07248efdcac759852a38777745e9a51
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58789721"
---
# <a name="modify-visual-studio-by-adding-or-removing-workloads-and-components"></a>Modyfikowanie programu Visual Studio, dodając lub usuwając obciążenia i składniki

::: moniker range="vs-2019"

Jest łatwy do zmodyfikowania programu Visual Studio, aby obejmowała tylko to, czego potrzebujesz kiedy go potrzebujesz. Aby to zrobić, otwórz Instalator programu Visual Studio, aby dodać lub usunąć obciążeń i składników.

::: moniker-end

::: moniker range="vs-2017"

Nie tylko mieć ułatwiliśmy umożliwia personalizowanie programu Visual Studio, aby dopasować zadań, należy wykonać, została również ułatwiliśmy zbyt dostosować Visual Studio. Aby to zrobić, uruchom nowy Instalator programu Visual Studio i wprowadzić zmiany, które chcesz.

::: moniker-end

Poniżej przedstawiono sposób.

## <a name="modify-workloads"></a>Modyfikowanie obciążeń

 Obciążenia zawierają funkcje potrzebne do programowania języka lub platformy, którego używasz. Zmodyfikować programu Visual Studio, dzięki czemu obsługuje pracę, którą chcesz zrobić, jeśli chcesz to zrobić za pomocą obciążeń.

>[!IMPORTANT]
>Aby zainstalować, zaktualizować lub zmodyfikuj program Visual Studio, musisz zalogować się przy użyciu konta z uprawnieniami administracyjnymi. Aby uzyskać więcej informacji, zobacz [uprawnienia użytkownika i program Visual Studio](../ide/user-permissions-and-visual-studio.md).

::: moniker range="vs-2017"

1. Znajdowanie Instalatora programu Visual Studio na komputerze.

     Na przykład na komputerze z systemem Windows 10, wybierz pozycję **Start**, a następnie przewiń do list **V**, w którym znajduje się w **Instalatora programu Visual Studio**.

     ![Instalator programu Visual Studio](media/vs2017-locate-the-visual-studio-installer.PNG "zlokalizować Instalatora programu Microsoft Visual Studio")

     >[!NOTE]
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

     ![Otwórz Instalator programu Visual Studio](media/vs2019-visual-studio-installer.png "Otwórz Instalatora programu Visual Studio")

     > [!NOTE]
     > Instalator programu Visual Studio można również znaleźć w następującej lokalizacji:
     >
     > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

    Trzeba zaktualizować Instalatora przed kontynuowaniem. Jeśli tak, postępuj zgodnie z monitami.

1. W oknie Instalatora, poszukaj wersji programu Visual Studio, który został zainstalowany, a następnie wybierz **Modyfikuj**.

     ![Aktualizowanie lub modyfikowanie programu Visual Studio](media/vs-2019/vs-installer-modify.png "aktualizacji lub zmodyfikować programu Visual Studio 2017")

1. W **obciążeń** kartę, zaznacz lub odznacz opcję obciążeń, które chcesz zainstalować lub odinstalować.

    ![Okno dialogowe Ustawienia programu Visual Studio 2019](media/vs-2019/vs-installer-modify-workloads.png "wybierz obciążenie w Visual Studio 2019 r.")

1. Wybierz, czy chcesz zaakceptować wartości domyślne **Zainstaluj podczas pobierania** opcji lub **Pobierz wszystko, a następnie zainstaluj** opcji.

    ![Opcje instalacji w usłudze Visual Studio 2019](media/vs-2019/vs-installer-choose-install-or-download.png "chce do zainstalowania podczas pobierania lub najpierw pobrać i zainstalować je później")

    "Pobierz wszystko, a następnie zainstaluj" opcja jest przydatna, jeśli chcesz najpierw pobrać i zainstalować go później.

1. Wybierz **zmodyfikować**.

1. Po zainstalowaniu nowych obciążeń i składników, wybierz **Uruchom** za pomocą Instalatora programu Visual Studio.

::: moniker-end

## <a name="modify-individual-components"></a>Zmodyfikować poszczególne składniki

Jeśli nie chcesz zainstalować obciążenia, aby dostosować instalację programu Visual Studio, wybierz opcję **poszczególne składniki** za pomocą Instalatora programu Visual Studio, a następnie wybierz co, a następnie postępuj zgodnie z monitami.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz także

* [Aktualizowanie programu Visual Studio](update-visual-studio.md)
* [Aktualizowanie instalacji sieciowej programu Visual Studio](update-a-network-installation-of-visual-studio.md)
* [Odinstalowywanie programu Visual Studio](uninstall-visual-studio.md)
