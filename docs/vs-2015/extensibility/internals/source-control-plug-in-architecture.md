---
title: Architektura wtyczki kontroli źródła | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control plug-ins, architecture
ms.assetid: 35351d4c-9414-409b-98fc-f2023e2426b7
caps.latest.revision: 25
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c7ded33f6296d9ddb0b87a3d2916a95249169f82
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51805218"
---
# <a name="source-control-plug-in-architecture"></a>Architektura wtyczki kontroli kodu źródłowego
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Można dodać Lepsza obsługa kontroli źródła do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] zintegrowanego środowiska programistycznego (IDE) przez implementację i dołączanie wtyczki kontroli źródła. Łączy się wtyczka do kontroli źródła za pomocą dobrze zdefiniowanych interfejsu API wtyczki kontroli źródła z IDE. IDE udostępnia funkcje kontroli wersji z systemu kontroli źródła, zapewniając interfejs użytkownika (UI), który składa się z poleceń menu i paski narzędzi. Wtyczka do kontroli źródła implementuje funkcji kontroli źródła.  
  
## <a name="source-control-plug-in-resources"></a>Zasoby dotyczące wtyczki kontroli źródła  
 Wtyczki kontroli źródła zawiera zasoby, aby utworzyć i połączyć aplikację versioning [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE. Wtyczki kontroli źródła, zawiera specyfikację interfejsu API, które muszą być zaimplementowane przez wtyczki kontroli źródła, tak aby mogła zostać włączona w [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE. Zawiera również przykładowy kod (napisanego w języku C++), który implementuje źródło szkielet kontroli wtyczki ilustrujące implementacji podstawowe funkcje zgodne z interfejsem API wtyczki kontroli źródła.  
  
 Specyfikacja interfejsu API wtyczki kontroli źródła umożliwia korzystanie z dowolnego systemu kontroli źródła wybranych przez użytkownika, w przypadku utworzenia kontroli źródła DLL wymagany zestaw funkcji realizowanych zgodnie z interfejsu API wtyczki kontroli źródła.  
  
## <a name="components"></a>Składniki  
 Pakietu karty kontroli źródła na diagramie jest składnikiem, IDE, który tłumaczy żądania użytkownika dla operacji kontroli źródła na wywołanie funkcji obsługiwanych przez wtyczka do kontroli źródła. W tym celu IDE i wtyczka do kontroli źródła może być skuteczne okno dialogowe, które przekazuje informacje i z powrotem między IDE i wtyczki. Dla tego okna dialogowego została wykonana oba muszą używać tego samego języka. API wtyczki kontroli źródła opisane w tej dokumentacji jest wspólnego słownika dla tej wymiany.  
  
 ![Diagram architektury kontroli kodu źródłowego](../../extensibility/internals/media/vs-sccsdk-plug-in-arch.gif "vs_sccsdk_plug_in_arch")  
Diagram architektury przedstawiający interakcji między VS i kontroli źródła wtyczek  
  
 Jak pokazano na diagramie architektury [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] powłoki, oznaczone jako powłoki VS shell na diagramie obsługuje skojarzone składniki, takie jak edytory i Eksplorator rozwiązań i projekty robocze użytkownika. Źródłowy pakiet karty Kontrola obsługuje interakcje między IDE i wtyczka do kontroli źródła. Pakiet karty kontroli źródła zawiera swój własny kontroli źródła interfejsu użytkownika. Jest najwyższego poziomu interfejsu użytkownika, który użytkownik wchodzi w interakcję z celu inicjowania i zdefiniuj zakres operacji kontroli źródła.  
  
 Wtyczka do kontroli źródła może mieć własny interfejs użytkownika może składać się z dwóch części, jak pokazano na rysunku. Pole o nazwie "Dostawca interfejsu użytkownika" reprezentuje niestandardowe elementy interfejsu użytkownika, twórcy wtyczki kontroli źródła, podane. Są one widoczne bezpośrednio przez wtyczka do kontroli źródła, gdy użytkownik wywołuje operacja kontroli źródła zaawansowane. Pole o nazwie "Pomocnika interfejsu użytkownika" to zestaw funkcji kontroli źródła wtyczek interfejsu użytkownika, które pośrednio są wywoływane za pośrednictwem środowiska IDE. Wtyczka do kontroli źródła przekazuje komunikaty dotyczące interfejsu użytkownika do środowiska IDE, za pomocą funkcji wywołania zwrotnego specjalne dostarczane przez środowisko IDE. Pomocnik interfejs użytkownika ułatwia Bezproblemowa integracja z IDE (często z **zaawansowane** przycisku) i w ten sposób zapewnia bardziej ujednolicone środowisko użytkownika końcowego.  
  
 Wtyczka do kontroli źródła nie może wprowadzać zmian do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] powłoki i w związku z tym, do pakietu karty kontroli źródła lub źródło kontroli interfejsu użytkownika IDE. Musi stworzyć maksymalnego wykorzystania elastyczności oferowanej za pośrednictwem implementacji różnych funkcji API wtyczki kontroli źródła, które przyczyniają się do zintegrowane środowisko użytkownika końcowego. Dokumentacja części dokumentacji interfejsu API wtyczki kontroli źródła zawiera informacje o niektóre funkcje wtyczki kontroli źródła zaawansowane. Aby wykorzystać te funkcje, wtyczka do kontroli źródła należy zadeklarować zaawansowane możliwości środowiska IDE podczas inicjowania i musi on implementować określone funkcje zaawansowane, dla każdej funkcji.  
  
## <a name="see-also"></a>Zobacz też  
 [Wtyczek kontroli kodu źródłowego](../../extensibility/source-control-plug-ins.md)   
 [Słownik](../../extensibility/source-control-plug-in-glossary.md)   
 [Tworzenie wtyczki kontroli kodu źródłowego](../../extensibility/internals/creating-a-source-control-plug-in.md)

