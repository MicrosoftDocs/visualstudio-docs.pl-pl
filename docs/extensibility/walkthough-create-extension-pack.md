---
title: Tworzenie pakietu rozszerzenia za pomocą szablonu elementu pakietu rozszerzenia | Dokumentacja firmy Microsoft
ms.date: 07/27/2018
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: 5388EEBA-211D-4114-8CD9-70C899919F7E
author: gregvanl
ms.author: gregvanl
manager: Meng
ms.workload:
- vssdk
ms.openlocfilehash: 7899a096bb2a56e93ea55a4ba0a17cde272bd615
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62950978"
---
# <a name="walkthrough-create-an-extension-pack"></a>Przewodnik: Tworzenie pakietu rozszerzeń

Pakiet rozszerzenia jest zestaw rozszerzeń, które mogą być instalowane razem. Pakietów rozszerzeń pozwalają na łatwe udostępnianie Ulubione rozszerzenia innym użytkownikom lub pakietu zestaw rozszerzeń, które ze sobą dla danego scenariusza.

## <a name="prerequisites"></a>Wymagania wstępne

Począwszy od programu Visual Studio 2015, Visual Studio SDK jest dołączony jako opcjonalna funkcja w Instalatorze programu Visual Studio. Możesz także zainstalować zestaw SDK programu VS później. Aby uzyskać więcej informacji, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

Funkcja pakiet rozszerzenia jest dostępna, począwszy od programu Visual Studio 2 15.8 (wersja zapoznawcza).

## <a name="create-an-extension-with-an-extension-pack-item-template"></a>Tworzenie rozszerzenia za pomocą szablonu elementu pakiet rozszerzenia

Szablon elementu pakietu rozszerzenia tworzy pakiet rozszerzenia z zestaw rozszerzeń, które mogą być instalowane razem.

1. W **nowy projekt** okno dialogowe, wyszukaj "vsix", a następnie wybierz pozycję **projekt VSIX**. Aby uzyskać **Nazwa projektu**, wpisz "Pakiet rozszerzenia testów". Wybierz pozycję **Utwórz**.

2. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł projektu i wybierz **Dodaj** > **nowy element**. Przejdź do programu Visual C# **rozszerzalności** a następnie wybierz węzeł **pakietu rozszerzenia**. Pozostaw domyślną nazwę pliku (ExtensionPack1.cs).

3. ExtensionPack1.vsext plik zostanie dodany, który zawiera następujący kod

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

4. Vsixid rozszerzenia do uwzględnienia w pakiecie rozszerzenia można znaleźć na [Visual Studio Marketplace](https://marketplace.visualstudio.com/). Znajdź rozszerzenia mają do uwzględnienia, a następnie kliknij pozycję **identyfikator kopii**. Możesz zaktualizować istniejące **vsixId** powyżej pliku lub dodać innego rozszerzenia do listy.

    ![Skopiuj VsixId z witryny Marketplace](media/vsixid-marketplace.png)

5. Skompilować projekt i przekazać rozszerzenie do portalu Marketplace. Zobacz [publikowanie rozszerzenia programu Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md).

> [!NOTE]
> Pakiet rozszerzenia można zainstalować tylko rozszerzenia, które są dostępne na [Visual Studio Marketplace](https://marketplace.visualstudio.com/) lub [prywatną galerię](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md).

## <a name="install-the-extension-pack-from-the-visual-studio-marketplace"></a>Zainstaluj pakiet rozszerzenia z witryny Marketplace programu Visual Studio

Teraz, gdy rozszerzenie zostanie opublikowany, zainstaluj go w programie Visual Studio i przetestować.

::: moniker range="vs-2017"

1. W programie Visual Studio na **narzędzia** menu, kliknij przycisk **rozszerzenia i aktualizacje**.

::: moniker-end

::: moniker range=">=vs-2019"

1. W programie Visual Studio na **rozszerzenia** menu, kliknij przycisk **zarządzanych rozszerzeń**.

::: moniker-end

2. Kliknij przycisk **Online** a następnie wyszukaj "Pakiet rozszerzenia testów".

3. Kliknij przycisk **Pobierz**. Rozszerzenie i jego listy rozszerzenia zawarte w pakiecie rozszerzenia są planowane do zainstalowania.

4. Poniżej znajduje się przykładowy pakiet rozszerzenia pobierania **Zarządzaj rozszerzeniami** okna dialogowego. Jeśli wolisz zainstalować niektóre rozszerzenia uwzględnione w pakiecie rozszerzenia, możesz zmodyfikować listy rozszerzeń w **zaplanowane do zainstalowania**.

    ![Pobieranie pakietu rozszerzenia z witryny Marketplace](media/vside-extensionpack.png)

5. Aby ukończyć instalację, zamknij wszystkie wystąpienia programu Visual Studio.

## <a name="remove-the-extension"></a>Usuń rozszerzenie

Aby usunąć rozszerzenie z komputera:

::: moniker range="vs-2017"

1. W programie Visual Studio na **narzędzia** menu, kliknij przycisk **rozszerzenia i aktualizacje**.

::: moniker-end

::: moniker range=">=vs-2019"

1. W programie Visual Studio na **rozszerzenia** menu, kliknij przycisk **zarządzanych rozszerzeń**.

::: moniker-end

2. Wybierz **pakiet rozszerzenia testów** a następnie kliknij przycisk **Odinstaluj**. Rozszerzenie i jego listy rozszerzenia zawarte w pakiecie rozszerzenia są planowane do odinstalowania.

3. Aby ukończyć dezinstalację, zamknij wszystkie wystąpienia programu Visual Studio.
