---
title: Co nowego w kontroli źródła w zestawie SDK programu Visual Studio 2015 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80703408"
---
# <a name="whats-new-in-source-control-for-the-visual-studio-2015-sdk"></a>Co nowego w kontroli źródła dla zestawu SDK programu Visual Studio 2015

W programie [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] można zapewnić głębokie zintegrowane rozwiązanie kontroli źródła, implementując pakietu VSPackage kontroli źródła. W tej sekcji opisano funkcje kontroli źródła pakietów VSPackage i przedstawiono przegląd kroków implementacji.

## <a name="the-source-control-vspackage"></a>Pakietu VSPackage kontroli źródła

Program Visual Studio obsługuje dwa typy rozwiązań kontroli źródła. We wszystkich wersjach programu Visual Studio można nadal zintegrować wtyczkę typu plug-in z interfejsem API kontroli źródła. Można również utworzyć pakietu VSPackage dla kontroli źródła, która zapewnia głębokiej integracji, [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] ścieżkę odpowiednią do rozwiązań kontroli źródła, które wymagają wysokiego poziomu złożoności i autonomii.

Pakietu VSPackage może dodawać niemal dowolny rodzaj funkcjonalności do programu Visual Studio. Pakietu VSPackage kontroli źródła udostępnia kompletną funkcję kontroli źródła dla programu Visual Studio, z interfejsu użytkownika prezentowanego użytkownikowi na potrzeby komunikacji wewnętrznej z systemem kontroli źródła.

Implementacja kontroli źródła pakietu VSPackage wymaga strategii "all or Nothing". Twórca kontroli źródła pakietu VSPackage musi zainwestować znaczną ilość wysiłku w celu zaimplementowania wielu interfejsów kontroli źródła i nowych elementów interfejsu użytkownika (okien dialogowych, menu i pasków narzędzi), aby pokryć wszystkie funkcje kontroli źródła, a także interfejsy wymagane do pomyślnego zintegrowania dowolnego pakietu z programem Visual Studio.

Poniższe kroki zawierają ogólny przegląd informacji potrzebnych do zaimplementowania pakietu kontroli źródła. Aby uzyskać szczegółowe informacje, zobacz [Tworzenie pakietu VSPackage kontroli źródła](../../extensibility/internals/creating-a-source-control-vspackage.md).

1. Utwórz element pakietu VSPackage, który proffers usługę kontroli źródła prywatnego.

2. Zaimplementuj interfejsy w usługach związanych z kontrolą źródła, które są proffered przez program Visual Studio (na przykład <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> interfejs i).

3. Zarejestruj pakietu VSPackage kontroli źródła.

4. Zaimplementuj cały interfejs użytkownika kontroli źródła, w tym elementy menu, okna dialogowe, paski narzędzi i menu kontekstowe.

5. Wszystkie zdarzenia związane z kontrolą źródła są przesyłane do VSackage kontroli źródła, gdy jest aktywny i muszą być obsługiwane przez pakietu VSPackage.

6. Pakietu VSPackage kontroli źródła musi nasłuchiwać zdarzeń, takich jak te implementujące <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> interfejs, a także śledzić zdarzenia dokumentu projektu (TPD) (zgodnie z implementacją <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> interfejsu) i podejmować odpowiednie działania.

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- [Omówienie](../../extensibility/internals/source-control-integration-overview.md)
- [Tworzenie pakietu VSPackage kontroli kodu źródłowego](../../extensibility/internals/creating-a-source-control-vspackage.md)
