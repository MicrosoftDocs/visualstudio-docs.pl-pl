---
title: Co nowego w kontroli źródła w programie Visual Studio 2015 SDK | Dokumenty firmy Microsoft
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- what's new [Visual Studio SDK], source control
- source control [Visual Studio SDK], what's new
ms.assetid: bcf85418-18fb-4824-9dae-d14bf3d56a77
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f90ae3e1d327b10e99713ad28aa2d5a06c0be34b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703408"
---
# <a name="whats-new-in-source-control-for-the-visual-studio-2015-sdk"></a>Co nowego w formancie źródła dla sdk programu Visual Studio 2015

W [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]programie można zapewnić głęboko zintegrowane rozwiązanie kontroli źródła, implementując formant źródła VSPackage. W tej sekcji opisano funkcje kontroli źródła VSPackages i zawiera omówienie kroków implementacji.

## <a name="the-source-control-vspackage"></a>Formant źródła VSPackage

Visual Studio obsługuje dwa typy rozwiązań kontroli źródła. We wszystkich wersjach programu Visual Studio nadal można zintegrować wtyczkę opartą na interfejsie API opartą na usłudze Source Control Plug-in. Można również utworzyć VSPackage for source control, który [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] zapewnia głęboką integrację, ścieżkę odpowiednią dla rozwiązań kontroli źródła, które wymagają wysokiego poziomu wyrafinowania i autonomii.

A VSPackage można dodać prawie każdy rodzaj funkcji do programu Visual Studio. Formant źródła VSPackage zapewnia pełną funkcję kontroli źródła dla programu Visual Studio, od interfejsu użytkownika przedstawionego użytkownikowi do komunikacji zaplecza z systemem kontroli źródła.

Implementowanie kontroli źródła VSPackage wymaga strategii "wszystko albo nic". Twórca formantu źródła VSPackage musi zainwestować znaczną ilość wysiłku w implementację wielu interfejsów kontroli źródła i nowych elementów interfejsu użytkownika (okna dialogowe, menu i paski narzędzi) w celu uwzględnienia całej funkcji kontroli źródła, a także interfejsów wymaganych od dowolnego pakietu do pomyślnej integracji z programem Visual Studio.

Poniższe kroki zawierają ogólny przegląd tego, co jest potrzebne do zaimplementowania pakietu kontroli źródła. Aby uzyskać szczegółowe informacje, zobacz [Tworzenie formantu źródła VSPackage](../../extensibility/internals/creating-a-source-control-vspackage.md).

1. Utwórz vspackage, który oferuje prywatną usługę kontroli źródła.

2. Zaimplementuj interfejsy w usługach związanych z kontrolą źródła, <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> które <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> są oferowane przez program Visual Studio (na przykład interfejs i interfejs).

3. Zarejestruj formant źródła VSPackage.

4. Zaimplementuj cały interfejs użytkownika kontroli źródła, w tym elementy menu, okna dialogowe, paski narzędzi i menu kontekstowe.

5. Wszystkie zdarzenia związane z kontrolą źródła są przekazywane do vsackage kontroli źródła, gdy jest aktywny i muszą być obsługiwane przez VSPackage.

6. Formantu źródła VSPackage musi nasłuchiwać <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> zdarzeń, takich jak te implementujące interfejs, a także <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> śledzenia dokumentu projektu (TPD) zdarzenia (zaimplementowane przez interfejs) i podjąć niezbędne działania.

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- [Omówienie](../../extensibility/internals/source-control-integration-overview.md)
- [Tworzenie pakietu VSPackage kontroli kodu źródłowego](../../extensibility/internals/creating-a-source-control-vspackage.md)
