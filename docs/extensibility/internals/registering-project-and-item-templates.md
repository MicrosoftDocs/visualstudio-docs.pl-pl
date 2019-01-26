---
title: Rejestrowanie szablonów projektów i elementów | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], adding items
- registry, Add New Item dialog box
- Add New Item dialog box
- Add New Project dialog box
- registry, Add New Project dialog box
ms.assetid: 6b909f93-d7f5-4aec-81c6-ee9ff0f31638
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7ca4723d24c45a11422eae4b7d8b288671e0b921
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55041090"
---
# <a name="registering-project-and-item-templates"></a>Rejestrowanie szablonów projektów i elementów
Typy projektów, należy zarejestrować katalogi, w którym znajdują się swoje szablony projektów i elementów projektu. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] informacje rejestracji skojarzony z typów projektu są używane do określenia, jakie do wyświetlenia w **Dodaj nowy projekt** i **Dodaj nowy element** okien dialogowych.  

 Aby uzyskać więcej informacji na temat szablonów, zobacz [Dodawanie projektu i szablonów elementów projektów](../../extensibility/internals/adding-project-and-project-item-templates.md).  

## <a name="registry-entries-for-projects"></a>Wpisy rejestru dla projektów  
 Poniższe przykłady przedstawiają wpisy rejestru w HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\<*wersji*>. Towarzyszących tabelach opisano elementy używane w przykładach.  

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
|Nazwa wyświetlana|REG_SZ|Identyfikator zasobu o nazwie mają zostać pobrane satelitarną bibliotekę DLL jest zarejestrowany w ramach pakietów.|  
|Package|REG_SZ|Identyfikator klasy pakiet, który został zarejestrowany w ramach pakietów.|  
|ProjectTemplatesDir|REG_SZ|Domyślna ścieżka pliku szablonu projektu. Pliki szablonu projektu są wyświetlane przez **nowy projekt** szablonu.|  

### <a name="registering-item-templates"></a>Rejestrowanie szablonów elementów  
 Należy zarejestrować katalogu, w którym są przechowywane szablony elementów.  

```  
[Projects\{ProjectGUID}\AddItemTemplates\TemplateDirs\{VSPackageGUID}\1]  
@="#7"  
"TemplatesDir"="C:\\MyProduct\\MyProjectItemTemplates "  
"TemplatesLocalizedSubDir"="#10"  
"SortPriority"=dword:00000064  
```  


| Nazwa | Typ | Opis |
|--------------------------|-----------| - |
| @ | REG_SZ | Identyfikator zasobu dla szablonów Dodaj element. |
| TemplatesDir | REG_SZ | Ścieżka wyświetlanych w oknie dialogowym dla elementów projektu **Dodaj nowy element** kreatora. |
| TemplatesLocalizedSubDir | REG_SZ | Identyfikator zasobu ciągu, który nazwy podkatalogu TemplatesDir, który zawiera zlokalizowane szablony. Ponieważ [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ładowania zasobu ciągu z biblioteki DLL satellite jeśli one istnieją, każdy satelitarną bibliotekę DLL mogą zawierać nazwę podkatalogu zlokalizowane w różnych. |
| SortPriority | REG_DWORD | Ustaw SortPriority, które pozwalają zarządzać sposobem kolejność, w którym szablony są wyświetlane w **Dodaj nowy element** okno dialogowe. Większe wartości SortPriority się pojawić wcześniej na liście szablonów. |

### <a name="registering-file-filters"></a>Rejestrowanie filtry plików  
 Opcjonalnie można zarejestrować filtry, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] używa po wyświetleniu monitu dla nazw plików. Na przykład [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] filtrować **Otwórz plik** jest okno dialogowe:  

 **Pliki Visual C# (\*.CS,\*resx,\*.settings,\*XSD,\*.wsdl);\*. CS,\*resx,\*.settings,\*XSD,\*.wsdl)**  

 Do obsługi rejestracji wielu filtrów, każdy filtr jest zarejestrowany w jego własnej podklucza w HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\<*wersji*> \Projects\\{ \< *ProjectGUID*>} \Filters\\<*podklucz*>. Dowolne; jest nazwą podklucza [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ignoruje nazwa podklucza który i używa tylko jego wartości.  

 Można kontrolować kontekstów, w których filtr jest używany przez ustawienie flagi, co pokazano w poniższej tabeli. Jeśli filtr nie ma żadnych flag ustawionych, będzie ono wyświetlane po wspólne filtry w **Dodaj istniejący element** okno dialogowe i **Otwórz plik** okno dialogowe, ale nie będą używane w **Znajdź w plikach**  okno dialogowe.  

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
|CommonFindFilesFilter|REG_DWORD|Sprawia, że filtr jednego z typowych filtrów w **Znajdź w plikach** okno dialogowe. Wspólne filtry są wymienione na liście filtrów przed filtrami niezaznaczonych jako wspólne.|  
|CommonOpenFilesFilter|REG_DWORD|Sprawia, że filtr jednego z typowych filtrów w **Otwórz plik** okno dialogowe. Wspólne filtry są wymienione na liście filtrów przed filtrami niezaznaczonych jako wspólne.|  
|FindInFilesFilter|REG_DWORD|Wyświetla listę filtru po wspólne filtry w **Znajdź w plikach** okno dialogowe.|  
|NotOpenFileFilter|REG_DWORD|Wskazuje, że filtr nie jest używany w **Otwórz plik** okno dialogowe.|  
|NotAddExistingItemFilter|REG_DWORD|Wskazuje, że filtr nie jest używany w **Dodaj istniejący element** okno dialogowe.|  
|SortPriority|REG_DWORD|Ustaw SortPriority do określają kolejność, w którym są wyświetlane filtrów. Większe wartości SortPriority się pojawić wcześniej na liście filtrów.|  

## <a name="directory-structure"></a>Struktura katalogów  
 Pakietów VSPackage można umieścić szablonu pliki i foldery dowolne miejsce na dysku lokalnym lub zdalnym, tak długo, jak lokalizacja jest rejestrowane za pomocą zintegrowanego środowiska programistycznego (IDE). Jednak w celu ułatwienia organizacji, firma Microsoft zaleca następującą strukturę katalogów w ścieżce instalacji produktu.  

 \Templates  

 \Projects (zawiera szablony projektów)  

 \Applications  

 \Components  

 \ ...  

 \ProjectItems (zawiera elementy projektu)  

 \Class  

 \Form  

 \Web strony  

 \HelperFiles (zawiera pliki używane w elementach projektu wielu plików)  

 \WizardFiles  

## <a name="see-also"></a>Zobacz też  
 [Dodawanie projektu i szablony elementów projektu](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [Kreatorzy](../../extensibility/internals/wizards.md)   
 [Lokalizowanie aplikacji](../../ide/localizing-applications.md)   
 [Identyfikatory CATID obiektów, które są zwykle używane do rozszerzania projektów](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)