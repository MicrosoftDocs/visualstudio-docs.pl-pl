---
title: Projekt różne pliki | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- files, adding existing files to solutions
- Miscellaneous Files project
- Solution Items folder
- files, opening with Miscellaneous Files project
ms.assetid: 93a278a8-d4f4-400b-8945-4f1b0a2b5bac
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 281213751cb25a05e8298ee35ba43453d48ed250
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53853112"
---
# <a name="miscellaneous-files-project"></a>Projekt Różne pliki
Gdy użytkownik otwiera elementów projektu, IDE przypisuje projekcie plików pozostałych wszystkie elementy, które nie są członkami żadnych projektów w rozwiązaniu.  
  
 Projekty odgrywają istotną rolę w określaniu, edytor, którego jest używany, gdy użytkownik otwiera element projektu. Można zaprojektować projektu do otwierania niektórych plików za pomocą edytora specyficznych dla projektu lub standardowy edytor.  
  
 Edytora specyficznych dla projektu zwykle wymaga, że użytkownik ma specjalnej wiedzy lub użyj specjalne interfejsy z projektu. Aby uzyskać więcej informacji, zobacz [jak: Otwieranie edytorów specyficznych dla projektu](../../extensibility/how-to-open-project-specific-editors.md).  
  
 Edytor standardowy, można otworzyć dowolny plik określone rozszerzenie w każdym projekcie. Użytkownik może dostosować niektóre standardowe edytory, takich jak [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Edytor tekstu, w przypadku projektów ale zachować ich publicznych znaków. Standardowe edytory są tworzone za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> metody.  
  
 Jeśli brak projektu w rozwiązaniu odpowiada, otworzyć element projektu, IDE udostępnia specjalne projekt o nazwie projektu różne pliki, który otwiera każdego pliku.  
  
 Tego projektu zawiera otwierania pliku poza kontekstem projektu. Podczas przetwarzania <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> metody projekcie plików pozostałych zawsze odpowiada za pomocą bardzo niskim priorytecie. W związku z tym zawsze plony do każdego projektu wyższy priorytet, który można otworzyć pliki projektu różne pliki.  
  
 Projekt różne pliki wymaga aby użytkownik jawnie utworzyć ją za pomocą **nowy projekt** okno dialogowe. Ponadto projekt różne pliki nie zarządza trwałe listę członków projektu. Opcjonalna funkcja używa, aby zarejestrować listę ostatnio używanych plików dla każdego użytkownika.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>   
 <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>   
 [Instrukcje: Otwieranie edytorów specyficznych dla projektu](../../extensibility/how-to-open-project-specific-editors.md)   
 [Instrukcje: Otwieranie standardowych edytorów](../../extensibility/how-to-open-standard-editors.md)   
 [Dodawanie projektu i szablony elementów projektu](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [Dodawanie projektu i szablonów elementów projektu](../../extensibility/internals/adding-project-and-project-item-templates.md)