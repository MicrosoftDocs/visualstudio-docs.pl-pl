---
title: Rejestrowanie szablonów projektów i elementów | Microsoft Docs
description: Dowiedz się, Visual Studio używa informacji rejestracyjnych dla typów projektów, aby określić, co ma być wyświetlane w oknach dialogowych Dodawanie nowego projektu i Dodawanie nowego elementu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- projects [Visual Studio SDK], adding items
- registry, Add New Item dialog box
- Add New Item dialog box
- Add New Project dialog box
- registry, Add New Project dialog box
ms.assetid: 6b909f93-d7f5-4aec-81c6-ee9ff0f31638
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8b60022c6adf65d0b0d60d32b4ad7ae72067726d
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905635"
---
# <a name="registering-project-and-item-templates"></a>Rejestrowanie szablonów projektów i elementów
Typy projektów muszą rejestrować katalogi, w których znajdują się ich szablony projektów i elementów projektu. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Używa informacji rejestracyjnych skojarzonych z typami projektów, aby określić, co ma być wyświetlane w oknach dialogowych Dodaj nowy **projekt** i Dodaj nowy element. 

 Aby uzyskać więcej informacji na temat szablonów, zobacz [Dodawanie szablonów projektów i elementów projektu](../../extensibility/internals/adding-project-and-project-item-templates.md).

## <a name="registry-entries-for-projects"></a>Wpisy rejestru dla projektów
 Poniższe przykłady pokazują wpisy rejestru w obszarze HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\ < *Version*>. W towarzyszących tabelach wyjaśniono elementy używane w przykładach.

```
[Projects\{ProjectGUID}]
@="MyProjectType"
"DisplayName"="#2"
"Package"="{VSPackageGUID}"
"ProjectTemplatesDir"="C:\\MyProduct\\MyProjectTemplates"
```

|Nazwa|Typ|Opis|
|----------|----------|-----------------|
|@|REG_SZ|Domyślna nazwa projektów tego rodzaju.|
|Nazwa wyświetlana|REG_SZ|Identyfikator zasobu nazwy, która ma zostać pobrana z biblioteki DLL satelicie zarejestrowanej w obszarze Pakiety.|
|Pakiet|REG_SZ|Identyfikator klasy pakietu zarejestrowanego w obszarze Pakiety.|
|ProjectTemplatesDir|REG_SZ|Domyślna ścieżka plików szablonu projektu. Pliki szablonu projektu są wyświetlane przez **szablon Nowy** projekt.|

### <a name="registering-item-templates"></a>Rejestrowanie szablonów elementów
 Należy zarejestrować katalog, w którym są przechowywane szablony elementów.

```
[Projects\{ProjectGUID}\AddItemTemplates\TemplateDirs\{VSPackageGUID}\1]
@="#7"
"TemplatesDir"="C:\\MyProduct\\MyProjectItemTemplates "
"TemplatesLocalizedSubDir"="#10"
"SortPriority"=dword:00000064
```

| Nazwa | Typ | Opis |
|--------------------------|-----------| - |
| @ | REG_SZ | Identyfikator zasobu dla pozycji Dodaj szablony elementów. |
| TemplatesDir | REG_SZ | Ścieżka elementów projektu wyświetlanych w oknie dialogowym Kreatora **dodawania nowego** elementu. |
| TemplatesLocalizedSubDir | REG_SZ | Identyfikator zasobu ciągu, który nazwa podkatalogu TemplatesDir, który zawiera zlokalizowane szablony. Ponieważ ładuje zasób ciągu z bibliotek DLL satelicie, jeśli je masz, każda biblioteka DLL satelicie może zawierać inną nazwę [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] zlokalizowanego podkatalogu. |
| SortPriority | REG_DWORD | Ustaw pozycję SortPriority, aby określić kolejność wyświetlania szablonów w oknie dialogowym Dodawanie **nowego** elementu. Większe wartości SortPriority są wyświetlane wcześniej na liście szablonów. |

### <a name="registering-file-filters"></a>Rejestrowanie filtrów plików
 Opcjonalnie można zarejestrować filtry, które [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] będą używane podczas monitowania o nazwy plików. Na przykład filtr [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] okna dialogowego **Otwieranie** pliku to:

 **Pliki Visual C# \* (cs, \* resx, \* settings, \* xsd, \* wsdl); \* . cs, \* .resx, \* .settings, \* .xsd, \* .wsdl)**

 Aby obsługiwać rejestrację wielu filtrów, każdy filtr jest rejestrowany we własnym podkluczu w obszarze HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\ < *Version*>\Projects \\ { \<*ProjectGUID*> }\Filters \\ < *Subkey*>. Nazwa podklucza jest dowolna; [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Ignoruje nazwę podklucza i używa tylko jego wartości.

 Możesz kontrolować konteksty, w których filtr jest używany, ustawiając flagi, jak pokazano w poniższej tabeli. Jeśli filtr nie ma ustawionych żadnych flag, zostanie on wymieniony po wspólnych  filtrach w oknie dialogowym Dodawanie istniejącego  elementu i oknie dialogowym Otwieranie pliku, ale nie będzie używany w oknie dialogowym Znajdź w plikach. 

```
[Projects\{ProjectGUID}\Filters\MyLanguageFilter]
@="#3"
"CommonOpenFilesFilter"=dword:00000000
"CommonFindFilesFilter"=dword:00000000
"FindInFilesFilter"=dword:00000000
"NotOpenFileFilter"=dword:00000000
"NotAddExistingItemFilter"=dword:00000000
"SortPriority"=dword:00000064
```

|Nazwa|Typ|Opis|
|----------|----------|-----------------|
|CommonFindFilesFilter|REG_DWORD|Sprawia, że filtr jest jednym z typowych filtrów w **oknie dialogowym Znajdowanie w** plikach. Typowe filtry są wyświetlane na liście filtrów przed filtrami, które nie są oznaczone jako typowe.|
|CommonOpenFilesFilter|REG_DWORD|Sprawia, że filtr jest jednym z typowych filtrów w **oknie dialogowym Otwieranie** pliku. Typowe filtry są wyświetlane na liście filtrów przed filtrami, które nie są oznaczone jako typowe.|
|FindInFilesFilter|REG_DWORD|Wyświetla listę filtru po typowych filtrach w **oknie dialogowym Znajdź w** plikach.|
|NotOpenFileFilter|REG_DWORD|Wskazuje, że filtr nie jest używany w **oknie dialogowym Otwieranie** pliku.|
|NotAddExistingItemFilter|REG_DWORD|Wskazuje, że filtr nie jest używany w **oknie dialogowym Dodawanie istniejącego** elementu.|
|SortPriority|REG_DWORD|Ustaw ustawienie SortPriority, aby określać kolejność wyświetlania filtrów. Większe wartości SortPriority są wyświetlane wcześniej na liście filtrów.|

## <a name="directory-structure"></a>Struktura katalogów
 Pakiet VSPackages może umieszczać pliki szablonów i foldery w dowolnym miejscu na dysku lokalnym lub zdalnym, o ile lokalizacja jest zarejestrowana za pośrednictwem zintegrowanego środowiska projektowego (IDE). Jednak w celu ułatwienia organizacji zalecamy następującą strukturę katalogów w ramach ścieżki instalacji produktu.

 \Templates

 \Projects (zawiera szablony projektów)

 \Applications

 \Components

 \ ...

 \ProjectItems (zawiera elementy projektu)

 \Class

 \Form

 \Web Page

 \HelperFiles (zawiera pliki używane w elementach projektów wieloplikowych)

 \WizardFiles

## <a name="see-also"></a>Zobacz też

- [Dodawanie szablonów projektów i elementów projektu](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [Kreatory](../../extensibility/internals/wizards.md)
- [Lokalizowanie aplikacji](../../ide/globalizing-and-localizing-applications.md)
- [Identyfikatory CATID obiektów, które są zwykle używane do rozszerzania projektów](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)
