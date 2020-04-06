---
title: Utrwalanie danych w pliku projektu MSBuild | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project files, persisting data in
ms.assetid: 6a920cb7-453d-4ffd-af1c-6f3084bd03f7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e83526007f676ae94ddce57936b627bcb4308c2a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706697"
---
# <a name="persisting-data-in-the-msbuild-project-file"></a>Utrwalanie danych w pliku projektu programu MSBuild
Podtyp projektu może być konieczne utrwalenie danych specyficznych dla podtypu w pliku projektu do późniejszego użycia. Podtyp projektu używa trwałości pliku projektu, aby spełnić następujące wymagania:

1. Utrwalanie danych używanych w ramach tworzenia projektu. (Aby uzyskać więcej informacji na temat aparatu kompilacji firmy Microsoft, zobacz [MSBuild](../../msbuild/msbuild.md).) Informacje związane z kompilacją mogą:

    1. Dane niezależne od konfiguracji. Oznacza to, że dane przechowywane w MSBuild elementów z pustymi lub brakujących warunków.

    2. Dane zależne od konfiguracji. Oznacza to, że dane przechowywane w MSBuild elementów, które są uwarunkowane dla określonej konfiguracji projektu. Przykład:

        ```
        <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">
        ```

2. Utrwalać dane, które nie są istotne dla kompilacji. Te dane mogą być wyrażone w formacie XML w postaci swobodnej, który nie jest sprawdzany względem schematu XML.

    1. Dane niezależne od konfiguracji.

    2. Dane zależne od konfiguracji.

## <a name="persisting-build-related-information"></a>Utrwalanie informacji związanych z kompilacją
 Trwałość danych przydatnych do tworzenia projektu jest obsługiwany za pośrednictwem MSBuild. System MSBuild przechowuje główną tabelę informacji związanych z kompilacją. Podtypy projektu są odpowiedzialne za dostęp do tych danych, aby uzyskać i ustawić wartości właściwości. Podtypy projektu można również rozszerzyć tabelę danych związanych z kompilacją, dodając dodatkowe właściwości do utrwalenia i usuwając właściwości, aby nie były utrwalone.

 Aby zmodyfikować dane MSBuild, podtyp projektu jest odpowiedzialny za pobieranie obiektu właściwości <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>MSBuild z podstawowego systemu projektów za pośrednictwem programu . <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>jest interfejsem zaimplementowanym w podstawowym systemie projektu i agregującymi zapytania podtypu projektu przez uruchomienie `QueryInterface`.

 Poniższa procedura przedstawia kroki usuwania właściwości <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>przy użyciu programu .

#### <a name="to-remove-a-property-from-an-msbuild-project-file"></a>Aby usunąć właściwość z pliku projektu MSBuild

1. <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> Wywołanie `QueryInterface` podtypu projektu.

2. <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.RemoveProperty%2A> Wywołanie `pszPropName` z zestawem do właściwości, którą chcesz usunąć.

### <a name="persisting-non-build-related-information"></a>Utrwalanie informacji powiązanych bez kompilacji
 Trwałość danych w plikach projektu, które nie <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>ma znaczenia do kompilacji jest obsługiwany przez .

 Można zaimplementować <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> na `project subtype aggregator` głównym obiekcie, `project subtype project configuration` obiekcie lub obu.

 W poniższych punktach przedstawiono główne pojęcia dotyczące trwałości informacji niezwiązanych z kompilacją.

- Projekt podstawowy wywołuje główny podtyp projektu (czyli najbardziej zewnętrzny podtyp projektu) obiekt agregatora, aby załadować i zapisać niezależne dane konfiguracji i wywołuje obiekty konfiguracji projektu podtypu projektu projektu, aby załadować lub zapisać dane zależne od konfiguracji.

- Projekt podstawowy wywołuje metody <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> wiele razy dla każdego poziomu agregacji podtypu projektu i przekazuje identyfikator GUID dla każdego poziomu.

- Projekt podstawowy przekazuje lub odbiera fragment XML, który jest przeznaczony dla określonego podtypu projektu i używa tego mechanizmu jako sposób utrwalania stanu między poziomami agregacji.

- Projekt podstawowy wywołuje implementacji podtypu <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>projektu zewnętrznego przekazywania w guiD. Jeśli identyfikator GUID należy do najbardziej zewnętrznego podtypu projektu, obsługuje samo wywołanie; w przeciwnym razie deleguje wywołanie do podtypu projektu wewnętrznego i tak dalej, dopóki podtyp projektu, który odpowiada identyfikatorowi GUID zostanie znaleziony.

- Podtyp projektu można również zmodyfikować fragment XML przed lub po deleguje wywołanie do podtypu projektu wewnętrznego. W poniższym przykładzie przedstawiono fragment pliku projektu, w którym nazwa pliku zawierającego właściwości specyficzne dla podtypu projektu jest przekazywana do tego podtypu projektu.

    ```
    <ProjectExtensions>
        <VisualStudio>
          <FlavorProperties GUID="{<FlavorGUID>}">
            <FlavorProject TestFileFolder="TestFile" />
          </FlavorProperties>
        </VisualStudio>
      </ProjectExtensions>
    ```

## <a name="see-also"></a>Zobacz też
- [Podtypy projektów](../../extensibility/internals/project-subtypes.md)
