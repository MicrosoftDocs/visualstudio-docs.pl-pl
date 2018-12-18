---
title: 'Porady: otwieranie edytorów dla otwartych dokumentów | Dokumentacja firmy Microsoft'
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
- editors [Visual Studio SDK], opening for open documents
ms.assetid: 1a0fa49c-efa4-4dcc-bdc0-299b7052acdc
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4bb21def7e9d283c287c375bd9b8b4cc6bd30c3c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51750983"
---
# <a name="how-to-open-editors-for-open-documents"></a>Porady: otwieranie edytorów dla otwartych dokumentów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Przed projektu powoduje otwarcie okna dokumentów, projektu najpierw należy określić czy plik jest już otwarty w oknie dokumentu innym edytorze. Może to być plik albo otworzyć w edytorze specyficzne dla projektu lub jednego z standardowych edytorów zarejestrowane w usłudze [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="opening-a-project-specific-editor"></a>Otwieranie Edytora specyficznych dla projektu  
 Użyj poniższej procedury, można otworzyć edytora specyficznych dla projektu, dla pliku, który jest już otwarty.  
  
#### <a name="to-open-a-project-specific-editor-for-an-open-file"></a>Aby otworzyć Edytor specyficzne dla projektu, dla otwartego pliku  
  
1. Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> metody.  
  
    To wywołanie zwraca wskaźników do hierarchii, element hierarchii i ramki okna dokumentu, jeśli to stosowne.  
  
2. Jeśli dokument jest otwarty, projekt musi sprawdzić, czy istnieje tylko obiekt danych dokumentów, czy obiekt widoku dokumentu również znajduje się.  
  
   - Jeśli istnieje obiekt widoku dokumentu, a ten widok jest w innej hierarchii lub element hierarchii, projekt używa wskaźnik do ramki okna w widoku do resurface istniejące okno.  
  
   - Jeśli istnieje obiekt widoku dokumentu, a ten widok służy do tej samej hierarchii i element hierarchii, projektu mogą otwierać drugi widok, jeśli można dołączyć do bazowego obiektu danych dokumentu. W przeciwnym razie projektu należy za pomocą wskaźnika do ramki okna widoku resurface istniejące okno.  
  
   - Jeśli istnieje obiekt danych dokumentu, tylko projekt należy określić, czy obiekt danych dokumentu może używać jej widoku. Jeśli obiekt danych dokumentu jest zgodny, pełną kroki omówione w [otwierania Edytora specyficznych dla projektu](../extensibility/how-to-open-project-specific-editors.md).  
  
     Jeśli obiekt danych dokumentu nie jest zgodny, błąd powinien zostać wyświetlony do użytkownika, który wskazuje, że plik jest obecnie w użyciu. Ten błąd tylko powinna być wyświetlana w przejściowe przypadki, np. gdy plik jest kompilowany w tym samym czasie użytkownik próbuje otworzyć plik za pomocą edytora innych niż [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] podstawowy edytor tekstu. Podstawowy edytor tekstu można udostępniać obiekt danych dokumentu za pomocą kompilatora.  
  
3. Jeśli dokument nie jest otwarty, ponieważ nie ma obiektu danych dokumentu lub obiektu widoku dokumentu, wykonaj kroki opisane w [otwierania Edytora specyficznych dla projektu](../extensibility/how-to-open-project-specific-editors.md).  
  
## <a name="opening-a-standard-editor"></a>Otwieranie Edytora Standard  
 Użyj poniższej procedury, aby otworzyć Edytor standardowy w pliku, który jest już Otwórz.  
  
#### <a name="to-open-a-standard-editor-for-an-open-file"></a>Aby otworzyć Edytor standardowy dla otwartego pliku  
  
1.  Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>.  
  
     Ta metoda sprawdza najpierw, że dokument nie jest już otwarty przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A>. Jeśli dokument jest już otwarty, to resurfaced jej okna edytora.  
  
2.  Jeśli dokument nie jest otwarty, wykonaj kroki [porady: otwieranie standardowych edytorów](../extensibility/how-to-open-standard-editors.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Otwieranie i zapisywanie elementów projektu](../extensibility/internals/opening-and-saving-project-items.md)   
 [Porady: otwieranie edytorów specyficznych dla projektu](../extensibility/how-to-open-project-specific-editors.md)   
 [Instrukcje: otwieranie standardowych edytorów](../extensibility/how-to-open-standard-editors.md)

