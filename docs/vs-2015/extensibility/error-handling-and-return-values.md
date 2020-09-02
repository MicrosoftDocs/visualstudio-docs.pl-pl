---
title: Obsługa błędów i zwracane wartości | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- errors [Visual Studio SDK], handling
- error handling
- return values
ms.assetid: b2d9079d-39a6-438a-8010-290056694b5c
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 74e61e60384b3e98bf26eb8208696ecb9223efa3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696329"
---
# <a name="error-handling-and-return-values"></a>Obsługa błędów i wartości zwracane
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pakietów VSPackage i COM używają tej samej architektury w przypadku błędów. `SetErrorInfo`Funkcje i `GetErrorInfo` są częścią interfejsu programowania aplikacji Win32 (API). Wszystkie pakietu VSPackage w zintegrowanym środowisku programistycznym (IDE) mogą wywoływać te globalne interfejsy API Win32 do rejestrowania szczegółowych informacji o błędach podczas otrzymywania powiadomienia o błędzie. [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)]Zawiera zestawy międzyoperacyjności do zarządzania informacjami o błędzie.  
  
## <a name="interop-methods"></a>Metody międzyoperacyjności  
 Jako wygoda, środowisko IDE udostępnia metodę, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> która służy zamiast wywoływania interfejsów API Win32. W używanym kodzie zarządzanym <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> . Gdy pojawia się błąd `HRESULT` na poziomie, na którym powinien zostać wyświetlony komunikat o błędzie (jest to często obiekt implementujący <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> procedurę obsługi poleceń), IDE używa innej metody, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> , aby wyświetlić odpowiednie okno komunikatu. W kodzie zarządzanym Użyj <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> metody.  
  
 Jako implementujący pakietu VSPackage obiekty COM są zwykle implementowane `ISupportErrorInfo` . `ISupportErrorInfo`Interfejs zapewnia, że zaawansowane informacje o błędzie można przenieść w górę w górę łańcucha wywołań. Obiekty, które mogą być używane między procesami lub między wątkami, muszą obsługiwać `ISupportErrorInfo` , aby zaawansowana informacja o błędzie została prawidłowo przeprowadzona z powrotem do obiektu wywołującego.  
  
 Wszystkie obiekty, które są powiązane z pakietów VSPackage i które mają rozszerzenie IDE, w tym fabryki edytora, edytory, hierarchie i oferowane usługi, powinny obsługiwać zaawansowane informacje o błędzie. Chociaż IDE nie wymaga zaimplementowania tych obiektów pakietu VSPackage `ISupportErrorInfo` , jest to zawsze zalecane.  
  
 Środowisko IDE jest odpowiedzialne za raportowanie informacji o błędach i wyświetlanie ich użytkownikowi, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] gdy `HRESULT` jest on propagowany do IDE. IDE jest również mechanizmem tworzenia `ErrorInfo` obiektów.  
  
## <a name="general-guidelines"></a>Ogólne wskazówki  
 Przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> metod i można <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> ustawiać i raportować błędy, które są wewnętrzne dla implementacji pakietu VSPackage. Jednak jako ogólna reguła postępuj zgodnie z poniższymi wskazówkami dotyczącymi obsługi komunikatów o błędach w pakietu VSPackage:  
  
- Zaimplementuj `ISupportErrorInfo` w obiektach COM pakietu VSPackage.  
  
- Utwórz mechanizm raportowania błędów, który wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> metodę w obiektach, które implementują <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .  
  
- Pozwól, aby IDE wyświetlał błędy dla użytkowników za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> metody.  
  
## <a name="error-information-in-the-ide"></a>Informacje o błędzie w środowisku IDE  
 Poniższe reguły wskazują, jak obsługiwać informacje o błędach w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE:  
  
- Jako strategia obrony przed zagwarantowaniem, że nieodświeżone informacje o błędzie nie są raportowane użytkownikom, funkcja wywołująca <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> metodę powinna najpierw wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> metodę. Przekaż `null` , aby wyczyścić buforowane komunikaty o błędach przed wywołaniem wszystkich elementów, które mogą ustawiać nowe informacje o błędzie.  
  
- Funkcje, które nie zgłaszają bezpośrednio komunikatów o błędach, mogą wywołać metodę tylko wtedy, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> gdy zwracają błąd `HRESULT` . Dozwolone jest wyczyszczenie `ErrorInfo` wpisu do funkcji lub po powrocie <xref:Microsoft.VisualStudio.VSConstants.S_OK> . Jedynym wyjątkiem od tej reguły jest wywołanie, które zwraca błąd `HRESULT` , z którego Strona otrzymująca może jawnie odzyskać lub bezpiecznie zignorować.  
  
- Każda Strona, która jawnie ignoruje błąd `HRESULT` , musi wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> metodę z <xref:Microsoft.VisualStudio.VSConstants.S_OK> . W przeciwnym razie `ErrorInfo` obiekt może być przypadkowo używany, gdy inna strona generuje błąd bez podawania własnych `ErrorInfo` .  
  
- Wszystkie metody, które pochodzą z błędu, `HRESULT` są zachęcane do wywołania <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> metody w celu zapewnienia szczegółowych informacji o błędzie. Jeśli zwracana `HRESULT` jest `FACILITY_ITF` błąd specjalny, metoda jest wymagana do zapewnienia prawidłowego `ErrorInfo` obiektu. Jeśli zwrócony błąd jest standardowym błędem systemu (na przykład,,,, itd <xref:Microsoft.VisualStudio.VSConstants.E_OUTOFMEMORY> <xref:Microsoft.VisualStudio.VSConstants.E_ABORT> <xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG> <xref:Microsoft.VisualStudio.VSConstants.E_UNEXPECTED> .), można zwrócić kod błędu bez jawnego wywołania <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> metody. Jako obronna strategia kodowania, gdy pochodzi błąd (w `HRESULT` tym błędy systemowe), zawsze Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> metodę, albo z `ErrorInfo` opisywanie błędu bardziej szczegółowo lub `null` .  
  
- Wszystkie funkcje, które zwracają błąd pochodzący z innego wywołania, muszą przekazać informacje otrzymane od nieudanego wywołania w `HRESULT` obiekcie bez modyfikowania `ErrorInfo` obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 [SetErrorInfo (Automatyzacja składników)](https://msdn.microsoft.com/8eaacfac-fc37-4eaa-870b-10b99d598d66)   
 [GetErrorInfo](https://msdn.microsoft.com/03317526-8c4f-4173-bc10-110c8112676a)   
 [ISupportErrorInfo, interfejs](https://msdn.microsoft.com/42d33066-36b4-4a5b-aa5d-46682e560f32)
