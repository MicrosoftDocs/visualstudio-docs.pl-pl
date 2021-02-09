---
title: Tworzenie typów projektów | Microsoft Docs
description: Dowiedz się, jak rozciągnąć program Visual Studio przez projektowanie, tworzenie i rejestrowanie nowego typu projektu, który obsługuje zadania programistyczne.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, new
- projects [Visual Studio SDK], new project types
ms.assetid: bdb2d22e-d622-450c-bb2d-98152a745fcf
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 26e616ac9862f6a077115c23bef426a94ab3ecbf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99903032"
---
# <a name="create-project-types"></a>Tworzenie typów projektów
Można ją rozciągnąć [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , tworząc nowy typ projektu. Aby utworzyć nowy typ projektu, należy zapoznać się z kilkoma pojęciami i wykonać kilka kroków. W poniższych tematach przedstawiono omówienie sposobu tworzenia typów projektów.

## <a name="in-this-section"></a>W tej sekcji
- [Decyzje projektowe typu projektu](../../extensibility/internals/project-type-design-decisions.md)

 Omawia element, trwałość pliku projektu i decyzje projektowe dotyczące zaangażowania, które należy wykonać przed utworzeniem nowego typu projektu.

- [Lista kontrolna: tworzenie nowych typów projektów](../../extensibility/internals/checklist-creating-new-project-types.md)

 Zawiera przegląd czynności, które należy wykonać, aby utworzyć nowy typ projektu, który obsługuje takie zadania programistyczne jak edytowanie kodu i kompilowanie, kompilowanie, debugowanie i wdrażanie aplikacji w projekcie.

- [Tworzenie wystąpień projektu przy użyciu fabryk projektów](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)

 Zawiera informacje o sposobach dostarczania i używania fabryki projektu do tworzenia wystąpień nowego projektu.

- [Zarejestruj typ projektu](../../extensibility/internals/registering-a-project-type.md)

 Zapewnia przykłady kodu instrukcji z rejestru, które udostępniają domyślne ścieżki i dane, oraz tabelę zawierającą wpisy ze skryptu rejestru dla każdej instrukcji.

- [Trwałość projektu](../../extensibility/internals/project-persistence.md)

 W tym artykule omówiono `IPersistFileFormat` sposób utrwalania zarówno obiektów projektu, jak i nieopartych na plikach.

- [Korzystanie z programu MSBuild](../../extensibility/internals/using-msbuild.md)

 Opisuje, w jaki sposób typ projektu może używać [!INCLUDE[vstecmsbuild](../../extensibility/internals/includes/vstecmsbuild_md.md)] aparatu kompilacji, aby umożliwić użytkownikom Kompilowanie z [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] i w wierszu polecenia.

## <a name="related-sections"></a>Sekcje pokrewne
- [Obsługa narzędzi do przeglądania symboli](../../extensibility/internals/supporting-symbol-browsing-tools.md)

 Wyjaśnia architekturę narzędzi do wyświetlania kodu, takich jak okno **Przeglądarka obiektów** i **Widok klasy** . Opisuje interfejsy i metody, które są używane do implementowania przeglądania obiektów w pakietu VSPackage.

- [Dodaj projekty i szablony elementów projektu](../../extensibility/internals/adding-project-and-project-item-templates.md)

 W tym artykule omówiono znaczenie, w których projekty są odtwarzane w celu określenia edytora, który jest używany podczas otwierania elementu projektu i sposobu manipulowania zasobami projektu.

- [Zainstaluj pakietów VSPackage z Instalator Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)

 Pokazuje, w jaki sposób nadawać swoją pakietu VSPackage własną unikatową tożsamość oraz jak otoczyć biblioteki dll pakietu VSPackage i inne informacje w pakiecie Instalator Windows (*. Plik MSI* ) do wdrożenia dla klientów.

- [Hierarchie w programie Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)

 Opisuje sposób wyświetlania [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] hierarchii i adresów.

- [Pakiety VSPackage](../../extensibility/internals/vspackages.md)

 Zawiera omówienie pakietu VSPackage, instalowalnego obiektu COM, który rozszerza [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] środowisko i omawia sposób implementacji własnych pakietu VSPackage.

- [Typy projektów](../../extensibility/internals/project-types.md)

 W tym artykule omówiono sposób używania projektów do modyfikowania kodu, kompilowania i kompilowania kodu oraz uruchamiania i debugowania kodu oraz zawiera linki do szczegółowych tematów dotyczących sposobu tworzenia typów projektów.
