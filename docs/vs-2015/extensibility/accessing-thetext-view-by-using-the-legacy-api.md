---
title: Uzyskiwanie dostępu do widoku theText przy użyciu starszej wersji interfejsu API | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text view
ms.assetid: 8f751f72-c972-4be3-84ee-19c281e02e25
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8f9396e4523e38e7313efb5668c4680f551558ab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184954"
---
# <a name="accessing-thetext-view-by-using-the-legacy-api"></a>Uzyskiwanie dostępu do widoku tekstowego przy użyciu starszego interfejsu API
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Widok tekstu jest prezentacją tekstu, który jest przechowywany w buforze tekstu. Dostęp do widoku tekstu można uzyskać przy użyciu starszej wersji interfejsu API, jak pokazano w poniższej sekcji.  
  
## <a name="text-view-object"></a>Obiekt widoku tekstu  
 Każdy widok jest skojarzony z własnym buforem tekstu, a widok jest oknem danych w buforze. Na poniższym diagramie przedstawiono główne interfejsy obiektu widoku tekstu, który jest reprezentowany przez <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> .  
  
 ![Obiekt widoku tekstu programu Visual Studio](../extensibility/media/vstextview.gif "vstextview")  
Obiekt widoku tekstu  
  
 Widok jest sposobem prezentowania tekstu w buforze. Zawiera ona funkcje, takie jak Zawijanie wierszy i konspekt, tak aby elementy wyświetlane w widoku nie były dokładną reprezentacją tekstu w buforze.  
  
 Widok umożliwia innym usługom lub procesom przechwycenie przychodzących poleceń i wykonywanie na nich działań przed ich wyświetleniem. Najbardziej typową usługą jest usługa języka. Usługa języka może potrzebować na przykład przechwycić polecenie dla klawisza ENTER w celu zapewnienia niestandardowego zachowania wcięcia lub etykiet narzędzi.  
  
## <a name="adding-functionality-to-the-text-view"></a>Dodawanie funkcji do widoku tekstu  
 Możesz dostosować zachowanie widoku tekstu przez obsługę konkretnych naciśnięć klawiszy. Aby przechwycić naciśnięcia klawiszy, zaimplementuj je <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> na obiekcie i podaj obiekt docelowy polecenia ( <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> ) do monitorowania i przechwycenia poleceń.  
  
 W widoku tekstu jest stosowana architektura sekwencyjna dla filtrów poleceń. Nowe filtry poleceń ( <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> obiekty) są dodawane do sekwencji przez wywołanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> metody.  
  
 Powiadomienie o zdarzeniu dla widoku tekstu jest dostarczane przy użyciu `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEvents` interfejsu. Zaimplementuj ten interfejs w obiekcie klienta, aby otrzymywać powiadomienia o zmianach w widoku tekstu. Uwidocznij ten interfejs w widoku tekstu przy użyciu <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> interfejsu w widoku tekstu, aby otrzymywać powiadomienia o zmianach z widoku.  
  
## <a name="see-also"></a>Zobacz też  
 [Zmiana ustawień widoku przy użyciu starszego interfejsu API](../extensibility/changing-view-settings-by-using-the-legacy-api.md)   
 [Używanie menedżera tekstu do monitorowania ustawień globalnych](../extensibility/using-the-text-manager-to-monitor-global-settings.md)
