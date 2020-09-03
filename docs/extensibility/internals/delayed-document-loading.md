---
title: Opóźnione ładowanie dokumentu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: fb07b8e2-a4e3-4cb0-b04f-8eb11c491f35
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2f78d49013c1f0bd359d4439b73620a159a9ccc0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80708810"
---
# <a name="delayed-document-loading"></a>Opóźnione ładowanie dokumentu

Gdy użytkownik ponownie otworzy rozwiązanie programu Visual Studio, większość skojarzonych dokumentów nie zostanie załadowana natychmiast. Ramka okna dokumentu jest tworzona w stanie oczekiwania na inicjalizację, a dokument zastępczy (nazywany ramką zastępczą) jest umieszczany w uruchomionej tabeli dokumentu (RDT).

Rozszerzenie może spowodować niepotrzebne załadowanie dokumentów projektu przez wykonanie zapytania o elementy w dokumentach przed ich załadowaniem, co może spowodować zwiększenie całkowitego rozmiaru pamięci dla programu Visual Studio.

## <a name="document-loading"></a>Ładowanie dokumentu

Ramka i dokument zastępczy są w pełni inicjowane, gdy użytkownik uzyskuje dostęp do dokumentu, na przykład wybierając kartę ramki okna. Dokument może być również inicjowany przez rozszerzenie, które żąda danych dokumentu, przez uzyskanie dostępu do RDT bezpośrednio w celu uzyskania danych dokumentu lub uzyskanie dostępu do RDT pośrednio przez utworzenie jednego z następujących wywołań:

- Metoda ramki okna <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> .

- Metoda ramki okna <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> dla dowolnej z następujących właściwości:

  - [__VSFPROPID. VSFPROPID_DocView](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_DocView>)

  - [__VSFPROPID. VSFPROPID_ViewHelper](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_ViewHelper>)

  - [__VSFPROPID. VSFPROPID_DocData](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_DocData>)

  - [__VSFPROPID. VSFPROPID_AltDocData](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_AltDocData>)

  - [__VSFPROPID. VSFPROPID_RDTDocData](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_RDTDocData>)

  - [__VSFPROPID. VSFPROPID_SPProjContext](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_SPProjContext>)

- Jeśli rozszerzenie korzysta z kodu zarządzanego, nie należy wywoływać, <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> chyba że masz pewność, że dokument nie znajduje się w stanie oczekiwania na inicjację lub że dokument ma być w pełni zainicjowany. Przyczyną jest to, że metoda zawsze zwraca obiekt danych doc, tworząc go w razie potrzeby. Zamiast tego należy wywołać jedną z metod w `IVsRunningDocumentTable4` interfejsie.

- Jeśli rozszerzenie używa języka C++, można przekazać do niepotrzebnych `null` parametrów.

- Można uniknąć niepotrzebnych załadowania dokumentu, wywołując jedną z następujących metod przed poproszeniem o podanie odpowiednich właściwości przed poproszeniem o inne właściwości:

  - <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> przy użyciu [__VSFPROPID6. VSFPROPID_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID6.VSFPROPID_PendingInitialization>).

  - <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A>. Ta metoda zwraca <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> obiekt, który zawiera wartość dla [_VSRDTFLAGS4. RDT_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4.RDT_PendingInitialization>) , jeśli dokument nie został jeszcze zainicjowany.

Możesz sprawdzić, kiedy dokument został załadowany przez zasubskrybowanie zdarzenia RDT, które jest zgłaszane, gdy dokument jest w pełni zainicjowany. Istnieją dwie możliwości:

- W przypadku zaimplementowania ujścia zdarzeń <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2> można subskrybować <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2.OnAfterAttributeChangeEx%2A> ,

- W przeciwnym razie można subskrybować <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterAttributeChange%2A> .

Poniższy przykład to hipotetyczny scenariusz dostępu do dokumentów: rozszerzenie programu Visual Studio chce wyświetlić pewne informacje o otwartych dokumentach, na przykład w przypadku edycji liczby blokad i czegoś dotyczącego danych dokumentu. Wylicza dokumenty w RDT przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.IEnumRunningDocuments> , a następnie wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> każdy dokument w celu pobrania liczby i danych dokumentu. Jeśli dokument jest w stanie oczekiwania na zainicjowanie, żądanie danych dokumentu powoduje niepotrzebne zainicjowanie.

Bardziej wydajnym sposobem uzyskiwania dostępu do dokumentu jest użycie programu <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentEditLockCount%2A> w celu pobrania liczby blokad edycji, a następnie użycia <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A> w celu określenia, czy dokument został zainicjowany. Jeśli flagi nie zawierają [_VSRDTFLAGS4. RDT_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4.RDT_PendingInitialization>)dokument został już zainicjowany i żądanie danych dokumentu <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentData%2A> nie powoduje żadnych niepotrzebnych inicjalizacji. Jeśli flagi zawierają [_VSRDTFLAGS4. RDT_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4.RDT_PendingInitialization>), rozszerzenie powinno unikać żądania danych dokumentu do momentu zainicjowania dokumentu. Ta Inicjalizacja może zostać wykryta w `OnAfterAttributeChange(Ex)` obsłudze zdarzeń.

## <a name="test-extensions-to-see-if-they-force-initialization"></a>Sprawdź rozszerzenia, aby sprawdzić, czy wymusić inicjalizację

Nie ma widocznej wskazówki wskazującej, czy dokument został zainicjowany, dlatego może być trudne do sprawdzenia, czy rozszerzenie wymusza inicjalizację. Można ustawić klucz rejestru, który ułatwia weryfikację, ponieważ powoduje to, że tytuł każdego dokumentu, który nie jest w pełni zainicjowany, ma tekst *[stub]* w tytule.

W **HKEY_CURRENT_USER \software\microsoft\visualstudio\14.0\backgroundsolutionload**ustaw wartość **StubTabTitleFormatString** na * {0} [stub]*.
