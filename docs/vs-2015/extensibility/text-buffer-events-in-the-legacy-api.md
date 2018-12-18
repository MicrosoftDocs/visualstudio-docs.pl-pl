---
title: Zdarzenia buforu tekstu w starszej wersji interfejsu API | Dokumentacja firmy Microsoft
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
- editors [Visual Studio SDK], legacy - text buffer events
ms.assetid: 9be49e9f-1864-41c2-8a3c-f66895881341
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 677824142f2e7e497888627041cfe7a82487d342
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51735514"
---
# <a name="text-buffer-events-in-the-legacy-api"></a>Zdarzenia buforu tekstu w starszej wersji interfejsu API
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Obiekt buforu tekstu emituje szereg różnych zdarzeń, które umożliwiają reagowanie na różnych sytuacjach.  
  
 Jeśli używasz starszej wersji interfejsu API, należy zaimplementować następujące interfejsy w celu otrzymywania powiadomień o zmianach w buforze tekstu. Uwidacznia interfejsów do buforu tekstu przy użyciu `IConnectionPointContainer` interfejsu w buforze tekstu, aby otrzymać powiadomienie o wiersz zmieni się z buforu. Aby uzyskać więcej informacji, zobacz [porady: rejestrowanie zdarzeń buforu tekstu przy użyciu starszej wersji interfejsu API](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md). W przypadku właściwości `IVsTextStreamEvents` lub `IVsTextLinesEvents` interfejsów, zmiany są zwracane w albo jednego lub dwu dimensional współrzędne, odpowiednio.  
  
## <a name="text-buffer-interfaces"></a>Interfejsy buforu tekstu  
 Poniżej przedstawiono interfejsy implementowane przez obiekt buforu tekstu.  
  
|Interface|Opis|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Włącza funkcję tworzenia działania złożonego (czyli akcje, które są grupowane w jednostce pojedynczego Cofnij/ponów).|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Włącza trwałość danych dokumentu zarządzanych przez bufor tekstowy.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|Oferuje podstawowe usługi; używane przez wielu klientów.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|Umożliwia odczytywanie i zapisywanie funkcji przy użyciu dwuwymiarowe współrzędne. Dziedziczy `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|Udostępnia szybką, zorientowane na strumień, sekwencyjnych tekstu w buforze.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|Umożliwia odczytywanie i zapisywanie funkcji przy użyciu współrzędnych jednowymiarowa. Dziedziczy `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|Zapewnia dostęp do ogólnego zbiór właściwości. Najważniejsze właściwości jest nazwa lub krótkiej nazwy buforu. Losowe dane można przechowywać w buforze z tym interfejsem, tworząc identyfikator GUID i używać go jako klucza.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|Obsługuje punkty połączenia dla zdarzeń.|  
  
## <a name="text-buffer-event-interfaces"></a>Interfejsów zdarzeń buforu tekstu  
 Poniżej przedstawiono interfejsów dla powiadomień o zdarzeniach buforu tekstu.  
  
|Interface|Opis|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferEvents>|Powiadamia klientów, gdy nowa usługa języka jest skojarzona z buforu tekstowego.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferDataEvents>|Powiadamia klientów po zainicjowaniu bufor tekstowy i kiedy zmiany zostały wprowadzone dane w buforze tekstu.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamEvents>|Powiadamia klientów o zmianach w podstawowej bufor tekstowy we współrzędnych jednowymiarowa.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>|Powiadamia klientów o zmianach w podstawowej bufor tekstowy w dwuwymiarowe współrzędne.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserDataEvents>|Powiadamia klientów o zmianach w danych użytkownika.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents>|Powiadamia klientów o ostatnim gestu zatwierdzenia, aby wyzwolić zdarzenie i oferuje zakres zmiany tekstu. `IVsPreliminaryTextChangeCommitEvents` Interfejsu nie jest uruchamiany w odpowiedzi na cofanie lub ponowne wykonywanie poleceń. Zdarzenia wyzwalać tylko dla buforów, które mają menedżera cofania. `IVsPreliminaryTextChangeCommitEvents` jest wywoływane przed inne zdarzenia, takie jak lista pretty, aby upewnić się, że inne zdarzenia nie należy zmieniać tekst, aby zmiany zostały zatwierdzone. Usługi pakietu VSPackage należy monitorować, albo `IVsPreliminaryTextChangeCommitEvents` interfejsu lub `IVsFinalTextChangeCommitEvents` interfejs, ale nie oba.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents>|Powiadamia klientów o ostatnim gestu zatwierdzenia, aby wyzwolić zdarzenie i oferuje zakres zmiany tekstu. `IVsFinalTextChangeCommitEvents` Interfejsu nie jest uruchamiany w odpowiedzi na cofanie lub ponowne wykonywanie poleceń. Zdarzenia wyzwalać tylko dla buforów, które mają menedżera cofania. `IVsFinalTextChangeCommitEvents` jest przeznaczony do użytku tylko przez usługi w języka lub inne obiekty, które mają pełną kontrolę nad edytowaniem. Usługi pakietu VSPackage należy monitorować, albo `IVsPreliminaryTextChangeCommitEvents` interfejsu lub `IVsFinalTextChangeCommitEvents` interfejs, ale nie oba.|  
  
## <a name="see-also"></a>Zobacz też  
 [Dostęp do buforu tekstowego przy użyciu starszej wersji interfejsu API](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)   
 [Instrukcje: rejestrowanie w zdarzeniach buforu tekstowego przy użyciu starszego interfejsu API](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)

