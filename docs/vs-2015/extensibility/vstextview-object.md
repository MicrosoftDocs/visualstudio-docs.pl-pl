---
title: Obiekt VSTextView | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- VSTextView
helpviewer_keywords:
- VSTextView object, reference
- views [Visual Studio SDK], reference
ms.assetid: 78272ddc-9718-4c65-a94e-a44a2e8d54f4
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f99587af3d16210305181f6435905521561f8500
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54765042"
---
# <a name="vstextview-object"></a>VSTextView, obiekt
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Widok tekstu jest oknem które umożliwia użytkownikom wyświetlanie i edytowanie tekst w formacie Unicode bufor tekstowy. Zasadniczo jest to widok co dotyczą większości użytkowników jako edytora. Ponieważ widok jest oddzielone z buforu różne warstwy tekstu (zawijanie wyrazów, konspektu tekstu i tak dalej), widoku nie może być dokładne reprezentacja tekstu w buforze. Aby uzyskać więcej informacji na temat widoku tekstu, zobacz [dostęp do theText widoku przy użyciu starszej wersji interfejsu API](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)  
  
 W poniższej tabeli przedstawiono interfejsów w <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> obiektu.  
  
|Interface|Opis|  
|---------------|-----------------|  
|[IDropSource](http://msdn.microsoft.com/library/windows/desktop/ms690071)|Standardowy interfejs OLE.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget>|Standardowy interfejs OLE.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>|Standardowy interfejs OLE.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Standardowy interfejs OLE.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Włącza funkcję tworzenia działania złożonego (czyli akcje, które są grupowane w jednostce pojedynczego Cofnij/ponów).|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|Zawiera podstawowe metody do zarządzania i uzyskiwania dostępu do tego widoku. `IVsTextView` nie jest wątek bezpieczne.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Tworzy i zarządza okienka w oknie.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|Współdziała z warstwami tekstu.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsThreadSafeTextView>|Wykonuje operacje na widok z innego wątku.|  
  
## <a name="see-also"></a>Zobacz też  
 [Edytuj dane](http://msdn.microsoft.com/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)   
 [VSTextBuffer Object](../extensibility/vstextbuffer-object.md)   
 [Uzyskiwanie dostępu do widoku tekstowego przy użyciu starszego interfejsu API](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)
