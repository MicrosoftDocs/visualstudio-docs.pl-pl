---
title: Modyfikowanie Visual Studio, składników i & pakietów językowych
titleSuffix: ''
description: Dowiedz się, jak Visual Studio instrukcje krok po kroku.
ms.date: 10/12/2020
ms.topic: how-to
ms.custom: acquisition
helpviewer_keywords:
- modify Visual Studio
- change visual studio
- changing Visual Studio
- customize Visual Studio
ms.assetid: 3399ea7b-a291-4a9e-80a1-b861a21afa1d
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 638ec555a6fbef53d19a15c8a6cde26ff121aa0e
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2021
ms.locfileid: "112306985"
---
# <a name="modify-visual-studio-workloads-components-and-language-packs"></a>Modyfikowanie Visual Studio, składników i pakietów językowych

::: moniker range=">=vs-2019"

Łatwo jest zmodyfikować Visual Studio tak, aby zawierał tylko to, czego chcesz, kiedy chcesz. W tym celu otwórz Instalator programu Visual Studio, aby dodać lub usunąć obciążenia i składniki.

::: moniker-end

::: moniker range="vs-2017"

Nie tylko ułatwiliśmy Personalizowanie Visual Studio w celu dopasowania do zadań, które chcesz wykonać, ale także ułatwiliśmy dostosowywanie Visual Studio zadań. W tym celu otwórz nowy Instalator programu Visual Studio i wprowadzić zmiany.

::: moniker-end

## <a name="prerequisites"></a>Wymagania wstępne

+ Aby zainstalować, zaktualizować lub zmodyfikować Visual Studio, musisz zalogować się przy użyciu konta z uprawnieniami administracyjnymi. Aby uzyskać więcej informacji, zobacz [Uprawnienia użytkownika i Visual Studio](../ide/user-permissions-and-visual-studio.md).

+ W poniższych procedurach przyjęto założenie, że masz połączenie z Internetem. Aby uzyskać więcej informacji na temat modyfikowania wcześniej utworzonej instalacji programu Visual Studio w trybie [offline,](create-an-offline-installation-of-visual-studio.md) zobacz stronę Aktualizowanie instalacji sieciowej programu [Visual Studio](update-a-network-installation-of-visual-studio.md) i stronę Kontrolowanie aktualizacji do wdrożeń Visual Studio [sieciowych.](controlling-updates-to-visual-studio-deployments.md)

## <a name="launch-the-installer"></a>Uruchom instalatora

Aby wprowadzić zmiany w instalacji, należy uruchomić instalatora Visual Studio instalatora.

::: moniker range="vs-2017"

1. Znajdź Instalator programu Visual Studio na komputerze.

     Na przykład na komputerze z systemem Windows 10 start wybierz pozycję **,** a następnie przewiń do litery **V,** gdzie jest ona wymieniona jako **Instalator programu Visual Studio**.

     ![Instalator programu Visual Studio](media/locate-the-visual-studio-installer.png "Lokalizowanie Microsoft Visual Studio instalatora")

     >[!TIP]
     >Na niektórych komputerach Instalator programu Visual Studio być wyświetlane pod literą **"M"** jako Microsoft Visual Studio **Instalatora** programu .<br/><br/> Alternatywnie możesz znaleźć Instalator programu Visual Studio w następującej lokalizacji: `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. Otwórz instalatora, a następnie wybierz pozycję **Modyfikuj.**

     ![Uruchamianie lub modyfikowanie Visual Studio](media/modify-visual-studio.png "Modyfikowanie programu Visual Studio 2017")

     > [!IMPORTANT]
     > Jeśli masz oczekującą aktualizację, przycisk Modyfikuj znajduje się w innym miejscu. W ten sposób możesz modyfikować Visual Studio bez aktualizowania go, jeśli chcesz to zrobić. Kliknij **pozycję Więcej,** a następnie wybierz pozycję **Modyfikuj.**
     >
     > ![Aktualizowanie lub modyfikowanie Visual Studio](media/modify-or-update-visual-studio.png "Aktualizowanie lub modyfikowanie Visual Studio 2017 r.")

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

1. W instalatorze poszukaj zainstalowanej wersji Visual Studio, a następnie wybierz pozycję **Modyfikuj.**

     ![Wybierz Visual Studio edycji, a następnie zmodyfikuj](media/vs-2019/vs-installer-modify.png "Wybierz Visual Studio 2019, a następnie zmodyfikuj")

     > [!IMPORTANT]
     > Jeśli masz oczekującą aktualizację, przycisk Modyfikuj znajduje się w innym miejscu. W ten sposób możesz modyfikować Visual Studio bez aktualizowania go, jeśli chcesz. Wybierz **pozycję Więcej,** a następnie wybierz pozycję **Modyfikuj.**
     >
     > ![Aktualizowanie lub modyfikowanie Visual Studio](media/vs-2019/modify-update-visual-studio.png "Aktualizowanie lub modyfikowanie Visual Studio 2019 r.")

::: moniker-end

## <a name="change-workloads-or-individual-components"></a>Zmienianie obciążeń lub poszczególnych składników

::: moniker range="vs-2017"

 [Obciążenia zawierają](https://visualstudio.microsoft.com/vs/support/selecting-workloads-visual-studio-2017/) funkcje potrzebne dla języka programowania lub platformy, której używasz. Obciążenia są modyfikowane Visual Studio tak, aby obsługiły pracę, którą chcesz wykonać, gdy chcesz to zrobić.

1. W Instalator programu Visual Studio wybierz **kartę Obciążenia,** a następnie wybierz lub usuń zaznaczenie wybranych obciążeń.

   Jeśli nie chcesz używać obciążeń do dostosowywania instalacji programu Visual Studio, wybierz  kartę Poszczególne składniki i wybierz odpowiednie składniki, a następnie postępuj zgodnie z monitami.

    ![Visual Studio instalacji programu Visual Studio 2017](media/modify-workloads.png "Wybieranie obciążenia w Visual Studio 2019 r.")

1. Wybierz, czy chcesz zaakceptować domyślną opcję **Zainstaluj** podczas pobierania, czy opcję **Pobierz wszystko,** a następnie opcję instalacji.

    ![Visual Studio instalacji programu Visual Studio 2017](media/vs-2019/vs-installer-choose-install-or-download.png "Wybierz instalację podczas pobierania lub pobierz najpierw i zainstaluj później")

    Opcja "Pobierz wszystko, a następnie zainstaluj" jest przydatna, jeśli chcesz pobrać najpierw, a następnie zainstalować później.

1. Wybierz **pozycję Modyfikuj.**

1. W razie potrzeby wybierz **kartę Obciążenia,** a następnie wybierz lub usuń zaznaczenie żądanych obciążeń.

1. Po zainstalowaniu nowych obciążeń wybierz **pozycję** Uruchom z Instalator programu Visual Studio, aby otworzyć Visual Studio.

::: moniker-end

::: moniker range=">=vs-2019"

 Obciążenia zawierają funkcje potrzebne dla języka programowania lub platformy, której używasz. Obciążenia są modyfikowane Visual Studio tak, aby obsługiły pracę, którą chcesz wykonać, gdy chcesz to zrobić.

 > [!TIP]
>Aby uzyskać więcej informacji o pakietach narzędzi i składników potrzebnych do tworzenia aplikacji, zobacz [Visual Studio obciążenia.](https://visualstudio.microsoft.com/vs/#workloads)

1. W Instalator programu Visual Studio wybierz **kartę Obciążenia,** a następnie wybierz lub usuń zaznaczenie wybranych obciążeń.

    ![Visual Studio instalacji programu Visual Studio 2019](media/vs-2019/vs-installer-modify-workloads.png "Wybieranie obciążenia w Visual Studio 2019 r.")

1. Wybierz, czy chcesz zaakceptować domyślną opcję **Zainstaluj** podczas pobierania, czy opcję **Pobierz wszystko,** a następnie opcję instalacji.

    ![Visual Studio 2019 r.](media/vs-2019/vs-installer-choose-install-or-download.png "Wybierz instalację podczas pobierania lub pobierz najpierw i zainstaluj później")

    Opcja "Pobierz wszystko, a następnie zainstaluj" jest przydatna, jeśli chcesz pobrać najpierw, a następnie zainstalować później.

1. Wybierz **pozycję Modyfikuj.**

1. Po zainstalowaniu nowych obciążeń wybierz **pozycję** Uruchom z Instalator programu Visual Studio, aby otworzyć Visual Studio.

::: moniker-end

>[!TIP]
> Aby uzyskać informacje o składniku narzędzi SQL Server Data Tools (SSDT), zobacz Pobieranie i instalowanie narzędzi [SSDT](/sql/ssdt/download-sql-server-data-tools-ssdt?view=sql-server-ver15&preserve-view=true)dla Visual Studio .

## <a name="modify-language-packs"></a>Modyfikowanie pakietów językowych

Domyślnie instalator jest w języku systemu operacyjnego uruchamianym po raz pierwszy. Język można jednak zmienić w dowolnym momencie. 

W tym celu:

1. Wybierz **kartę Pakiety językowe** w Instalator programu Visual Studio.
1. Wybierz preferowany język.
1. Postępuj zgodnie z monitami.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Zobacz też

* [Lista identyfikatorów Visual Studio obciążenia & składników](workload-and-component-ids.md)
* [Aktualizowanie programu Visual Studio](update-visual-studio.md)
* [Aktualizowanie instalacji sieciowej programu Visual Studio](update-a-network-installation-of-visual-studio.md)
* [Odinstalowywanie programu Visual Studio](uninstall-visual-studio.md)
