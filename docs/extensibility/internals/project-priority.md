---
title: Priorytet projektu | Microsoft Docs
description: Dowiedz się więcej na temat schematu priorytetowego używanego przez środowisko IDE programu Visual Studio w celu określenia najlepszego projektu do otwarcia elementu, jeśli element jest członkiem więcej niż jednego projektu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: 9f707592-2fb6-4f75-9269-f6d4700a998e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1389668bbcd1239fbb1ae0e865478bf0e0f6a7e8
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877380"
---
# <a name="project-priority"></a>Priorytet projektu
Element projektu jest zwykle członkiem tylko jednego projektu w rozwiązaniu. W związku z tym IDE może łatwo określić, który projekt jest używany do otwierania elementu. Jeśli jednak element jest członkiem więcej niż jednego projektu, IDE używa schematu priorytetowego do określenia najlepszego projektu do otwierania elementu.

 Na poniższej liście przedstawiono schemat priorytetu projektu:

- IDE wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2.IsDocumentInProject%2A> metodę dla każdego projektu w rozwiązaniu, aby określić, czy dokument jest członkiem tego projektu.

- Jeśli dokument jest członkiem projektu, projekt reaguje na priorytet, który projekt przypisuje zgodnie z obsługą tego dokumentu. Na przykład projekt języka reaguje na wysoki priorytet dla plików źródłowych języka, ale reaguje z niższym priorytetem dla nierozpoznanego typu pliku, który nie jest używany jako część procesu kompilacji.

- Projekty, które udostępniają niestandardowe edytory charakterystyczne dla projektu lub projektanci dla dokumentu, otrzymują również wysoki priorytet.

- <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>Wyliczenie zawiera wartości priorytetu dokumentu.

- W projekcie, który określa najwyższy priorytet, jest przyznany kontekst służący do otwierania dokumentu. Jeśli dwa projekty zwracają wartości priorytetowe, preferowany jest aktywny projekt. Jeśli żaden projekt w rozwiązaniu nie odpowiada, że może otworzyć dokument, IDE umieści dokument w projekcie różne pliki. Aby uzyskać więcej informacji, zobacz temat [różne pliki projektu](../../extensibility/internals/miscellaneous-files-project.md).

## <a name="see-also"></a>Zobacz też
- [Projekt Różne pliki](../../extensibility/internals/miscellaneous-files-project.md)
- [Instrukcje: otwieranie edytorów dla otwartych dokumentów](../../extensibility/how-to-open-editors-for-open-documents.md)
- [Dodawanie szablonów projektów i elementów projektu](../../extensibility/internals/adding-project-and-project-item-templates.md)
