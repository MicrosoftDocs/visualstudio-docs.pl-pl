---
title: Obsługa błędów i wartości zwracane | Dokumenty firmy Microsoft
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
ms.openlocfilehash: 30b6b9bff9056360f9ea840f47b1488f05bee872
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711934"
---
# <a name="error-handling-and-return-values"></a>Obsługa błędów i zwracanie wartości
VsPackages i COM używać tej samej architektury dla błędów. `SetErrorInfo` Funkcje `GetErrorInfo` i są częścią interfejsu programowania aplikacji Win32 (API). Każdy vspackage w zintegrowanym środowisku programistycznym (IDE) można wywołać te globalne interfejsy API Win32 do rejestrowania bogatych informacji o błędzie podczas odbierania powiadomienia o błędzie. Zapewnia [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] zestawy międzyoperacyjne do zarządzania informacjami o błędach.

## <a name="interop-methods"></a>Metody interop
 Dla wygody IDE udostępnia metodę, <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>, aby użyć zamiast wywoływania interfejsów API Win32. W kodzie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>zarządzanym użyj . Gdy błąd `HRESULT` dociera do poziomu, na którym powinien być wyświetlany komunikat o <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> błędzie (często jest to <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>obiekt implementujący program obsługi poleceń), IDE używa innej metody, aby wyświetlić odpowiednie okno komunikatu. W kodzie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> zarządzanym użyj metody.

 Jako realizator VSPackage obiekty COM zwykle `ISupportErrorInfo`implementują . Interfejs `ISupportErrorInfo` zapewnia, że bogate informacje o błędach mogą przesuwać się pionowo w górę łańcucha wywołań. Obiekty, które mogą być używane w `ISupportErrorInfo` procesach lub między wątkami musi obsługiwać, aby upewnić się, że informacje o błędach bogatych jest poprawnie zorganizowane z powrotem do obiektu wywołującego.

 Wszystkie obiekty, które są związane z VSPackages i które są zaangażowane w rozszerzanie IDE, w tym edytora fabryki, edytory, hierarchie i oferowane usługi, powinny obsługiwać informacje o błędach bogatych. Chociaż IDE nie wymaga tych VSPackage `ISupportErrorInfo`obiektów do zaimplementowania, zawsze jest zachęcany.

 IDE jest odpowiedzialny za raportowanie informacji o błędach i wyświetlanie go do użytkownika, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] gdy `HRESULT` jest propagowany do IDE. IDE jest również mechanizm tworzenia `ErrorInfo` obiektów.

## <a name="general-guidelines"></a>Ogólne wskazówki
 Można użyć <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> metody, aby ustawić i zgłosić błędy, które są wewnętrzne do implementacji VSPackage, jak również. Jednak zgodnie z ogólną zasadą postępuj zgodnie z tymi wskazówkami dotyczącymi obsługi komunikatów o błędach w pakiecie VSPackage:

- Zaimplementuj `ISupportErrorInfo` w obiektach VSPackage COM.

- Utwórz mechanizm raportowania <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> błędów, który <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>wywołuje metodę w obiektach, które implementują .

- Pozwól IDE wyświetlić błędy dla <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> użytkowników za pomocą metody.

## <a name="error-information-in-the-ide"></a>Informacje o błędzie w IDE
 Następujące reguły wskazują, jak obsługiwać informacje o błędach w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE:

- Jako strategia obronna, aby zagwarantować, że nieaktualne <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> informacje o błędzie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> nie są zgłaszane użytkownikom, funkcje, które wywołują metodę, należy najpierw wywołać metodę. Przekaż, `null` aby wyczyścić buforowane komunikaty o błędach przed wywołaniem czegokolwiek, co może ustawić nowe informacje o błędzie.

- Funkcje, które nie zgłaszają bezpośrednio komunikatów o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> błędach, mogą wywoływać metodę tylko wtedy, gdy zwracają błąd. `HRESULT` Dopuszczalne jest wyczyszczenie `ErrorInfo` wpisu do funkcji lub <xref:Microsoft.VisualStudio.VSConstants.S_OK>przy powrocie . Jedynym wyjątkiem od tej reguły jest, `HRESULT` gdy wywołanie zwraca błąd, z którego strona odbierająca można jawnie odzyskać lub bezpiecznie zignorować.

- Każda strona, która jawnie `HRESULT` ignoruje <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> błąd, musi wywołać metodę za pomocą pliku <xref:Microsoft.VisualStudio.VSConstants.S_OK>. W przeciwnym `ErrorInfo` razie obiekt może zostać przypadkowo użyty, gdy `ErrorInfo`inna strona wygeneruje błąd bez podania własnego pliku .

- Wszystkie metody, które `HRESULT` pochodzą błąd są <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> zachęcani do wywołania metody, aby zapewnić informacje o błędzie bogate. Jeśli zwrócony `HRESULT` jest `FACILITY_ITF` specjalny błąd, a następnie metoda `ErrorInfo`jest wymagana do zapewnienia właściwego obiektu. Jeśli zwracany błąd jest standardowym błędem <xref:Microsoft.VisualStudio.VSConstants.E_ABORT> <xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG>systemu <xref:Microsoft.VisualStudio.VSConstants.E_UNEXPECTED>(na przykład <xref:Microsoft.VisualStudio.VSConstants.E_OUTOFMEMORY>, , , i tak dalej.) <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> dopuszczalne jest zwrócenie kodu błędu bez jawnego wywoływania metody. Jako strategia kodowania obronnego, `HRESULT` gdy pochodzi błąd (w <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> tym błędy systemu), zawsze wywołać metodę, albo z `ErrorInfo` opisaniem awarii bardziej szczegółowo, lub `null`.

- Wszystkie funkcje, które zwracają błąd pochodzący z innego wywołania musi przekazać `HRESULT` informacje, które `ErrorInfo` zostały odebrane z wywołanie nie po awarii w bez modyfikowania obiektu.

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [SetErrorInfo (automatyzacja komponentów)](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-seterrorinfo)
- [GetErrorInfo](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-geterrorinfo)
- [Interfejs ISupportErrorInfo](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-isupporterrorinfo)
