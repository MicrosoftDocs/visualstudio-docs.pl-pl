---
title: Generatebootstrapper — zadanie | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 85ea10b956069415198feb74be8c9e546ecc7ff8
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54769226"
---
# <a name="generatebootstrapper-task"></a>GenerateBootstrapper — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Umożliwia automatyczne wykrywanie, pobieranie i instalowanie aplikacji i jej wstępnie wymagane składniki. Służy on jako jeden Instalator, który integruje osobne instalatory dla wszystkich składników tworzących aplikację.  
  
## <a name="task-parameters"></a>Parametry zadania  
 W poniższej tabeli opisano parametry `GenerateBootstrapper` zadania.  
  
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
  
  ```  
  <BootstrapperItem  
      Include="ProductCode">  
      <ProductName>  
          ProductName  
      </ProductName>  
  </BootstrapperItem>  
  ```  
  
   `Include` Atrybut jest używany do reprezentowania nazwy testów wymagań wstępnych, która powinna zostać zainstalowana. `ProductName` Metadanych elementu jest opcjonalna i używaną przez aparat kompilacji jako nazwę przyjazną dla użytkownika w przypadku, gdy nie można odnaleźć pakietu. Te elementy nie są wymagane [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] parametrów wejściowych, o ile nie `ApplicationFile` jest określony. Powinien zawierać jeden element dla każdego wstępnie wymaganego składnika, który musi być zainstalowany dla swojej aplikacji.  
  
   Spowoduje błąd kompilacji, jeśli żadna `BootstrapperItems` ani `ApplicationFile` określono parametr.  
  
- `BootstrapperKeyFile`  
  
   Opcjonalnie `String` parametr wyjściowy.  
  
   Określa lokalizację utworzonych setup.exe  
  
- `ComponentsLocation`  
  
   Opcjonalnie `String` parametru.  
  
   Określa lokalizację programu inicjującego do sprawdzania wymagań wstępnych dotyczących instalacji zainstalować. Ten parametr może mieć następujące wartości:  
  
  - `HomeSite`: Wskazuje, że wstępnie wymaganego składnika jest hostowany przez dostawcę składnika.  
  
  - `Relative`: Wskazuje, że preqrequisite znajduje się w tej samej lokalizacji aplikacji.  
  
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
  
   Określa kulturę pomocniczego na użytek bootstraper interfejsu użytkownika i wymagania wstępne instalacji.  
  
- `OutputPath`  
  
   Opcjonalnie `String` parametru.  
  
   Określa lokalizację kopii setup.exe i wszystkie pliki pakietu.  
  
- `Path`  
  
   Opcjonalnie `String` parametru.  
  
   Określa lokalizację wszystkie dostępne wstępnie wymagane pakiety.  
  
- `SupportUrl`  
  
   Opcjonalnie `String` parametru.  
  
   Określa adres URL, aby zapewnić, w przypadku instalacji programu inicjującego nie  
  
- `Validate`  
  
   Opcjonalnie `Boolean` parametru.  
  
   Jeśli `true`, program inicjujący przeprowadza weryfikację XSD elementów określony wejściowy programu inicjującego. Wartość domyślna tego parametru to `false`.  
  
## <a name="remarks"></a>Uwagi  
 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasa, która sama dziedziczy <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisów, zobacz [taskextension — klasa bazowa](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `GenerateBootstrapper` zadanie, aby zainstalować aplikację, która musi mieć [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] zainstalowany jako warunek wstępny.  
  
```  
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
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
