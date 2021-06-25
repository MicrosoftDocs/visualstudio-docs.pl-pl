---
title: Stan trwały projektu | Microsoft Docs
description: Dowiedz się więcej na temat trwałości w projekcie, w tym użycia formatu IPersistFileFormat do utrwalania zarówno obiektów projektu opartych na plikach, jak i innych.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- persistence, projects
- projects [Visual Studio SDK], persistance
ms.assetid: 42907bcf-4e27-46bd-a8cb-01c2ccd2bde5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 17b9fc40a93a926fde5edc28e93f7751b919611c
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903649"
---
# <a name="project-persistence"></a>Trwałość projektu
Trwałość jest kluczową kwestią podczas projektowania projektu. Większość projektów używa elementów projektu reprezentujących pliki; [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Obsługuje również projekty, których dane nie są oparte na plikach. Zarówno pliki należące do projektu, jak i plik projektu muszą być utrwalone. Ide nakazuje projektowi zapisanie samego siebie lub elementu projektu.

 Szablony projektów są przekazywane do fabryki projektów. Szablony powinny obsługiwać inicjowanie wszystkich elementów projektu zgodnie z wymaganiami określonego typu projektu. Te szablony mogą być później zapisywane jako pliki projektu i zarządzane przez ideę za pośrednictwem rozwiązania. Aby uzyskać więcej informacji, zobacz [Creating Project Instances By Using Project Factories](../../extensibility/internals/creating-project-instances-by-using-project-factories.md) and Solutions (Tworzenie wystąpień projektu przy użyciu fabryk projektów i [rozwiązań).](../../extensibility/internals/solutions-overview.md)

 Elementy projektu mogą być oparte na plikach lub nie na plikach:

- Elementy oparte na plikach mogą być lokalne lub zdalne. Na przykład w projektach sieci Web w języku C# połączenia z plikami w systemie zdalnym są utrwalane lokalnie, a same pliki są utrwalane w systemie zdalnym.

- Elementy inne niż oparte na plikach mogą zapisywać elementy w bazie danych lub repozytorium.

## <a name="commit-models"></a>Zatwierdzanie modeli
 Po podjęciu decyzji o tym, gdzie znajdują się elementy projektu, należy wybrać odpowiedni model zatwierdzania. Na przykład w modelu opartym na plikach z plikami lokalnymi każdy projekt można zapisać autonomicznie. W modelu repozytorium można zapisać kilka elementów w jednej transakcji. Aby uzyskać więcej informacji, zobacz [Project Type Design Decisions (Decyzje projektowe dotyczące typu projektu).](../../extensibility/internals/project-type-design-decisions.md)

 Aby określić rozszerzenia nazw plików, projekty implementują interfejs, który udostępnia informacje umożliwiające klientowi obiektu zaimplementowanie okna dialogowego Zapisz jako , czyli wypełnienie listy rozwijanej Zapisz jako typ i zarządzanie początkowym rozszerzeniem nazwy <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> pliku.  

 Ide wywołuje interfejs w projekcie, aby wskazać, że projekt powinien `IPersistFileFormat` utrwalić elementy projektu zgodnie z potrzebami. W związku z tym obiekt jest właścicielem wszystkich aspektów jego pliku i formatu. Obejmuje to nazwę formatu obiektu.

 W przypadku, gdy elementy nie są plikami, nadal jest sposób utrwalania elementów `IPersistFileFormat` nieo opartych na plikach. Pliki projektu, takie jak pliki vbp dla projektów lub [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] pliki vcproj dla [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] projektów, również muszą być utrwalane.

 W przypadku akcji zapisywania ide sprawdza tabelę uruchomionych dokumentów (RDT), a hierarchia przekazuje polecenia do <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> interfejsów i . Metoda <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.IsItemDirty%2A> jest implementowane w celu określenia, czy element został zmodyfikowany. Jeśli element ma, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.SaveItem%2A> metoda jest implementowane w celu zapisania zmodyfikowanego elementu.

 Metody w interfejsie służą do określania, czy można ponownie załadować element i, jeśli element może `IVsPersistHierarchyItem2` być, aby go ponownie załadować. Ponadto można zaimplementować metodę , aby spowodować odrzucenie zmienionych elementów <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IgnoreItemFileChanges%2A> bez ich zapisania.

## <a name="see-also"></a>Zobacz też
- [Lista kontrolna: Tworzenie nowych typów projektów](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Tworzenie wystąpień projektów przy użyciu fabryk projektów](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
