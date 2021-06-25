---
title: Struktura vspackage (pakiet VSPackage kontroli kodu źródłowego) | Microsoft Docs
description: Dowiedz się więcej o zestawie SDK pakietu kontroli kodu źródłowego, który zawiera wskazówki dotyczące pakietu VSPackage z implementatorem kontroli źródła w celu integracji z Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VSPackages, structure
- source control packages, VSPackage overview
ms.assetid: 92722be7-b397-48c3-a7a7-0b931a341961
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b95c382342675d79c0c6e854b5fc087d495827e2
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898825"
---
# <a name="vspackage-structure-source-control-vspackage"></a>Struktura pakietu VSPackage (pakiet VSPackage kontroli kodu źródłowego)

Zestaw SDK pakietu kontroli kodu źródłowego zawiera wskazówki dotyczące tworzenia pakietu VSPackage, które umożliwiają implementatorowi kontroli źródła zintegrowanie jego funkcji kontroli źródła ze środowiskiem Visual Studio kodu. Pakiet VSPackage to składnik COM, który jest zwykle ładowany na żądanie przez zintegrowane środowisko projektowe (IDE) programu Visual Studio na podstawie usług anonsowanych przez pakiet we wpisach rejestru. Każdy pakiet VSPackage musi implementować . <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> Pakiet VSPackage zwykle używa usług oferowanych przez Visual Studio IDE i pobiera niektóre usługi samodzielnie.

Pakiet VSPackage deklaruje swoje elementy menu i ustanawia domyślny stan elementu za pośrednictwem pliku vsct. W Visual Studio IDE są wyświetlane elementy menu w tym stanie, dopóki pakiet VSPackage nie zostanie załadowany. Następnie implementacja metody vsPackage jest wywoływana w celu włączenia <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> lub wyłączenia elementów menu.

## <a name="source-control-package-characteristics"></a>Charakterystyka pakietu kontroli kodu źródłowego

Pakiet VSPackage kontroli źródła jest głęboko zintegrowany z Visual Studio. Semantyka pakietów VSPackage obejmuje:

- Interfejs, który ma być implementowany przez bycie pakietem VSPackage `IVsPackage` (interfejsem)

- Implementacja poleceń interfejsu użytkownika (plik vsct i implementacja <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfejsu)

- Rejestracja pakietów VSPackage za pomocą Visual Studio.

Pakiet VSPackage kontroli źródła musi komunikować się z tymi innymi Visual Studio jednostkami:

- Projekty

- Edytory

- Rozwiązania

- Windows

- Uruchomiona tabela dokumentów

### <a name="visual-studio-environment-services-that-may-be-consumed"></a>Visual Studio środowiska, które mogą być używane

<xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>

Usługa SVsRegisterScciProvider

<xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>

<xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>

### <a name="vsip-interfaces-implemented-and-called"></a>Zaimplementowane i wywoływane interfejsy VSIP

Pakiet kontroli źródła jest pakietem VSPackage i dlatego może wchodzić w bezpośrednią interakcję z innymi pakietami VSPackage zarejestrowanymi w Visual Studio. Aby zapewnić pełny zakres funkcji kontroli źródła, pakiet VSPackage kontroli źródła może zająć się interfejsami dostarczanymi przez projekty lub powłokę.

Każdy projekt w Visual Studio musi zostać zaimplementowany, aby został rozpoznany jako <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> projekt w Visual Studio IDE. Jednak ten interfejs nie jest wystarczająco wyspecjalizowany do kontroli źródła. Projekty, które powinny być pod kontrolą źródła, implementują . <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> Ten interfejs jest używany przez pakiet VSPackage kontroli kodu źródłowego do wykonywania zapytań dotyczących zawartości projektu oraz do podania do niego glifów i informacji o powiązaniach (informacje potrzebne do nawiązania połączenia między lokalizacją serwera a lokalizacją dysku projektu, który jest pod kontrolą źródła).

Pakiet VSPackage kontroli źródła implementuje pakiet , co z kolei umożliwia projektom rejestrowanie się w celu kontroli źródła i pobieranie ich <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> glifów stanu.

Aby uzyskać pełną listę interfejsów, które musi wziąć pod uwagę pakiet VSPackage kontroli źródła, zobacz [Powiązane usługi i interfejsy](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md).

## <a name="see-also"></a>Zobacz też

- [Elementy projektu](../../extensibility/internals/source-control-vspackage-design-elements.md)
- [Powiązane usługi i interfejsy](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)
