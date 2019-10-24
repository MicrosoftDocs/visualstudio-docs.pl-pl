---
title: Utrwalanie danych w pliku projektu MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project files, persisting data in
ms.assetid: 6a920cb7-453d-4ffd-af1c-6f3084bd03f7
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7772f633c44c50b24995b7cc8a3f2f8bbbb01863
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726052"
---
# <a name="persisting-data-in-the-msbuild-project-file"></a>Utrwalanie danych w pliku projektu programu MSBuild
Podtyp projektu może wymagać utrwalenia danych specyficznych dla określonego typu w pliku projektu w celu późniejszego użycia. Podtyp projektu używa trwałości pliku projektu, aby spełnić następujące wymagania:

1. Utrwalaj dane używane w ramach kompilowania projektu. (Aby uzyskać więcej informacji na Microsoft Build Engine, zobacz [MSBuild](../../msbuild/msbuild.md).) Informacje związane z kompilacją mogą:

    1. Dane niezależne od konfiguracji. Oznacza to, że dane przechowywane w elementach MSBuild mają puste lub brakujące warunki.

    2. Dane zależne od konfiguracji. Oznacza to, że dane przechowywane w elementach programu MSBuild są kondycjonowane dla konkretnej konfiguracji projektu. Na przykład:

        ```
        <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">
        ```

2. Utrwalaj dane, które nie są istotne do kompilowania. Te dane mogą być wyrażone w postaci formatu XML bez sprawdzania poprawności względem schematu XML.

    1. Dane niezależne od konfiguracji.

    2. Dane zależne od konfiguracji.

## <a name="persisting-build-related-information"></a>Utrwalanie informacji związanych z kompilacją
 Trwałość danych przydatnych do kompilowania projektu jest obsługiwana za pomocą programu MSBuild. System MSBuild zachowuje główną tabelę informacji związanych z kompilacją. Podtypy projektu są odpowiedzialne za uzyskiwanie dostępu do tych danych w celu uzyskania i ustawienia wartości właściwości. Podtypy projektu mogą również rozszerzać tabelę danych związanych z kompilacją przez dodanie dodatkowych właściwości, które mają zostać utrwalone i przez usunięcie właściwości, aby nie były utrwalane.

 Aby zmodyfikować dane programu MSBuild, podtyp projektu jest odpowiedzialny za pobieranie obiektu właściwości programu MSBuild z podstawowego systemu projektu za pośrednictwem <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>. <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> jest interfejsem zaimplementowanym w podstawowym systemie projektu i agregowanym podtypem projektu zapytania dla niego przez uruchomienie `QueryInterface`.

 Poniższa procedura zawiera opis czynności usuwania właściwości przy użyciu <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>.

#### <a name="to-remove-a-property-from-an-msbuild-project-file"></a>Aby usunąć właściwość z pliku projektu MSBuild

1. Wywołaj `QueryInterface` na <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> podtyp projektu.

2. Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.RemoveProperty%2A> z `pszPropName` ustawioną na właściwość, którą chcesz usunąć.

### <a name="persisting-non-build-related-information"></a>Utrwalanie informacji dotyczących niezwiązanych z kompilacją
 Trwałość danych w plikach projektu, które nie mają znaczenia dla kompilacji, jest obsługiwana przez <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>.

 Można zaimplementować <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> w głównym obiekcie `project subtype aggregator`, obiekcie `project subtype project configuration` lub obu.

 Poniższe punkty przedstawiają główne koncepcje dotyczące trwałości informacji niezwiązanych z niekompilacją.

- Projekt podstawowy nawołuje się do głównego podtypu projektu (czyli tego, że skrajny podtyp projektu) do załadowania i zapisania danych niezależnych od konfiguracji, a następnie wywołuje obiekty konfiguracji projektu podtypu projektu w celu załadowania lub zapisania zależnej od konfiguracji Data.

- Projekt podstawowy wywołuje metody <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> wiele razy dla każdego poziomu agregacji podtypu projektu i przekazuje identyfikator GUID dla każdego poziomu.

- Projekt podstawowy przekazuje lub odbiera fragment XML, który jest przeznaczony dla określonego podtypu projektu i używa tego mechanizmu jako sposobu utrwalania stanu między poziomami agregacji.

- Projekt podstawowy wywołuje <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>implementation przekazaniem najbardziej zewnętrznego podtypu projektu w identyfikatorze GUID. Jeśli identyfikator GUID należy do zewnętrznego podtypu projektu, obsługuje wywołanie. w przeciwnym razie deleguje wywołanie do wewnętrznego podtypu projektu i tak dalej, aż zostanie znaleziony podtyp projektu, do którego odnosi się identyfikator GUID.

- Podtyp projektu może również zmodyfikować fragment XML przed lub po oddelegowaniu wywołania do wewnętrznego podtypu projektu. Poniższy przykład przedstawia fragment z pliku projektu, gdzie nazwa pliku, który zawiera właściwości specyficzne dla podtypu projektu, jest przenoszona do tego podtypu projektu.

    ```
    <ProjectExtensions>
        <VisualStudio>
          <FlavorProperties GUID="{<FlavorGUID>}">
            <FlavorProject TestFileFolder="TestFile" />
          </FlavorProperties>
        </VisualStudio>
      </ProjectExtensions>
    ```

## <a name="see-also"></a>Zobacz także
- [Podtypy projektów](../../extensibility/internals/project-subtypes.md)