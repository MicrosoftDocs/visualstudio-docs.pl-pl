---
title: Wyświetlanie plików za pomocą polecenia Otwórz za pomocą | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, supporting Open With command
- Open With command
- persistence, supporting Open With command
ms.assetid: 53794bc3-1b73-4d40-954e-cfade1abddcf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4051793077e613981e1dd5b44f1736878f5853e9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708577"
---
# <a name="display-files-by-using-the-open-with-command"></a>Wyświetlanie plików za pomocą polecenia Otwórz za pomocą
Projekt może poprosić IDE o wyświetlenie okna dialogowego **Otwórz za pomocą.** To żądanie monituje użytkownika o otwarcie pliku, który ma wybór standardowych edytorów. W poniższych krokach opisano ten proces:

1. Projekt wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>, określając wartość `OSE_UseOpenWithDialog` dla `OSEOpenDocEditor` parametru.

2. Na podstawie rozszerzenia nazwy pliku dokumentu IDE określa, którzy edytorzy wymienieni w rejestrze mogą otwierać określony dokument i wyświetla te informacje w oknie dialogowym **Otwórz z.**

    > [!NOTE]
    > Projekty, które mają edytor wewnętrznego, który musi być uwzględniony w oknie dialogowym **Otwórz za pomocą,** muszą zarejestrować fabrykę edytora dla każdego takiego edytora. Edytory wewnętrzne działają tylko razem z określonym typem projektu, który jest <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> wymuszany w implementacji metody. IDE ma wbudowaną fabrykę edytora dla edytora tekstu core i edytora binarnego. IDE tworzy również wystąpienie fabryki edytora w imieniu każdego zarejestrowanego skojarzenia plików systemu Windows. Przykładem takiego pliku jest Microsoft Word.

3. Jak tylko użytkownik wybierze element z okna dialogowego **Otwórz za** pomocą, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> IDE następnie otwiera dokument przez wywołanie metody. Aby uzyskać więcej informacji, zobacz [Jak: Otwórz edytory standardowe](../../extensibility/how-to-open-standard-editors.md).

## <a name="see-also"></a>Zobacz też
- [Otwieranie i zapisywanie elementów projektu](../../extensibility/internals/opening-and-saving-project-items.md)
- [Wyświetlanie plików za pomocą polecenia Otwórz plik](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)
- [Jak: Otwórz edytory standardowe](../../extensibility/how-to-open-standard-editors.md)
