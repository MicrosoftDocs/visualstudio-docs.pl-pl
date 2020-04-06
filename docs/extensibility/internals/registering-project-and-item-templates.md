---
title: Rejestrowanie szablonów projektów i elementów | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], adding items
- registry, Add New Item dialog box
- Add New Item dialog box
- Add New Project dialog box
- registry, Add New Project dialog box
ms.assetid: 6b909f93-d7f5-4aec-81c6-ee9ff0f31638
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b64504c39b1fc3c4a82530b265cfd0e96832b4f2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705823"
---
# <a name="registering-project-and-item-templates"></a>Rejestrowanie szablonów projektów i elementów
Typy projektów muszą rejestrować katalogi, w których znajdują się ich szablony projektu i elementu projektu. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]używa informacji rejestracyjnych skojarzonych z typami projektów, aby określić, co ma być wyświetlane w oknach dialogowych **Dodawanie nowego projektu** i Dodawanie nowego **elementu.**

 Aby uzyskać więcej informacji o szablonach, zobacz [Dodawanie szablonów elementów projektu i projektu](../../extensibility/internals/adding-project-and-project-item-templates.md).

## <a name="registry-entries-for-projects"></a>Wpisy rejestru dla projektów
 Poniższe przykłady przedstawiają wpisy rejestru w obszarze HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\<*Version*>. W załączonych tabelach wyjaśniono elementy użyte w przykładach.

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
|DisplayName|REG_SZ|Identyfikator zasobu nazwy, która ma zostać pobrana z biblioteki DLL satelity zarejestrowanej w obszarze Pakiety.|
|Pakiet|REG_SZ|Identyfikator klasy pakietu zarejestrowanego w obszarze Pakiety.|
|ProjectTemplatesDir|REG_SZ|Domyślna ścieżka plików szablonu projektu. Pliki szablonu projektu są wyświetlane przez szablon **Nowy projekt.**|

### <a name="registering-item-templates"></a>Rejestrowanie szablonów elementów
 Należy zarejestrować katalog, w którym przechowywane są szablony towarów.

```
[Projects\{ProjectGUID}\AddItemTemplates\TemplateDirs\{VSPackageGUID}\1]
@="#7"
"TemplatesDir"="C:\\MyProduct\\MyProjectItemTemplates "
"TemplatesLocalizedSubDir"="#10"
"SortPriority"=dword:00000064
```

| Nazwa | Typ | Opis |
|--------------------------|-----------| - |
| @ | REG_SZ | Identyfikator zasobu dla szablonów dodaj elementy. |
| SzablonyDir | REG_SZ | Ścieżka elementów projektu wyświetlana w oknie dialogowym kreatora **Dodawanie nowego elementu.** |
| SzablonyLocalizedSubDir | REG_SZ | Identyfikator zasobu ciągu, który nazywa podkatalog TemplatesDir zawierający zlokalizowane szablony. Ponieważ [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ładuje zasób ciągów z bibliotek DLL sateli satelitarnych, jeśli je masz, każda biblioteka DLL satelity może zawierać inną zlokalizowaną nazwę podkatalogu. |
| SortPriority (SortPriority) | REG_DWORD | Ustaw sortpriority, aby zarządzać kolejnością wyświetlania szablonów w oknie dialogowym **Dodawanie nowego elementu.** Większe wartości sortpriority są wyświetlane wcześniej na liście szablonów. |

### <a name="registering-file-filters"></a>Rejestrowanie filtrów plików
 Opcjonalnie można zarejestrować filtry, które [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] używa, gdy monituje o nazwy plików. Na przykład [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] filtr okna dialogowego **Otwieranie pliku** to:

 **Pliki języka Visual\*C#\*( .cs, .resx,\*.settings,\*.xsd,\*.wsdl); \*.cs,\*.resx,\*.settings,\*.xsd,\*.wsdl)**

 Aby obsługiwać rejestrację wielu filtrów, każdy filtr jest zarejestrowany we własnym podkluczu w obszarze HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\<*Version*>\Projects\\{\<*ProjectGUID*>}\Filters\\<*Subkey*>. Nazwa podklucza jest dowolna; [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ignoruje nazwę podklucza i używa tylko jego wartości.

 Można kontrolować konteksty, w których filtr jest używany przez ustawienie flag, pokazane w poniższej tabeli. Jeśli filtr nie ma żadnych flag ustawionych, zostanie wyświetlony po popularnych filtrach w oknie dialogowym **Dodawanie istniejącego elementu** i w oknie dialogowym **Otwórz plik,** ale nie będzie używany w oknie dialogowym **Znajdowanie w plikach.**

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
|Filtr CommonFindFiles|REG_DWORD|Sprawia, że filtr jest jednym ze wspólnych filtrów w oknie dialogowym **Znajdowanie w plikach.** Typowe filtry są wyświetlane na liście filtrów, zanim filtry nie są oznaczone jako typowe.|
|Filtr CommonOpenFiles|REG_DWORD|Sprawia, że filtr jest jednym ze wspólnych filtrów w oknie dialogowym **Otwieranie pliku.** Typowe filtry są wyświetlane na liście filtrów, zanim filtry nie są oznaczone jako typowe.|
|Filtr Znajdź InFiles|REG_DWORD|Wyświetla listę filtrów po typowych filtrach w oknie dialogowym **Znajdowanie w plikach.**|
|NotOpenFileFilter|REG_DWORD|Wskazuje, że filtr nie jest używany w oknie dialogowym **Otwieranie pliku.**|
|NotAddExistingItemFilter|REG_DWORD|Wskazuje, że filtr nie jest używany w oknie dialogowym **Dodawanie istniejącego elementu.**|
|SortPriority (SortPriority)|REG_DWORD|Ustaw SortPriority, aby zarządzać kolejnością wyświetlania filtrów. Większe wartości sortpriority są wyświetlane wcześniej na liście filtrów.|

## <a name="directory-structure"></a>Struktura katalogów
 Pakiety VSPackages można umieścić pliki szablonów i folderów w dowolnym miejscu na dysku lokalnym lub zdalnym, tak długo, jak lokalizacja jest zarejestrowana za pośrednictwem zintegrowanego środowiska programistycznego (IDE). Jednak ze względu na łatwość organizacji zaleca się następującą strukturę katalogów w ścieżce instalacji produktu.

 \Szablony

 \Projekty (zawiera szablony projektów)

 \Aplikacje

 \Komponenty

 \ ...

 \ProjectItems (zawiera elementy projektu)

 \Klasa

 \Formularz

 \Strona sieci Web

 \HelperFiles (zawiera pliki używane w elementach projektu wieloplikowego)

 \WizardFiles

## <a name="see-also"></a>Zobacz też

- [Dodawanie szablonów projektów i elementów projektu](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [Kreatory](../../extensibility/internals/wizards.md)
- [Lokalizowanie aplikacji](../../ide/globalizing-and-localizing-applications.md)
- [Identyfikatory CATID obiektów, które są zwykle używane do rozszerzania projektów](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)
