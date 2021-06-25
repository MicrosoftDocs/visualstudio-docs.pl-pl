---
title: Priorytet projektu | Microsoft Docs
description: Dowiedz się więcej o schemacie priorytetu używanym przez Visual Studio IDE, aby określić najlepszy projekt do otwarcia elementu, jeśli element jest elementem członkowskim więcej niż jednego projektu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: 9f707592-2fb6-4f75-9269-f6d4700a998e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2ac0556e63b25f0f2a0df399cb23d5e2e9473008
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899644"
---
# <a name="project-priority"></a>Priorytet projektu
Element projektu zazwyczaj jest elementem członkowskim tylko jednego projektu w rozwiązaniu. W związku z tym ide może łatwo określić, który projekt jest używany do otwierania elementu. Jeśli jednak element jest elementem członkowskim więcej niż jednego projektu, w idee jest używany schemat priorytetu w celu określenia najlepszego projektu do otwarcia elementu.

 Na poniższej liście przedstawiono schemat priorytetu projektu:

- Ide wywołuje metodę dla każdego projektu w rozwiązaniu, aby określić, czy dokument jest <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2.IsDocumentInProject%2A> członkiem tego projektu.

- Jeśli dokument jest członkiem projektu, projekt odpowiada priorytetem przypisanym do projektu zgodnie z jego obsługą tego dokumentu. Na przykład projekt języka odpowiada z wysokim priorytetem dla plików źródłowych języka, ale odpowiada z niższym priorytetem dla nierozpoznanych typów plików, które nie są używane w procesie kompilacji.

- Projekty, które zapewniają niestandardowe edytory specyficzne dla projektu lub projektantów dla dokumentu, również mają wysoki priorytet.

- <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>Wyliczenie zawiera wartości priorytetów dokumentu.

- Projekt, który określa najwyższy priorytet, ma nadany kontekst otwierania dokumentu. Jeśli dwa projekty zwracają takie same wartości priorytetów, preferowany jest aktywny projekt. Jeśli żaden projekt w rozwiązaniu nie odpowie, że może otworzyć dokument, idee umieszczają dokument w projekcie Różne pliki. Aby uzyskać więcej informacji, zobacz [Temat Różne pliki Project](../../extensibility/internals/miscellaneous-files-project.md).

## <a name="see-also"></a>Zobacz też
- [Projekt Różne pliki](../../extensibility/internals/miscellaneous-files-project.md)
- [Instrukcje: otwieranie edytorów dla otwartych dokumentów](../../extensibility/how-to-open-editors-for-open-documents.md)
- [Dodawanie szablonów projektów i elementów projektu](../../extensibility/internals/adding-project-and-project-item-templates.md)
