---
title: Obiekt VSTextBuffer | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VSTextBuffer
helpviewer_keywords:
- VSTextBuffer object, reference
- views [Visual Studio SDK], VSTextBuffer object
ms.assetid: c5f94b45-7249-4e1f-a53d-1d2a1c61e0ef
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 987514f20746b8480391a35d7a9c9a9d3663cac2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51728785"
---
# <a name="vstextbuffer-object"></a>VSTextBuffer, obiekt
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Obiekt bufor tekstowy przedstawia strumień tekst Unicode, który jest zazwyczaj skojarzone z plikiem. A <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> obiekt może być używany poza kontekstem podstawowy edytor, jak w przypadku kreatora.  
  
 W poniższej tabeli przedstawiono interfejsy `VSTextBuffer`.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IOleCommandTarget](http://msdn.microsoft.com/library/windows/desktop/ms683797)|Standardowy interfejs OLE. Używane głównie do obsługi w buforze Cofnij/Ponów.|  
|[IPersistFile](http://msdn.microsoft.com/library/windows/desktop/ms687223)|Standardowy interfejs OLE.|  
|[IPersistStream](http://msdn.microsoft.com/library/windows/desktop/ms690091)|Standardowy interfejs OLE.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Umożliwia tworzenie akcji związki (czyli akcje, które są grupowane w jednostce pojedynczego Cofnij/ponów).|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Włącza trwałość danych dokumentu zarządzanych przez bufor tekstowy.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|Oferuje podstawowe usługi; używane przez wielu klientów.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextFind>|Służy do wyszukiwania buforu.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|Umożliwia odczytywanie i zapisywanie funkcji przy użyciu dwuwymiarowe współrzędne. Dziedziczy `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|Umożliwia odczytywanie i zapisywanie funkcji przy użyciu współrzędnych jednowymiarowa. Dziedziczy `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|Udostępnia szybką, zorientowane na strumień, sekwencyjnych tekstu w buforze.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|Zapewnia dostęp do ogólnego zbiór właściwości. Najważniejsze właściwości jest nazwa lub krótkiej nazwy buforu. Losowe dane można przechowywać w buforze z tym interfejsem, tworząc identyfikator GUID i używać go jako klucza.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|Obsługuje punkty połączenia dla zdarzeń.|  
  
## <a name="remarks"></a>Uwagi  
 `VSTextBuffer` Znajduje się zwykle przez `QueryInterface` wywołanie na `IVsTextBuffer`. Aby uzyskać więcej informacji, zobacz [bufor tekstowy](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 [Edytuj dane](http://msdn.microsoft.com/en-us/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)

