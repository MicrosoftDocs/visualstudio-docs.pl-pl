---
title: Nowe lub zmienione zachowanie przy użyciu adapterów edytora | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - adapter behavior
ms.assetid: 5555b116-cfdb-4773-ba62-af80fda64abd
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fc7ddaf7ec67a1e33248d5ce424868849200d3e6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194180"
---
# <a name="new-or-changed-behavior-with-editor-adapters"></a>Nowe lub zmienione działanie z użyciem adapterów edytora
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jeśli aktualizujesz kod, który został zapisany w starszych wersjach programu Visual Studio Core Editor i planujesz używać adapterów edytora (lub podkładki) zamiast korzystać z nowego interfejsu API, należy pamiętać o następujących różnicach w zachowaniu kart edytora w odniesieniu do poprzedniego podstawowego edytora.  
  
## <a name="features"></a>Funkcje  
  
#### <a name="using-setsite"></a>Przy użyciu SetSite ()  
 Należy wywołać, <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite.SetSite%2A> gdy CoCreate się bufory tekstu, widoki tekstowe i okna kodu przed wykonaniem innych operacji na nich. Jednak nie jest to konieczne, jeśli używasz <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> , aby je utworzyć, ponieważ metody tworzenia () tej usługi są wywoływane <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.SetSite%2A> .  
  
#### <a name="hosting-ivscodewindow-and-ivstextview-in-your-own-content"></a>Hosting IVsCodeWindow i IVsTextView we własnej zawartości  
 Można hostować zarówno <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> we własnej zawartości przy użyciu trybu Win32, jak i w trybie WPF. Należy jednak pamiętać, że istnieją pewne różnice w obu trybach.  
  
##### <a name="using-win32-and-wpf-versions-of-ivscodewindow"></a>Korzystanie z wersji Win32 i WPF IVsCodeWindow  
 Okno kod edytora pochodzi od <xref:Microsoft.VisualStudio.Shell.WindowPane> , który implementuje starszy interfejs Win32, <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> a także nowy <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane> interfejs WPF. Możesz użyć <xref:Microsoft.VisualStudio.Shell.WindowPane.Microsoft%23VisualStudio%23Shell%23Interop%23IVsWindowPane%23CreatePaneWindow%2A> metody, aby utworzyć środowisko hostingu oparte na HWND lub <xref:Microsoft.VisualStudio.Shell.WindowPane.Microsoft%23VisualStudio%23Shell%23Interop%23IVsUIElementPane%23CreateUIElementPane%2A> metodę tworzenia środowiska hostingu WPF. Podstawowy edytor zawsze korzysta z platformy WPF, ale można utworzyć rodzaj okienka, który spełnia wymagania dotyczące hostingu, jeśli osadzasz to okienko bezpośrednio w własnej zawartości.  
  
##### <a name="using-win32-and-wpf-versions-of-ivstextview"></a>Korzystanie z wersji Win32 i WPF IVsTextView  
 Można ustawić <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> tryb na Win32 lub tryb WPF.  
  
 Gdy fabryka edytora tworzy widok tekstu, domyślnie jest hostowana wewnątrz elementu HWND i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWindowHandle%2A> zwraca właściwość HWND. Nie należy używać tego trybu do osadzenia edytora wewnątrz kontrolki WPF.  
  
 Aby ustawić widok tekstu na tryb WPF, należy wywołać <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.Initialize%2A> i przekazać <xref:Microsoft.VisualStudio.TextManager.Interop.TextViewInitFlags3> jako jedną z flag inicjalizacji w `InitView` parametrze. Możesz uzyskać, <xref:System.Windows.FrameworkElement> wywołując metodę <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane.CreateUIElementPane%2A> .  
  
 Tryb WPF różni się od trybu Win32 na dwa sposoby. Najpierw widok tekstu może być hostowany w kontekście WPF. Możesz uzyskać dostęp do okienka WPF przez rzutowanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> do <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane> i wywoływanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElement.GetUIObject%2A> . Sekunda, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWindowHandle%2A> nadal zwraca właściwość HWND, ale ta właściwość HWND może być używana tylko do sprawdzania jej położenia i ustawiania fokusu. Nie można używać tego elementu HWND do odpowiadania na komunikat WM_PAINT, ponieważ nie wpłynie to na wygląd okna przez Edytor. Ta właściwość HWND jest obecna tylko w celu ułatwienia przejścia do nowego kodu edytora przy użyciu kart sieciowych. Zdecydowanie zaleca się, aby nie używać `VIF_NO_HWND_SUPPORT` , jeśli składnik wymaga elementu HWND do działania, ze względu na ograniczenia w elemencie HWND zwróconym przez program `GetWindowHandle` w tym trybie.  
  
#### <a name="passing-arrays-as-parameters-in-native-code"></a>Przekazywanie tablic jako parametrów w kodzie natywnym  
 Istnieje wiele metod w interfejsie API starszego edytora, które zawierają parametry zawierające tablicę i jej liczbę. Oto przykłady:  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.AppendViewOnlyMarkerTypes%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.RemoveViewOnlyMarkerTypes%2A>  
  
 Jeśli wywołujesz te metody w kodzie natywnym, musisz przekazać tylko jeden element naraz. Jeśli przejdziesz do więcej niż jednego elementu, wywołanie zostanie odrzucone z powodu problemów z podstawową implementacją międzyoperacyjności.  
  
 Problem jest bardziej skomplikowany przy użyciu metod takich jak <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.SetIgnoreMarkerTypes%2A> . Za każdym razem, gdy ta metoda jest wywoływana, czyści poprzednią listę ignorowanych typów znaczników, więc nie jest możliwe po prostu wywołanie tej metody trzy razy z trzema różnymi typami znaczników. Jedynym środkiem jest wywołanie tej metody tylko w kodzie zarządzanym.  
  
#### <a name="threading"></a>Wątkowość  
 Należy zawsze wywołać adapter buforu z wątku interfejsu użytkownika. Adapter bufora jest obiektem zarządzanym, co oznacza, że wywoływanie go z kodu zarządzanego spowoduje obejście kierowania modelu COM, a połączenie nie zostanie automatycznie zorganizowane z wątkiem interfejsu użytkownika.  Jeśli wywoływana jest karta buforu z wątku w tle, należy użyć <xref:System.Windows.Threading.Dispatcher.Invoke%2A> lub podobną metodę.  
  
#### <a name="lockbuffer-methods"></a>Metody LockBuffer  
 Wszystkie metody LockBuffer () są przestarzałe. Oto przykłady:  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.LockBuffer%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.LockBuffer%2A>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.LockBuffer%2A>  
  
#### <a name="commit-events"></a>Zatwierdź zdarzenia  
 Zdarzenia zatwierdzania nie są obsługiwane. Wywołanie metody, która doradza dla tych zdarzeń, powoduje, że metoda zwraca kod błędu.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents>  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUndoRedoClusterWithCommitEvents>  
  
#### <a name="texteditorevents"></a>TextEditorEvents  
 <xref:EnvDTE.TextEditorEvents>Nie jest już wyzwalane po zatwierdzeniu (). Zamiast tego są uruchamiane na każdej zmianie tekstu.  
  
#### <a name="text-markers"></a>Znaczniki tekstu  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker.Invalidate%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker> Po usunięciu obiektów należy wywołać metody. W poprzednich wersjach, musisz tylko zwolnić znaczniki.  
  
#### <a name="line-numbers"></a>Numery wierszy  
 W przypadku różnych metod w systemach <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx> numery wierszy odpowiadają numerom wierszy bufora, a nie z numerami wierszy, które są używane do tworzenia konspektu i zawijania wyrazów, jak w programie Visual Studio 2008.  
  
 Uwzględnione metody obejmują następujące (lista nie jest wyczerpująca):  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.CenterLines%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetCaretPos%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetLineAndColumn%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetNearestPosition%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetPointOfLineColumn%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetTextStream%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWordExtent%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.PositionCaretForEditing%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.ReplaceTextOnLine%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetCaretPos%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetSelection%2A>  
  
- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.SetTopLine%2A>  
  
#### <a name="outlining"></a>Tworzenie konspektu  
 Klienci programu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> będą widzieć tylko te regiony, które zostały dodane przy użyciu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> lub <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSessionEx.AddHiddenRegionsEx%2A> . Nie będą wyświetlane regiony ad hoc, ponieważ nie są dodawane za pomocą adapterów edytora. Podobnie klienci nie będą widzieć regionów tworzenia konspektu dodanych przez języki (w tym C# i C++), które używają nowego kodu edytora zamiast kart edytora.  
  
#### <a name="line-heights"></a>Wysokość linii  
 W nowym edytorze wiersze tekstu mogą mieć różne wysokość, w zależności od rozmiaru czcionki i możliwego przekształcenia wierszy, które mogą przenosić linię względem innych wierszy. Wysokość linii zwracana przez metody, takie jak, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetLineHeight%2A> jest wysokością linii przy użyciu domyślnego rozmiaru czcionki bez zastosowanych przekształceń wierszy. Ta wysokość może być niezgodna z rzeczywistą wysokością linii w widoku.  
  
#### <a name="eventing-and-undo"></a>Zdarzenia i cofanie  
 W nowym edytorze widok kontynuuje wykonywanie operacji, takich jak renderowanie i wywoływanie zdarzeń w sposób ciągły, nawet gdy jest otwarty klaster cofania. To zachowanie jest inne niż w przypadku starszych widoków, które nie wykonywały tych operacji do momentu zamknięcia klastra cofania.  
  
#### <a name="intellisense"></a>IntelliSense  
  
- Metoda zakończy <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.UpdateTipWindow%2A> się niepowodzeniem w przypadku przekazania klasy, która nie implementuje żadnej <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextTipWindow2> lub <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow3> . Niestandardowe okna podręczne rysowane przez właściciela systemu Win32 nie są już obsługiwane.  
  
#### <a name="smarttags"></a>SmartTags  
 Nie ma obsługi kart inteligentnych utworzonych przy użyciu, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagData> , <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagTipWindow> i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagTipWindow2> interfejsów.  
  
#### <a name="dte"></a>DTE  
 <xref:EnvDTE80.IncrementalSearch> nie została zaimplementowana.  
  
## <a name="unimplemented-methods"></a>Niezaimplementowane metody  
 Niektóre metody nie zostały zaimplementowane na karcie buforu tekstu, karcie widoku tekstu i karcie warstwy tekstu.  
  
|Interfejs|Nie zaimplementowano|  
|---------------|---------------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|`Reload(false)` nie została zaimplementowana.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.EnumSpans%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetBufferMappingModes%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.GetMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.ReleaseMarkerData%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CanReplaceLines%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CopyLineText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CreateTrackingPoint%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.EnumLayerMarkers%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetBaseBuffer%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLengthOfLine%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLineCount%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLineText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.LockBufferEx%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.MapLocalSpansToTextOriginatingLayer%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReleaseMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReplaceLines%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReplaceLinesEx%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.UnlockBufferEx%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView.GetSelectedAtom%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetSelectionDataObject%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.PositionCaretForEditing%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RestrictViewRange%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateViewFrameCaption%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.GetSmartTagRect%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.InvokeInsertionUI%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.SetHoverWaitTimer%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow.SetViewClassID%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.AfterCompletorCommit%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.BeforeCompletorCommit%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetContextLocation%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetServiceProvider%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSmartTagRect%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectCaretPos%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectSelection%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.ReplaceSubjectTextSpan%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.SetSubjectCaretPos%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.SetSubjectSelection%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.UpdateSmartTagWindow%2A>|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewIntellisenseHost>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewIntellisenseHost.SetSubjectFromPrimaryBuffer%2A> Program jest implementowany w kartach, ale ignorowany przez interfejs użytkownika tworzenia konspektu.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegionEx>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegionEx.GetBannerAttr%2A> Program jest implementowany w kartach, ale ignorowany przez interfejs użytkownika tworzenia konspektu.|
