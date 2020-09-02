---
title: Rozszerzanie i dostosowywanie okien narzędzi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, essentials
- tool windows, standard
ms.assetid: 46b2892e-7b2b-4b3f-83a7-b884f1e114ee
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4b232fa1275bce453e3b32cea6a5ff37fdd501c6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204540"
---
# <a name="extending-and-customizing-tool-windows"></a>Rozszerzanie i dostosowywanie okien narzędzi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Program Visual Studio udostępnia kilka różnych typów okien, na przykład okna narzędzi, okna dokumentów i okna dialogowe. Inne okna, takie jak okno Właściwości, okno dane wyjściowe i okno Lista zadań, są typami okien narzędzi.  
  
## <a name="tool-windows"></a>Okna narzędzi  
 Okna narzędzi programu Visual Studio są zwykle oknami tylko do odczytu, które nie są oparte na plikach. Różnią się one od okien dokumentu, które wyświetlają pliki w trybie odczytu i zapisu. **Przybornik**, **Eksplorator rozwiązań**, okno **Właściwości** i **przeglądarka sieci Web** są przykładami okien narzędzi.  
  
 Aby dowiedzieć się, jak utworzyć proste okno narzędzi, zobacz [Dodawanie okna narzędzi](../extensibility/adding-a-tool-window.md).  
  
 Aby zarejestrować okno narzędzi przy użyciu programu Visual Studio, zobacz [Rejestrowanie okna narzędzi](../extensibility/registering-a-tool-window.md).  
  
 Okna narzędzi są domyślnie jednym wystąpieniem, co oznacza, że w danym momencie może być otwarte tylko jedno wystąpienie okna narzędzi. Po otwarciu okna narzędzia z jednym wystąpieniem pozostaje otwarte do momentu zamknięcia środowiska IDE. Po zamknięciu okna narzędzia z pojedynczym wystąpieniem zmiany są zmieniane. Możesz również utworzyć okna narzędzi z wieloma wystąpieniami, aby można było otworzyć wiele wystąpień okna jednocześnie. Aby uzyskać więcej informacji, zobacz [Tworzenie okna narzędzia z wieloma wystąpieniami](../extensibility/creating-a-multi-instance-tool-window.md) .  
  
 Okna narzędzi mogą być *dynamiczne*, co oznacza, że są widoczne przy każdym zastosowaniu powiązanego kontekstu interfejsu użytkownika. Funkcja autowidoczności może ograniczyć bałagan systemu Windows w środowisku IDE. Aby uzyskać więcej informacji, zobacz [Otwieranie okna narzędzia dynamicznego](../extensibility/opening-a-dynamic-tool-window.md).  
  
 Okna narzędzi mogą być zadokowane, przestawne lub z zakładkami w ramce dokumentu. Ramka okna narzędzi jest udostępniana przez środowisko IDE i służy do kontrolowania rozmiaru, lokalizacji, stanu dokowania i innych właściwości trwałych. W okienku okna narzędzi zostanie wyświetlona zawartość. Domyślny rozmiar i lokalizacja są stosowane tylko wtedy, gdy okno narzędzia jest otwierane jako pierwsze. gdy stan okna narzędzi zostanie utrwalony.  
  
 Okienka narzędzi okna narzędzia mogą hostować formanty użytkownika WPF i pomocnicze paski narzędzi. Można zastąpić <xref:Microsoft.VisualStudio.Shell.WindowPane.Window%2A> Właściwość w celu zwrócenia uchwytu hostowanej kontrolki.  
  
 Do okien narzędzi można dodawać wiele różnych funkcji. Na przykład można dodać pasek narzędzi: [Dodawanie paska narzędzi do okna narzędzi](../extensibility/adding-a-toolbar-to-a-tool-window.md) lub menu skrótów: [Dodawanie menu skrótów w oknie narzędzi](../extensibility/adding-a-shortcut-menu-in-a-tool-window.md). Można dodać kontrolkę wyszukiwania, która pozwala wyszukiwać elementy w oknie narzędzia: [Dodawanie wyszukiwania do okna narzędzi](../extensibility/adding-search-to-a-tool-window.md).  
  
 Można subskrybować zdarzenia okna narzędzi: [subskrybowanie zdarzenia](../extensibility/subscribing-to-an-event.md).  
  
## <a name="extending-existing-tool-windows"></a>Rozszerzanie istniejących okien narzędzi  
 Możesz dodać informacje o oknie narzędzia do nowej strony **Opcje** i nowe ustawienie na stronie **Właściwości** , zapisywać w oknach **Lista zadań** i **danych wyjściowych** . Aby uzyskać więcej informacji, zobacz [rozszerzanie okna właściwości, lista zadań, Output i Options](../extensibility/extending-the-properties-task-list-output-and-options-windows.md) oraz [rozszerzanie okna właściwości, lista zadań, danych](../extensibility/extending-the-properties-task-list-output-and-options-windows.md)wyjściowych i opcji.  
  
## <a name="modal-dialog-boxes"></a>Modalne okna dialogowe  
 W rozszerzeniu programu Visual Studio należy utworzyć modalne okna dialogowe, wynosząc je z <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow?displayProperty=fullName> , co umożliwia kontrolowanie ich i pozostałej części interfejsu użytkownika. Aby uzyskać więcej informacji, zobacz . [Tworzenie modalnych okien dialogowych i zarządzanie nimi](../extensibility/creating-and-managing-modal-dialog-boxes.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie rozszerzenia za pomocą okna narzędzi](../extensibility/creating-an-extension-with-a-tool-window.md)
