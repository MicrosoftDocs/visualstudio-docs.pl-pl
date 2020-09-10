---
title: Tworzenie pakietu rozszerzeń
description: Dowiedz się, jak utworzyć pakiet rozszerzeń z szablonem elementu pakietu rozszerzenia
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
ms.openlocfilehash: b5a0021061aefceafc2b048a3e231d9c0300db7b
ms.sourcegitcommit: 2a201c93ed526b0f7e5848657500f1111b08ac2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2020
ms.locfileid: "89742913"
---
# <a name="walkthrough-create-an-extension-pack"></a>Przewodnik: tworzenie pakietu rozszerzeń

Pakiet rozszerzeń to zestaw rozszerzeń, które mogą być instalowane razem. Pakiety rozszerzeń umożliwiają łatwe udostępnianie ulubionych rozszerzeń innym użytkownikom lub Łączenie zestawu rozszerzeń w konkretnym scenariuszu.

## <a name="prerequisites"></a>Wymagania wstępne

Począwszy od programu Visual Studio 2015, zestaw Visual Studio SDK jest dołączony jako funkcja opcjonalna w Instalatorze programu Visual Studio. Zestaw VS SDK można także zainstalować później. Aby uzyskać więcej informacji, zobacz [Instalowanie zestawu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

Funkcja pakietu rozszerzeń jest dostępna od wersji Visual Studio 15,8 Preview 2.

## <a name="create-an-extension-with-an-extension-pack-item-template"></a>Utwórz rozszerzenie z szablonem elementu pakietu rozszerzenia

Szablon elementu pakietu rozszerzenia tworzy pakiet rozszerzeń z zestawem rozszerzeń, które mogą być instalowane razem.

1. W oknie dialogowym **Nowy projekt** Wyszukaj ciąg "VSIX" i wybierz pozycję **Projekt VSIX**. W obszarze **Nazwa projektu**wpisz "test Pack pakiet". Wybierz pozycję **Utwórz**.

2. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Dodaj**  >  **nowy element**. Przejdź do węzła **rozszerzalności** Visual C# i wybierz pozycję **pakiet rozszerzeń**. Pozostaw domyślną nazwę pliku (ExtensionPack1.cs).

3. Dodano plik ExtensionPack1. vsext, który zawiera następujący kod

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

4. Element vsixid rozszerzenia do dołączenia do pakietu rozszerzeń można znaleźć na [Visual Studio Marketplace](https://marketplace.visualstudio.com/). Znajdź rozszerzenie, które chcesz dołączyć, a następnie kliknij pozycję **Kopiuj identyfikator**. Istniejący **element vsixid** można zaktualizować w powyższym pliku lub dodać do listy inne rozszerzenie.

    ![Kopiuj element vsixid z witryny Marketplace](media/vsixid-marketplace.png)

5. Skompiluj projekt i Przekaż swoje rozszerzenie do portalu Marketplace. Zobacz [Publikowanie rozszerzenia programu Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md).

> [!NOTE]
> Pakiet rozszerzeń może instalować tylko rozszerzenia, które są dostępne w galerii [Visual Studio Marketplace](https://marketplace.visualstudio.com/) lub [prywatnej](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md).

## <a name="install-the-extension-pack-from-the-visual-studio-marketplace"></a>Zainstaluj pakiet rozszerzeń z Visual Studio Marketplace

Po opublikowaniu rozszerzenia zainstaluj je w programie Visual Studio i przetestuj je w tym miejscu.

::: moniker range="vs-2017"

1. W programie Visual Studio w menu **Narzędzia** kliknij pozycję **rozszerzenia i aktualizacje**.

::: moniker-end

::: moniker range=">=vs-2019"

1. W programie Visual Studio w menu **rozszerzenia** kliknij pozycję **zarządzane rozszerzenia**.

::: moniker-end

2. Kliknij pozycję **online** , a następnie wyszukaj ciąg "test Pack pakiet".

3. Kliknij pozycję **Pobierz**. Rozszerzenie i jego lista rozszerzeń zawarte w pakiecie rozszerzeń zostaną zaplanowane do instalacji.

4. Poniżej znajduje się przykładowy widok pobierania pakietu rozszerzeń okna dialogowego **Zarządzanie rozszerzeniami** . Jeśli wolisz zainstalować tylko niektóre rozszerzenia zawarte w pakiecie rozszerzeń, można zmodyfikować listę rozszerzeń **zaplanowaną na potrzeby instalacji**.

    ![Pobierz pakiet rozszerzeń z witryny Marketplace](media/vside-extensionpack.png)

5. Aby ukończyć instalację, zamknij wszystkie wystąpienia programu Visual Studio.

## <a name="remove-the-extension"></a>Usuwanie rozszerzenia

Aby usunąć rozszerzenie z komputera:

::: moniker range="vs-2017"

1. W programie Visual Studio w menu **Narzędzia** kliknij pozycję **rozszerzenia i aktualizacje**.

::: moniker-end

::: moniker range=">=vs-2019"

1. W programie Visual Studio w menu **rozszerzenia** kliknij pozycję **zarządzane rozszerzenia**.

::: moniker-end

2. Wybierz opcję **pakiet rozszerzenia testowego** , a następnie kliknij przycisk **Odinstaluj**. Rozszerzenie i jego lista rozszerzeń zawarte w pakiecie rozszerzeń zostaną zaplanowane do odinstalowania.

3. Aby ukończyć dezinstalację, zamknij wszystkie wystąpienia programu Visual Studio.
