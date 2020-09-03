---
title: Wyświetlanie plików przy użyciu polecenia Otwórz za pomocą | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80708577"
---
# <a name="display-files-by-using-the-open-with-command"></a>Wyświetlanie plików przy użyciu polecenia Otwórz za pomocą
Projekt może polecić środowisku IDE wyświetlenie okna dialogowego **Otwórz za pomocą** . To żądanie monituje użytkownika o otwarcie pliku, który ma wybór standardowych edytorów. Poniższe kroki opisują ten proces:

1. Projekt wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> , określając wartość `OSE_UseOpenWithDialog` `OSEOpenDocEditor` parametru.

2. Na podstawie rozszerzenia nazwy pliku dokumentu IDE Określa, które edytory wymienione w rejestrze mogą otworzyć określony dokument i wyświetlić te informacje w oknie dialogowym **Otwórz za pomocą** .

    > [!NOTE]
    > Projekty z wewnętrznym edytorem, które muszą być zawarte w oknie dialogowym **Otwórz za pomocą** , muszą zarejestrować fabrykę edytora dla każdego takiego edytora. Edytory wewnętrzne działają tylko razem z konkretnym typem projektu, który jest wymuszany w implementacji <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> metody. IDE ma wbudowaną fabrykę edytora dla podstawowego edytora tekstów i edytora binarnego. IDE tworzy również wystąpienie fabryki edytora w imieniu każdego zarejestrowanego skojarzenia pliku systemu Windows. Przykładem takiego pliku jest program Microsoft Word.

3. Gdy tylko użytkownik wybierze element z okna dialogowego **Otwórz za pomocą** , IDE następnie otworzy dokument przez wywołanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metody. Aby uzyskać więcej informacji, zobacz [How to: Open Standard Editors](../../extensibility/how-to-open-standard-editors.md).

## <a name="see-also"></a>Zobacz też
- [Otwieranie i zapisywanie elementów projektu](../../extensibility/internals/opening-and-saving-project-items.md)
- [Wyświetlanie plików przy użyciu polecenia Otwórz plik](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)
- [Instrukcje: otwieranie edytorów standardowych](../../extensibility/how-to-open-standard-editors.md)
