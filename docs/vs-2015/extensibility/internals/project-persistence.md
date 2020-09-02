---
title: Trwałość projektu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- persistence, projects
- projects [Visual Studio SDK], persistance
ms.assetid: 42907bcf-4e27-46bd-a8cb-01c2ccd2bde5
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: abbcc1fc1048866ef790a4b6779ed15ef80a9be1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62429525"
---
# <a name="project-persistence"></a>Trwałość projektu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Trwałość jest kluczowym zagadnieniem projektowym dla projektu. Większość projektów używa elementów projektu, które reprezentują pliki; Program [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] obsługuje również projekty, których dane nie są oparte na plikach. Zarówno pliki należące do projektu, jak i plik projektu muszą zostać utrwalone. IDE instruuje projekt, aby zapisywał sam lub element projektu.  
  
 Szablony projektów są przesyłane do fabryki projektu. Szablony powinny obsługiwać inicjalizację wszystkich elementów projektu zgodnie z wymaganiami określonego typu projektu. Te szablony można później zapisać jako pliki projektu i zarządzać nimi za pomocą rozwiązania. Aby uzyskać więcej informacji, zobacz [Tworzenie wystąpień projektu przy użyciu fabryk projektów](../../extensibility/internals/creating-project-instances-by-using-project-factories.md) i [rozwiązań](../../extensibility/internals/solutions-overview.md).  
  
 Elementy projektu mogą być oparte na plikach lub nie na plikach:  
  
- Elementy oparte na plikach mogą być lokalne lub zdalne. Na przykład w projektach sieci Web w języku C# połączenia z plikami w systemie zdalnym są przechowywane lokalnie, podczas gdy pliki są przechowywane w systemie zdalnym.  
  
- Elementy, które nie są oparte na plikach, mogą zapisywać elementy w bazie danych lub repozytorium.  
  
## <a name="commit-models"></a>Zatwierdź modele  
 Po wybraniu miejsca, w którym znajdują się elementy projektu, należy wybrać odpowiedni model zatwierdzania. Na przykład w modelu opartym na plikach z lokalnymi plikami każdy projekt może być zapisywany autonomicznie. W modelu repozytorium można zapisać kilka elementów w jednej transakcji. Aby uzyskać więcej informacji, zobacz [decyzje projektowe typu projektu](../../extensibility/internals/project-type-design-decisions.md).  
  
 Aby określić rozszerzenia nazw plików, projekty implementują <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> interfejs, który zapewnia informacje umożliwiające klientowi obiektu zaimplementowanie okna dialogowego **Zapisywanie jako** , czyli wypełnienie listy rozwijanej **Zapisz jako typ** i zarządzanie początkowym rozszerzeniem nazwy pliku.  
  
 IDE wywołuje `IPersistFileFormat` interfejs w projekcie, aby wskazać, że projekt powinien utrwalać elementy projektu, zgodnie z potrzebami. W związku z tym obiekt jest właścicielem wszystkich aspektów jego pliku i formatu. Obejmuje to nazwę formatu obiektu.  
  
 W przypadku, gdy elementy nie są plikami, `IPersistFileFormat` nadal są utrwalane elementy, które nie znajdują się na plikach. Pliki projektu, takie jak pliki. vbp dla projektów [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] lub pliki VCPROJ dla [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] projektów, również muszą być utrwalone.  
  
 W przypadku akcji zapisywania IDE bada uruchomioną tabelę dokumentu (RDT), a hierarchia przekazuje polecenia do <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> interfejsów. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.IsItemDirty%2A>Metoda jest zaimplementowana w celu ustalenia, czy element został zmodyfikowany. Jeśli element ma, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.SaveItem%2A> Metoda jest zaimplementowana w celu zapisania zmodyfikowanego elementu.  
  
 Metody w `IVsPersistHierarchyItem2` interfejsie służą do określenia, czy można ponownie załadować element i, jeśli element może być, aby go załadować. Ponadto <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IgnoreItemFileChanges%2A> Metoda może być implementowana, aby spowodować odrzucenie zmienionych elementów bez zapisywania.  
  
## <a name="see-also"></a>Zobacz też  
 [Lista kontrolna: tworzenie nowych typów projektów](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Tworzenie wystąpień projektów przy użyciu fabryk projektów](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
