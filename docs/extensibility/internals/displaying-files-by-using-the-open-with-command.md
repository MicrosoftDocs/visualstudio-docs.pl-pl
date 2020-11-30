---
title: Wyświetlanie plików przy użyciu polecenia Otwórz za pomocą | Microsoft Docs
description: Dowiedz się, jak projekt może wywoływać polecenie Otwórz za pomocą w zintegrowanym środowisku programistycznym (IDE) programu Visual Studio, aby wyświetlić pliki.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: f2cb6bd44148d470cac68addc09db9e9207e9d70
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/30/2020
ms.locfileid: "96329695"
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
