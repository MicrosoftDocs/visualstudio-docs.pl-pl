---
title: Trwałość projektu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, projects
- projects [Visual Studio SDK], persistance
ms.assetid: 42907bcf-4e27-46bd-a8cb-01c2ccd2bde5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a95c919de9b87ed1782cbdcb029efbf191958f5a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725462"
---
# <a name="project-persistence"></a>Trwałość projektu
Trwałość jest kluczowym zagadnieniem projektowym dla projektu. Większość projektów używa elementów projektu, które reprezentują pliki;  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] obsługuje również projekty, których dane nie są oparte na plikach. Zarówno pliki należące do projektu, jak i plik projektu muszą zostać utrwalone. IDE instruuje projekt, aby zapisywał sam lub element projektu.

 Szablony projektów są przesyłane do fabryki projektu. Szablony powinny obsługiwać inicjalizację wszystkich elementów projektu zgodnie z wymaganiami określonego typu projektu. Te szablony można później zapisać jako pliki projektu i zarządzać nimi za pomocą rozwiązania. Aby uzyskać więcej informacji, zobacz [Tworzenie wystąpień projektu przy użyciu fabryk projektów](../../extensibility/internals/creating-project-instances-by-using-project-factories.md) i [rozwiązań](../../extensibility/internals/solutions-overview.md).

 Elementy projektu mogą być oparte na plikach lub nie na plikach:

- Elementy oparte na plikach mogą być lokalne lub zdalne. Na przykład w projektach C#sieci Web w programie połączenia z plikami w systemie zdalnym są przechowywane lokalnie, podczas gdy pliki są przechowywane w systemie zdalnym.

- Elementy, które nie są oparte na plikach, mogą zapisywać elementy w bazie danych lub repozytorium.

## <a name="commit-models"></a>Zatwierdź modele
 Po wybraniu miejsca, w którym znajdują się elementy projektu, należy wybrać odpowiedni model zatwierdzania. Na przykład w modelu opartym na plikach z lokalnymi plikami każdy projekt może być zapisywany autonomicznie. W modelu repozytorium można zapisać kilka elementów w jednej transakcji. Aby uzyskać więcej informacji, zobacz [decyzje projektowe typu projektu](../../extensibility/internals/project-type-design-decisions.md).

 Aby określić rozszerzenia nazw plików, projekty implementują interfejs <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>, który zapewnia informacje umożliwiające klientowi obiektu zaimplementowanie okna dialogowego **Zapisywanie jako** , czyli wypełnienie listy rozwijanej **Zapisz jako typ** i zarządzanie początkowe rozszerzenie nazwy pliku.

 IDE wywołuje interfejs `IPersistFileFormat` w projekcie, aby wskazać, że projekt powinien utrwalać elementy projektu, zgodnie z potrzebami. W związku z tym obiekt jest właścicielem wszystkich aspektów jego pliku i formatu. Obejmuje to nazwę formatu obiektu.

 W przypadku, gdy elementy nie są plikami, `IPersistFileFormat` nadal są utrwalane elementy, które nie są oparte na plikach. Pliki projektu, takie jak pliki. vbp dla projektów [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] lub pliki VCPROJ dla projektów [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)], również muszą być utrwalone.

 W przypadku akcji zapisywania IDE bada uruchomioną tabelę dokumentu (RDT), a hierarchia przekazuje polecenia do <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> i interfejsów <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2>. Metoda <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.IsItemDirty%2A> jest zaimplementowana w celu ustalenia, czy element został zmodyfikowany. Jeśli element ma, Metoda <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.SaveItem%2A> jest zaimplementowana w celu zapisania zmodyfikowanego elementu.

 Metody interfejsu `IVsPersistHierarchyItem2` są używane do określenia, czy element może zostać ponownie załadowany i, jeśli element może być, w celu ponownego załadowania. Ponadto można zaimplementować metodę <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IgnoreItemFileChanges%2A>, aby spowodować odrzucenie zmienionych elementów bez zapisywania.

## <a name="see-also"></a>Zobacz także
- [Lista kontrolna: tworzenie nowych typów projektów](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Tworzenie wystąpień projektów przy użyciu fabryk projektów](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)