---
title: Tworzenie pakietu rozszerzeń
description: Dowiedz się, jak utworzyć pakiet rozszerzeń za pomocą szablonu elementu pakietu rozszerzeń
ms.custom: SEO-VS-2020
ms.date: 07/27/2018
ms.topic: tutorial
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: 5388EEBA-211D-4114-8CD9-70C899919F7E
author: leslierichardson95
ms.author: lerich
manager: Meng
ms.workload:
- vssdk
ms.openlocfilehash: 213e3e71503ebea8074594bbc88a06980e3e64b4
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905140"
---
# <a name="walkthrough-create-an-extension-pack"></a>Przewodnik: tworzenie pakietu rozszerzeń

Pakiet rozszerzeń to zestaw rozszerzeń, które można zainstalować razem. Pakiety rozszerzeń umożliwiają łatwe udostępnianie ulubionych rozszerzeń innym użytkownikom lub dołączanie zestawu rozszerzeń do określonego scenariusza.

## <a name="prerequisites"></a>Wymagania wstępne

Począwszy od Visual Studio 2015 r., zestaw VISUAL STUDIO SDK jest dołączony jako opcjonalna funkcja w Visual Studio konfiguracji. Zestaw VS SDK można również zainstalować później. Aby uzyskać więcej informacji, zobacz [Instalowanie zestawu SDK Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

Funkcja pakietu rozszerzeń jest dostępna od wersji Visual Studio 15.8 (wersja zapoznawcza 2).

## <a name="create-an-extension-with-an-extension-pack-item-template"></a>Tworzenie rozszerzenia za pomocą szablonu elementu pakietu rozszerzeń

Szablon elementu pakietu rozszerzeń tworzy pakiet rozszerzeń z zestawem rozszerzeń, które można zainstalować razem.

1. W **oknie dialogowym Nowy** projekt wyszukaj pozycję "vsix", a następnie wybierz pozycję **Projekt VSIX.** W **polach Project name**(Nazwa projektu) wpisz "Test Extension Pack". Wybierz przycisk **Utwórz**.

2. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy węzeł projektu i wybierz **polecenie Dodaj**  >  **nowy element**. Przejdź do węzła Rozszerzalność Visual **C#** i wybierz **pozycję Pakiet rozszerzeń**. Pozostaw domyślną nazwę pliku (ExtensionPack1.cs).

3. Dodano plik ExtensionPack1.vsext, który zawiera następujący kod

   ```json
   {
    "id": "ExtensionPack1",
    "name": "ExtensionPack1",
    "description": "Read about creating extension packs at https://aka.ms/vsextpack",
    "version": "1.0.0.0",
    "extensions": [  // List of extensions that are included in the Extension Pack.
      {
        "vsixId": "41858b2d-ff0b-4a43-80b0-f1b2d6084935", // The vsix id of the extension you want to   include.
        "name": "AlignAssignments"
      },
      {
          "vsixId": "42374550-426a-400e-96f9-237682e8dea6",
        "name": "CopyAsHtml"
      }
    ]
   }
   ```

4. Vsixid rozszerzenia do dołączyć do pakietu rozszerzeń można znaleźć na [stronie Visual Studio Marketplace](https://marketplace.visualstudio.com/). Znajdź rozszerzenie, które chcesz dołączyć, a następnie kliknij pozycję **Copy ID (Identyfikator kopiowania).** Możesz zaktualizować istniejący **vsixId w** powyższym pliku lub dodać kolejne rozszerzenie do listy.

    ![Kopiowanie vsixId z witryny Marketplace](media/vsixid-marketplace.png)

5. Skompilowanie projektu i przekazanie rozszerzenia do witryny Marketplace. Zobacz [Publikowanie rozszerzenia Visual Studio .](../extensibility/walkthrough-publishing-a-visual-studio-extension.md)

> [!NOTE]
> Pakiet rozszerzeń może instalować tylko rozszerzenia, które są dostępne w [galerii Visual Studio Marketplace](https://marketplace.visualstudio.com/) lub [prywatnej.](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md)

## <a name="install-the-extension-pack-from-the-visual-studio-marketplace"></a>Zainstaluj pakiet rozszerzeń z Visual Studio Marketplace

Teraz, po opublikowaniu rozszerzenia, zainstaluj je w Visual Studio i tam przetestuj.

::: moniker range="vs-2017"

1. W Visual Studio menu Narzędzia **kliknij** pozycję **Rozszerzenia i aktualizacje.**

::: moniker-end

::: moniker range=">=vs-2019"

1. W Visual Studio menu **Rozszerzenia** kliknij pozycję **Rozszerzenia zarządzane.**

::: moniker-end

2. Kliknij **pozycję Online,** a następnie wyszukaj pozycję "Test Extension Pack".

3. Kliknij pozycję **Pobierz**. Rozszerzenie i jego lista rozszerzeń zawartych w pakiecie Extension Pack zostaną zaplanowane do zainstalowania.

4. Poniżej znajduje się przykładowy widok pobierania pakietu rozszerzeń w **oknie dialogowym Zarządzanie rozszerzeniami.** Jeśli wolisz zainstalować tylko niektóre rozszerzenia uwzględnione w pakiecie rozszerzenia, możesz zmodyfikować listę rozszerzeń w tece **Zaplanowane do zainstalowania.**

    ![Pobieranie pakietu rozszerzeń z witryny Marketplace](media/vside-extensionpack.png)

5. Aby ukończyć instalację, zamknij wszystkie wystąpienia Visual Studio.

## <a name="remove-the-extension"></a>Usuwanie rozszerzenia

Aby usunąć rozszerzenie z komputera:

::: moniker range="vs-2017"

1. W Visual Studio menu Narzędzia **kliknij** pozycję **Rozszerzenia i aktualizacje.**

::: moniker-end

::: moniker range=">=vs-2019"

1. W Visual Studio menu **Rozszerzenia** kliknij pozycję **Rozszerzenia zarządzane.**

::: moniker-end

2. Wybierz **pozycję Test Extension Pack ,a** następnie kliknij przycisk **Odinstaluj.** Rozszerzenie i jego lista rozszerzeń uwzględnionych w pakiecie Extension Pack zostaną zaplanowane do odinstalowania.

3. Aby ukończyć dezinstalację, zamknij wszystkie wystąpienia Visual Studio.
