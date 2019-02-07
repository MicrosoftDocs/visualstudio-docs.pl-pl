---
title: Generatebootstrapper — zadanie | Dokumentacja firmy Microsoft
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5a8736e27337aa2b2512eb96b3325489c96b0e93
ms.sourcegitcommit: 01334abf36d7e0774329050d34b3a819979c95a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/07/2019
ms.locfileid: "55853784"
---
# <a name="generatebootstrapper-task"></a>GenerateBootstrapper — zadanie
Umożliwia automatyczne wykrywanie, pobieranie i instalowanie aplikacji i jej wstępnie wymagane składniki. Służy on jako jeden Instalator, który integruje osobne instalatory dla wszystkich składników tworzących aplikację.

## <a name="task-parameters"></a>Parametry zadania
Poniżej opisano parametry `GenerateBootstrapper` zadania.

- `ApplicationFile`  
  
   Opcjonalnie `String` parametru.  
  
   Określa plik, który program inicjujący będzie używać do instalowania aplikacji po wszystkie wstępnie wymagane składniki zostały zainstalowane. Spowoduje błąd kompilacji, jeśli żadna `BootstrapperItems` ani `ApplicationFile` określono parametr.  
  
- `ApplicationName`  
  
   Opcjonalnie `String` parametru.  
  
   Określa nazwę aplikacji, w którym zostanie zainstalowany program inicjujący. Ta nazwa będzie wyświetlana w Interfejsie użytkownika program inicjujący używany podczas instalacji.  
  
- `ApplicationRequiresElevation`  
  
   Opcjonalnie `Boolean` parametru.  
  
   Jeśli `true`, składnik jest uruchamiany z podwyższonym poziomem uprawnień, gdy jest zainstalowany na komputerze docelowym.  
  
- `ApplicationUrl`  
  
   Opcjonalnie `String` parametru.  
  
   Określa lokalizację sieci Web, który jest hostem Instalator aplikacji.  
  
- `BootstrapperComponentFiles`  
  
   Opcjonalnie `String[]` parametr wyjściowy.  
  
   Określa lokalizację skompilowane pliki pakietu programu inicjującego.  
  
- `BootstrapperItems`  
  
   Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.  
  
   Określa produktów, które mają wbudowane w program inicjujący. Elementy przekazany do tego parametru powinna mieć następującą składnię:  
  
  ```xml
  <BootstrapperItem
      Include="ProductCode">
      <ProductName>
          ProductName
      </ProductName>
  </BootstrapperItem>
  ```
  
   `Include` Atrybut oznacza nazwę wstępnie wymaganego składnika, który powinien być zainstalowany. `ProductName` Metadanych elementu jest opcjonalna i będzie używany przez aparat kompilacji jako przyjaznej nazwy nie można odnaleźć pakietu. Te elementy nie są wymagane [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] wprowadzania parametrów, chyba że nie `ApplicationFile` jest określony. Powinien zawierać jeden element dla każdego wymagania wstępne, które musi być zainstalowany dla swojej aplikacji.  
  
   Spowoduje błąd kompilacji, jeśli żadna `BootstrapperItems` ani `ApplicationFile` określono parametr.  
  
- `BootstrapperKeyFile`  
  
   Opcjonalnie `String` parametr wyjściowy.  
  
   Określa lokalizację utworzonych *setup.exe*  
  
- `ComponentsLocation`  
  
   Opcjonalnie `String` parametru.  
  
   Określa lokalizację programu inicjującego do sprawdzania wymagań wstępnych dotyczących instalacji zainstalować. Ten parametr może mieć następujące wartości:  
  
  - `HomeSite`: Wskazuje, że wstępnie wymaganego składnika jest hostowany przez dostawcę składnika.  
  
  - `Relative`: Wskazuje, że wymagań wstępnych znajduje się w tej samej lokalizacji aplikacji.  
  
  - `Absolute`: Wskazuje, że wszystkie składniki znajdują się pod adresem URL scentralizowany. Ta wartość będzie używana w połączeniu z `ComponentsUrl` parametr wejściowy.  
  
    Jeśli `ComponentsLocation` nie zostanie określony, `HomeSite` jest używane domyślnie.  
  
- `ComponentsUrl`  
  
   Opcjonalnie `String` parametru.  
  
   Określa adres URL zawierający wymagania wstępne instalacji.  
  
- `CopyComponents`  
  
   Opcjonalnie `Boolean` parametru.  
  
   Jeśli `true`, program inicjujący kopiuje wszystkie pliki wyjściowe do ścieżki określonej w `OutputPath` parametru. Wartości `BootstrapperComponentFiles` parametr powinien wszystkie opierać się na tę ścieżkę. Jeśli `false`, pliki nie są kopiowane i `BootstrapperComponentFiles` wartości są oparte na wartości `Path` parametru.  Wartość domyślna tego parametru to `true`.  
  
- `Culture`  
  
   Opcjonalnie `String` parametru.  
  
   Określa kulturę do użycia dla programu inicjującego interfejsu użytkownika i wymagania wstępne instalacji. Jeśli określona kultura jest niedostępny, zadanie używa wartości `FallbackCulture` parametru.  
  
- `FallbackCulture`  
  
   Opcjonalnie `String` parametru.  
  
   Określa kulturę pomocniczego na użytek programu inicjującego interfejsu użytkownika i wymagania wstępne instalacji.  
  
- `OutputPath`  
  
   Opcjonalnie `String` parametru.  
  
   Określa lokalizację, aby skopiować *setup.exe* i wszystkie pliki pakietu.  
  
- `Path`  
  
   Opcjonalnie `String` parametru.  
  
   Określa lokalizację wszystkie dostępne wstępnie wymagane pakiety.  
  
- `SupportUrl`  
  
   Opcjonalnie `String` parametru.  
  
   Określa adres URL, aby zapewnić, jeśli instalacja programu inicjującego nie powiedzie się.  
  
- `Validate`  
  
   Opcjonalnie `Boolean` parametru.  
  
   Jeśli `true`, program inicjujący przeprowadza weryfikację XSD elementów określony wejściowy programu inicjującego. Wartość domyślna tego parametru to `false`.

## <a name="remarks"></a>Uwagi
Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasa, która sama dziedziczy <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisów, zobacz [taskextension — klasa bazowa](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Przykład
W poniższym przykładzie użyto `GenerateBootstrapper` zadanie, aby zainstalować aplikację, która musi mieć [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] zainstalowany jako warunek wstępny.

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

## <a name="see-also"></a>Zobacz także
[Zadania](../msbuild/msbuild-tasks.md)  
[Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
