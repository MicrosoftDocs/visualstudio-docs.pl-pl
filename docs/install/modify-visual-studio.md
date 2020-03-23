---
title: Modyfikowanie programu Visual Studio
titleSuffix: ''
description: Dowiedz się, jak zmodyfikować program Visual Studio krok po kroku.
ms.date: 02/10/2019
ms.topic: conceptual
helpviewer_keywords:
- modify Visual Studio
- change visual studio
- changing Visual Studio
- customize Visual Studio
ms.assetid: 3399ea7b-a291-4a9e-80a1-b861a21afa1d
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 57aa5531eb6d6517b520991ababefc38b25a9a2d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77125354"
---
# <a name="modify-visual-studio-by-adding-or-removing-workloads-and-components"></a>Modyfikowanie programu Visual Studio przez dodawanie lub usuwanie obciążeń i składników

::: moniker range="vs-2019"

Łatwo jest zmodyfikować visual studio, tak aby zawiera tylko to, co chcesz, kiedy chcesz. Aby to zrobić, otwórz Instalatora programu Visual Studio, aby dodać lub usunąć obciążenia i składniki.

::: moniker-end

::: moniker range="vs-2017"

Nie tylko ułatwiliśmy spersonalizowanie programu Visual Studio w celu dopasowania do zadań, które chcesz wykonać, ale także ułatwiliśmy dostosowywanie programu Visual Studio. Aby to zrobić, otwórz nowy Instalator programu Visual Studio i wykonuj żądane zmiany.

::: moniker-end

Oto jak to zrobić.

>[!IMPORTANT]
>Aby zainstalować, zaktualizować lub zmodyfikować program Visual Studio, należy zalogować się przy użyciu konta, które ma uprawnienia administracyjne. Aby uzyskać więcej informacji, zobacz [Uprawnienia użytkownika i Visual Studio](../ide/user-permissions-and-visual-studio.md).

>[!NOTE]
> W poniższych procedurach założono, że masz połączenie z Internetem.
>
> Aby uzyskać więcej informacji na temat modyfikowania wcześniej utworzonej instalacji programu Visual Studio w [trybie offline,](create-an-offline-installation-of-visual-studio.md) zobacz zarówno [stronę Aktualizowanie instalacji sieciowej programu Visual Studio,](update-a-network-installation-of-visual-studio.md) jak i [aktualizacje formantu na](controlling-updates-to-visual-studio-deployments.md) stronie wdrożenia programu Visual Studio oparte na sieci.

## <a name="open-the-visual-studio-installer"></a>Otwieranie Instalatora programu Visual Studio

::: moniker range="vs-2017"

1. Znajdź Instalator programu Visual Studio na komputerze.

     Na przykład na komputerze z systemem Windows 10 wybierz pozycję **Start**, a następnie przewiń do litery **V**, gdzie jest ona wymieniona jako **Instalator programu Visual Studio**.

     ![Instalator programu Visual Studio](media/locate-the-visual-studio-installer.png "Lokalizowanie Instalatora programu Microsoft Visual Studio")

     >[!TIP]
     >Na niektórych komputerach Instalator programu Visual Studio może być wymieniony pod literą **"M"** jako **Instalator programu Microsoft Visual Studio**.<br/><br/> Alternatywnie można znaleźć Instalatora programu Visual Studio w następującej lokalizacji:`C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. Otwórz instalatora, a następnie wybierz pozycję **Modyfikuj**.

     ![Uruchamianie lub modyfikowanie programu Visual Studio](media/modify-visual-studio.png "Modyfikowanie programu Visual Studio 2017")

     > [!IMPORTANT]
     > Jeśli masz oczekujące na aktualizację, przycisk Modyfikuj znajduje się w innym miejscu. W ten sposób można zmodyfikować visual studio bez aktualizowania go, należy to zrobić. Kliknij pozycję **Więcej**, a następnie wybierz pozycję **Modyfikuj**.
     >
     > ![Aktualizowanie lub modyfikowanie programu Visual Studio](media/modify-or-update-visual-studio.png "Aktualizowanie lub modyfikowanie programu Visual Studio 2017")

::: moniker-end

::: moniker range="vs-2019"

1. Znajdź Instalator programu Visual Studio na komputerze.

     Na przykład na komputerze z systemem Windows 10 wybierz pozycję **Start**, a następnie przewiń do litery **V**, gdzie jest ona wymieniona jako **Instalator programu Visual Studio**.

     ![Otwieranie Instalatora programu Visual Studio z systemu Windows](media/vs-2019/vs-installer-windows-start.png "Otwieranie Instalatora programu Visual Studio")

     > [!NOTE]
     > Instalator programu Visual Studio można również znaleźć w następującej lokalizacji:
     >
     > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

    Może być trzeba zaktualizować instalatora przed kontynuowaniem. Jeśli tak, postępuj zgodnie z instrukcjami.

1. W instalatorze poszukaj zainstalowanej wersji programu Visual Studio, a następnie wybierz pozycję **Modyfikuj**.

     ![Aktualizowanie lub modyfikowanie programu Visual Studio](media/vs-2019/vs-installer-modify.png "Aktualizowanie lub modyfikowanie programu Visual Studio 2019")

     > [!IMPORTANT]
     > Jeśli masz oczekujące na aktualizację, przycisk Modyfikuj znajduje się w innym miejscu. W ten sposób można zmodyfikować visual studio bez aktualizowania go, należy to zrobić. Wybierz pozycję **Więcej**, a następnie wybierz pozycję **Modyfikuj**.
     >
     > ![Aktualizowanie lub modyfikowanie programu Visual Studio](media/vs-2019/modify-update-visual-studio.png "Aktualizowanie lub modyfikowanie programu Visual Studio 2019")

::: moniker-end

## <a name="modify-workloads"></a>Modyfikowanie obciążeń

::: moniker range="vs-2017"

 Obciążenia zawierają [funkcje](https://visualstudio.microsoft.com/vs/support/selecting-workloads-visual-studio-2017/) potrzebne dla języka programowania lub platformy, której używasz. Użyj obciążeń, aby zmodyfikować program Visual Studio, tak aby obsługuje pracę, którą chcesz wykonać, gdy chcesz to zrobić.

1. W Instalatorze programu Visual Studio wybierz kartę **Obciążenia,** a następnie wybierz lub usuń zaznaczenie żądanych obciążeń.

    ![Okno dialogowe ustawień programu Visual Studio 2017](media/modify-workloads.png "Wybieranie obciążenia w programie Visual Studio 2019")

1. Wybierz, czy chcesz zaakceptować domyślną opcję **Zainstaluj podczas pobierania,** czy opcję **Pobierz wszystko, a następnie zainstaluj.**

    ![Opcje konfiguracji programu Visual Studio 2017](media/vs-2019/vs-installer-choose-install-or-download.png "Wybierz instalację podczas pobierania lub pobranie najpierw i zainstalowanie później")

    Opcja "Pobierz wszystko, a następnie zainstaluj" jest przydatna, jeśli chcesz najpierw pobrać, a następnie zainstalować później.

1. Wybierz **pozycję Modyfikuj**.

1. Po zainstalowaniu nowych obciążeń wybierz pozycję **Uruchom** instalator programu Visual Studio, aby otworzyć program Visual Studio.

::: moniker-end

::: moniker range="vs-2019"

 Obciążenia zawierają funkcje potrzebne dla języka programowania lub platformy, której używasz. Użyj obciążeń, aby zmodyfikować program Visual Studio, tak aby obsługuje pracę, którą chcesz wykonać, gdy chcesz to zrobić.

 > [!TIP]
>Aby uzyskać więcej informacji na temat pakietów narzędzi i składników potrzebnych do tworzenia, zobacz [Obciążenia programu Visual Studio.](https://visualstudio.microsoft.com/vs/#workloads)

1. W Instalatorze programu Visual Studio wybierz kartę **Obciążenia,** a następnie wybierz lub usuń zaznaczenie żądanych obciążeń.

    ![Okno dialogowe ustawień programu Visual Studio 2019](media/vs-2019/vs-installer-modify-workloads.png "Wybieranie obciążenia w programie Visual Studio 2019")

1. Wybierz, czy chcesz zaakceptować domyślną opcję **Zainstaluj podczas pobierania,** czy opcję **Pobierz wszystko, a następnie zainstaluj.**

    ![Opcje konfiguracji programu Visual Studio 2019](media/vs-2019/vs-installer-choose-install-or-download.png "Wybierz instalację podczas pobierania lub pobranie najpierw i zainstalowanie później")

    Opcja "Pobierz wszystko, a następnie zainstaluj" jest przydatna, jeśli chcesz najpierw pobrać, a następnie zainstalować później.

1. Wybierz **pozycję Modyfikuj**.

1. Po zainstalowaniu nowych obciążeń wybierz pozycję **Uruchom** instalator programu Visual Studio, aby otworzyć program Visual Studio.

::: moniker-end

## <a name="modify-individual-components"></a>Modyfikowanie poszczególnych komponentów

Jeśli nie chcesz używać obciążeń do dostosowywania instalacji programu Visual Studio, wybierz kartę **Poszczególne składniki** w Instalatorze programu Visual Studio, wybierz żądane składniki, a następnie postępuj zgodnie z monitami.

>[!TIP]
> Aby uzyskać informacje na temat składnika SQL Server Data Tools (SSDT), zobacz [Pobieranie i instalowanie pliku SSDT dla programu Visual Studio](/sql/ssdt/download-sql-server-data-tools-ssdt?view=sql-server-ver15).

## <a name="modify-language-packs"></a>Modyfikowanie pakietów językowych

Domyślnie instalator dopasowuje język systemu operacyjnego, gdy działa po raz pierwszy. Można jednak zmienić język w dowolnym momencie. Aby to zrobić, wybierz kartę **Pakiety językowe** w Instalatorze programu Visual Studio, wybierz preferowany język, a następnie postępuj zgodnie z instrukcjami.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz też

* [Lista identyfikatorów składników & obciążenia programu Visual Studio](workload-and-component-ids.md)
* [Aktualizowanie programu Visual Studio](update-visual-studio.md)
* [Aktualizowanie instalacji sieciowej programu Visual Studio](update-a-network-installation-of-visual-studio.md)
* [Aktualizowanie programu Visual Studio w obrębie punktu odniesienia obsługi](update-servicing-baseline.md)
* [Sterowanie aktualizacjami wdrożeń programu Visual Studio opartych na sieci](controlling-updates-to-visual-studio-deployments.md)
* [Odinstalowywanie programu Visual Studio](uninstall-visual-studio.md)
