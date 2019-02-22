---
title: Priorytet projektu | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: 9f707592-2fb6-4f75-9269-f6d4700a998e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 47c96e9384d561aeda3a966ca8bc5b305a9351e2
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56628263"
---
# <a name="project-priority"></a>Priorytet projektu
Element projektu jest zazwyczaj członkiem tylko jednego projektu w rozwiązaniu. W związku z tym IDE może łatwo ustalić, który projekt jest używany do otwierania elementu. Jednak jeśli element jest członkiem więcej niż jeden projekt, IDE używa schematu priorytetu do określenia najlepsze projektu do otwierania elementu.

 Na poniższej liście przedstawiono schemat priorytet projektu:

-   Wywołania środowiska IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2.IsDocumentInProject%2A> metody dla każdego projektu w rozwiązaniu, aby ustalić, czy dokument jest członkiem tego projektu.

-   Jeśli dokument jest członkiem projektu, projektu odpowiada za pomocą priorytet czy projektu przypisuje się zgodnie z jego obsługa tego dokumentu. Na przykład projekt języka odpowiada za pomocą wysoki priorytet dla jego plików źródłowych języka, ale odpowiada o niższym priorytecie typu nierozpoznanego pliku, który nie jest używany jako część procesu kompilacji.

-   Projekty, które zapewniają projektantów lub edytorach niestandardowych, specyficzne dla projektu dla dokumentu otrzymają wysoki priorytet.

-   <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> Wyliczenia zawiera dokument wartości priorytetu.

-   Projekt, który określa najwyższy priorytet otrzymuje kontekstu do otwierania tego dokumentu. Jeśli dwa projekty zwracają wartości w taki sam priorytet, aktywnego projektu jest preferowana. Jeśli brak projektu w rozwiązaniu odpowiada otworzyć dokument, IDE umieszcza dokument w projekcie różne pliki. Aby uzyskać więcej informacji, zobacz [projekt różne pliki](../../extensibility/internals/miscellaneous-files-project.md).

## <a name="see-also"></a>Zobacz też
- [Projekt Różne pliki](../../extensibility/internals/miscellaneous-files-project.md)
- [Instrukcje: Otwieranie edytorów dla otwartych dokumentów](../../extensibility/how-to-open-editors-for-open-documents.md)
- [Dodawanie projektu i szablonów elementów projektu](../../extensibility/internals/adding-project-and-project-item-templates.md)