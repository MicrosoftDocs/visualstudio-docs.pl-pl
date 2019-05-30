---
title: Model pakietów kontroli kodu źródłowego | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], model
ms.assetid: 6164b2d3-a622-4de8-bef3-a6de985e9ebd
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 65f212496d152236579e63ba037fe351a4dd3370
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66349222"
---
# <a name="model-for-source-control-packages"></a>Model pakietów kontroli kodu źródłowego
Poniższy model reprezentuje przykładem implementacji kontroli źródła. W modelu Zobacz interfejsów, które należy zaimplementować i usług środowiska, które należy wywołać. Podobnie jak wszystkie usługi faktycznie wywołanie metody określonego interfejsu, którą można uzyskać za pomocą usługi. Nazwy klas są identyfikowane ułatwiają zobacz sposób wykonywania kontroli źródła.

 ![SCC&#95;przykłady INSTALACYJNY](../../extensibility/internals/media/scc_tup.gif "SCC_TUP") przykładowy projekt kontroli źródła

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
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>
- [Obsługa kontroli kodu źródłowego](../../extensibility/internals/supporting-source-control.md)