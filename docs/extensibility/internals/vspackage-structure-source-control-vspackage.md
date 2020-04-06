---
title: VSPackage Structure (Kontrola źródła VSPackage) | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, structure
- source control packages, VSPackage overview
ms.assetid: 92722be7-b397-48c3-a7a7-0b931a341961
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b3f09b189e1e4b47187586e66c74315ee32495c8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703809"
---
# <a name="vspackage-structure-source-control-vspackage"></a>Struktura pakietu VSPackage (pakiet VSPackage kontroli kodu źródłowego)

Pakiet pakietu kontroli źródła SDK zawiera wskazówki dotyczące tworzenia vspackage, które umożliwiają implementator kontroli źródła do integracji jego funkcji kontroli źródła ze środowiskiem programu Visual Studio. VSPackage jest składnikiem COM, który jest zazwyczaj ładowany na żądanie przez zintegrowane środowisko programistyczne programu Visual Studio (IDE) na podstawie usług, które są anonsowane przez pakiet w jego wpisów rejestru. Każdy VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>musi zaimplementować . VsPackage zazwyczaj zużywa usługi oferowane przez ide programu Visual Studio i oferuje niektóre usługi własne.

VsPackage deklaruje swoje elementy menu i ustanawia domyślny stan elementu za pośrednictwem pliku vsct. Ide programu Visual Studio wyświetla elementy menu w tym stanie, dopóki nie zostanie załadowany vspackage. Następnie vsPackage implementacji <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metody jest wywoływana, aby włączyć lub wyłączyć elementy menu.

## <a name="source-control-package-characteristics"></a>Charakterystyka pakietu kontroli źródła

Formant źródłowy VSPackage jest głęboko zintegrowany z programem Visual Studio. Semantyka VSPackage obejmuje:

- Interfejs, który ma być zaimplementowany `IVsPackage` ze względu na to, że jest VSPackage (interfejs)

- Implementacja polecenia interfejsu użytkownika (plik vsct i implementacja <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejsu)

- Rejestracja vspackage z visual studio.

Formant źródłowy VSPackage musi komunikować się z tymi innymi encjami programu Visual Studio:

- Projekty

- Edytory

- Rozwiązania

- Windows

- Uruchomiona tabela dokumentów

### <a name="visual-studio-environment-services-that-may-be-consumed"></a>Usługi środowiska programu Visual Studio, które mogą być używane

<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>

Usługa SVsRegisterScciProvider

<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>

### <a name="vsip-interfaces-implemented-and-called"></a>Interfejsy VSIP zaimplementowane i wywoływane

Pakiet kontroli źródła jest VSPackage i dlatego może wchodzić w interakcje bezpośrednio z innymi VSPackages, które są zarejestrowane w programie Visual Studio. W celu zapewnienia pełnego zakresu funkcji kontroli źródła, vspackage kontroli źródła może zajmować się interfejsami dostarczonymi przez projekty lub powłoki.

Każdy projekt w programie <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> Visual Studio musi zostać zaimplementowane, aby być rozpoznawany jako projekt w programie Visual Studio IDE. Jednak ten interfejs nie jest wystarczająco wyspecjalizowane dla kontroli źródła. Projekty, które mają być pod <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>kontrolą źródła implementują . Ten interfejs jest używany przez formant źródła VSPackage do kwerendy projektu dla jego zawartości i dostarczyć go glifów i informacji wiążących (informacje potrzebne do ustanowienia połączenia między lokalizacją serwera i lokalizacji dysku projektu, który jest pod kontrolą źródła).

Formant źródła VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>implementuje , co z kolei umożliwia projektom rejestrowanie się w celu kontroli źródła i pobieranie ich glifów stanu.

Aby uzyskać pełną listę interfejsów, które vspackage kontroli źródła należy wziąć pod uwagę, zobacz [Powiązanych usług i interfejsów](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md).

## <a name="see-also"></a>Zobacz też

- [Elementy projektu](../../extensibility/internals/source-control-vspackage-design-elements.md)
- [Powiązane usługi i interfejsy](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)
