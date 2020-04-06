---
title: Opóźnione ładowanie dokumentów | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: fb07b8e2-a4e3-4cb0-b04f-8eb11c491f35
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2f78d49013c1f0bd359d4439b73620a159a9ccc0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708810"
---
# <a name="delayed-document-loading"></a>Opóźnione ładowanie dokumentów

Gdy użytkownik ponownie otwiera rozwiązanie programu Visual Studio, większość skojarzonych dokumentów nie są ładowane natychmiast. Ramka okna dokumentu jest tworzona w stanie inicjowania oczekującego, a dokument zastępczy (nazywany ramką skrótową) jest umieszczany w tabeli Uruchomiony dokument (RDT).

Rozszerzenie może spowodować, że dokumenty projektu mają być ładowane niepotrzebnie przez wykonywanie zapytań elementów w dokumentach przed ich załadowaniem, co może zwiększyć ogólny rozmiar pamięci dla programu Visual Studio.

## <a name="document-loading"></a>Ładowanie dokumentów

Ramka skrótowa i dokument są w pełni inicjowane, gdy użytkownik uzyskuje dostęp do dokumentu, na przykład wybierając kartę ramki okna. Dokument można również zainicjować przez rozszerzenie, które żąda danych dokumentu, albo uzyskując dostęp do RDT bezpośrednio do uzyskania danych dokumentu lub pośrednio uzyskując dostęp do RDT, wykonując jedną z następujących wywołań:

- Metoda ramki <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> okna.

- Metoda ramki <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> okna na dowolnej z następujących właściwości:

  - [__VSFPROPID. VSFPROPID_DocView](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_DocView>)

  - [__VSFPROPID. VSFPROPID_ViewHelper](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_ViewHelper>)

  - [__VSFPROPID. VSFPROPID_DocData](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_DocData>)

  - [__VSFPROPID. VSFPROPID_AltDocData](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_AltDocData>)

  - [__VSFPROPID. VSFPROPID_RDTDocData](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_RDTDocData>)

  - [__VSFPROPID. VSFPROPID_SPProjContext](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID.VSFPROPID_SPProjContext>)

- Jeśli rozszerzenie używa kodu zarządzanego, <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> nie należy wywoływać, chyba że masz pewność, że dokument nie jest w stanie inicjowania oczekującego lub chcesz, aby dokument został w pełni zainicjowany. Powodem jest to, że metoda zawsze zwraca obiekt danych doc, tworząc go w razie potrzeby. Zamiast tego należy wywołać jedną z `IVsRunningDocumentTable4` metod w interfejsie.

- Jeśli rozszerzenie używa języka C++, `null` można przekazać dla parametrów, które nie mają.

- Można uniknąć niepotrzebnego ładowania dokumentów, wywołując jedną z następujących metod, zanim poprosisz o odpowiednie właściwości, zanim poprosisz o inne właściwości:

  - <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A>za pomocą [__VSFPROPID6. VSFPROPID_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID6.VSFPROPID_PendingInitialization>).

  - <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A>. Ta metoda <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> zwraca obiekt, który zawiera wartość [dla _VSRDTFLAGS4. RDT_PendingInitialization,](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4.RDT_PendingInitialization>) jeśli dokument nie został jeszcze zainicjowany.

Można dowiedzieć się, kiedy dokument został załadowany przez subskrybowanie zdarzenia RDT, który jest wywoływany, gdy dokument jest w pełni zainicjowany. Istnieją dwie możliwości:

- Jeśli zatapię <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2>zdarzenia, można subskrybować <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2.OnAfterAttributeChangeEx%2A>,

- W przeciwnym razie możesz <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterAttributeChange%2A>zasubskrybować plik .

Poniższy przykład jest hipotetyczny scenariusz dostępu do dokumentu: Rozszerzenie programu Visual Studio chce wyświetlić pewne informacje o otwartych dokumentów, na przykład liczba blokady edycji i coś o danych dokumentu. Wylicza dokumenty w RDT <xref:Microsoft.VisualStudio.Shell.Interop.IEnumRunningDocuments>przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> , a następnie wywołuje dla każdego dokumentu w celu pobrania licznika blokady edycji i danych dokumentu. Jeśli dokument jest w stanie inicjowania oczekującego, żądanie danych dokumentu powoduje, że jest niepotrzebnie inicjowany.

Bardziej efektywnym sposobem uzyskiwania dostępu <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentEditLockCount%2A> do dokumentu jest użycie do <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A> uzyskania liczby blokady edycji, a następnie użycie do określenia, czy dokument został zainicjowany. Jeśli flagi nie zawierają [_VSRDTFLAGS4. RDT_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4.RDT_PendingInitialization>)dokument został już zainicjowany, a żądanie danych dokumentu <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentData%2A> nie powoduje niepotrzebnego inicjowania. Jeśli flagi zawierają [_VSRDTFLAGS4. RDT_PendingInitialization](<xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4.RDT_PendingInitialization>)rozszerzenie powinno unikać żądania danych dokumentu do momentu zainicjowania dokumentu. Ta inicjalizacja można `OnAfterAttributeChange(Ex)` wykryć w programie obsługi zdarzeń.

## <a name="test-extensions-to-see-if-they-force-initialization"></a>Rozszerzenia testowe, aby sprawdzić, czy wymuszają inicjowanie

Nie ma widocznych wskazówek wskazujących, czy dokument został zainicjowany, więc może być trudno dowiedzieć się, czy rozszerzenie wymusza inicjowanie. Można ustawić klucz rejestru, który ułatwia weryfikację, ponieważ powoduje, że tytuł każdego dokumentu, który nie jest w pełni zainicjowany, ma tekst *[Skrót]* w tytule.

W **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0\BackgroundSolutionLoad**, ustaw **StubTabTitleFormatString** na * {0} [Stub]*.
