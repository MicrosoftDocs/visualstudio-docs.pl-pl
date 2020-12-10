---
title: 'Instrukcje: otwieranie edytorów Project-Specific | Microsoft Docs'
description: Dowiedz się, jak zaimplementować metodę OpenItem z edytorem specyficznym dla projektu, aby projekt mógł otworzyć plik powiązany z edytorem dla tego projektu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: 4cbba1f4d6cf0a2a5a45dd2999afa5bbf3443fca
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2020
ms.locfileid: "96993786"
---
# <a name="how-to-open-project-specific-editors"></a>Instrukcje: otwieranie edytorów specyficznych dla projektu
Jeśli plik elementu, który jest otwierany przez projekt, jest w sposób wewnętrzny powiązany z określonym edytorem dla danego projektu, projekt musi otworzyć plik przy użyciu edytora specyficznego dla projektu. Nie można delegować pliku do mechanizmu IDE w celu wybrania edytora. Na przykład zamiast używać standardowego edytora mapy bitowej, można użyć tej opcji edytora dla danego projektu, aby określić konkretny Edytor mapy bitowej, który rozpoznaje informacje w pliku, który jest unikatowy dla Twojego projektu.

 IDE wywołuje metodę, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A> gdy określa, że plik powinien być otwarty przez określony projekt. Aby uzyskać więcej informacji, zobacz [Wyświetlanie plików przy użyciu polecenia Otwórz plik](../extensibility/internals/displaying-files-by-using-the-open-file-command.md). Skorzystaj z poniższych wskazówek, aby zaimplementować `OpenItem` metodę, aby projekt mógł otworzyć plik przy użyciu edytora specyficznego dla projektu.

## <a name="to-implement-the-openitem-method-with-a-project-specific-editor"></a>Aby zaimplementować metodę OpenItem z edytorem specyficznym dla projektu

1. Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A> metodę ( `RDT_EditLock` ), aby określić, czy plik (obiekt danych dokumentu) jest już otwarty.

    > [!NOTE]
    > Aby uzyskać więcej informacji o danych dokumentu i obiektach widoku dokumentu, zobacz [dane dokumentu i widok dokumentu w edytorach niestandardowych](../extensibility/document-data-and-document-view-in-custom-editors.md).

2. Jeśli plik jest już otwarty, należy go ponownie utworzyć, wywołując <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> metodę i określając wartość IDO_ActivateIfOpen dla `grfIDO` parametru.

     Jeśli plik jest otwarty, a dokument jest własnością projektu innego niż wywołujący projekt, do użytkownika zostanie wyświetlone ostrzeżenie, że otwarty Edytor pochodzi z innego projektu. Następnie zostanie wyświetlone okno plik.

3. Jeśli bufor tekstowy (obiekt danych dokumentu) jest już otwarty i chcesz dołączyć do niego inny widok, użytkownik jest odpowiedzialny za podłączenie tego widoku. Zalecane podejście do tworzenia wystąpienia widoku (obiekt widoku dokumentu) z projektu jest następujące:

    1. Zadzwoń do `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SLocalRegistry> usługi, aby uzyskać wskaźnik do <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2> interfejsu.

    2. Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry2.CreateInstance%2A> metodę, aby utworzyć wystąpienie klasy widoku dokumentu.

4. Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.CreateDocumentWindow%2A> metodę, określając obiekt widoku dokumentu.

     Ta metoda służy do wyświetlania obiektu widoku dokumentu w oknie dokumentu.

5. Wykonaj odpowiednie wywołania <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.InitNew%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat.Load%2A> metody lub.

     W tym momencie widok powinien być w pełni zainicjowany i gotowy do otwarcia.

6. Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> metodę, aby wyświetlić widok i otworzyć go.

## <a name="see-also"></a>Zobacz też
- [Otwieranie i zapisywanie elementów projektu](../extensibility/internals/opening-and-saving-project-items.md)
- [Instrukcje: otwieranie edytorów standardowych](../extensibility/how-to-open-standard-editors.md)
- [Instrukcje: otwieranie edytorów dla otwartych dokumentów](../extensibility/how-to-open-editors-for-open-documents.md)
