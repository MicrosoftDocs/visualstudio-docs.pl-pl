---
title: Tworzenie pakietu rozszerzeń z szablonem elementu pakietu rozszerzeń | Dokumenty firmy Microsoft
ms.date: 07/27/2018
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: 5388EEBA-211D-4114-8CD9-70C899919F7E
author: acangialosi
ms.author: anthc
manager: Meng
ms.workload:
- vssdk
ms.openlocfilehash: fa1c141e18a3870eaad4b155d816e30ee207f45d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697747"
---
# <a name="walkthrough-create-an-extension-pack"></a>Przewodnik: tworzenie pakietu rozszerzeń

Pakiet rozszerzeń to zestaw rozszerzeń, które można zainstalować razem. Pakiety rozszerzeń umożliwiają łatwe udostępnianie ulubionych rozszerzeń innym użytkownikom lub łączenie zestawu rozszerzeń dla określonego scenariusza.

## <a name="prerequisites"></a>Wymagania wstępne

Począwszy od programu Visual Studio 2015 zestaw SDK programu Visual Studio jest dołączony jako opcjonalna funkcja w konfiguracji programu Visual Studio. Można również zainstalować vs SDK później. Aby uzyskać więcej informacji, zobacz [Instalowanie zestawu SDK programu Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

Funkcja pakietu rozszerzeń jest dostępna począwszy od programu Visual Studio 15.8 Preview 2.

## <a name="create-an-extension-with-an-extension-pack-item-template"></a>Tworzenie rozszerzenia z szablonem elementu pakietu rozszerzeń

Szablon elementu pakietu rozszerzeń tworzy pakiet rozszerzeń z zestawem rozszerzeń, które można zainstalować razem.

1. W oknie dialogowym **Nowy projekt** wyszukaj hasło "vsix" i wybierz pozycję **VSIX Project**. W przypadku **nazwy projektu**wpisz "Test Extension Pack". Wybierz **pozycję Utwórz**.

2. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Dodaj** > **nowy element**. Przejdź do węzła **Rozszerzalność** języka Visual C# i wybierz opcję **Pakiet rozszerzeń**. Pozostaw domyślną nazwę pliku (ExtensionPack1.cs).

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

4. Vsixid rozszerzenia, które ma zostać uwzględnione w pakiecie rozszerzeń, można znaleźć w [portalu Visual Studio Marketplace](https://marketplace.visualstudio.com/). Znajdź rozszerzenie, które chcesz dołączyć, i kliknij **identyfikator kopii**. Można zaktualizować istniejący **vsixId** w powyższym pliku lub dodać inne rozszerzenie do listy.

    ![Kopiowanie vsixid z marketplace](media/vsixid-marketplace.png)

5. Skompiluj projekt i przekaż swoje rozszerzenie do marketplace. Zobacz [Publikowanie rozszerzenia programu Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md).

> [!NOTE]
> Pakiet rozszerzeń może instalować tylko rozszerzenia dostępne w portalu [Visual Studio Marketplace](https://marketplace.visualstudio.com/) lub Private [gallery](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md).

## <a name="install-the-extension-pack-from-the-visual-studio-marketplace"></a>Instalowanie pakietu rozszerzeń z portalu Visual Studio Marketplace

Teraz, gdy rozszerzenie zostanie opublikowane, zainstaluj je w programie Visual Studio i przetestuj je tam.

::: moniker range="vs-2017"

1. W programie Visual Studio w menu **Narzędzia** kliknij polecenie **Rozszerzenia i aktualizacje**.

::: moniker-end

::: moniker range=">=vs-2019"

1. W programie Visual Studio w menu **Rozszerzenia** kliknij polecenie **Rozszerzenia zarządzane**.

::: moniker-end

2. Kliknij **przycisk Online,** a następnie wyszukaj hasło "Test Extension Pack".

3. Kliknij **pozycję Pobierz**. Rozszerzenie i jego lista rozszerzeń zawartych w pakiecie rozszerzeń zostaną następnie zaplanowane do zainstalowania.

4. Poniżej znajduje się przykładowy widok pobierania pakietu rozszerzeń okna dialogowego **Zarządzanie rozszerzeniami.** Jeśli wolisz zainstalować tylko niektóre z dołączonych rozszerzeń w pakiecie rozszerzeń, możesz zmodyfikować listę rozszerzeń w **pliku Zaplanowane do zainstalowania**.

    ![Pobierz pakiet rozszerzeń z Marketplace](media/vside-extensionpack.png)

5. Aby zakończyć instalację, zamknij wszystkie wystąpienia programu Visual Studio.

## <a name="remove-the-extension"></a>Usuwanie rozszerzenia

Aby usunąć rozszerzenie z komputera:

::: moniker range="vs-2017"

1. W programie Visual Studio w menu **Narzędzia** kliknij polecenie **Rozszerzenia i aktualizacje**.

::: moniker-end

::: moniker range=">=vs-2019"

1. W programie Visual Studio w menu **Rozszerzenia** kliknij polecenie **Rozszerzenia zarządzane**.

::: moniker-end

2. Wybierz **pozycję Test Extension Pack,** a następnie kliknij przycisk **Odinstaluj**. Rozszerzenie i jego lista rozszerzeń zawartych w pakiecie rozszerzeń zostaną następnie zaplanowane do odinstalowania.

3. Aby zakończyć dezinstalację, zamknij wszystkie wystąpienia programu Visual Studio.
