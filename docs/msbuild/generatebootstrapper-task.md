---
title: Generowanie zadaniabootstrapper | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GenerateBootstrapper
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GenerateBootstrapper task
- GenerateBootstrapper task [MSBuild]
ms.assetid: ca3ba2c6-d2ea-41f2-b7e3-0fc2b0730460
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6da773fdf6cd84819ea0e73083995f60e3c17e2d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634087"
---
# <a name="generatebootstrapper-task"></a>GenerateBootstrapper — zadanie

Zapewnia zautomatyzowany sposób wykrywania, pobierania i instalowania aplikacji i jej wymagań wstępnych. Służy jako pojedynczy instalator, który integruje oddzielne instalatory dla wszystkich składników tworzących aplikację.

## <a name="task-parameters"></a>Parametry zadania

Poniżej opisano parametry `GenerateBootstrapper` zadania.

- `ApplicationFile`

   Parametr `String` opcjonalny.

   Określa plik, którego program uruchamiany będzie używany do rozpoczęcia instalacji aplikacji po zainstalowaniu wszystkich wymagań wstępnych. Błąd kompilacji spowoduje, jeśli `BootstrapperItems` nie `ApplicationFile` określono ani parametru.

- `ApplicationName`

   Parametr `String` opcjonalny.

   Określa nazwę aplikacji, którą zainstaluje program inichuracyjny. Ta nazwa pojawi się w interfejsie użytkownika używanym przez program inicjujący podczas instalacji.

- `ApplicationRequiresElevation`

   Parametr `Boolean` opcjonalny.

   Jeśli `true`składnik jest uruchamiany z podwyższonym poziomem uprawnień po zainstalowaniu go na komputerze docelowym.

- `ApplicationUrl`

   Parametr `String` opcjonalny.

   Określa lokalizację sieci Web, w którym znajduje się instalator aplikacji.

- `BootstrapperComponentFiles`

   Opcjonalny parametr wyjściowy. `String[]`

   Określa lokalizację wbudowanych plików pakietów programu inicjującego.

- `BootstrapperItems`

   Parametr <xref:Microsoft.Build.Framework.ITaskItem> `[]` opcjonalny.

   Określa produkty, które mają być wbudowane w program inichura. Elementy przekazywane do tego parametru powinny mieć następującą składnię:

  ```xml
  <BootstrapperItem
      Include="ProductCode">
      <ProductName>
          ProductName
      </ProductName>
  </BootstrapperItem>
  ```

   Atrybut `Include` reprezentuje nazwę warunek wstępny, który powinien być zainstalowany. Metadane `ProductName` elementu jest opcjonalne i będą używane przez aparat kompilacji jako przyjazną dla użytkownika nazwę, jeśli nie można odnaleźć pakietu. Te elementy nie są wymagane MSBuild `ApplicationFile` parametry wejściowe, chyba że nie jest określony. Należy dołączyć jeden element dla każdego wymaganego przygotowania, który musi być zainstalowany dla aplikacji.

   Błąd kompilacji spowoduje, jeśli `BootstrapperItems` nie `ApplicationFile` określono ani parametru.

- `BootstrapperKeyFile`

   Opcjonalny parametr wyjściowy. `String`

   Określa wbudowaną lokalizację *pliku setup.exe*

- `ComponentsLocation`

   Parametr `String` opcjonalny.

   Określa lokalizację, w którym program inicjał wyszukuje wymagania wstępne dotyczące instalacji. Ten parametr może mieć następujące wartości:

  - `HomeSite`: Wskazuje, że warunek wstępny jest obsługiwany przez dostawcę składnika.

  - `Relative`: Wskazuje, że warunek wstępny znajduje się w tej samej lokalizacji aplikacji.

  - `Absolute`: Wskazuje, że wszystkie składniki znajdują się pod scentralizowanym adresem URL. Ta wartość powinna być używana `ComponentsUrl` w połączeniu z parametrem wejściowym.

    Jeśli `ComponentsLocation` nie jest `HomeSite` określony, jest używany domyślnie.

- `ComponentsUrl`

   Parametr `String` opcjonalny.

   Określa adres URL zawierający wymagania wstępne dotyczące instalacji.

- `CopyComponents`

   Parametr `Boolean` opcjonalny.

   Jeśli `true`program inichowy kopiuje wszystkie pliki `OutputPath` wyjściowe do ścieżki określonej w parametrze. Wartości parametru `BootstrapperComponentFiles` powinny być oparte na tej ścieżce. Jeśli `false`pliki nie są kopiowane, `BootstrapperComponentFiles` a wartości są oparte `Path` na wartości parametru.  Domyślną wartością tego `true`parametru jest .

- `Culture`

   Parametr `String` opcjonalny.

   Określa kulturę, która ma być używana dla interfejsu użytkownika programu inicjującego i wymagań wstępnych instalacji. Jeśli określona kultura jest niedostępna, zadanie `FallbackCulture` używa wartości parametru.

- `FallbackCulture`

   Parametr `String` opcjonalny.

   Określa kultury pomocniczej do użycia dla interfejsu użytkownika programu inicjującego i wymagania wstępne instalacji.

- `OutputPath`

   Parametr `String` opcjonalny.

   Określa lokalizację *kopiowania pliku setup.exe* i wszystkie pliki pakietów.

- `Path`

   Parametr `String` opcjonalny.

   Określa lokalizację wszystkich dostępnych pakietów wstępnych.

- `SupportUrl`

   Parametr `String` opcjonalny.

   Określa adres URL, który ma być podajonych w przypadku niepowodzenia instalacji inichatoryjego.

- `Validate`

   Parametr `Boolean` opcjonalny.

   Jeśli `true`program inichowy wykonuje sprawdzanie poprawności XSD na określonych elementach wejściowych programów inichuracyjnych. Domyślną wartością tego `false`parametru jest .

## <a name="remarks"></a>Uwagi

Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, <xref:Microsoft.Build.Utilities.Task> która sama dziedziczy z klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisy, zobacz [TaskExtension klasy podstawowej](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Przykład

W poniższym przykładzie `GenerateBootstrapper` użyto zadania do zainstalowania aplikacji, która musi mieć zainstalowany program .NET Framework 2.0 jako warunek wstępny.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <BootstrapperFile Include="Microsoft.Net.Framework.2.0">
            <ProductName>Microsoft .NET Framework 2.0</ProductName>
        </BootstrapperFile>
    </ItemGroup>

    <Target Name="BuildBootstrapper">
        <GenerateBootstrapper
            ApplicationFile="WindowsApplication1.application"
            ApplicationName="WindowsApplication1"
            ApplicationUrl="http://mycomputer"
            BootstrapperItems="@(BootstrapperFile)"
            OutputPath="C:\output" />
    </Target>

</Project>
```

## <a name="see-also"></a>Zobacz też

- [Zadania](../msbuild/msbuild-tasks.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
