---
title: Opóźnione ładowanie dokumentu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb07b8e2-a4e3-4cb0-b04f-8eb11c491f35
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 94d79af00fced81dc7da38f323598ade926d26f4
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51755476"
---
# <a name="delayed-document-loading"></a>Opóźnione ładowanie dokumentu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Po użytkownik ponownie otwiera rozwiązanie programu Visual Studio, większość skojarzone dokumenty nie będą ładowane bezpośrednio. Ramka okna dokumentu jest tworzony w stanie oczekiwania na zainicjowanie, a dokument symbolu zastępczego (o nazwie ramki wycinka) znajduje się w tabeli systemem dokumentu (Normalizacją).  
  
 Rozszerzenie może spowodować dokumenty projektu mają być załadowane niepotrzebnie, badając elementy w dokumentach przed załadowaniem. Może to zwiększyć ogólną zużycie pamięci dla programu Visual Studio.  
  
## <a name="document-loading"></a>Ładowanie dokumentu  
 W dokumencie i ramki wycinka są w pełni zainicjowany po użytkownik uzyskuje dostęp do dokumentu, na przykład, wybierając kartę ramki okna. Dokument, również mogą być inicjowane przez rozszerzenie, który żąda danych dokumentu, uzyskiwanie dostępu do Normalizacją bezpośrednio w celu uzyskania danych dokumentu lub uzyskiwanie dostępu do Normalizacją pośrednio poprzez określenie jednego z następujących połączeń:  
  
- Ramka okna Pokaż metody: <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A>.  
  
- Ramka okna Metoda GetProperty <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> na dowolnym z następujących właściwości:  
  
  -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  -   <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
  Jeśli rozszerzenie używa kodu zarządzanego, nie należy wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> chyba że masz pewność, że dokument nie jest w stanie oczekiwania inicjowania lub dokument, który ma być w pełni zainicjowane... Jest to, ponieważ ta metoda zawsze zwraca dokumentów obiektu danych, tworzenie jej, jeśli jest to konieczne. Zamiast tego należy wywołać jedną z metod interfejsu IVsRunningDocumentTable4.  
  
  Jeśli rozszerzenie używa języka C++, można przekazać `null` parametrów nie chcesz.  
  
  Ładowanie dokumentu niepotrzebne można uniknąć, wywołując jedną z następujących metod przed skontaktowaniem się odpowiednie właściwości: przed skontaktowaniem się inne właściwości.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID6>.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A>. Ta metoda zwraca <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> obiektu, który zawiera wartość <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> Jeśli dokument nie została jeszcze zainicjowana.  
  
  Użytkownik może ustalić, kiedy dokument został załadowany przez subskrypcję zdarzenia Normalizacją, które jest wywoływane, gdy dokument jest w pełni zainicjowany. Istnieją dwie możliwości:  
  
- Jeśli obiekt sink zdarzenia implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2>, możesz zasubskrybować <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2.OnAfterAttributeChangeEx%2A>,  
  
- W przeciwnym razie możesz zasubskrybować <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterAttributeChange%2A>.  
  
  Poniżej przedstawiono scenariusz dostęp do dokumentu hipotetycznych. Visual Studio rozszerzenia mają być wyświetlane niektóre informacje na temat otwartych dokumentów, na przykład Edycja blokada liczba i coś o danych dokumentu. Wylicza dokumentów za pomocą Normalizacją <xref:Microsoft.VisualStudio.Shell.Interop.IEnumRunningDocuments>, następnie wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> dla każdego dokumentu w celu pobrania danych i liczba dokumentów blokady edycji. Jeśli dokument jest w stanie oczekiwania na zainicjowanie, żąda danych dokumentu powoduje, że na inicjację niepotrzebnie.  
  
  Bardziej wydajny sposób zrobić, to jest użycie <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentEditLockCount%2A> Pobierz liczbę blokad edycji, a następnie użyć <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A> do określenia, czy dokument został zainicjowany. Jeśli nie ma flagi <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>, dokument został już zainicjowany oraz za dane dokumentu z <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentData%2A> nie powoduje, że wszelkie niepotrzebne inicjowania. Jeśli zawiera flagi <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>, rozszerzenia należy unikać wnioskujące o udostępnienie danych dokumentów, dopóki nie zainicjowano dokumentu. Może to zostać wykryte w obsłudze zdarzeń OnAfterAttributeChange(Ex).  
  
## <a name="testing-extensions-to-see-if-they-force-initialization"></a>Testowanie rozszerzeń, aby zobaczyć, wymusić inicjowania  
 Nie ma żadnych widoczne sygnalizacji, aby wskazać, czy dokument został zainicjowany, dzięki czemu może być trudne dowiedzieć się, jeśli rozszerzenie jest wymuszenie inicjowania. Można ustawić klucz rejestru, który ułatwia weryfikacji, ponieważ sprawia, że tytuł każdego dokumentu, który nie jest w pełni zainicjowany do nazwy zawierają tekst `[Stub]` w tytule.  
  
 W **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0\BackgroundSolutionLoad]** ustaw **StubTabTitleFormatString** do  **{0} [Stub]**.

