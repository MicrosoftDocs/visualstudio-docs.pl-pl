---
title: Obsługa błędów i zwracane wartości | Microsoft Docs
description: Dowiedz się, jak Visual Studio SDK udostępnia zestawy międzyoptykowe do nagrywania rozbudowanych informacji o błędach podczas odbierania powiadomień o błędach.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- errors [Visual Studio SDK], handling
- error handling
- return values
ms.assetid: b2d9079d-39a6-438a-8010-290056694b5c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: ef33936e3dc36d98cc88b1285aa0b198a84cbd59
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898322"
---
# <a name="error-handling-and-return-values"></a>Obsługa błędów i zwracane wartości
Pakiet VSPackages i com używają tej samej architektury w przypadku błędów. Funkcje `SetErrorInfo` i są częścią `GetErrorInfo` interfejsu programowania aplikacji (API) Win32. Każdy pakiet VSPackage w zintegrowanym środowisku projektowym (IDE) może wywołać te globalne interfejsy API Win32, aby rejestrować rozbudowane informacje o błędach podczas odbierania powiadomienia o błędzie. Udostępnia [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] zestawy międzyopłacowe do zarządzania informacjami o błędach.

## <a name="interop-methods"></a>Metody międzyopmiędowe
 Dla wygody środowiska IDE udostępnia metodę , do użycia zamiast <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> wywoływania interfejsów API Win32. W kodzie zarządzanym <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> użyj . Gdy błąd zostanie wyświetlony na poziomie, na którym powinien być wyświetlany komunikat o błędzie (jest to często obiekt implementujący program obsługi poleceń), w ide jest używana inna metoda , aby wyświetlić `HRESULT` <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> odpowiednie okno <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> komunikatu. W kodzie zarządzanym użyj <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> metody .

 Jako implementator VSPackage obiekty COM zwykle implementują `ISupportErrorInfo` . Interfejs `ISupportErrorInfo` zapewnia, że rozbudowane informacje o błędach mogą być przesuwane w pionie w górę łańcucha wywołań. Obiekty, które mogą być używane między procesami lub wątkami, muszą obsługiwać, aby upewnić się, że szczegółowe informacje o błędach są prawidłowo przekierowywyne z powrotem `ISupportErrorInfo` do obiektu wywołującego.

 Wszystkie obiekty związane z pakietami VSPackage i związane z rozszerzaniem środowiska IDE, w tym fabryki edytorów, edytory, hierarchie i oferowane usługi, powinny obsługiwać rozbudowane informacje o błędach. Chociaż idee nie wymagają implementacji tych obiektów VSPackage, zawsze `ISupportErrorInfo` jest to zachęcane.

 Ide jest odpowiedzialny za raportowanie informacji o błędach i wyświetlanie ich użytkownikowi za każdym razem, gdy element jest [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] `HRESULT` propagowany do środowiska IDE. Ide jest również mechanizmem tworzenia `ErrorInfo` obiektów.

## <a name="general-guidelines"></a>Ogólne wskazówki
 Za pomocą metod i można również ustawiać i zgłaszać błędy, które są wewnętrzne dla implementacji <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> pakietów VSPackage. Jednak ogólną regułą jest postępowanie zgodnie z tymi wytycznymi dotyczącymi obsługi komunikatów o błędach w pakcie VSPackage:

- `ISupportErrorInfo`Zaim implementuj w obiektach COM pakietów VSPackage.

- Utwórz mechanizm raportowania błędów, który wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> metodę w obiektach, które implementują <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> metodę .

- Pozwól, aby idee wyświetlały błędy użytkownikom za pośrednictwem <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> metody .

## <a name="error-information-in-the-ide"></a>Informacje o błędzie w idee
 Następujące reguły wskazują sposób obsługi informacji o błędach w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] idee IDE:

- Jako strategia obronna gwarantująca, że nieodświeżone informacje o błędach nie będą zgłaszane do użytkowników, funkcje wywołujące metodę powinny <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> najpierw wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> metodę . Przekaż w `null` celu wyczyszczenia buforowanych komunikatów o błędach przed wywołaniem czegokolwiek, co może ustawić nowe informacje o błędzie.

- Funkcje, które nie zgłaszają bezpośrednio komunikatów o błędach, mogą wywołać metodę tylko wtedy, gdy <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> zwracają błąd `HRESULT` . Dozwolone jest wyczyszczenie wartości we wpisie funkcji `ErrorInfo` lub podczas zwracania . <xref:Microsoft.VisualStudio.VSConstants.S_OK> Jedynym wyjątkiem od tej reguły jest sytuacja, w której wywołanie zwraca błąd, z którego strona odbieraca może jawnie odzyskać lub `HRESULT` bezpiecznie zignorować.

- Każda strona, która jawnie ignoruje `HRESULT` błąd, musi wywołać <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> metodę z <xref:Microsoft.VisualStudio.VSConstants.S_OK> . W przeciwnym razie obiekt może zostać przypadkowo użyty, gdy inna strona wygeneruje `ErrorInfo` błąd bez podano własnego `ErrorInfo` obiektu .

- Wszystkie metody, które pochodzą z błędu, są zachęcane do wywołania metody w celu `HRESULT` <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> zapewnienia rozbudowanych informacji o błędach. Jeśli zwracany jest `HRESULT` specjalny `FACILITY_ITF` błąd, metoda jest wymagana do zapewnienia odpowiedniego `ErrorInfo` obiektu. Jeśli zwrócony błąd jest standardowym błędem systemu (na przykład <xref:Microsoft.VisualStudio.VSConstants.E_OUTOFMEMORY> , <xref:Microsoft.VisualStudio.VSConstants.E_ABORT> , , <xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG> <xref:Microsoft.VisualStudio.VSConstants.E_UNEXPECTED> itp.), <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> akceptowalny jest zwracanie kodu błędu bez jawnego wywoływania metody . Jako defensywną strategię kodowania, gdy występuje błąd (w tym błędy systemowe), zawsze wywołaj metodę z bardziej szczegółowym opisem błędu `HRESULT` <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> lub `ErrorInfo` `null` .

- Wszystkie funkcje, które zwracają błąd pochodzący z innego wywołania, muszą przekazać informacje odebrane z nieudanego wywołania w obiekcie bez `HRESULT` modyfikowania `ErrorInfo` obiektu .

## <a name="see-also"></a>Zobacz też
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [SetErrorInfo (Automatyzacja składników)](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-seterrorinfo)
- [GetErrorInfo](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-geterrorinfo)
- [ISupportErrorInfo, interfejs](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-isupporterrorinfo)
