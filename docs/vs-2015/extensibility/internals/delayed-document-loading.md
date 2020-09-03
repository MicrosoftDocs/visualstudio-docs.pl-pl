---
title: Opóźnione ładowanie dokumentu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: fb07b8e2-a4e3-4cb0-b04f-8eb11c491f35
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5565749a21614bb0b882beab8c83ed63bc839229
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196869"
---
# <a name="delayed-document-loading"></a>Opóźnione ładowanie dokumentu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Gdy użytkownik ponownie otworzy rozwiązanie programu Visual Studio, większość skojarzonych dokumentów nie zostanie załadowana natychmiast. Ramka okna dokumentu jest tworzona w stanie oczekiwania na inicjalizację, a dokument zastępczy (nazywany ramką zastępczą) jest umieszczany w uruchomionej tabeli dokumentu (RDT).  
  
 Rozszerzenie może spowodować niepotrzebne załadowanie dokumentów projektu przez wykonanie zapytania o elementy w dokumentach przed ich załadowaniem. Może to spowodować zwiększenie całkowitego rozmiaru pamięci dla programu Visual Studio.  
  
## <a name="document-loading"></a>Ładowanie dokumentu  
 Ramka i dokument zastępczy są w pełni inicjowane, gdy użytkownik uzyskuje dostęp do dokumentu, na przykład wybierając kartę ramki okna. Dokument może być również inicjowany przez rozszerzenie, które żąda danych dokumentu, przez uzyskanie dostępu do RDT bezpośrednio w celu uzyskania danych dokumentu lub uzyskanie dostępu do RDT pośrednio przez utworzenie jednego z następujących wywołań:  
  
- Ramka okna Pokaż metodę: <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> .  
  
- Ramka okna Metoda GetProperty <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> dla dowolnej z następujących właściwości:  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  Jeśli rozszerzenie korzysta z kodu zarządzanego, nie należy wywoływać, <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> chyba że masz pewność, że dokument nie znajduje się w stanie oczekiwania na inicjację lub że dokument ma być w pełni zainicjowany. Wynika to z faktu, że ta metoda zawsze zwraca obiekt danych doc, tworząc go w razie potrzeby. Zamiast tego należy wywołać jedną z metod w interfejsie IVsRunningDocumentTable4.  
  
  Jeśli rozszerzenie używa języka C++, można przekazać do niepotrzebnych `null` parametrów.  
  
  Można uniknąć niepotrzebnego ładowania dokumentu, wywołując jedną z następujących metod przed zaproszeniem o odpowiednie właściwości: przed poproszeniem o podanie innych właściwości.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID6> .  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A>. Ta metoda zwraca <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> obiekt, który zawiera wartość dla, <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> Jeśli dokument nie został jeszcze zainicjowany.  
  
  Możesz sprawdzić, kiedy dokument został załadowany przez zasubskrybowanie zdarzenia RDT, które jest zgłaszane, gdy dokument jest w pełni zainicjowany. Istnieją dwie możliwości:  
  
- W przypadku zaimplementowania ujścia zdarzeń <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2> można subskrybować <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2.OnAfterAttributeChangeEx%2A> ,  
  
- W przeciwnym razie można subskrybować <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterAttributeChange%2A> .  
  
  Poniżej przedstawiono hipotetyczny scenariusz dostępu do dokumentów. Rozszerzenie programu Visual Studio, które ma wyświetlać pewne informacje o otwartych dokumentach, na przykład w przypadku edycji liczby blokad i czegoś dotyczącego danych dokumentu. Wylicza dokumenty w RDT przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.IEnumRunningDocuments> , a następnie wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> każdy dokument w celu pobrania liczby i danych dokumentu. Jeśli dokument jest w stanie oczekiwania na zainicjowanie, żądanie danych dokumentu powoduje niepotrzebne zainicjowanie.  
  
  Bardziej wydajnym sposobem wykonania tej czynności jest użycie <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentEditLockCount%2A> w celu uzyskania liczby operacji edycji, a następnie użycie metody <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A> w celu ustalenia, czy dokument został zainicjowany. Jeśli flagi nie obejmują <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> , dokument został już zainicjowany i żądanie danych dokumentu <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentData%2A> nie powoduje żadnych niepotrzebnych inicjalizacji. Jeśli flagi obejmują <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> , rozszerzenie powinno unikać żądania danych dokumentu do momentu zainicjowania dokumentu. Ta wartość może zostać wykryta w obsłudze zdarzeń OnAfterAttributeChange (np.).  
  
## <a name="testing-extensions-to-see-if-they-force-initialization"></a>Testowanie rozszerzeń, aby sprawdzić, czy wymuszają inicjalizację  
 Nie ma widocznej wskazówki wskazującej, czy dokument został zainicjowany, dlatego może być trudne do sprawdzenia, czy rozszerzenie wymusza inicjalizację. Można ustawić klucz rejestru, który ułatwia weryfikację, ponieważ powoduje to, że tytuł każdego dokumentu, który nie jest w pełni zainicjowany, ma tekst `[Stub]` w tytule.  
  
 W **HKEY_CURRENT_USER \software\microsoft\visualstudio\14.0\backgroundsolutionload]** ustaw wartość **StubTabTitleFormatString** na ** {0} [stub]**.
