---
title: Rozszerzanie i dostosowywanie narzędzia Windows | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, essentials
- tool windows, standard
ms.assetid: 46b2892e-7b2b-4b3f-83a7-b884f1e114ee
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 76c094ec73a69baa46a5e8313dd26febd57e5887
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711818"
---
# <a name="extend-and-customize-tool-windows"></a>Rozszerzanie i dostosowywanie okien narzędzi
Program Visual Studio udostępnia kilka różnych typów okien, na przykład okna narzędzi, okna dokumentów i okna dialogowe. Inne okna, takie jak okno **Właściwości,** Okno **Dane wyjściowe** i **Lista zadań,** to typy okien narzędzi.

## <a name="tool-windows"></a>Okna narzędzi
 Okna narzędzi programu Visual Studio są zwykle oknami tylko do odczytu, które nie są oparte na plikach. W tym różnią się od okien dokumentów, które wyświetlają pliki w trybie odczytu i zapisu. Okno **Przybornik**, **Eksplorator** **rozwiązań, Właściwości** i **Przeglądarka sieci Web** są przykładami okien narzędzi.

 Aby dowiedzieć się, jak utworzyć proste okno narzędzia, zobacz [Dodawanie okna narzędzia](../extensibility/adding-a-tool-window.md).

 Aby zarejestrować okno narzędzia w programie Visual Studio, zobacz [Rejestrowanie okna narzędzia](../extensibility/registering-a-tool-window.md).

 Okna narzędzi są domyślnie pojedynczym wystąpieniem, co oznacza, że tylko jedno wystąpienie okna narzędzia może być otwarte jednocześnie. Po otwarciu okna narzędzia pojedynczego wystąpienia pozostaje ono otwarte do momentu zamknięcia IDE. Po zamknięciu okna narzędzia pojedynczego wystąpienia zmienia się tylko jego widoczność. Można również utworzyć okna narzędzi wielu wystąpień, tak aby wiele wystąpień okna można było otworzyć jednocześnie. Aby uzyskać więcej informacji, zobacz [Tworzenie okna narzędzia z wieloma wystąpieniami.](../extensibility/creating-a-multi-instance-tool-window.md)

 Okna narzędzi mogą być *dynamiczne,* co oznacza, że są widoczne za każdym razem, gdy ma zastosowanie ich powiązany kontekst interfejsu użytkownika. Użycie automatycznej widoczności może zmniejszyć bałagan w oknach w IDE. Aby uzyskać więcej informacji, zobacz [Otwieranie dynamicznego okna narzędzia](../extensibility/opening-a-dynamic-tool-window.md).

 Okna narzędzi mogą być zadokowane, przestawne lub z kartami w ramce dokumentu. Ramka okna narzędzia jest dostarczana przez IDE i służy do kontrolowania rozmiaru, lokalizacji, stanu dokowania i innych trwałych właściwości. W okienku okna narzędzia zostanie wyświetlona zawartość. Domyślny rozmiar i lokalizacja mają zastosowanie tylko wtedy, gdy okno narzędzia jest otwierane po raz pierwszy; po tym stan okna narzędzia jest zachowywany.

 Okienka okien narzędzia mogą obsługiwać formanty użytkownika WPF i paski narzędzi obsługi. Można zastąpić właściwość, <xref:Microsoft.VisualStudio.Shell.WindowPane.Window%2A> aby zwrócić dojście hostowanego formantu.

 Do okien narzędzi można dodać wiele różnych funkcji. Na przykład można dodać pasek narzędzi: [Dodaj pasek narzędzi do okna narzędzia](../extensibility/adding-a-toolbar-to-a-tool-window.md) lub menu skrótów: Dodaj menu [skrótów w oknie narzędzia](../extensibility/adding-a-shortcut-menu-in-a-tool-window.md). Można dodać kontrolkę wyszukiwania, która umożliwia wyszukiwanie elementów wewnątrz okna narzędzia: [Dodaj wyszukiwanie do okna narzędzia](../extensibility/adding-search-to-a-tool-window.md).

 Możesz subskrybować zdarzenia okna narzędzia: [Subskrybuj zdarzenie](../extensibility/subscribing-to-an-event.md).

## <a name="extend-existing-tool-windows"></a>Rozszerzanie istniejących okien narzędzi
 Informacje o oknie narzędzia można dodać do nowej strony **Opcje** i nowego ustawienia na stronie **Właściwości,** zapisuj do okien **Lista zadań** i **Dane wyjściowe.** Aby uzyskać więcej informacji, zobacz [Rozszerzanie okien Właściwości, Lista zadań, Dane wyjściowe i Opcje](../extensibility/extending-the-properties-task-list-output-and-options-windows.md).

## <a name="modal-dialog-boxes"></a>Modalne okna dialogowe
 W rozszerzeniu programu Visual Studio należy utworzyć <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow?displayProperty=fullName>modalne okna dialogowe, wyprowadzając je z programu , co pozwala kontrolować je i pozostałą część interfejsu użytkownika. Aby uzyskać więcej informacji, zobacz [Tworzenie okien dialogowych modalnych i zarządzanie nimi](../extensibility/creating-and-managing-modal-dialog-boxes.md).

## <a name="see-also"></a>Zobacz też
- [Tworzenie rozszerzenia za pomocą okna narzędzia](../extensibility/creating-an-extension-with-a-tool-window.md)
- [Rozszerzanie projektów](../extensibility/extending-projects.md)
- [Rozszerzanie rozwiązań](../extensibility/extending-solutions.md)
