---
title: Struktura pakietu VSPackage (pakiet VSPackage kontroli) | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, structure
- source control packages, VSPackage overview
ms.assetid: 92722be7-b397-48c3-a7a7-0b931a341961
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3e71b8675aad05f45d13be5a86e8729266a3a017
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54954101"
---
# <a name="vspackage-structure-source-control-vspackage"></a>Struktura pakietu VSPackage (pakiet VSPackage kontroli kodu źródłowego)

Zestaw SDK pakietu kontroli źródła zawiera wytyczne dotyczące tworzenia pakietu VSPackage, który zezwala na implementujący kontroli źródła zintegrować wykorzystywaniu funkcji kontroli źródła przy użyciu środowiska Visual Studio. Pakietu VSPackage jest składnik modelu COM, który zazwyczaj jest ładowany przez program Visual Studio zintegrowane środowisko programistyczne (IDE) opartych na usługach, które są anonsowane przez pakiet w swoich wpisach rejestru na żądanie. Każdego pakietu VSPackage musi implementować <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>. Pakietu VSPackage zwykle korzysta z usług oferowanych przez środowiska IDE programu Visual Studio i proffers niektórych usług własnych.

Pakietu VSPackage deklaruje jego elementy menu i ustanawia domyślny stan elementu przy użyciu pliku vsct. Środowiska IDE programu Visual Studio Wyświetla elementy menu w tym stanie do momentu załadowania pakietu VSPackage. Następnie VSPackage implementacji <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metoda jest wywoływana, aby włączyć lub wyłączyć elementy menu.

## <a name="source-control-package-characteristics"></a>Właściwości pakietu kontroli źródła

Pakietu VSPackage kontroli źródła jest głęboko zintegrowana w programie Visual Studio. Semantyka pakietu VSPackage obejmują:

-   Interfejs do zaimplementowania bycia pakietu VSPackage ( `IVsPackage` interfejsu)

-   Implementacja poleceń interfejsu użytkownika (pliku vsct i stosowania <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejsu)

-   Rejestracja pakietu VSPackage przy użyciu programu Visual Studio.

Kontrola źródła pakietu VSPackage muszą komunikować się z innymi jednostkami programu Visual Studio:

-   Projekty

-   Edytory

-   Rozwiązania

-   Windows

-   Uruchamianie tabeli dokumentu

### <a name="visual-studio-environment-services-that-may-be-consumed"></a>Usługi środowiska Visual Studio, które mogą być używane

<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>

SVsRegisterScciProvider Service

<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>

### <a name="vsip-interfaces-implemented-and-called"></a>VSIP interfejsy implementowane oraz nazywany

Pakiet kontroli źródła jest pakietu VSPackage, a w związku z tym można korzystać bezpośrednio z innych pakietów VSPackage, które są zarejestrowane w usłudze Visual Studio. W celu zapewnienia pełnego zakresu funkcji kontroli źródła, kontroli źródła pakietu VSPackage poradzenie sobie z dostarczanych przez projektów lub powłoki.

Każdy projekt w programie Visual Studio musi implementować <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> uznawana za projektu w środowisku IDE programu Visual Studio. Jednak ten interfejs nie jest przeznaczone wystarczający do kontroli źródła. Projekty, które powinny być w obszarze źródło sterowania Implementowanie <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>. Ten interfejs jest wykorzystywany przez kontrolę źródła pakietu VSPackage, aby wyszukać projekt służący do jego zawartości, a do tego celu symbole i informacje o powiązaniu (informacje potrzebne do nawiązania połączenia między lokalizacją serwera i lokalizację dysku projektu, który znajduje się w kontroli źródła).

Implementuje pakietu VSPackage kontroli źródła <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>, co z kolei pozwala projektów, które rejestrują się do kontroli źródła i pobierać symbole ich stanu.

Aby uzyskać pełną listę interfejsów, które należy wziąć pod uwagę pakietu VSPackage kontroli źródła, zobacz [powiązane usługi i interfejsy](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md).

## <a name="see-also"></a>Zobacz także

- [Elementy projektu](../../extensibility/internals/source-control-vspackage-design-elements.md)
- [Powiązane usługi i interfejsy](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)