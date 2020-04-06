---
title: 'Jak: Otwórz edytory specyficzne dla projektu | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, opening a project-specific editor
- editors [Visual Studio SDK], opening project-specific editors
- projects [Visual Studio SDK], opening folders
ms.assetid: 83e56d39-c97b-4c6b-86d6-3ffbec97e8d1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3cb6e360a38d64de4976f83b0167d47dc03fbc87
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710838"
---
# <a name="how-to-open-project-specific-editors"></a>Jak: Otwieranie edytorów specyficznych dla projektu
Jeśli plik elementu otwierany przez projekt jest wewnętrznie powiązany z określonym edytorem dla tego projektu, projekt musi otworzyć plik przy użyciu edytora specyficznego dla projektu. Nie można delegować pliku do mechanizmu IDE do wybierania edytora. Na przykład zamiast standardowego edytora bitmap można użyć tej opcji edytora specyficznej dla projektu, aby określić określony edytor bitmap, który rozpoznaje informacje w pliku, który jest unikatowy dla projektu.

 IDE wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> metodę, gdy określa, że plik powinien być otwarty przez określony projekt. Aby uzyskać więcej informacji, zobacz [Wyświetlanie plików za pomocą polecenia Otwórz plik](../extensibility/internals/displaying-files-by-using-the-open-file-command.md). Skorzystaj z poniższych `OpenItem` wskazówek, aby zaimplementować metodę, aby projekt otworzył plik przy użyciu edytora specyficznego dla projektu.

## <a name="to-implement-the-openitem-method-with-a-project-specific-editor"></a>Aby zaimplementować metodę OpenItem za pomocą edytora specyficznego dla projektu

1. Wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> metody`RDT_EditLock`( ), aby ustalić, czy plik (obiekt danych dokumentu) jest już otwarty.

    > [!NOTE]
    > Aby uzyskać więcej informacji o danych dokumentu i obiektach widoku dokumentu, zobacz [Dane dokumentu i widok dokumentu w edytorach niestandardowych](../extensibility/document-data-and-document-view-in-custom-editors.md).

2. Jeśli plik jest już otwarty, ponownie nakryj plik, wywołując <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> metodę i określając `grfIDO` wartość IDO_ActivateIfOpen dla parametru.

     Jeśli plik jest otwarty, a dokument jest własnością projektu innego niż projekt wywołujący, zostanie wyświetlone ostrzeżenie dla użytkownika, że otwierany edytor pochodzi z innego projektu. Okno pliku zostanie następnie uka przeze, gdy zostanie ono otwarte.

3. Jeśli bufor tekstu (obiekt danych dokumentu) jest już otwarty i chcesz dołączyć do niego inny widok, użytkownik jest odpowiedzialny za podłączenie tego widoku. Zalecane podejście do tworzenia wystąpienia widoku (obiekt widoku dokumentu) z projektu, jest w następujący sposób:

    1. Wezwiej `QueryService` usługę, <xref:Microsoft.VisualStudio.Shell.Interop.SLocalRegistry> aby <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> uzyskać wskaźnik do interfejsu.

    2. Wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> metody, aby utworzyć wystąpienie klasy widoku dokumentu.

4. Wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> metody, określając obiekt widoku dokumentu.

     Ta metoda witryn obiektu widoku dokumentu w oknie dokumentu.

5. Wykonaj odpowiednie wywołania do <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.InitNew%2A> lub <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> metody.

     W tym momencie widok powinien być w pełni zainicjowany i gotowy do otwarcia.

6. Wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> metody, aby pokazać i otworzyć widok.

## <a name="see-also"></a>Zobacz też
- [Otwieranie i zapisywanie elementów projektu](../extensibility/internals/opening-and-saving-project-items.md)
- [Jak: Otwórz edytory standardowe](../extensibility/how-to-open-standard-editors.md)
- [Jak: Otwieranie edytorów otwartych dokumentów](../extensibility/how-to-open-editors-for-open-documents.md)
