---
title: Model pakietów kontroli kodu źródłowego | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], model
ms.assetid: 6164b2d3-a622-4de8-bef3-a6de985e9ebd
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 811cdfa2cbae85d6509e7cd883c5675b81639fa0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68198433"
---
# <a name="model-for-source-control-packages"></a>Model pakietów kontroli kodu źródłowego
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Poniższy model reprezentuje przykładem implementacji kontroli źródła. W modelu Zobacz interfejsów, które należy zaimplementować i usług środowiska, które należy wywołać. Podobnie jak wszystkie usługi faktycznie wywołanie metody określonego interfejsu, którą można uzyskać za pomocą usługi. Nazwy klas są identyfikowane ułatwiają zobacz sposób wykonywania kontroli źródła.  
  
 ![SCC&#95;przykłady INSTALACYJNY](../../extensibility/internals/media/scc-tup.gif "SCC_TUP")  
Przykładowy projekt kontroli źródła  
  
## <a name="interfaces"></a>Interfejsy  
 Możesz zaimplementować kontrolę źródła dla nowych typów projektów, w programie Visual Studio przy użyciu listy interfejsów pokazano w poniższej tabeli.  
  
|Interface|Zastosowanie|  
|---------------|---------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|Metoda wywoływana przez projektach i edytorach przed ich zapisywania lub pliki zmiany (dirty). Ten interfejs jest dostępny za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> usługi.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|Metoda wywoływana przez projektów, aby poprosić o uprawnienie do dodawania, usuwania lub zmiany nazwy pliku lub katalogu. Ten interfejs jest również wywoływany przez projekty poinformować, że środowisko podczas dodawania, usuń lub zmień nazwę akcji zostało ukończone. Odbywa się przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments> usługi.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|Implementowany przez wszystkie jednostki, który rejestruje, aby otrzymywać powiadomienia, gdy projektów dodać, zmienić lub usunąć pliku lub katalogu. Aby zarejestrować dla powiadomień o zdarzeniach, należy wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|Metoda wywoływana przez projekty do rejestracji przy użyciu pakietu kontroli źródła i uzyskiwania informacji na temat stan kontroli źródła. Ten interfejs jest dostępny za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> usługi.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Implementowany przez projekt, odpowiadanie na żądania kontroli źródła informacji na temat plików i uzyskanie źródła kontrolki skonfigurowano ustawienia wymagane do pliku projektu.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>   
 [Obsługa kontroli kodu źródłowego](../../extensibility/internals/supporting-source-control.md)
