---
title: GenerateBootstrapper — — Zadanie | Microsoft Docs
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
ms.openlocfilehash: 488caf02a20b4f0855df1ba2ef64c85e70e1a6a4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149632"
---
# <a name="generatebootstrapper-task"></a>GenerateBootstrapper — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zapewnia zautomatyzowany sposób wykrywania, pobierania i instalowania aplikacji oraz jej wymagań wstępnych. Służy on jako pojedynczy Instalator, który integruje osobne Instalatory dla wszystkich składników tworzących aplikację.  
  
## <a name="task-parameters"></a>Parametry zadania  
 W poniższej tabeli opisano parametry `GenerateBootstrapper` zadania.  
  
- `ApplicationFile`  
  
   Opcjonalny `String` parametr.  
  
   Określa plik używany przez program inicjujący do rozpoczęcia instalacji aplikacji po zainstalowaniu wszystkich wymagań wstępnych. Wystąpił błąd kompilacji, jeśli nie `BootstrapperItems` `ApplicationFile` zostanie określony ani parametr.  
  
- `ApplicationName`  
  
   Opcjonalny `String` parametr.  
  
   Określa nazwę aplikacji, która zostanie zainstalowana przez program inicjujący. Ta nazwa będzie wyświetlana w interfejsie użytkownika używanego przez program inicjujący podczas instalacji.  
  
- `ApplicationRequiresElevation`  
  
   Opcjonalny `Boolean` parametr.  
  
   Jeśli `true` składnik jest uruchomiony z podwyższonym poziomem uprawnień, gdy jest zainstalowany na komputerze docelowym.  
  
- `ApplicationUrl`  
  
   Opcjonalny `String` parametr.  
  
   Określa lokalizację sieci Web, w której znajduje się Instalator aplikacji.  
  
- `BootstrapperComponentFiles`  
  
   Opcjonalny `String[]` parametr wyjściowy.  
  
   Określa wbudowaną lokalizację plików pakietu programu inicjującego.  
  
- `BootstrapperItems`  
  
   Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.  
  
   Określa produkty do skompilowania do programu inicjującego. Elementy przesłane do tego parametru powinny mieć następującą składnię:  
  
  ```  
  <BootstrapperItem  
      Include="ProductCode">  
      <ProductName>  
          ProductName  
      </ProductName>  
  </BootstrapperItem>  
  ```  
  
   Ten `Include` atrybut jest używany do reprezentowania nazwy wymagania wstępnego, które należy zainstalować. `ProductName`Metadane elementu są opcjonalne i będą używane przez aparat kompilacji jako przyjazna dla użytkownika nazwa na wypadek, gdyby nie można znaleźć pakietu. Te elementy nie są wymaganymi [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] parametrami wejściowymi, chyba że żadne nie `ApplicationFile` zostanie określone. Należy uwzględnić jeden element dla każdego wymagania wstępnego, które musi być zainstalowane dla aplikacji.  
  
   Wystąpił błąd kompilacji, jeśli nie `BootstrapperItems` `ApplicationFile` zostanie określony ani parametr.  
  
- `BootstrapperKeyFile`  
  
   Opcjonalny `String` parametr wyjściowy.  
  
   Określa zbudowaną lokalizację setup.exe  
  
- `ComponentsLocation`  
  
   Opcjonalny `String` parametr.  
  
   Określa lokalizację programu inicjującego, aby znaleźć wymagania wstępne instalacji do zainstalowania. Ten parametr może mieć następujące wartości::  
  
  - `HomeSite`: Wskazuje, że wymaganie wstępne jest obsługiwane przez dostawcę składnika.  
  
  - `Relative`: Wskazuje, że preqrequisite znajduje się w tej samej lokalizacji aplikacji.  
  
  - `Absolute`: Wskazuje, że wszystkie składniki mają być znalezione w scentralizowanym adresie URL. Ta wartość powinna być używana w połączeniu z `ComponentsUrl` parametrem wejściowym.  
  
    Jeśli `ComponentsLocation` nie jest określony, `HomeSite` jest używany domyślnie.  
  
- `ComponentsUrl`  
  
   Opcjonalny `String` parametr.  
  
   Określa adres URL zawierający wymagania wstępne instalacji.  
  
- `CopyComponents`  
  
   Opcjonalny `Boolean` parametr.  
  
   Jeśli `true` program inicjujący kopiuje wszystkie pliki wyjściowe do ścieżki określonej w `OutputPath` parametrze. `BootstrapperComponentFiles`Wszystkie wartości parametru powinny być oparte na tej ścieżce. Jeśli `false` pliki nie są kopiowane, a `BootstrapperComponentFiles` wartości są zależne od wartości `Path` parametru.  Wartość domyślna tego parametru to `true` .  
  
- `Culture`  
  
   Opcjonalny `String` parametr.  
  
   Określa kulturę, która ma być używana przez interfejs użytkownika programu inicjującego i wymagania wstępne instalacji. Jeśli określona kultura to niedostępny, zadanie używa wartości `FallbackCulture` parametru.  
  
- `FallbackCulture`  
  
   Opcjonalny `String` parametr.  
  
   Określa kulturę pomocniczą, która ma być używana dla interfejsu użytkownika programu Bootstrap i wymagań wstępnych instalacji.  
  
- `OutputPath`  
  
   Opcjonalny `String` parametr.  
  
   Określa lokalizację do skopiowania setup.exe i wszystkich plików pakietów.  
  
- `Path`  
  
   Opcjonalny `String` parametr.  
  
   Określa lokalizację wszystkich dostępnych wstępnie wymaganych pakietów.  
  
- `SupportUrl`  
  
   Opcjonalny `String` parametr.  
  
   Określa adres URL, który należy podać, jeśli instalacja programu inicjującego nie powiedzie się  
  
- `Validate`  
  
   Opcjonalny `Boolean` parametr.  
  
   Jeśli `true` program inicjujący wykonuje walidację XSD dla określonych wejściowych elementów programu inicjującego. Wartość domyślna tego parametru to `false` .  
  
## <a name="remarks"></a>Uwagi  
 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.TaskExtension> klasy, która sama dziedziczy z <xref:Microsoft.Build.Utilities.Task> klasy. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa `GenerateBootstrapper` zadania w celu zainstalowania aplikacji, która musi mieć zainstalowany program [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] jako warunek wstępny.  
  
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
 [Widoku](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
