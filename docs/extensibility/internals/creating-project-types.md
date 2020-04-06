---
title: Tworzenie typów projektów | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, new
- projects [Visual Studio SDK], new project types
ms.assetid: bdb2d22e-d622-450c-bb2d-98152a745fcf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d2398b63b8cd52784252cfc764bb6c6a30e1accc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709067"
---
# <a name="create-project-types"></a>Tworzenie typów projektów
Można rozszerzyć, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tworząc nowy typ projektu. Aby utworzyć nowy typ projektu, należy zrozumieć kilka pojęć i wykonać kilka kroków. Poniższe tematy zawierają omówienie sposobu tworzenia typów projektów.

## <a name="in-this-section"></a>W tej sekcji
- [Decyzje dotyczące projektowania typu projektu](../../extensibility/internals/project-type-design-decisions.md)

 W tym artykule omówiono element, trwałość pliku projektu i zobowiązania mechanika projektowania decyzji, które należy podjąć przed utworzeniem nowego typu projektu.

- [Lista kontrolna: tworzenie nowych typów projektów](../../extensibility/internals/checklist-creating-new-project-types.md)

 Zawiera omówienie kroków, które należy wykonać, aby utworzyć nowy typ projektu, który obsługuje takie zadania programowania, jak edytowanie kodu i kompilowanie, tworzenie, debugowanie i wdrażanie aplikacji w projekcie.

- [Tworzenie wystąpień projektu przy użyciu fabryk projektów](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)

 Zawiera informacje dotyczące sposobu dostarczania i używania fabryki projektów do tworzenia wystąpień nowego projektu.

- [Rejestrowanie typu projektu](../../extensibility/internals/registering-a-project-type.md)

 Zawiera przykłady kodu instrukcji z rejestru, które zapewniają domyślne ścieżki i dane oraz tabelę zawierającą wpisy ze skryptu rejestru dla każdej instrukcji.

- [Trwałość projektu](../../extensibility/internals/project-persistence.md)

 W tym artykule omówiono użycie `IPersistFileFormat` do utrwalania obiektów projektu zarówno plików, jak i obiektów projektu nieopartych na plikach.

- [Korzystanie z programu MSBuild](../../extensibility/internals/using-msbuild.md)

 W tym artykule opisano, jak typ projektu można użyć aparatu [!INCLUDE[vstecmsbuild](../../extensibility/internals/includes/vstecmsbuild_md.md)] kompilacji, aby umożliwić użytkownikom tworzenie z [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] i w wierszu polecenia.

## <a name="related-sections"></a>Powiązane sekcje
- [Obsługa narzędzi do przeglądania symboli](../../extensibility/internals/supporting-symbol-browsing-tools.md)

 W tym artykule wyjaśniono architekturę narzędzi do wyświetlania kodu, takich jak **przeglądarka obiektów** i okno **Widok klasy.** W tym artykule opisano interfejsy i metody, które są używane do implementowania przeglądania obiektów w vsPackage.

- [Dodawanie szablonów elementów projektu i projektu](../../extensibility/internals/adding-project-and-project-item-templates.md)

 W tym artykule omówiono znaczenie, jakie projekty odgrywają w określaniu edytora, który jest używany podczas otwarcia elementu projektu i jak można manipulować zasobami projektu.

- [Instalowanie pakietów VSPackages za pomocą Instalatora Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)

 Pokazuje, jak nadać vsPackage własną unikatową tożsamość i jak zawinąć biblioteki DLL VSPackage i inne informacje w pakiecie Instalatora Windows (*. MSI)* do wdrożenia dla klientów.

- [Hierarchie w programie Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)

 Opisuje [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sposób widoków i adresów hierarchii.

- [Pakiety VSPackage](../../extensibility/internals/vspackages.md)

 Zawiera omówienie VSPackage, instalowalny obiekt COM, który rozszerza [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] środowisko i omówiono sposób implementacji własnego VSPackage.

- [Typy projektów](../../extensibility/internals/project-types.md)

 W tym artykule omówiono sposób używania projektów do modyfikowania kodu, kompilowania i kompilacji kodu oraz uruchamiania i debugowania kodu oraz zawiera łącza do szczegółowych tematów dotyczących tworzenia typów projektów.
