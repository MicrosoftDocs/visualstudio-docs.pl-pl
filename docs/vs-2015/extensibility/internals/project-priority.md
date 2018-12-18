---
title: Priorytet projektu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: 9f707592-2fb6-4f75-9269-f6d4700a998e
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1d052658cc6f61027def4fdae89c2981581b7e27
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51742319"
---
# <a name="project-priority"></a>Priorytet projektu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Element projektu jest zazwyczaj członkiem tylko jednego projektu w rozwiązaniu. W związku z tym IDE może łatwo ustalić, który projekt jest używany do otwierania elementu. Jednak jeśli element jest członkiem więcej niż jeden projekt, IDE używa schematu priorytetu do określenia najlepsze projektu do otwierania elementu.  
  
 Na poniższej liście przedstawiono schemat priorytet projektu:  
  
-   Wywołania środowiska IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2.IsDocumentInProject%2A> metody dla każdego projektu w rozwiązaniu, aby ustalić, czy dokument jest członkiem tego projektu.  
  
-   Jeśli dokument jest członkiem projektu, projektu odpowiada za pomocą priorytet czy projektu przypisuje się zgodnie z jego obsługa tego dokumentu. Na przykład projekt języka odpowiada za pomocą wysoki priorytet dla jego plików źródłowych języka, ale odpowiada o niższym priorytecie typu nierozpoznanego pliku, który nie jest używany jako część procesu kompilacji.  
  
-   Projekty, które zapewniają projektantów lub edytorach niestandardowych, specyficzne dla projektu dla dokumentu otrzymają wysoki priorytet.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> Wyliczenia zawiera dokument wartości priorytetu.  
  
-   Projekt, który określa najwyższy priorytet otrzymuje kontekstu do otwierania tego dokumentu. Jeśli dwa projekty zwracają wartości w taki sam priorytet, aktywnego projektu jest preferowana. Jeśli brak projektu w rozwiązaniu odpowiada otworzyć dokument, IDE umieszcza dokument w projekcie różne pliki. Aby uzyskać więcej informacji, zobacz [projekt różne pliki](../../extensibility/internals/miscellaneous-files-project.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Projekt różne pliki](../../extensibility/internals/miscellaneous-files-project.md)   
 [Porady: otwieranie edytorów dla otwartych dokumentów](../../extensibility/how-to-open-editors-for-open-documents.md)   
 [Dodawanie projektu i szablonów elementów projektu](../../extensibility/internals/adding-project-and-project-item-templates.md)

