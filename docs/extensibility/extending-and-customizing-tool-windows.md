---
title: Rozszerzanie i dostosowywanie okien narzędzi | Microsoft Docs
description: Dowiedz się więcej na temat rozszerzania i dostosowywania okien narzędzi dostępnych w programie Visual Studio, w tym okno Właściwości, okna danych wyjściowych i okna Lista zadań.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, essentials
- tool windows, standard
ms.assetid: 46b2892e-7b2b-4b3f-83a7-b884f1e114ee
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f9f17c16d051bdb42750d91971d2be0d3c09b47f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99953087"
---
# <a name="extend-and-customize-tool-windows"></a>Rozszerzone i dostosowane okna narzędzi
Program Visual Studio udostępnia kilka różnych typów okien, na przykład okna narzędzi, okna dokumentów i okna dialogowe. Inne okna, takie jak okno **Właściwości** , okno **dane wyjściowe** i okno **Lista zadań** , są typami okien narzędzi.

## <a name="tool-windows"></a>Okna narzędzi
 Okna narzędzi programu Visual Studio są zwykle oknami tylko do odczytu, które nie są oparte na plikach. Różnią się one od okien dokumentu, które wyświetlają pliki w trybie odczytu i zapisu. **Przybornik**, **Eksplorator rozwiązań**, okno **Właściwości** i **przeglądarka sieci Web** są przykładami okien narzędzi.

 Aby dowiedzieć się, jak utworzyć proste okno narzędzi, zobacz [Dodawanie okna narzędzi](../extensibility/adding-a-tool-window.md).

 Aby zarejestrować okno narzędzi za pomocą programu Visual Studio, zobacz [Rejestrowanie okna narzędzi](../extensibility/registering-a-tool-window.md).

 Okna narzędzi są domyślnie jednym wystąpieniem, co oznacza, że w danym momencie może być otwarte tylko jedno wystąpienie okna narzędzi. Po otwarciu okna narzędzia z jednym wystąpieniem pozostaje otwarte do momentu zamknięcia środowiska IDE. Po zamknięciu okna narzędzia z pojedynczym wystąpieniem zmiany są zmieniane. Możesz również utworzyć okna narzędzi z wieloma wystąpieniami, aby można było otworzyć wiele wystąpień okna jednocześnie. Aby uzyskać więcej informacji, zobacz [Tworzenie okna narzędzi z wieloma wystąpieniami](../extensibility/creating-a-multi-instance-tool-window.md) .

 Okna narzędzi mogą być *dynamiczne*, co oznacza, że są widoczne przy każdym zastosowaniu powiązanego kontekstu interfejsu użytkownika. Funkcja autowidoczności może ograniczyć bałagan systemu Windows w środowisku IDE. Aby uzyskać więcej informacji, zobacz [Otwieranie okna narzędzia dynamicznego](../extensibility/opening-a-dynamic-tool-window.md).

 Okna narzędzi mogą być zadokowane, przestawne lub z zakładkami w ramce dokumentu. Ramka okna narzędzi jest udostępniana przez środowisko IDE i służy do kontrolowania rozmiaru, lokalizacji, stanu dokowania i innych właściwości trwałych. W okienku okna narzędzi zostanie wyświetlona zawartość. Domyślny rozmiar i lokalizacja są stosowane tylko wtedy, gdy okno narzędzia jest otwierane jako pierwsze. gdy stan okna narzędzi zostanie utrwalony.

 Okienka narzędzi okna narzędzia mogą hostować formanty użytkownika WPF i pomocnicze paski narzędzi. Można zastąpić <xref:Microsoft.VisualStudio.Shell.WindowPane.Window%2A> Właściwość w celu zwrócenia uchwytu hostowanej kontrolki.

 Do okien narzędzi można dodawać wiele różnych funkcji. Na przykład możesz dodać pasek narzędzi: [Dodaj pasek narzędzi do okna narzędzi](../extensibility/adding-a-toolbar-to-a-tool-window.md) lub menu skrótów: [Dodaj menu skrótów w oknie narzędzi](../extensibility/adding-a-shortcut-menu-in-a-tool-window.md). Można dodać kontrolkę wyszukiwania, która umożliwia wyszukiwanie elementów wewnątrz okna narzędzi: [Dodawanie wyszukiwania do okna narzędzi](../extensibility/adding-search-to-a-tool-window.md).

 Możesz subskrybować zdarzenia okna narzędzi: [Subskrybuj zdarzenie](../extensibility/subscribing-to-an-event.md).

## <a name="extend-existing-tool-windows"></a>Rozwiń istniejące okna narzędzi
 Możesz dodać informacje o oknie narzędzia do nowej strony **Opcje** i nowe ustawienie na stronie **Właściwości** , zapisywać w oknach **Lista zadań** i **danych wyjściowych** . Aby uzyskać więcej informacji, zobacz sekcję Rozpoznaj [okna właściwości, lista zadań, dane wyjściowe i opcje](../extensibility/extending-the-properties-task-list-output-and-options-windows.md).

## <a name="modal-dialog-boxes"></a>Modalne okna dialogowe
 W rozszerzeniu programu Visual Studio należy utworzyć modalne okna dialogowe, wynosząc je z <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow?displayProperty=fullName> , co umożliwia kontrolowanie ich i pozostałej części interfejsu użytkownika. Aby uzyskać więcej informacji, zobacz [Tworzenie modalnych okien dialogowych i zarządzanie nimi](../extensibility/creating-and-managing-modal-dialog-boxes.md).

## <a name="see-also"></a>Zobacz też
- [Tworzenie rozszerzenia za pomocą okna narzędziowego](../extensibility/creating-an-extension-with-a-tool-window.md)
- [Rozwiń projekty](../extensibility/extending-projects.md)
- [Rozszeranie rozwiązań](../extensibility/extending-solutions.md)
