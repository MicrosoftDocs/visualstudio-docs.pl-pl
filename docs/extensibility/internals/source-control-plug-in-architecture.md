---
title: Architektura wtyczki kontroli źródła | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, architecture
ms.assetid: 35351d4c-9414-409b-98fc-f2023e2426b7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6f06f023a46fc9bc417e9630613a716f8dd448d2
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723446"
---
# <a name="source-control-plug-in-architecture"></a>Architektura wtyczki kontroli kodu źródłowego
Można dodać obsługę kontroli źródła do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zintegrowanego środowiska programistycznego (IDE) przez implementację i dołączenie wtyczki kontroli źródła. IDE nawiązuje połączenie z wtyczką kontroli źródła za pomocą dobrze zdefiniowanego interfejsu API Plug-in kontroli źródła. Środowisko IDE udostępnia funkcje kontroli wersji systemu kontroli źródła, dostarczając interfejs użytkownika, który składa się z pasków narzędzi i poleceń menu. Wtyczka do kontroli źródła implementuje funkcje kontroli źródła.

## <a name="source-control-plug-in-resources"></a>Zasoby wtyczki kontroli źródła
 Wtyczka do kontroli źródła udostępnia zasoby, które ułatwiają tworzenie i łączenie aplikacji do obsługi wersji z [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE. Wtyczka do kontroli źródła zawiera specyfikację interfejsu API, która musi zostać wdrożona przez wtyczkę kontroli źródła, aby można było ją zintegrować z [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE. Zawiera również przykładowy kod (zapisywana C++), który implementuje szkieletową wtyczkę kontroli źródła pokazującą implementację istotnych funkcji zgodnych z interfejsem API kontroli źródła.

 Specyfikacja interfejsu API wtyczki kontroli źródła pozwala korzystać z dowolnego wybranego systemu kontroli źródła w przypadku utworzenia biblioteki DLL kontroli źródła z wymaganym zestawem funkcji wdrożonych zgodnie z interfejsem API kontroli źródła.

## <a name="components"></a>Składniki
 Pakiet adaptera kontroli źródła na diagramie jest składnikiem środowiska IDE, które tłumaczy żądanie użytkownika dotyczące operacji kontroli źródła na wywołanie funkcji obsługiwane przez wtyczkę kontroli źródła. W takim przypadku środowisko IDE i wtyczka do kontroli źródła muszą mieć efektywne okno dialogowe, które przekazuje informacje między IDE i wtyczką. W przypadku tego okna dialogowego te osoby muszą mówić do tego samego języka. Interfejs API dodatku plug-in kontroli źródła przedstawiony w tej dokumentacji to typowy słownik dla tej wymiany.

 ![Diagram architektury kontroli kodu źródłowego](../../extensibility/internals/media/vs_sccsdk_plug_in_arch.gif "vs_sccsdk_plug_in_arch") Diagram architektury przedstawiający interakcję między plug-in a i kontroli źródła

 Jak pokazano na diagramie architektury, powłoka [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], oznakowana jako powłoka VS na diagramie, hostuje projekty robocze użytkownika i skojarzone składniki, takie jak edytory i Eksplorator rozwiązań. Pakiet adaptera kontroli źródła obsługuje interakcję między środowiskiem IDE a wtyczką kontroli źródła. Pakiet adaptera kontroli źródła udostępnia własny interfejs użytkownika kontroli źródła. Jest to interfejs użytkownika najwyższego poziomu, z którym pracuje użytkownik, aby zainicjować i zdefiniować zakres operacji kontroli źródła.

 Wtyczka do kontroli źródła może mieć własny interfejs użytkownika, który może składać się z dwóch części, jak pokazano na rysunku. Pole o nazwie "interfejs użytkownika dostawcy" reprezentuje niestandardowe elementy interfejsu użytkownika, które są używane jako twórca wtyczki kontroli źródła. Są one wyświetlane bezpośrednio przez wtyczkę kontroli źródła, gdy użytkownik wywołuje zaawansowaną operację kontroli źródła. Pole o nazwie "pomocnik UI" to zestaw funkcji interfejsu użytkownika wtyczek kontroli źródła, które są pośrednio wywoływane przez IDE. Wtyczka do kontroli źródła przekazuje komunikaty związane z interfejsem użytkownika do środowiska IDE za pomocą specjalnych funkcji wywołania zwrotnego zapewnianych przez IDE. Interfejs użytkownika pomocnika ułatwia bezproblemowe integrację z IDE (często przy użyciu przycisku **zaawansowanego** ) i w ten sposób zapewnia bardziej ujednolicone środowisko użytkownika końcowego.

 Wtyczka do kontroli źródła nie może wprowadzać zmian w powłoce [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] i, w związku z tym, z pakietem lub interfejsem użytkownika kontroli źródła dostarczonym przez IDE. Musi ona mieć maksymalne użycie elastyczności oferowanej przez implementację różnych funkcji interfejsu API Plug-in kontroli źródła, które przyczyniają się do zintegrowanego środowiska użytkownika końcowego. Sekcja Reference dokumentacji interfejsu API dodatku plug-in kontroli źródła zawiera informacje o niektórych zaawansowanych możliwościach dodatku plug-in do kontroli źródła. Aby wykorzystać te funkcje, wtyczka do kontroli źródła musi zadeklarować zaawansowane możliwości środowiska IDE podczas inicjowania i musi zaimplementować określone funkcje zaawansowane dla każdej funkcji.

## <a name="see-also"></a>Zobacz także
- [Wtyczki kontroli źródła](../../extensibility/source-control-plug-ins.md)
- [Słownik](../../extensibility/source-control-plug-in-glossary.md)
- [Tworzenie wtyczki kontroli kodu źródłowego](../../extensibility/internals/creating-a-source-control-plug-in.md)