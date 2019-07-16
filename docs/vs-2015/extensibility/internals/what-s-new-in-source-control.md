---
title: Nowości dotyczące kontroli kodu źródłowego
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- what's new [Visual Studio SDK], source control
- source control [Visual Studio SDK], what's new
ms.assetid: bcf85418-18fb-4824-9dae-d14bf3d56a77
caps.latest.revision: 28
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 31b55c57f47f25814eff24f13bcf91408468d0f4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68200957"
---
# <a name="what39s-new-in-source-control-in-visual-studio-2015"></a>Co&#39;s Nowość w kontroli źródła w programie Visual Studio 2015

[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

W [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] może udostępnić rozwiązanie kontroli źródła ściśle zintegrowana z zastosowaniem kontroli źródła pakietu VSPackage. Ta sekcja zawiera opis funkcji kontroli źródła pakietów VSPackage i zawiera omówienie kroków wdrożenia.  
  
## <a name="the-source-control-vspackage"></a>Pakietu VSPackage kontroli kodu źródłowego  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] obsługuje dwa typy rozwiązania kontroli źródła. We wszystkich wersjach [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], nadal można zintegrować oparte na interfejsie API wtyczki kontroli źródła wtyczek. Można również utworzyć VSPackage do kontroli źródła, który zapewnia integrację głębokiego [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] odpowiednie dla rozwiązań kontroli źródła, które wymagają wysokiego poziomu zaawansowania dostosowanie i Autonomia ścieżki.  
  
 Dodać niemal każdego rodzaju funkcje pakietu VSPackage [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Kontroli źródła pakietu VSPackage udostępnia funkcję kontroli źródła ukończone dla [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], z poziomu interfejsu użytkownika, użytkownik komunikacja między zaplecza przy użyciu systemu kontroli źródła.  
  
 Implementowanie kontroli źródła pakietu VSPackage wymaga strategii "wszystko lub nic". Twórca pakietu VSPackage kontroli źródła należy zakupić znacznej ilości wysiłku we wdrażaniu pewną liczbę interfejsów kontroli źródła i nowych elementów interfejsu użytkownika (okna dialogowe, menu i pasków narzędzi) obejmuje funkcjonalność formantu całego źródła, a także interfejsów wymagane dla dowolnego pakietu pomyślnie zintegrować z [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 Poniższe kroki zapewniają ogólne omówienie, co jest potrzebne do wdrożenia pakietu kontroli źródła. Aby uzyskać więcej informacji, zobacz [tworzenia VSPackage kontroli kodu](../../extensibility/internals/creating-a-source-control-vspackage.md).  
  
1. Tworzenie pakietu VSPackage, który proffers usługi kontroli źródła prywatne.  
  
2. Implementowanie interfejsów w usługi związane z kontroli źródła, które są proffered przez [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] (na przykład <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> interfejsu).  
  
3. Rejestrowanie pakietu VSPackage kontroli źródła.  
  
4. Zaimplementuj wszystkie kontroli źródła w interfejsie użytkownika, łącznie z elementami menu, okna dialogowe, paski narzędzi i menu kontekstowe.  
  
5. Wszystkie zdarzenia związane z kontroli źródła są przekazywane do VSackage do kontroli źródła, gdy jest aktywny i muszą być obsługiwane przez Twoje pakietu VSPackage.  
  
6. Do kontroli źródła pakietu VSPackage musi nasłuchiwać zdarzeń, takich jak implementującej <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> interfejsu, a także zdarzenia śledzenia projektu dokumentu (TPD) (jako implementowany przez <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> interfejsu) i podejmowanie wymaganych działań.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 [Omówienie](../../extensibility/internals/source-control-integration-overview.md)   
 [Tworzenie pakietu VSPackage kontroli kodu źródłowego](../../extensibility/internals/creating-a-source-control-vspackage.md)
