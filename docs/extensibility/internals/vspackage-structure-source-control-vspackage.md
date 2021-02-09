---
title: Struktura pakietu VSPackage (pakietu VSPackage kontroli źródła) | Microsoft Docs
description: Dowiedz się więcej o zestawie SDK pakietu kontroli źródła, który zawiera wskazówki dotyczące pakietu VSPackage z implementacją kontroli źródła do integracji z programem Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, structure
- source control packages, VSPackage overview
ms.assetid: 92722be7-b397-48c3-a7a7-0b931a341961
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 886ff7112a5e455bfc07e51b30f4ac60eb10136a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99899947"
---
# <a name="vspackage-structure-source-control-vspackage"></a>Struktura pakietu VSPackage (pakiet VSPackage kontroli kodu źródłowego)

Zestaw SDK pakietu kontroli źródła zawiera wskazówki dotyczące tworzenia pakietu VSPackage, które umożliwiają implementowanie kontroli źródła w celu zintegrowania jej funkcji kontroli źródła ze środowiskiem programu Visual Studio. Pakietu VSPackage jest składnikiem COM, który zwykle jest ładowany na żądanie przez zintegrowane środowisko programistyczne (IDE) programu Visual Studio na podstawie usług anonsowanych przez pakiet w jego wpisach rejestru. Każdy pakietu VSPackage musi implementować <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> . Pakietu VSPackage zazwyczaj zużywa usługi oferowane przez środowisko IDE programu Visual Studio i proffers niektóre usługi.

Pakietu VSPackage deklaruje elementy menu i ustanawia domyślny stan elementu za pośrednictwem pliku. vsct. Środowisko IDE programu Visual Studio wyświetla elementy menu w tym stanie do momentu załadowania pakietu VSPackage. Następnie implementacja pakietu VSPackage <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metody jest wywoływana w celu włączenia lub wyłączenia elementów menu.

## <a name="source-control-package-characteristics"></a>Charakterystyki pakietu kontroli źródła

Pakietu VSPackage kontroli źródła jest głęboko zintegrowany z Visual Studio. Semantyka pakietu VSPackage obejmuje:

- Interfejs, który ma być zaimplementowany przez pakietu VSPackage ( `IVsPackage` interfejs)

- Implementacja polecenia interfejsu użytkownika (plik. vsct i implementacja <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejsu)

- Rejestracja pakietu VSPackage w programie Visual Studio.

Pakietu VSPackage kontroli źródła musi komunikować się z tymi innymi jednostkami programu Visual Studio:

- Projekty

- Edytory

- Rozwiązania

- Windows

- Uruchomiona tabela dokumentów

### <a name="visual-studio-environment-services-that-may-be-consumed"></a>Usługi środowiska Visual Studio, które mogą być używane

<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>

Usługa SVsRegisterScciProvider

<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>

### <a name="vsip-interfaces-implemented-and-called"></a>Interfejsy VSIP zaimplementowane i wywoływane

Pakiet kontroli źródła jest pakietu VSPackage i w związku z tym może współdziałać bezpośrednio z innymi pakietów VSPackage, które są zarejestrowane w programie Visual Studio. Aby zapewnić pełną szerokość funkcji kontroli źródła, pakietu VSPackage kontroli źródła może odnosić się do interfejsów udostępnianych przez projekty lub powłokę.

Każdy projekt w programie Visual Studio musi <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> zostać wdrożony jako projekt w środowisku IDE programu Visual Studio. Jednak ten interfejs nie jest wystarczająco wyspecjalizowany dla kontroli źródła. Projekty, które powinny być objęte implementacją kontroli źródła <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> . Ten interfejs jest używany przez pakietu VSPackage kontroli źródła w celu wykonywania zapytań dotyczących projektu i zapewniania symboli i informacji wiążących (informacje niezbędne do ustanowienia połączenia między lokalizacją serwera a lokalizacją dysku projektu, który jest pod kontrolą źródła).

Pakietu VSPackage kontroli źródła implementuje <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> , co z kolei umożliwia projektom zarejestrowanie się w celu kontroli źródła i pobranie ich symboli stanu.

Aby zapoznać się z pełną listą interfejsów, które należy wziąć pod uwagę pakietu VSPackage kontroli źródła, zobacz [pokrewne usługi i interfejsy](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md).

## <a name="see-also"></a>Zobacz też

- [Elementy projektu](../../extensibility/internals/source-control-vspackage-design-elements.md)
- [Powiązane usługi i interfejsy](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)
