---
title: Co nowego w kontroli źródła w Visual Studio 2015 SDK | Dokumentacja firmy Microsoft
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- what's new [Visual Studio SDK], source control
- source control [Visual Studio SDK], what's new
ms.assetid: bcf85418-18fb-4824-9dae-d14bf3d56a77
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3b667a6c6322a925b49290ab3234788a4eee3544
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57867959"
---
# <a name="whats-new-in-source-control-for-the-visual-studio-2015-sdk"></a>What's New in kontroli źródła dla programu Visual Studio 2015 SDK

W [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], może udostępnić rozwiązanie kontroli źródła ściśle zintegrowana z zastosowaniem kontroli źródła pakietu VSPackage. Ta sekcja zawiera opis funkcji kontroli źródła pakietów VSPackage i zawiera omówienie kroków wdrożenia.

## <a name="the-source-control-vspackage"></a>Pakietu VSPackage kontroli kodu źródłowego

Program Visual Studio obsługuje dwa typy rozwiązań kontroli źródła. We wszystkich wersjach programu Visual Studio, możesz nadal zintegrować oparte na interfejsie API wtyczki kontroli źródła wtyczek. Można również utworzyć VSPackage do kontroli źródła, który zapewnia integrację głębokiego [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] odpowiednie dla rozwiązań kontroli źródła, które wymagają wysokiego poziomu zaawansowania dostosowanie i Autonomia ścieżki.

Pakietu VSPackage można dodać niemal każdego rodzaju funkcje programu Visual Studio. Kontroli źródła pakietu VSPackage zapewnia funkcji kontroli źródła ukończone dla programu Visual Studio z poziomu interfejsu użytkownika, użytkownik komunikacja między zaplecza przy użyciu systemu kontroli źródła.

Implementowanie kontroli źródła pakietu VSPackage wymaga strategii "wszystko lub nic". Twórca pakietu VSPackage kontroli źródła należy zakupić znacznej ilości wysiłku we wdrażaniu pewną liczbę interfejsów kontroli źródła i nowych elementów interfejsu użytkownika (okna dialogowe, menu i pasków narzędzi) obejmuje funkcjonalność formantu całego źródła, a także interfejsów wymagane dla dowolnego pakietu pomyślnie integracji z programem Visual Studio.

Poniższe kroki zapewniają ogólne omówienie, co jest potrzebne do wdrożenia pakietu kontroli źródła. Aby uzyskać więcej informacji, zobacz [tworzenia VSPackage kontroli kodu](../../extensibility/internals/creating-a-source-control-vspackage.md).

1. Tworzenie pakietu VSPackage, który proffers usługi kontroli źródła prywatne.

2. Implementowanie interfejsów w usługi związane z kontroli źródła, które są proffered przez program Visual Studio (na przykład <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> interfejsu).

3. Rejestrowanie pakietu VSPackage kontroli źródła.

4. Zaimplementuj wszystkie kontroli źródła w interfejsie użytkownika, łącznie z elementami menu, okna dialogowe, paski narzędzi i menu kontekstowe.

5. Wszystkie zdarzenia związane z kontroli źródła są przekazywane do VSackage do kontroli źródła, gdy jest aktywny i muszą być obsługiwane przez Twoje pakietu VSPackage.

6. Do kontroli źródła pakietu VSPackage musi nasłuchiwać zdarzeń, takich jak implementującej <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> interfejsu, a także zdarzenia śledzenia projektu dokumentu (TPD) (jako implementowany przez <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> interfejsu) i podejmowanie wymaganych działań.

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>
- [Omówienie](../../extensibility/internals/source-control-integration-overview.md)
- [Tworzenie pakietu VSPackage kontroli kodu źródłowego](../../extensibility/internals/creating-a-source-control-vspackage.md)