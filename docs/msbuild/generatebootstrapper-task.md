---
title: GenerateBootstrapper — — Zadanie | Microsoft Docs
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
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634087"
---
# <a name="generatebootstrapper-task"></a>GenerateBootstrapper — zadanie

Zapewnia zautomatyzowany sposób wykrywania, pobierania i instalowania aplikacji oraz jej wymagań wstępnych. Służy on jako pojedynczy Instalator, który integruje osobne Instalatory dla wszystkich składników tworzących aplikację.

## <a name="task-parameters"></a>Parametry zadania

Poniżej opisano parametry zadania `GenerateBootstrapper`.

- `ApplicationFile`

   Opcjonalny parametr `String`.

   Określa plik używany przez program inicjujący do rozpoczęcia instalacji aplikacji po zainstalowaniu wszystkich wymagań wstępnych. Jeśli nie zostanie określony `BootstrapperItems` ani parametr `ApplicationFile`, zostanie zwrócony błąd kompilacji.

- `ApplicationName`

   Opcjonalny parametr `String`.

   Określa nazwę aplikacji, która zostanie zainstalowana przez program inicjujący. Ta nazwa będzie wyświetlana w interfejsie użytkownika używanego przez program inicjujący podczas instalacji.

- `ApplicationRequiresElevation`

   Opcjonalny parametr `Boolean`.

   W przypadku `true`składnik zostanie uruchomiony z podwyższonym poziomem uprawnień, gdy zostanie zainstalowany na komputerze docelowym.

- `ApplicationUrl`

   Opcjonalny parametr `String`.

   Określa lokalizację sieci Web, w której znajduje się Instalator aplikacji.

- `BootstrapperComponentFiles`

   Opcjonalny `String[]` parametr wyjściowy.

   Określa wbudowaną lokalizację plików pakietu programu inicjującego.

- `BootstrapperItems`

   Opcjonalny parametr `[]` <xref:Microsoft.Build.Framework.ITaskItem>.

   Określa produkty do skompilowania do programu inicjującego. Elementy przesłane do tego parametru powinny mieć następującą składnię:

  ```xml
  <BootstrapperItem
      Include="ProductCode">
      <ProductName>
          ProductName
      </ProductName>
  </BootstrapperItem>
  ```

   Atrybut `Include` reprezentuje nazwę wymagania wstępnego, które należy zainstalować. Metadane elementu `ProductName` są opcjonalne i będą używane przez aparat kompilacji jako przyjazna nazwa użytkownika, jeśli nie można znaleźć pakietu. Te elementy nie są wymagane przez parametry wejściowe programu MSBuild, chyba że `ApplicationFile` nie zostały określone. Należy uwzględnić jeden element dla każdego wymagania wstępnego, które musi zostać zainstalowane dla aplikacji.

   Jeśli nie zostanie określony `BootstrapperItems` ani parametr `ApplicationFile`, zostanie zwrócony błąd kompilacji.

- `BootstrapperKeyFile`

   Opcjonalny `String` parametr wyjściowy.

   Określa wbudowaną lokalizację pliku *Setup. exe*

- `ComponentsLocation`

   Opcjonalny parametr `String`.

   Określa lokalizację programu inicjującego, aby znaleźć wymagania wstępne instalacji do zainstalowania. Ten parametr może mieć następujące wartości:

  - `HomeSite`: wskazuje, że wymaganie wstępne jest obsługiwane przez dostawcę składnika.

  - `Relative`: wskazuje, że wymaganie wstępne znajduje się w tej samej lokalizacji aplikacji.

  - `Absolute`: wskazuje, że wszystkie składniki mają być znalezione przy użyciu scentralizowanego adresu URL. Ta wartość powinna być używana w połączeniu z parametrem wejściowym `ComponentsUrl`.

    Jeśli nie określono `ComponentsLocation`, `HomeSite` jest używana domyślnie.

- `ComponentsUrl`

   Opcjonalny parametr `String`.

   Określa adres URL zawierający wymagania wstępne instalacji.

- `CopyComponents`

   Opcjonalny parametr `Boolean`.

   Jeśli `true`, program inicjujący skopiuje wszystkie pliki wyjściowe do ścieżki określonej w parametrze `OutputPath`. Wszystkie wartości parametru `BootstrapperComponentFiles` powinny być oparte na tej ścieżce. Jeśli `false`, pliki nie są kopiowane, a wartości `BootstrapperComponentFiles` są zależne od wartości parametru `Path`.  Wartość domyślna tego parametru to `true`.

- `Culture`

   Opcjonalny parametr `String`.

   Określa kulturę, która ma być używana przez interfejs użytkownika programu inicjującego i wymagania wstępne instalacji. Jeśli określona kultura jest niedostępna, zadanie używa wartości parametru `FallbackCulture`.

- `FallbackCulture`

   Opcjonalny parametr `String`.

   Określa kulturę pomocniczą, która ma być używana przez interfejs użytkownika programu inicjującego i wymagania wstępne instalacji.

- `OutputPath`

   Opcjonalny parametr `String`.

   Określa lokalizację kopiowania pliku *Setup. exe* i wszystkich plików pakietu.

- `Path`

   Opcjonalny parametr `String`.

   Określa lokalizację wszystkich dostępnych wstępnie wymaganych pakietów.

- `SupportUrl`

   Opcjonalny parametr `String`.

   Określa adres URL, który ma zostać określony w przypadku niepowodzenia instalacji programu inicjującego.

- `Validate`

   Opcjonalny parametr `Boolean`.

   Jeśli `true`, program inicjujący wykonuje walidację XSD na określonych elementach wejściowych programu inicjującego. Wartość domyślna tego parametru to `false`.

## <a name="remarks"></a>Uwagi

Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z klasy <xref:Microsoft.Build.Tasks.TaskExtension>, która sama dziedziczy z klasy <xref:Microsoft.Build.Utilities.Task>. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Przykład

Poniższy przykład używa zadania `GenerateBootstrapper`, aby zainstalować aplikację, która musi mieć zainstalowany .NET Framework 2,0 jako warunek wstępny.

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
