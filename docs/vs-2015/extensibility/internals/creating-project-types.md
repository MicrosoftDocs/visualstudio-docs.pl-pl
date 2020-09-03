---
title: Tworzenie typów projektów | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types, new
- projects [Visual Studio SDK], new project types
ms.assetid: bdb2d22e-d622-450c-bb2d-98152a745fcf
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bbe65d1615603e4dc7546dbfe3530093c62528e5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155030"
---
# <a name="creating-project-types"></a>Tworzenie typów projektów
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Można ją rozciągnąć [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , tworząc nowy typ projektu. Aby utworzyć nowy typ projektu, należy zapoznać się z kilkoma pojęciami i wykonać kilka kroków. W poniższych tematach przedstawiono omówienie sposobu tworzenia typów projektów.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Decyzje projektowe dotyczące typów projektów](../../extensibility/internals/project-type-design-decisions.md)  
 Omawia element, trwałość pliku projektu i decyzje projektowe dotyczące zaangażowania, które należy wykonać przed utworzeniem nowego typu projektu.  
  
 [Lista kontrolna: Tworzenie nowych typów projektów](../../extensibility/internals/checklist-creating-new-project-types.md)  
 Zawiera przegląd czynności, które należy wykonać, aby utworzyć nowy typ projektu, który obsługuje zadania programistyczne jako edytujące kod i kompilowanie, kompilowanie, debugowanie i wdrażanie aplikacji w projekcie.  
  
 [Tworzenie wystąpień projektów przy użyciu fabryk projektów](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)  
 Zawiera informacje o sposobach dostarczania i używania fabryki projektu do tworzenia wystąpień nowego projektu.  
  
 [Rejestrowanie typu projektu](../../extensibility/internals/registering-a-project-type.md)  
 Zapewnia przykłady kodu instrukcji z rejestru, które udostępniają domyślne ścieżki i dane, oraz tabelę zawierającą wpisy ze skryptu rejestru dla każdej instrukcji.  
  
 [Trwałość projektu](../../extensibility/internals/project-persistence.md)  
 W tym artykule omówiono `IPersistFileFormat` sposób utrwalania zarówno obiektów projektu, jak i nieopartych na plikach.  
  
 [Korzystanie z programu MSBuild](../../extensibility/internals/using-msbuild.md)  
 Opisuje, w jaki sposób typ projektu może używać [!INCLUDE[vstecmsbuild](../../includes/vstecmsbuild-md.md)] aparatu kompilacji, aby umożliwić użytkownikom Kompilowanie z [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] i w wierszu polecenia.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Obsługa narzędzi do przeglądania symboli](../../extensibility/internals/supporting-symbol-browsing-tools.md)  
 Wyjaśnia architekturę narzędzi do wyświetlania kodu, takich jak okno **Przeglądarka obiektów** i **Widok klasy** . Opisuje interfejsy i metody, które są używane do implementowania przeglądania obiektów w pakietu VSPackage.  
  
 [Dodawanie szablonów projektów i elementów projektu](../../extensibility/internals/adding-project-and-project-item-templates.md)  
 W tym artykule omówiono znaczenie, w których projekty są odtwarzane w celu określenia edytora, który jest używany podczas otwierania elementu projektu i sposobu manipulowania zasobami projektu.  
  
 [Instalowanie pakietów VSPackage przy użyciu Instalatora Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)  
 Pokazuje, w jaki sposób nadawać swoją pakietu VSPackage własną unikatową tożsamość oraz jak otoczyć biblioteki dll pakietu VSPackage i inne informacje w pakiecie Instalator Windows (. Plik MSI) do wdrożenia dla klientów.  
  
 [Hierarchie w programie Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)  
 Opisuje sposób wyświetlania [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] hierarchii i adresów.  
  
 [Pakiety VSPackage](../../extensibility/internals/vspackages.md)  
 Zawiera omówienie pakietu VSPackage, instalowalnego obiektu COM, który rozszerza [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] środowisko i omawia sposób implementacji własnych pakietu VSPackage.  
  
 [Typy projektów](../../extensibility/internals/project-types.md)  
 W tym artykule omówiono sposób używania projektów do modyfikowania kodu, kompilowania i kompilowania kodu oraz uruchamiania i debugowania kodu oraz zawiera linki do szczegółowych tematów dotyczących sposobu tworzenia typów projektów.
