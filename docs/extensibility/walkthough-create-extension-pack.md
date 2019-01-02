---
title: Tworzenie pakietu rozszerzenia za pomocą szablonu elementu pakietu rozszerzenia | Dokumentacja firmy Microsoft
ms.date: 07/27/2018
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: 5388EEBA-211D-4114-8CD9-70C899919F7E
author: chitray
ms.author: chitray
manager: Meng
ms.workload:
- vssdk
ms.openlocfilehash: 55ceb788807f5d4fc9de2a96b4d359f290218dda
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53866325"
---
# <a name="walkthrough-create-an-extension-pack"></a>Przewodnik: Utwórz pakiet rozszerzenia

Pakiet rozszerzenia jest zestaw rozszerzeń, które mogą być instalowane razem. Pakietów rozszerzeń pozwalają na łatwe udostępnianie Ulubione rozszerzenia innym użytkownikom lub pakietu zestaw rozszerzeń, które ze sobą dla danego scenariusza.
  
## <a name="prerequisites"></a>Wymagania wstępne

Począwszy od programu Visual Studio 2015, możesz nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest dołączony jako opcjonalna funkcja w Instalatorze programu Visual Studio. Możesz także zainstalować zestaw SDK programu VS później. Aby uzyskać więcej informacji, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  

Funkcja pakiet rozszerzenia jest dostępna, począwszy od programu Visual Studio 2 15.8 (wersja zapoznawcza).
  
## <a name="create-an-extension-with-an-extension-pack-item-template"></a>Tworzenie rozszerzenia za pomocą szablonu elementu pakiet rozszerzenia

Szablon elementu pakietu rozszerzenia tworzy pakiet rozszerzenia z zestaw rozszerzeń, które mogą być instalowane razem.
  
1. W **nowy projekt** okna dialogowego rozwiń **Visual C#** lub **języka Visual Basic** a następnie kliknij przycisk **rozszerzalności**. W **szablony** okienku wybierz **projekt VSIX**. W **nazwa** wpisz `Test Extension Pack`. Kliknij przycisk **OK**.  
  
2. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł projektu i wybierz **Add / nowy element**. Przejdź do programu Visual C# **rozszerzalności** a następnie wybierz węzeł **pakietu rozszerzenia**. Pozostaw domyślną nazwę pliku (ExtensionPack1.cs).  
  
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

1. W programie Visual Studio na **narzędzia** menu, kliknij przycisk **rozszerzenia i aktualizacje...** .

2. Kliknij przycisk **Online** a następnie wyszukaj `Test Extension Pack`.

3. Kliknij przycisk **Pobierz**. Rozszerzenie i jego listy rozszerzenia zawarte w pakiecie rozszerzenia są planowane do zainstalowania.

4. Poniżej znajduje się przykładowy pakiet rozszerzenia pobierania **rozszerzenia i aktualizacje** okna dialogowego. Jeśli wolisz zainstalować niektóre rozszerzenia uwzględnione w pakiecie rozszerzenia, możesz zmodyfikować listy rozszerzeń w **zaplanowane do zainstalowania**.

    ![Pobieranie pakietu rozszerzenia z witryny Marketplace](media/vside-extensionpack.png)

5. Aby ukończyć instalację, zamknij wszystkie wystąpienia programu Visual Studio.

## <a name="remove-the-extension"></a>Usuń rozszerzenie

Aby usunąć rozszerzenie z komputera:

1. W programie Visual Studio na **narzędzia** menu, kliknij przycisk **rozszerzenia i aktualizacje...** .

2. Wybierz `Test Extension Pack` a następnie kliknij przycisk **Odinstaluj**. Rozszerzenie i jego listy rozszerzenia zawarte w pakiecie rozszerzenia są planowane do odinstalowania.

3. Aby ukończyć dezinstalację, zamknij wszystkie wystąpienia programu Visual Studio.
