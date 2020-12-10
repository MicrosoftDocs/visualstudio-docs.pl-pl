---
title: Obsługa błędów i zwracane wartości | Microsoft Docs
description: Dowiedz się, w jaki sposób zestaw SDK programu Visual Studio zawiera zestawy międzyoperacyjne do rejestrowania szczegółowych informacji o błędach podczas uzyskiwania powiadomienia o błędzie.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- errors [Visual Studio SDK], handling
- error handling
- return values
ms.assetid: b2d9079d-39a6-438a-8010-290056694b5c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b8e8385e0b270cd6e359ef03a3060d5eefb97479
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2020
ms.locfileid: "96995853"
---
# <a name="error-handling-and-return-values"></a>Obsługa błędów i zwracane wartości
Pakietów VSPackage i COM używają tej samej architektury w przypadku błędów. `SetErrorInfo`Funkcje i `GetErrorInfo` są częścią interfejsu programowania aplikacji Win32 (API). Wszystkie pakietu VSPackage w zintegrowanym środowisku programistycznym (IDE) mogą wywoływać te globalne interfejsy API Win32 do rejestrowania szczegółowych informacji o błędach podczas otrzymywania powiadomienia o błędzie. [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]Zawiera zestawy międzyoperacyjności do zarządzania informacjami o błędzie.

## <a name="interop-methods"></a>Metody międzyoperacyjności
 Jako wygoda, środowisko IDE udostępnia metodę, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> która służy zamiast wywoływania interfejsów API Win32. W używanym kodzie zarządzanym <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> . Gdy pojawia się błąd `HRESULT` na poziomie, na którym powinien zostać wyświetlony komunikat o błędzie (jest to często obiekt implementujący <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> procedurę obsługi poleceń), IDE używa innej metody, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> , aby wyświetlić odpowiednie okno komunikatu. W kodzie zarządzanym Użyj <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> metody.

 Jako implementujący pakietu VSPackage obiekty COM są zwykle implementowane `ISupportErrorInfo` . `ISupportErrorInfo`Interfejs zapewnia, że zaawansowane informacje o błędzie można przenieść w górę w górę łańcucha wywołań. Obiekty, które mogą być używane między procesami lub między wątkami, muszą obsługiwać `ISupportErrorInfo` , aby zaawansowana informacja o błędzie została prawidłowo przeprowadzona z powrotem do obiektu wywołującego.

 Wszystkie obiekty, które są powiązane z pakietów VSPackage i które mają rozszerzenie IDE, w tym fabryki edytora, edytory, hierarchie i oferowane usługi, powinny obsługiwać zaawansowane informacje o błędzie. Chociaż IDE nie wymaga zaimplementowania tych obiektów pakietu VSPackage `ISupportErrorInfo` , jest to zawsze zalecane.

 Środowisko IDE jest odpowiedzialne za raportowanie informacji o błędach i wyświetlanie ich użytkownikowi, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] gdy `HRESULT` jest on propagowany do IDE. IDE jest również mechanizmem tworzenia `ErrorInfo` obiektów.

## <a name="general-guidelines"></a>Ogólne wskazówki
 Przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> metod i można <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> ustawiać i raportować błędy, które są wewnętrzne dla implementacji pakietu VSPackage. Jednak jako ogólna reguła postępuj zgodnie z poniższymi wskazówkami dotyczącymi obsługi komunikatów o błędach w pakietu VSPackage:

- Zaimplementuj `ISupportErrorInfo` w obiektach COM pakietu VSPackage.

- Utwórz mechanizm raportowania błędów, który wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> metodę w obiektach, które implementują <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .

- Pozwól, aby IDE wyświetlał błędy dla użytkowników za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> metody.

## <a name="error-information-in-the-ide"></a>Informacje o błędzie w środowisku IDE
 Poniższe reguły wskazują, jak obsługiwać informacje o błędach w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE:

- Jako strategia obrony przed zagwarantowaniem, że nieodświeżone informacje o błędzie nie są raportowane użytkownikom, funkcja wywołująca <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> metodę powinna najpierw wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> metodę. Przekaż `null` , aby wyczyścić buforowane komunikaty o błędach przed wywołaniem wszystkich elementów, które mogą ustawiać nowe informacje o błędzie.

- Funkcje, które nie zgłaszają bezpośrednio komunikatów o błędach, mogą wywołać metodę tylko wtedy, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> gdy zwracają błąd `HRESULT` . Dozwolone jest wyczyszczenie `ErrorInfo` wpisu do funkcji lub po powrocie <xref:Microsoft.VisualStudio.VSConstants.S_OK> . Jedynym wyjątkiem od tej reguły jest wywołanie, które zwraca błąd `HRESULT` , z którego Strona otrzymująca może jawnie odzyskać lub bezpiecznie zignorować.

- Każda Strona, która jawnie ignoruje błąd `HRESULT` , musi wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> metodę z <xref:Microsoft.VisualStudio.VSConstants.S_OK> . W przeciwnym razie `ErrorInfo` obiekt może być przypadkowo używany, gdy inna strona generuje błąd bez podawania własnych `ErrorInfo` .

- Wszystkie metody, które pochodzą z błędu, `HRESULT` są zachęcane do wywołania <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> metody w celu zapewnienia szczegółowych informacji o błędzie. Jeśli zwracana `HRESULT` jest `FACILITY_ITF` błąd specjalny, metoda jest wymagana do zapewnienia prawidłowego `ErrorInfo` obiektu. Jeśli zwrócony błąd jest standardowym błędem systemu (na przykład,,,, itd <xref:Microsoft.VisualStudio.VSConstants.E_OUTOFMEMORY> <xref:Microsoft.VisualStudio.VSConstants.E_ABORT> <xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG> <xref:Microsoft.VisualStudio.VSConstants.E_UNEXPECTED> .), można zwrócić kod błędu bez jawnego wywołania <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> metody. Jako obronna strategia kodowania, gdy pochodzi błąd (w `HRESULT` tym błędy systemowe), zawsze Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> metodę, albo z `ErrorInfo` opisywanie błędu bardziej szczegółowo lub `null` .

- Wszystkie funkcje, które zwracają błąd pochodzący z innego wywołania, muszą przekazać informacje otrzymane od nieudanego wywołania w `HRESULT` obiekcie bez modyfikowania `ErrorInfo` obiektu.

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [SetErrorInfo (Automatyzacja składników)](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-seterrorinfo)
- [GetErrorInfo](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-geterrorinfo)
- [ISupportErrorInfo, interfejs](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-isupporterrorinfo)
