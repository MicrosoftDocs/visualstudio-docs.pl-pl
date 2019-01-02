---
title: Opóźnione ładowanie dokumentu | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: fb07b8e2-a4e3-4cb0-b04f-8eb11c491f35
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 27edc56516293ff6502f0708a02faa7bae1e3719
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53940365"
---
# <a name="delayed-document-loading"></a>Opóźnione ładowanie dokumentu
Po użytkownik ponownie otwiera rozwiązanie programu Visual Studio, większość skojarzone dokumenty nie będą ładowane bezpośrednio. Ramka okna dokumentu jest tworzony w stanie oczekiwania na zainicjowanie, a dokument symbolu zastępczego (o nazwie ramki wycinka) znajduje się w tabeli systemem dokumentu (Normalizacją).  
  
Rozszerzenie może spowodować dokumenty projektu mają być załadowane niepotrzebnie, badając elementy w dokumentach, zanim zostały wczytane, co może zwiększyć ogólną zużycie pamięci dla programu Visual Studio.  
  
## <a name="document-loading"></a>Ładowanie dokumentu  
W dokumencie i ramki wycinka są w pełni zainicjowany po użytkownik uzyskuje dostęp do dokumentu, na przykład, wybierając kartę ramki okna. Dokument, również mogą być inicjowane przez rozszerzenie, który żąda danych dokumentu, uzyskiwanie dostępu do Normalizacją bezpośrednio w celu uzyskania danych dokumentu lub uzyskiwanie dostępu do Normalizacją pośrednio poprzez określenie jednego z następujących połączeń:  
  
- Ramka okna <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> metody.  
  
- Ramka okna <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> metodę na dowolne z następujących właściwości:  
  
   - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
   - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
   - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
   - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
   - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
   - <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>  
  
- Jeśli rozszerzenie używa kodu zarządzanego, nie należy wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> chyba że masz pewność, że dokument nie jest w stanie oczekiwania inicjowania lub dokument, który ma zostać w pełni zainicjowany. Ponieważ metoda ta zwraca zawsze dokumentów obiektu danych, tworzenie jej, jeśli jest to konieczne. Zamiast tego należy wywołać jedną z metod na `IVsRunningDocumentTable4` interfejsu.  
  
- Jeśli rozszerzenie używa języka C++, można przekazać `null` parametrów nie chcesz.  
  
- Możesz uniknąć niepotrzebnych dokumentu załadowanie, wywołując jedną z następujących metod przed skontaktowaniem się odpowiednie właściwości przed skontaktowaniem się inne właściwości:  
  
   - <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID6>.  
  
   - <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A>. Ta metoda zwraca <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> obiektu, który zawiera wartość <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4> Jeśli dokument nie została jeszcze zainicjowana.  
  
Użytkownik może ustalić, kiedy dokument został załadowany przez subskrypcję zdarzenia Normalizacją, które jest wywoływane, gdy dokument jest w pełni zainicjowany. Istnieją dwie możliwości:  
  
- Jeśli obiekt sink zdarzenia implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2>, możesz zasubskrybować <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents2.OnAfterAttributeChangeEx%2A>,  
  
- W przeciwnym razie możesz zasubskrybować <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterAttributeChange%2A>.  
  

 Poniższy przykład przedstawia scenariusz dostępu hipotetyczny dokumentu: Visual Studio rozszerzenia chce, aby wyświetlić niektóre informacje na temat otwartych dokumentów, na przykład Edycja blokada liczba i coś o danych dokumentu. Wylicza dokumentów za pomocą Normalizacją <xref:Microsoft.VisualStudio.Shell.Interop.IEnumRunningDocuments>, następnie wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.GetDocumentInfo%2A> dla każdego dokumentu w celu pobrania danych i liczba dokumentów blokady edycji. Jeśli dokument jest w stanie oczekiwania na zainicjowanie, żąda danych dokumentu powoduje, że na inicjację niepotrzebnie.  
  
 Bardziej efektywne sposobem uzyskiwania dostępu do dokumentu jest użycie <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentEditLockCount%2A> Pobierz liczbę blokad edycji, a następnie użyć <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentFlags%2A> do określenia, czy dokument został zainicjowany. Jeśli nie ma flagi <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>, dokument został już zainicjowany oraz za dane dokumentu z <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable4.GetDocumentData%2A> nie powoduje, że wszelkie niepotrzebne inicjowania. Jeśli zawiera flagi <xref:Microsoft.VisualStudio.Shell.Interop._VSRDTFLAGS4>, rozszerzenia należy unikać wnioskujące o udostępnienie danych dokumentów, dopóki nie zainicjowano dokumentu. Ten proces inicjowania może zostać wykryte w `OnAfterAttributeChange(Ex)` programu obsługi zdarzeń.  
  
## <a name="test-extensions-to-see-if-they-force-initialization"></a>Testowanie rozszerzeń, aby zobaczyć, wymusić inicjowania  
 Nie ma żadnych widoczne sygnalizacji, aby wskazać, czy dokument został zainicjowany, dzięki czemu może być trudne dowiedzieć się, jeśli rozszerzenie jest wymuszenie inicjowania. Można ustawić klucz rejestru, który ułatwia weryfikacji, ponieważ sprawia, że tytuł każdego dokumentu, który nie jest w pełni zainicjowany do nazwy zawierają tekst *[Stub]* w tytule.  
  
 W **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0\BackgroundSolutionLoad**ustaw **StubTabTitleFormatString** do  *{0} [Stub]*.