---
title: Rejestrowanie szablonów projektów i elementów | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], adding items
- registry, Add New Item dialog box
- Add New Item dialog box
- Add New Project dialog box
- registry, Add New Project dialog box
ms.assetid: 6b909f93-d7f5-4aec-81c6-ee9ff0f31638
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2e35a476ab8fe8d8de3ce11dd117de4c84a3befa
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72724624"
---
# <a name="registering-project-and-item-templates"></a>Rejestrowanie szablonów projektów i elementów
Typy projektów muszą rejestrować katalogi, w których znajdują się szablony projektów i elementów projektu. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] używa informacji o rejestracji skojarzonych z typami projektów, aby określić, co ma być wyświetlane w oknach dialogowych **Dodaj nowy projekt** i **Dodaj nowy element** .

 Aby uzyskać więcej informacji na temat szablonów, zobacz [Dodawanie projektów i szablonów elementów projektów](../../extensibility/internals/adding-project-and-project-item-templates.md).

## <a name="registry-entries-for-projects"></a>Wpisy rejestru dla projektów
 W poniższych przykładach przedstawiono wpisy rejestru w obszarze HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\<*wersja*>. Towarzyszące tabele objaśniają elementy używane w przykładach.

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
|Nazwa|REG_SZ|Identyfikator zasobu, który ma zostać pobrany z satelickiej biblioteki DLL zarejestrowanej w pakietach.|
|Package|REG_SZ|Identyfikator klasy pakietu zarejestrowanego w pakietach.|
|ProjectTemplatesDir|REG_SZ|Domyślna ścieżka do plików szablonów projektu. Pliki szablonu projektu są wyświetlane przez nowy szablon **projektu** .|

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
| @ | REG_SZ | Identyfikator zasobu dla szablonów dodawania elementów. |
| TemplatesDir | REG_SZ | Ścieżka elementów projektu wyświetlanych w oknie dialogowym kreatora **dodawania nowego elementu** . |
| TemplatesLocalizedSubDir | REG_SZ | Identyfikator zasobu ciągu, który zawiera nazwę podkatalogu TemplatesDir zawierającego zlokalizowane szablony. Ponieważ [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ładuje zasób ciągu z satelitarnych bibliotek DLL, jeśli są one, każda satelitarna Biblioteka DLL może zawierać inną zlokalizowaną nazwę podkatalogu. |
| SortPriority | REG_DWORD | Ustaw SortPriority, aby zarządzać kolejnością, w której szablony są wyświetlane w oknie dialogowym **Dodaj nowy element** . Większe wartości SortPriority są wyświetlane wcześniej na liście szablonów. |

### <a name="registering-file-filters"></a>Rejestrowanie filtrów plików
 Opcjonalnie można zarejestrować filtry, których [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] używa, gdy zostanie wyświetlony komunikat z nazwami plików. Na przykład filtr [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] dla okna dialogowego **Otwórz plik** to:

 **Pliki C# wizualne (\*. cs,\*. resx,\*. settings,\*. xsd,\*. WSDL);\*. cs,\*. resx,\*. Settings,\*. xsd,\*. WSDL)**

 W celu obsługi rejestracji wielu filtrów każdy filtr jest rejestrowany we własnym podkluczu w obszarze HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\<*wersja*> \Projects\\{\<*ProjectGUID*>} \ Filtruje\\*Podkluczy*<>. Nazwa podklucza jest dowolnie. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ignoruje nazwę podklucza i używa tylko jego wartości.

 Można kontrolować konteksty, w których filtr jest używany, ustawiając flagi, pokazane w poniższej tabeli. Jeśli filtr nie ma ustawionych flag, będzie wyświetlany po wspólnych filtrach w oknie dialogowym **Dodaj istniejący element** i oknie dialogowym **Otwórz plik** , ale nie będzie używany w oknie dialogowym **Znajdź w plikach** .

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
|CommonFindFilesFilter|REG_DWORD|Filtruje jeden ze wspólnych filtrów w oknie dialogowym **Znajdź w plikach** . Filtry wspólne są wymienione na liście filtrów przed filtrami, które nie są oznaczone jako wspólne.|
|CommonOpenFilesFilter|REG_DWORD|Powoduje, że filtr jest jednym ze wspólnych filtrów w oknie dialogowym **Otwórz plik** . Filtry wspólne są wymienione na liście filtrów przed filtrami, które nie są oznaczone jako wspólne.|
|FindInFilesFilter|REG_DWORD|Wyświetla filtr po wspólnych filtrach w oknie dialogowym **Znajdź w plikach** .|
|NotOpenFileFilter|REG_DWORD|Wskazuje, że filtr nie jest używany w oknie dialogowym **Otwórz plik** .|
|NotAddExistingItemFilter|REG_DWORD|Wskazuje, że filtr nie jest używany w oknie dialogowym **Dodaj istniejący element** .|
|SortPriority|REG_DWORD|Ustaw SortPriority, aby zarządzać kolejnością wyświetlania filtrów. Większe wartości SortPriority są wyświetlane wcześniej na liście filtrów.|

## <a name="directory-structure"></a>Struktura katalogów
 Pakietów VSPackage może umieścić pliki szablonów i foldery w dowolnym miejscu na dysku lokalnym lub zdalnym, o ile lokalizacja jest zarejestrowana za pomocą zintegrowanego środowiska programistycznego (IDE). Jednak w celu ułatwienia organizacji zalecamy zastosowanie następującej struktury katalogów w ścieżce instalacji produktu.

 \Templates

 \Projects (zawiera szablony projektów)

 \Applications

 \Components

 \ ...

 \ProjectItems (zawiera elementy projektu)

 \Class

 \Form

 Strona \Serwer sieci

 \HelperFiles (zawiera pliki używane w elementach projektu wieloplikowego)

 \WizardFiles

## <a name="see-also"></a>Zobacz także

- [Dodawanie projektu i szablonów elementów projektu](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [Kreatory](../../extensibility/internals/wizards.md)
- [Lokalizowanie aplikacji](../../ide/globalizing-and-localizing-applications.md)
- [Identyfikatory CATID obiektów, które są zwykle używane do rozszerzania projektów](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)