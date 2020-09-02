---
title: Języki zawarte | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - contained languages
ms.assetid: b75bbb51-8e42-41b1-bece-09ab0b1f03cc
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0920999eee7460c8bf697e245bae55a3641b8e18
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184277"
---
# <a name="contained-languages"></a>Zawarte języki
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)] 

*Języki zawarte* są językach, które są zawarte w innych językach. Na przykład HTML na [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] stronach może zawierać [!INCLUDE[csprcs](../includes/csprcs-md.md)] lub [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] skrypty. W edytorze plików aspx jest wymagana architektura dwujęzykowa, która zapewnia IntelliSense, kolorowanie i inne funkcje edycji dla języka HTML i skryptów.  
  
## <a name="implementation"></a>Implementacja  
 Najważniejszym interfejsem, który ma być zaimplementowany w zawartych językach, jest <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> interfejs. Ten interfejs jest implementowany przez dowolny język, który może być hostowany w języku podstawowym. Daje ona dostęp do tego koloru, filtru widoku tekstu i identyfikatora usługi języka podstawowego. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory>Umożliwia utworzenie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> interfejsu. W poniższych krokach przedstawiono sposób implementacji zawartego języka:  
  
1. Użyj, `QueryService()` Aby uzyskać identyfikator usługi językowej i identyfikator interfejsu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory> .  
  
2. Wywołaj <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguageFactory.GetLanguage%2A> metodę, aby utworzyć <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> interfejs. Przekaż <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> interfejs, co najmniej jeden [Identyfikator elementu](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID>) i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator> interfejs.  
  
3. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>Interfejs, który jest obiektem koordynatora bufora tekstowego, udostępnia podstawowe usługi, które są wymagane do mapowania lokalizacji w pliku podstawowym do buforu języka pomocniczego.  
  
     Na przykład w jednym pliku aspx plik podstawowy zawiera ASP, HTML i cały zawarty w nim kod. Jednak bufor pomocniczy, zawiera tylko zawarty kod, wraz z dowolnymi definicjami klas, aby bufor pomocniczy był prawidłowym plikiem kodu. Koordynator buforu obsługuje prace koordynujące edycje z jednego buforu do drugiego.  
  
4. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A>Metoda, która jest językiem podstawowym, informuje koordynatora bufora o tym, jaki tekst w buforze jest mapowany do odpowiadającego mu tekstu w buforze pomocniczym.  
  
     Język przekazuje tablicę <xref:Microsoft.VisualStudio.TextManager.Interop.NewSpanMapping> struktury, która obecnie zawiera tylko podstawowy i pomocniczy zakres.  
  
5. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapPrimaryToSecondarySpan%2A>Metoda i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.MapSecondaryToPrimarySpan%2A> Metoda zapewniają mapowanie od podstawowego do pomocniczego buforu i na odwrót.
