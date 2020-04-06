---
title: 'Jak: Otwieranie standardowych edytorów | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], opening
- projects [Visual Studio SDK], opening standard editors
ms.assetid: d5ce10f9-047a-4b74-aa1d-295128898b89
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f42cfa64106acc41358568f4c8f6bca2cd1141fd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710790"
---
# <a name="how-to-open-standard-editors"></a>Jak: Otwórz edytory standardowe
Po otwarciu edytora standardowego umożliwia ide określić standardowy edytor dla wyznaczonego typu pliku, zamiast określania edytora specyficznego dla projektu dla pliku.

 Wykonaj następującą procedurę, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> aby zaimplementować metodę. Spowoduje to otwarcie pliku projektu w edytorze standardowym.

## <a name="to-implement-the-openitem-method-with-a-standard-editor"></a>Aby zaimplementować metodę OpenItem za pomocą standardowego edytora

1. <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> Wywołanie`RDT_EditLock`( ), aby ustalić, czy plik obiektu danych dokumentu jest już otwarty.

2. Jeśli plik jest już otwarty, ponownie nakryj plik, wywołując <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> `IDO_ActivateIfOpen` metodę, `grfIDO` określając wartość parametru.

     Jeśli plik jest otwarty, a dokument jest własnością innego projektu niż projekt wywołujący, projekt otrzymuje ostrzeżenie, że otwierany edytor pochodzi z innego projektu. Okno pliku zostanie następnie uka przeze, gdy zostanie ono otwarte.

3. Jeśli dokument nie jest otwarty lub nie w <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> uruchomionej`OSE_ChooseBestStdEditor`tabeli dokumentów, wywołanie metody ( ) , aby otworzyć standardowy edytor pliku.

     Po wywołaniu metody IDE wykonuje następujące zadania:

    1. IDE skanuje podklucz Editors/{guidEditorType}/Extensions w rejestrze, aby określić, który edytor może otworzyć plik i ma najwyższy priorytet w tym celu.

    2. Po ide określić, który edytor można otworzyć <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>plik, IDE wywołuje . Implementacja edytora tej metody zwraca informacje, które są <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> wymagane do IDE do wywołania i witryny nowo otwarty dokument.

    3. Na koniec IDE ładuje dokument przy użyciu zwykłego interfejsu <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2>trwałości, takich jak .

    4. Jeśli IDE wcześniej ustalił, że element hierarchii lub hierarchii <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> jest dostępny, IDE wywołuje metodę <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> w projekcie, aby <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> uzyskać wskaźnik kontekstu na poziomie projektu, aby przekazać z powrotem z wywołaniem metody.

4. Zwraca <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> wskaźnik do IDE, gdy <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.GetItemContext%2A> IDE wywołuje projekt, jeśli chcesz, aby edytor uzyskać kontekst z projektu.

     Wykonanie tego kroku umożliwia projektowi oferowanie edytorowi dodatkowych usług.

     Jeśli widok dokumentu lub obiekt widoku dokumentu został pomyślnie zlokalizowany w ramce okna, obiekt jest inicjowany wraz z danymi przez wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.LoadDocData%2A>.

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>
- [Otwieranie i zapisywanie elementów projektu](../extensibility/internals/opening-and-saving-project-items.md)
- [Jak: Otwieranie edytorów specyficznych dla projektu](../extensibility/how-to-open-project-specific-editors.md)
- [Jak: Otwieranie edytorów otwartych dokumentów](../extensibility/how-to-open-editors-for-open-documents.md)
- [Wyświetlanie plików za pomocą polecenia Otwórz plik](../extensibility/internals/displaying-files-by-using-the-open-file-command.md)
