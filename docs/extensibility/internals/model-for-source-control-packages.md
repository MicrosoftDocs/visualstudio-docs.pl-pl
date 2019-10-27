---
title: Model dla pakietów kontroli źródła | Microsoft Docs
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
ms.openlocfilehash: 1a9ae5f2704d625da2212e92626c33fb384ebbc5
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726563"
---
# <a name="model-for-source-control-packages"></a>Model pakietów kontroli kodu źródłowego
Poniższy model reprezentuje przykład implementacji kontroli źródła. W modelu widoczne są interfejsy, które należy zaimplementować, oraz usługi środowiska, które należy wywołać. Podobnie jak wszystkie usługi, w rzeczywistości wywołujemy metody określonego interfejsu, które uzyskuje się w ramach usługi. Nazwy klas są identyfikowane, aby ułatwić sprawdzenie, jak jest przeprowadzana kontrola źródła.

 ![Przykłady&#95;instalacyjny SCC](../../extensibility/internals/media/scc_tup.gif "SCC_TUP") Przykładowy projekt kontroli źródła

## <a name="interfaces"></a>Interfejsy
 Można zaimplementować kontrolę źródła dla nowych typów projektów w programie Visual Studio przy użyciu listy interfejsów przedstawionych w poniższej tabeli.

|Interface|Zastosowanie|
|---------------|---------|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>|Wywoływane przez projekty i edytory, zanim zapiszą lub zmienią (zanieczyszczony) pliki. Dostęp do tego interfejsu odbywa się przy użyciu usługi <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>|Wywoływane przez projekty, aby zażądać uprawnień do dodawania, usuwania lub zmiany nazwy pliku lub katalogu. Ten interfejs jest również wywoływany przez projekty w celu informowania środowiska o zakończeniu zatwierdzonej akcji dodawania, usuwania lub zmiany nazwy. Dostęp do niego odbywa się za pomocą usługi <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>|Zaimplementowane przez każdą jednostkę, która ma zostać powiadomiona, gdy projekty dodają, zmienią nazwę lub usuwają plik lub katalog. Aby zarejestrować się w celu powiadomienia o zdarzeniach, wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>|Wywoływane przez projekty, aby zarejestrować się w pakiecie kontroli źródła i uzyskać informacje o stanie kontroli źródła. Dostęp do tego interfejsu odbywa się przy użyciu usługi <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>|Zaimplementowane przez projekt, aby odpowiedzieć na żądania kontroli źródła informacji o plikach i uzyskać ustawienia kontroli źródła wymagane dla pliku projektu.|

## <a name="see-also"></a>Zobacz także
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2.AdviseTrackProjectDocumentsEvents%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>
- [Obsługa kontroli kodu źródłowego](../../extensibility/internals/supporting-source-control.md)