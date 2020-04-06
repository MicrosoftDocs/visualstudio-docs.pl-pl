---
title: Priorytet projektu | Dokumenty firmy Microsoft
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
ms.openlocfilehash: a75c1c333d88e1bf5524281bee8b2a683ca6c98e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706418"
---
# <a name="project-priority"></a>Priorytet projektu
Element projektu zwykle jest członkiem tylko jednego projektu w rozwiązaniu. W związku z tym IDE można łatwo określić, który projekt jest używany do otwierania elementu. Jednak jeśli element jest członkiem więcej niż jednego projektu, IDE używa schematu priorytetu, aby określić najlepszy projekt do otwarcia elementu.

 Na poniższej liście przedstawiono schemat priorytetu projektu:

- IDE wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2.IsDocumentInProject%2A> metodę dla każdego projektu w rozwiązaniu, aby ustalić, czy dokument jest członkiem tego projektu.

- Jeśli dokument jest członkiem projektu, projekt odpowiada z priorytetem, który projekt przypisuje zgodnie z jego obsługi tego dokumentu. Na przykład projekt języka odpowiada z wysokim priorytetem dla swoich plików źródłowych języka, ale odpowiada z niższym priorytetem dla nierozpoznanego typu pliku, który nie jest używany jako część jego procesu kompilacji.

- Projekty, które zapewniają niestandardowe, specyficzne dla projektu edytory lub projektanci dokumentu również otrzymują wysoki priorytet.

- Wyliczenie <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> zawiera wartości priorytetu dokumentu.

- Projekt, który określa najwyższy priorytet, otrzymuje kontekst do otwarcia dokumentu. Jeśli dwa projekty zwracają równe wartości priorytetu, preferowany jest aktywny projekt. Jeśli żaden projekt w rozwiązaniu nie odpowiada, że można otworzyć dokument, IDE umieszcza dokument w projekcie Różne pliki. Aby uzyskać więcej informacji, zobacz [Różne pliki projektu](../../extensibility/internals/miscellaneous-files-project.md).

## <a name="see-also"></a>Zobacz też
- [Projekt Różne pliki](../../extensibility/internals/miscellaneous-files-project.md)
- [Instrukcje: otwieranie edytorów dla otwartych dokumentów](../../extensibility/how-to-open-editors-for-open-documents.md)
- [Dodawanie szablonów projektów i elementów projektu](../../extensibility/internals/adding-project-and-project-item-templates.md)
