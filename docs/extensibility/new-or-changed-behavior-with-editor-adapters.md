---
title: Zachowaniem nowe lub zostały zmienione z kartami edytora | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - adapter behavior
ms.assetid: 5555b116-cfdb-4773-ba62-af80fda64abd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 63c04e808228898e7542f67ec72bf9d36203547d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62433659"
---
# <a name="new-or-changed-behavior-with-editor-adapters"></a>Zachowaniem nowe lub zostały zmienione z kartami edytora
Jeśli aktualizujesz kodu napisanego dla wcześniejszych wersji podstawowy edytor programu Visual Studio i planujesz używać edytora karty (lub podkładki) zamiast przy użyciu nowego interfejsu API, należy pamiętać o następujących różnicach zachowania kart edytora w odniesieniu do poprzedniego podstawowy edytor.

## <a name="features"></a>Funkcje

### <a name="use-setsite"></a>Użyj SetSite()
 Należy wywołać <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite.SetSite%2A> po CoCreate bufory tekstu, widoki tekstu i kodu systemu windows, przed wykonaniem żadnych innych operacji na nich. Jednak nie jest to konieczne, jeśli używasz <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> do ich utworzenia, ponieważ ta usługa `Create()` wywołania metody, samodzielnie <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.SetSite%2A>.

### <a name="host-ivscodewindow-and-ivstextview-in-your-own-content"></a>IVsCodeWindow hosta i IVsTextView w Twojej własnej zawartość
 Możesz hostować zarówno <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> w Twojej własnej zawartość przy użyciu trybu Win32 lub trybie WPF. Należy jednak zachować należy pamiętać, że istnieją pewne różnice w dwóch trybach.

#### <a name="use-win32-and-wpf-versions-of-ivscodewindow"></a>Użyj wersji IVsCodeWindow Win32 i WPF
 Okna edytora kodu jest tworzony na podstawie <xref:Microsoft.VisualStudio.Shell.WindowPane>, który implementuje starsze Win32 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> interfejsu, a także nowe WPF <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane> interfejsu. Możesz użyć <xref:Microsoft.VisualStudio.Shell.WindowPane.Microsoft%23VisualStudio%23Shell%23Interop%23IVsWindowPane%23CreatePaneWindow%2A> metodę, aby utworzyć na podstawie HWND Środowisko hostingu, lub <xref:Microsoft.VisualStudio.Shell.WindowPane.Microsoft%23VisualStudio%23Shell%23Interop%23IVsUIElementPane%23CreateUIElementPane%2A> metodę, aby utworzyć środowisko hostingu WPF. Podstawowy edytor zawsze używa WPF, ale można utworzyć typu okienko, który odpowiada Twoim wymaganiom hostingu, w przypadku osadzania w tym okienku okna bezpośrednio we własnej zawartości.

#### <a name="use-win32-and-wpf-versions-of-ivstextview"></a>Użyj wersji IVsTextView Win32 i WPF
 Możesz ustawić <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> do trybu systemu Win32 lub WPF.

 Gdy fabryki edytora widoku tekstu jest domyślnie tworzony przez znajduje się wewnątrz HWND i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWindowHandle%2A> wraca HWND. Ten tryb nie należy używać do osadzenia edytora wewnątrz kontrolki WPF.

 Aby ustawić tryb WPF widoku tekstu, należy wywołać <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.Initialize%2A> i przekazać [TextViewInitFlags3.VIF_NO_HWND_SUPPORT](<xref:Microsoft.VisualStudio.TextManager.Interop.TextViewInitFlags3.VIF_NO_HWND_SUPPORT>) zgodnie z jedną inicjowania flagi w `InitView` parametru. Możesz uzyskać <xref:System.Windows.FrameworkElement> przez wywołanie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane.CreateUIElementPane%2A>.

 Tryb WPF różni się od trybu Win32 na dwa sposoby. Najpierw wyświetl tekst może być hostowana w kontekście WPF. Dostęp do okienka WPF przez rzutowanie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> do <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElementPane> i wywoływać metodę <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIElement.GetUIObject%2A>. Drugi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetWindowHandle%2A> nadal zwraca HWND, ale ta HWND można tylko sprawdź jego położenie i ustawić fokus na nim. Nie można używać tego HWND odpowiedzieć na komunikat WM_PAINT, ponieważ nie wpłynie to jak edytor umożliwia malowanie okna. Ta HWND znajduje się tylko po to, aby ułatwić przejście do nowego kodu w edytorze za pomocą kart. Zdecydowanie zaleca się, że nie należy używać `VIF_NO_HWND_SUPPORT` Jeśli składnik wymaga do pracy ze względu na ograniczenia w HWND zwrócony z właściwością HWND `GetWindowHandle` while, w tym trybie.

#### <a name="pass-arrays-as-parameters-in-native-code"></a>Przekazywanie tablic jako parametrów w kodzie natywnym
 Istnieje wiele metod w edytorze starszej wersji interfejsu API, które mają parametry, które zawierają tablicy i liczbę jej. Oto przykłady:

 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.AppendViewOnlyMarkerTypes%2A>

 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.RemoveViewOnlyMarkerTypes%2A>

 W przypadku wywołania tych metod w kodzie natywnym, możesz muszą przekazać tylko jeden element w danym momencie. Jeśli przekażesz w więcej niż jeden element, wywołanie zostanie odrzucone, z powodu problemów z podstawowego wdrożenia międzyoperacyjnego.

 Problem jest bardziej złożona, za pomocą metod takich jak <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.SetIgnoreMarkerTypes%2A>. Za każdym razem, gdy ta metoda jest wywoływana, czyści poprzedniej liście typów znaczników ignorowanych tak nie jest możliwe po prostu wywołać tę metodę trzy razy z trzech typów różnych znaczników. Jedynym rozwiązaniem jest wywołanie tej metody tylko w kodzie zarządzanym.

#### <a name="threading"></a>Wątkowość
 Karta bufor zawsze powinna wywołać z wątku interfejsu użytkownika. Karta buforu jest obiekt zarządzany, co oznacza, że wywołanie go z kodu zarządzanego pomijał kierowanie modelu COM i wywołania będą nie automatycznie być przekazywane do wątku interfejsu użytkownika.  W przypadku wywołania adapter buforu z wątku w tle, należy użyć <xref:System.Windows.Threading.Dispatcher.Invoke%2A> lub podobnej metody.

#### <a name="lockbuffer-methods"></a>Metody LockBuffer
 Wszystkie metody LockBuffer() są przestarzałe. Oto przykłady:

 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer.LockBuffer%2A>

 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.LockBuffer%2A>

 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.LockBuffer%2A>

#### <a name="commit-events"></a>Zatwierdzenie zdarzenia
 Zatwierdzenie zdarzenia nie są obsługiwane. Wywołanie metody, która powiadamia, te zdarzenia spowoduje, że metoda zwraca kod błędu.

 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents>

 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents>

 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsUndoRedoClusterWithCommitEvents>

#### <a name="texteditorevents"></a>TextEditorEvents
 <xref:EnvDTE.TextEditorEvents> Nie jest już uruchomiony na Commit(). Zamiast tego są uruchamiane dla każdej zmiany tekstu.

#### <a name="text-markers"></a>Znaczniki tekstu
 Należy wywołać <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker.Invalidate%2A> na <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker> obiekty podczas ich usuwania. W poprzednich wersjach potrzebna tylko dla wersji znaczników.

#### <a name="line-numbers"></a>Numery wierszy
 Dla różnych metod <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx>, numery wierszy odpowiadają bazowego numery wierszy w buforze, nie liczbami ten współczynnik konspekt i zawijania, tak jak w programie Visual Studio 2008.

 Metody, których to dotyczy m.in (lista nie jest wyczerpująca):

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
 Klienci z <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> zostanie wyświetlony tylko tych regionów konspektu, które zostały dodane za pomocą <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A>lub <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSessionEx.AddHiddenRegionsEx%2A>. Użytkownicy nie zobaczą regionów ad-hoc, ponieważ nie zostały dodane za pośrednictwem karty edytora. Podobnie Ci klienci nie są wyświetlane zwijanie regionów dodane przez języki (w tym C# i C++), które korzystają z nowego kodu w edytorze, a nie kart edytora.

#### <a name="line-heights"></a>Wysokość wiersza
 W nowym edytorze wiersze tekstu może mieć różnej wysokości, w zależności od tego, czy rozmiar czcionki i przekształcenia możliwe wiersza, łączące linii względem innych wierszy. Wysokość wiersza zwracane przez metody takie jak <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetLineHeight%2A> wysokość wiersza z użyciem domyślny rozmiar czcionki nie zastosowane przekształcenia wiersza. Wysokość tego mogą być lub może nie odzwierciedlać rzeczywiste wysokość wiersza w widoku.

#### <a name="eventing-and-undo"></a>Obsługi zdarzeń i cofania
 W nowym edytorze widoku w dalszym ciągu wykonywać operacje takie jak renderowania i wywoływanie zdarzeń w sposób ciągły. Operacje nadal, nawet wtedy, gdy klaster cofania został otwarty. To zachowanie różni się od tego dla starszych widoków, które nie wykonał te operacje dopiero po zamykającym klastra cofania.

#### <a name="intellisense"></a>IntelliSense

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.UpdateTipWindow%2A> Metoda zakończy się niepowodzeniem, jeśli przekażesz w klasie, który nie implementuje albo <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextTipWindow2> lub <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow3>. Niestandardowe akcje Win32 rysowanych przez właściciela podręczne nie są już obsługiwane.

#### <a name="smarttags"></a>SmartTags
 Brak obsługi karty tagów inteligentnych utworzonych za pomocą, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagData>, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagTipWindow>, i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSmartTagTipWindow2> interfejsów.

#### <a name="dte"></a>DTE
 <xref:EnvDTE80.IncrementalSearch> Nie jest zaimplementowana.

## <a name="unimplemented-methods"></a>Niezaimplementowana metody
 Niektóre metody nie została zaimplementowana na karty buforu tekstu, karty Widok tekst i tekstu warstwy karty.

|Interface|Nie zaimplementowano|
|---------------|---------------------|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|`Reload(false)` Nie jest zaimplementowana.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.EnumSpans%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetBufferMappingModes%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator.SetSpanMappings%2A>|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.GetMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.ReleaseMarkerData%2A>|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CanReplaceLines%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CopyLineText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CreateTrackingPoint%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.EnumLayerMarkers%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetBaseBuffer%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLengthOfLine%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLineCount%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetLineText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.GetMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.LockBufferEx%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.MapLocalSpansToTextOriginatingLayer%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReleaseMarkerData%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReplaceLines%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.ReplaceLinesEx%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.UnlockBufferEx%2A>|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Find%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsFindTarget.Replace%2A>|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView.GetSelectedAtom%2A>|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.GetSelectionDataObject%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.PositionCaretForEditing%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RestrictViewRange%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateViewFrameCaption%2A>|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.GetSmartTagRect%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.InvokeInsertionUI%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEx.SetHoverWaitTimer%2A>|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow.SetViewClassID%2A>|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.AfterCompletorCommit%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.BeforeCompletorCommit%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.Exec%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetContextLocation%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetServiceProvider%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSmartTagRect%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectCaretPos%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectSelection%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetSubjectText%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.QueryStatus%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.ReplaceSubjectTextSpan%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.SetSubjectCaretPos%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.SetSubjectSelection%2A><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.UpdateSmartTagWindow%2A>|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewIntellisenseHost>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewIntellisenseHost.SetSubjectFromPrimaryBuffer%2A> jest zaimplementowana w kartach, ale ignorowane przez konspektu interfejsu użytkownika.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegionEx>|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegionEx.GetBannerAttr%2A> jest zaimplementowana w kartach, ale ignorowane przez konspektu interfejsu użytkownika.|