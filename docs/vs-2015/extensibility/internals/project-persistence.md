---
title: Trwałość projektu | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 9627170ad65906af1bc7930897c374504cae4552
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58152569"
---
# <a name="project-persistence"></a>Trwałość projektu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Trwałość stanowi kluczy dla Twojego projektu. Większość projektów używać elementów projektu, które reprezentują plików. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] obsługuje również projektów, których dane są inne niż oparte na pliku. Pliki należące do projektu i pliku projektu musi być utrwalone. IDE powoduje, że projekt, aby zapisać siebie lub elementu projektu.  
  
 Szablony projektów są przekazywane do fabryki projektu. Szablony powinien obsługiwać inicjowanie wszystkich elementów projektu, zgodnie z wymogami projektu określonego typu. Szablony te można później zapisywanych jako pliki projektu i zarządzane przez środowisko IDE, za pomocą rozwiązania. Aby uzyskać więcej informacji, zobacz [tworzenia projektu wystąpień, przy użyciu fabryk projektów](../../extensibility/internals/creating-project-instances-by-using-project-factories.md) i [rozwiązania](../../extensibility/internals/solutions-overview.md).  
  
 Elementy projektu może być oparte na plikach lub systemem plików:  
  
-   Elementy opartej na plikach może być lokalny lub zdalny. W projektach sieci Web w języku C# na przykład połączenia z plikami w systemie zdalnym są zachowywane lokalnie, a same pliki utrwalanie w systemie zdalnym.  
  
-   Elementy non-file-based zapisać elementy z bazą danych lub repozytorium.  
  
## <a name="commit-models"></a>Zatwierdź modeli  
 Po podjęciu decyzji o tym, gdzie znajdują się elementy projektu, musisz wybrać model odpowiednie zatwierdzenia. Na przykład w modelu opartych na plikach z lokalnymi plikami, każdy projekt zapisaniem autonomicznie. W modelu repozytorium można zapisać kilka elementów w ramach jednej transakcji. Aby uzyskać więcej informacji, zobacz [decyzje projektowe dotyczące typów projektu](../../extensibility/internals/project-type-design-decisions.md).  
  
 Aby określić rozszerzenia nazw plików, należy zaimplementować projektów <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> interfejs, który zawiera informacje umożliwiające klientowi implementacji obiektu **Zapisz jako** okno dialogowe — oznacza to, aby wypełnić **Zapisz jako typ**  listy rozwijanej listy i zarządzanie nimi rozszerzenie nazwy pliku początkowej.  
  
 Wywołania środowiska IDE `IPersistFileFormat` interfejsu na projekt, aby wskazać, że projekt ma utrwalić projekt elementy odpowiednio. W związku z tym obiekt jest właścicielem wszystkich aspektów jego plik i format. W tym nazwę formatu obiektu.  
  
 W przypadku, gdy elementy nie są plikami `IPersistFileFormat` jest nadal o tym, jak inne niż file-based elementy są zachowywane. Pliki, takie jak pliki .vbp dla projektu [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] projektów lub .vcproj pliki [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] projektów, musi również zostać utrwalone.  
  
 Zapisz akcje, IDE sprawdza uruchomionej tabeli dokumentu (Normalizacją) i hierarchii przekazuje polecenia, aby <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> i <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> interfejsów. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.IsItemDirty%2A> Metoda jest implementowana w celu ustalenia, czy element został zmieniony. Jeśli element ma, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.SaveItem%2A> metoda jest implementowana można zapisać zmodyfikowanego elementu.  
  
 Metody na `IVsPersistHierarchyItem2` interfejsu są używane do ustalenia, czy można ponownie załadować elementu, a także, jeśli element można załadować go ponownie. Ponadto <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IgnoreItemFileChanges%2A> metoda może być implementowany spowodować zmienionych elementów do usunięcia, bez zapisywany.  
  
## <a name="see-also"></a>Zobacz też  
 [Lista kontrolna: Tworzenie nowych typów projektów](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Tworzenie wystąpień projektów przy użyciu fabryk projektów](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
