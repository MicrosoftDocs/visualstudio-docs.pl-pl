---
title: Zawiera języki | Dokumentacja firmy Microsoft
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
- editors [Visual Studio SDK], legacy - contained languages
ms.assetid: b75bbb51-8e42-41b1-bece-09ab0b1f03cc
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c4ff50fe0fe156c548351c378ba3a256e230ec43
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51772029"
---
# <a name="contained-languages"></a>Języki zawarte
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)] 

  
*Zawiera języki* języków, które znajdują się w innych językach. Na przykład HTML w [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] strony mogą zawierać [!INCLUDE[csprcs](../includes/csprcs-md.md)] lub [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] skryptów. Architektura podwójnego język jest wymagany dla edytora plików .aspx, do zapewnienia funkcji IntelliSense, kolorowanie i inne funkcje edytowania HTML i języka skryptów.  
  
## <a name="implementation"></a>Implementacja  
 Najważniejsze interfejs, należy wdrożyć dla języków zawartych <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> interfejsu. Ten interfejs jest implementowany za pomocą dowolnego języka, który może znajdować się wewnątrz podstawowy język. Jej daje dostęp do usługi języka colorizer filtr widoku tekstu i identyfikator podstawowy język usługi. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory> Pozwala na tworzenie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> interfejsu. Poniższe kroki pokazują, jak zaimplementować zawartej języka:  
  
1.  Użyj `QueryService()` można pobrać języka, identyfikator usługi i identyfikator interfejsu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory>.  
  
2.  Wywołaj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory.GetLanguage%2A> metodę w celu utworzenia <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> interfejsu. Przekaż <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> interfejsu, co najmniej jeden [elementu identyfikatory](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID>) i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> interfejsu.  
  
3.  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> Interfejs, który jest obiektem koordynatora buforu tekstu, oferuje podstawowe usługi, które są wymagane do mapowania lokalizacji w podstawowym pliku do buforu dodatkowej języka.  
  
     Na przykład w pliku .aspx pojedynczy plik podstawowy zawiera ASP, HTML i cały kod, który znajduje się. Jednak dodatkowej buforu obejmuje tylko kod, wraz z żadnych definicji klas zapewnienie dodatkowej buforu pliku prawidłowy kod. Koordynator buforu obsługuje pracę koordynowanie zmian z buforu do drugiego.  
  
4.  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A> Koordynator buforu informuje o metodę, która jest podstawowy język, jaki tekst w ramach jego buforu jest mapowany na odpowiedni tekst w buforze dodatkowej.  
  
     Język przekazuje tablicę <xref:Microsoft.VisualStudio.TextManager.Interop.NewSpanMapping> struktury, która obecnie zawiera tylko podstawowy i pomocniczy zakresu.  
  
5.  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapPrimaryToSecondarySpan%2A> Metody i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapSecondaryToPrimarySpan%2A> metoda dostarcza mapowanie z podstawowej do dodatkowej buforu i na odwrót.

