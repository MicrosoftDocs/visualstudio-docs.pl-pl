---
title: Zdarzenia buforu tekstu w starszym interfejsie API | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text buffer events
ms.assetid: 9be49e9f-1864-41c2-8a3c-f66895881341
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e82fa31ca435d0c850a4d9e75e927cff9613b046
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186405"
---
# <a name="text-buffer-events-in-the-legacy-api"></a>Zdarzenia buforu tekstowego w starszym interfejsie API
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Obiekt buforu tekstowego emituje kilka różnych zdarzeń, które umożliwiają reagowanie na różne sytuacje.  
  
 W przypadku korzystania ze starszej wersji interfejsu API należy zaimplementować następujące interfejsy, aby otrzymywać powiadomienia o zmianach w buforze tekstu. Uwidocznij interfejsy w buforze tekstu przy użyciu `IConnectionPointContainer` interfejsu w buforze tekstowym, aby otrzymywać powiadomienia o zmianach wierszy z bufora. Aby uzyskać więcej informacji, zobacz [How to: Register for text buffer Events With The Legacy API](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md). W przypadku `IVsTextStreamEvents` `IVsTextLinesEvents` interfejsów lub, zmiany są zwracane odpowiednio w jedno-lub dwuwymiarowe współrzędne.  
  
## <a name="text-buffer-interfaces"></a>Interfejsy buforu tekstu  
 Poniżej przedstawiono interfejsy zaimplementowane przez obiekt buforu tekstu.  
  
|Interfejs|Opis|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Umożliwia tworzenie akcji złożonych (czyli akcji, które są pogrupowane w jednej jednostce cofania/ponawiania).|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Włącza trwałość danych dokumentu zarządzanych przez bufor tekstu.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|Zapewnia podstawowe usługi; używany przez wielu klientów.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|Zapewnia możliwości odczytu i zapisu przy użyciu współrzędnych dwuwymiarowych. Dziedziczy z `IVsTextBuffer` .|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|Zapewnia szybki, zorientowany na strumień, sekwencyjny dostęp do tekstu w buforze.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|Zapewnia możliwości odczytu i zapisu przy użyciu współrzędnych jednowymiarowych. Dziedziczy z `IVsTextBuffer` .|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|Zapewnia dostęp do ogólnej kolekcji właściwości. Najważniejszym właściwość jest nazwa lub moniker buforu. Możesz przechowywać własne dane losowe w buforze przy użyciu tego interfejsu, tworząc identyfikator GUID i używając go jako klucz.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|Obsługuje punkty połączenia dla zdarzeń.|  
  
## <a name="text-buffer-event-interfaces"></a>Interfejsy zdarzeń buforu tekstu  
 Poniżej przedstawiono interfejsy dla powiadomienia o zdarzeniu buforu tekstu.  
  
|Interfejs|Opis|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferEvents>|Powiadamia klientów, gdy nowa usługa językowa jest skojarzona z buforem tekstu.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferDataEvents>|Powiadamia klientów o zainicjowaniu buforu tekstu oraz o wprowadzeniu zmian w danych w buforze tekstowym.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamEvents>|Powiadamia klientów o zmianach w źródłowym buforze tekstowym w współrzędnych jednowymiarowych.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>|Powiadamia klientów o zmianach w źródłowym buforze tekstowym we współrzędnych dwuwymiarowych.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserDataEvents>|Powiadamia klientów o zmianach danych użytkownika.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents>|Powiadamia klientów o ostatnim gestie zatwierdzeń, aby wyzwolić zdarzenie i zawiera zmieniony zakres tekstu. `IVsPreliminaryTextChangeCommitEvents`Interfejs nie jest uruchamiany w odpowiedzi na polecenia Cofnij lub wykonaj ponownie. Zdarzenia uruchamiają się tylko w przypadku buforów, które mają Menedżera cofania. `IVsPreliminaryTextChangeCommitEvents` Program jest uruchamiany przed innymi zdarzeniami, takimi jak łatwa lista, aby upewnić się, że inne zdarzenia nie zmieniają tekstu przed zatwierdzeniem zmian. Pakietu VSPackage musi monitorować `IVsPreliminaryTextChangeCommitEvents` interfejs lub `IVsFinalTextChangeCommitEvents` interfejs, ale nie oba jednocześnie.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents>|Powiadamia klientów o ostatnim gestie zatwierdzeń, aby wyzwolić zdarzenie i zawiera zmieniony zakres tekstu. `IVsFinalTextChangeCommitEvents`Interfejs nie jest uruchamiany w odpowiedzi na polecenia Cofnij lub wykonaj ponownie. Zdarzenia uruchamiają się tylko w przypadku buforów, które mają Menedżera cofania. `IVsFinalTextChangeCommitEvents` jest przeznaczony do użycia tylko przez usługi językowe lub inne obiekty, które mają pełną kontrolę nad edycją. Pakietu VSPackage musi monitorować `IVsPreliminaryTextChangeCommitEvents` interfejs lub `IVsFinalTextChangeCommitEvents` interfejs, ale nie oba jednocześnie.|  
  
## <a name="see-also"></a>Zobacz też  
 [Uzyskiwanie dostępu do buforu tekstowego przy użyciu starszego interfejsu API](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)   
 [Instrukcje: rejestrowanie w zdarzeniach buforu tekstowego przy użyciu starszego interfejsu API](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)
