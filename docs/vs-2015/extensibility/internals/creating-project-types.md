---
title: Tworzenie typów projektów | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54801950"
---
# <a name="creating-project-types"></a>Tworzenie typów projektów
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Możesz rozszerzyć [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , tworząc nowy typ projektu. Aby utworzyć nowy typ projektu, należy zrozumieć kilka koncepcji i wykonać kilka czynności. Omówienie sposobu tworzenia typów projektów można znaleźć w następujących tematach.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Decyzje projektowe dotyczące typów projektów](../../extensibility/internals/project-type-design-decisions.md)  
 W tym artykule omówiono elementów, trwałość pliku projektu i decyzje projektowe mechanika zobowiązania, które należy podjąć przed utworzeniem nowego typu projektu.  
  
 [Lista kontrolna: Tworzenie nowych typów projektów](../../extensibility/internals/checklist-creating-new-project-types.md)  
 Omówienie kroków, które należy wykonać, aby utworzyć nowy typ projektu, który obsługuje zadań programistycznych jako edytowanie kodu i kompilowanie, tworzenie, debugowanie i wdrażanie aplikacji w projekcie.  
  
 [Tworzenie wystąpień projektów przy użyciu fabryk projektów](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)  
 Zawiera informacje dotyczące sposobu i fabrykę projekt do tworzenia wystąpień tego nowego projektu.  
  
 [Rejestrowanie typu projektu](../../extensibility/internals/registering-a-project-type.md)  
 Zawiera przykłady kodu instrukcji z rejestru, które zapewniają domyślnych ścieżek i danych i tabeli, które zawierają wpisy z rejestru skryptu dla każdej instrukcji.  
  
 [Trwałość projektu](../../extensibility/internals/project-persistence.md)  
 Omawia stosowanie `IPersistFileFormat` można utrwalić zarówno w plikach, jak i obiekty nie opartych na pliku projektu.  
  
 [Korzystanie z programu MSBuild](../../extensibility/internals/using-msbuild.md)  
 W tym artykule opisano, jak przy użyciu typu projektu [!INCLUDE[vstecmsbuild](../../includes/vstecmsbuild-md.md)] aparatu, aby umożliwić użytkownikom opracowano na podstawie kompilacji [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] i w wierszu polecenia.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Obsługa narzędzi do przeglądania symboli](../../extensibility/internals/supporting-symbol-browsing-tools.md)  
 Wyjaśnia architektury kodu, takich jak wyświetlanie narzędzia **przeglądarki obiektów** i **Widok klas** okna. W tym artykule opisano interfejsy i metody, które są używane do implementowania przeglądania obiektów w VSPackage.  
  
 [Dodawanie projektu i szablonów elementów projektu](../../extensibility/internals/adding-project-and-project-item-templates.md)  
 W tym artykule omówiono znaczenia pełniące projektów w określaniu, który Edytor służy po otwarciu elementu projektu i jak mogą być zmieniane zasobów projektu.  
  
 [Instalowanie pakietów VSPackage przy użyciu Instalatora Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)  
 Pokazuje udzielanie Twojego pakietu VSPackage własną unikatową tożsamość i jak opakowywać Twojego pakietu VSPackage bibliotek DLL i inne informacje w pakiet Instalatora Windows (. Plik MSI) dla wdrożenia dla klientów.  
  
 [Hierarchie w programie Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)  
 W tym artykule opisano sposób [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] hierarchie widoków i adresów.  
  
 [Pakiety VSPackage](../../extensibility/internals/vspackages.md)  
 Omówienie pakietu VSPackage, możliwe do zainstalowania obiektu COM, który rozszerza [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] środowiska i w tym artykule omówiono sposób implementacji własnych pakietu VSPackage.  
  
 [Typy projektów](../../extensibility/internals/project-types.md)  
 W tym artykule omówiono sposób używania projektów można zmodyfikować kod, Kompiluj i kompilowanie kodu i uruchamiać oraz debugować kod i zawiera łącza do szczegółowych tematów dotyczących sposobu tworzenia typów projektów.
