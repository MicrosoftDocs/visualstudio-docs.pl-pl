---
title: Model pakietów kontroli źródła | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], model
ms.assetid: 6164b2d3-a622-4de8-bef3-a6de985e9ebd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 46845be1bc22a67d6703af12933945bdfcfa7f4b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707069"
---
# <a name="model-for-source-control-packages"></a>Model pakietów kontroli kodu źródłowego
Poniższy model przedstawia przykład implementacji kontroli źródła. W modelu zostaną wyświetlony interfejsy, które należy zaimplementować i usługi środowiska, które należy wywołać. Podobnie jak wszystkie usługi, faktycznie wywołać metody określonego interfejsu, które można uzyskać za pomocą usługi. Nazwy klas są identyfikowane, aby ułatwić, aby zobaczyć, jak kontrola źródła jest przeprowadzana.

 ![SCC&#95;TUP Przykłady](../../extensibility/internals/media/scc_tup.gif "SCC_TUP") Przykładowy projekt kontroli źródła

## <a name="interfaces"></a>Interfejsy
 Formant źródła dla nowych typów projektów w programie Visual Studio można zaimplementować przy użyciu listy interfejsów pokazano w poniższej tabeli.

|Interface|Użycie|
|---------------|---------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|Wywoływane przez projekty i edytory, zanim zapiszą lub zmienią (zabrudzone) pliki. Ten interfejs jest dostępny <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave> za pomocą usługi.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|Wywoływane przez projekty, aby poprosić o uprawnienie do dodawania, usuwania lub zmieniania nazwy pliku lub katalogu. Ten interfejs jest również wywoływany przez projekty, aby poinformować środowisko po zakończeniu zatwierdzonej akcji dodawania, usuwania lub zmiany nazwy. Jest on dostępny <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments> za pomocą usługi.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|Zaimplementowana przez dowolną jednostkę, która rejestruje się, aby otrzymywać powiadomienia, gdy projekty dodają, zmieniają nazwę lub usuwają plik lub katalog. Aby zarejestrować się <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>w celu powiadomienia o zdarzeniu, zadzwoń do .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|Wywoływane przez projekty, aby zarejestrować się w pakiecie kontroli źródła i uzyskać informacje na temat stanu kontroli źródła. Ten interfejs jest dostępny <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager> za pomocą usługi.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Zaimplementowane przez projekt, aby odpowiedzieć na żądania kontroli źródła informacji o plikach i uzyskać ustawienia kontroli źródła wymagane dla pliku projektu.|

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>
- [Obsługa kontroli kodu źródłowego](../../extensibility/internals/supporting-source-control.md)
