---
title: Trwałość projektu | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, projects
- projects [Visual Studio SDK], persistance
ms.assetid: 42907bcf-4e27-46bd-a8cb-01c2ccd2bde5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 10a9cde91c0181fbfefbaa353c7c3702f4b36819
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706457"
---
# <a name="project-persistence"></a>Trwałość projektu
Trwałość jest kluczowym czynnikiem projektowym dla projektu. Większość projektów używa elementów projektu, które reprezentują pliki; [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] obsługuje również projekty, których dane nie są oparte na plikach. Zarówno pliki należące do projektu, jak i plik projektu muszą być utrwalone. IDE instruuje projekt, aby zapisać siebie lub elementu projektu.

 Szablony dla projektów są przekazywane do fabryki projektów. Szablony powinny obsługiwać inicjowanie wszystkich elementów projektu zgodnie z wymaganiami określonego typu projektu. Szablony te mogą być później zapisywane jako pliki projektu i zarządzane przez IDE za pośrednictwem rozwiązania. Aby uzyskać więcej informacji, zobacz [Tworzenie wystąpień projektu przy użyciu fabryk](../../extensibility/internals/creating-project-instances-by-using-project-factories.md) i [rozwiązań](../../extensibility/internals/solutions-overview.md)projektu .

 Elementy projektu mogą być oparte na plikach lub nie oparte na plikach:

- Elementy oparte na plikach mogą być lokalne lub zdalne. W projektach sieci Web w języku C#, na przykład połączenia z plikami w systemie zdalnym utrzymują się lokalnie, podczas gdy same pliki utrzymują się w systemie zdalnym.

- Elementy nieoparte na plikach mogą zapisywać elementy w bazie danych lub repozytorium.

## <a name="commit-models"></a>Modele zatwierdzania
 Po podjęciu decyzji, gdzie znajdują się elementy projektu, należy wybrać odpowiedni model zatwierdzania. Na przykład w modelu opartym na plikach z plikami lokalnymi każdy projekt można zapisać autonomicznie. W modelu repozytorium można zapisać kilka elementów w jednej transakcji. Aby uzyskać więcej informacji, zobacz [Decyzje dotyczące projektu](../../extensibility/internals/project-type-design-decisions.md).

 Aby określić rozszerzenia nazw plików, projekty implementują <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> interfejs, który zawiera informacje umożliwiające klientowi obiektu zaimplementowanie okna dialogowego Zapisz **jako** — czyli wypełnienia listy rozwijanej Zapisz jako **typ** i zarządzania początkowym rozszerzeniem nazwy pliku.

 IDE wywołuje `IPersistFileFormat` interfejs w projekcie, aby wskazać, że projekt powinien utrwalić swoje elementy projektu, stosownie do przypadku. W związku z tym obiekt jest właścicielem wszystkich aspektów jego pliku i formatu. Obejmuje to nazwę formatu obiektu.

 W przypadku, gdy elementy `IPersistFileFormat` nie są plikami, jest nadal jak elementy nie oparte na plikach są zachowywane. Pliki projektu, takie jak pliki [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] .vbp dla projektów [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] lub .vcproj plików dla projektów, muszą być również utrwalone.

 W przypadku akcji zapisywania IDE sprawdza uruchomionej tabeli dokumentów (RDT), <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> a <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> hierarchia przekazuje polecenia do interfejsów i interfejsów. Metoda <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.IsItemDirty%2A> jest zaimplementowana w celu ustalenia, czy element został zmodyfikowany. Jeśli element ma, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.SaveItem%2A> metoda jest zaimplementowana, aby zapisać zmodyfikowany element.

 Metody w `IVsPersistHierarchyItem2` interfejsie są używane do określenia, czy element może być ponownie załadowany i, jeśli element może być, aby go ponownie załadować. Ponadto <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IgnoreItemFileChanges%2A> metoda może być zaimplementowana, aby spowodować, że zmienione elementy mają zostać odrzucone bez zapisywania.

## <a name="see-also"></a>Zobacz też
- [Lista kontrolna: tworzenie nowych typów projektów](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Tworzenie wystąpień projektów przy użyciu fabryk projektów](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
