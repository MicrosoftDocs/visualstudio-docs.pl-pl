---
title: Utrwalanie danych w pliku projektu MSBuild | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project files, persisting data in
ms.assetid: 6a920cb7-453d-4ffd-af1c-6f3084bd03f7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 307e8e5285dd0023d30772c5eac7a4e351287aa5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62909182"
---
# <a name="persisting-data-in-the-msbuild-project-file"></a>Utrwalanie danych w pliku projektu programu MSBuild
Podtypu projektu może być konieczne do utrwalenia danych specyficznych dla podtypu do pliku projektu do późniejszego użycia. Podtypu projektu używa trwałość plików projektu, aby spełniać następujące wymagania:

1. Utrwalanie danych używanych w ramach tworzenia projektu. (Aby uzyskać więcej informacji na temat aparatu Microsoft Build Engine, zobacz [MSBuild](../../msbuild/msbuild.md).) Informacje dotyczące kompilacji wykonać jedną z następujących:

    1. Dane niezależnie od konfiguracji. Oznacza to, że — dane przechowywane w elementach programu MSBuild z warunki pustego lub Brak.

    2. Dane zależne od konfiguracji. Oznacza to, że — dane przechowywane w elementy programu MSBuild, które są można korzystać w konfiguracji określonego projektu. Na przykład:

        ```
        <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">
        ```

2. Utrwalanie danych, która nie jest odpowiednia do kompilacji. Te dane mogą być wyrażone w dowolnej postaci XML, który nie jest weryfikowane względem schematu XML.

    1. Dane niezależnie od konfiguracji.

    2. Dane zależne od konfiguracji.

## <a name="persisting-build-related-information"></a>Przechowywanie informacji dotyczących kompilacji
 Trwałość danych, które są przydatne podczas tworzenia projektu odbywa się za pośrednictwem programu MSBuild. MSBuild system przechowuje tabelę główną informacji dotyczących kompilacji. Podtypy projektów są zobowiązani do uzyskania dostępu do tych danych do pobierania i ustawiania wartości właściwości. Podtypy projektów można także rozszerzyć w tabeli dane dotyczące kompilacji przez dodanie dodatkowych właściwości w celu jego utrwalenia i usuwając właściwości, więc nie zostaną utrwalone.

 Można zmodyfikować danych MSBuild, podtypu projektu jest odpowiedzialny za pobieranie obiektu właściwości programu MSBuild z systemu podstawowego projektu, za pośrednictwem <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>. <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> to interfejs implementowany podstawowego systemu projektu i agregację zapytania podtypu projektu dla niego, uruchamiając `QueryInterface`.

 Poniższa procedura przedstawiono procedurę usuwania właściwość za pomocą <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>.

#### <a name="to-remove-a-property-from-an-msbuild-project-file"></a>Aby usunąć właściwość z pliku projektu programu MSBuild

1. Wywołaj `QueryInterface` na <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> podtypu projektu.

2. Wywołaj <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.RemoveProperty%2A> z `pszPropName` ustawienia właściwości do usunięcia.

### <a name="persisting-non-build-related-information"></a>Utrwalanie-Build powiązane informacje.
 Trwałość danych w plikach projektu, który nie ma znaczenia, aby zbudować odbywa się za pośrednictwem <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>.

 Możesz zaimplementować <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> w głównym `project subtype aggregator` obiektu `project subtype project configuration` obiektu i / lub.

 Następujące punkty konturu główne pojęcia dotyczące trwałości-build powiązane informacje.

- Podstawowy projekt wywołuje na obiekcie agregatora podtyp (oznacza to, podtypu projektu najbardziej zewnętrznej) głównego projektu, tak aby ładują i zapisują dane niezależnie od konfiguracji i wywoływanych przez nią obiektów konfiguracji projektu podtypu projektu do załadowania lub zapisania zależne od konfiguracji dane.

- Podstawowy projekt wywołuje metody <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> wiele razy dla każdego poziomu Agregacja podtypu projektu i przekazuje identyfikator GUID dla poszczególnych poziomów.

- Podstawowy projekt przekazuje lub odbiera fragment XML dedykowanego podtypem konkretnego projektu, która używa tego mechanizmu jako sposób utrwalanie stanu między poziomach agregacji.

- Podstawowy projekt wywołuje podtypu projektu najbardziej zewnętrznej <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment>implementacji, przekazując identyfikatorem GUID. Jeśli identyfikator GUID należy do podtypu projektu najbardziej zewnętrznej, obsługuje on wywołania. w przeciwnym razie deleguje ona wywołanie podtypu projektu wewnętrzny i tak dalej, aż do znalezienia podtypu projektu, który odpowiada identyfikator GUID.

- Podtypu projektu można również zmodyfikować XML fragment przed lub po deleguje ona wywołanie podtypu projektu wewnętrznego. Poniższy przykład przedstawia fragment pliku projektu, w których nazwa pliku, który zawiera właściwości specyficzne dla podtypem projektu jest przekazywany do tego podtypu projektu.

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