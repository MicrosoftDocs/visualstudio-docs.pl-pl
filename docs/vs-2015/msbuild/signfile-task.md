---
title: Signfile — zadanie | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#SignFile
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, SignFile task
- SignFile task [MSBuild]
ms.assetid: edef1819-ddeb-4e09-95de-fc7063ba9388
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 08db6a5d22cacc348a9ef36fd9e9857d5b55642a
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65703736"
---
# <a name="signfile-task"></a>SignFile — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podpisuje określonego pliku przy użyciu określonego certyfikatu.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry `SignFile` zadania.  
  
 Należy pamiętać, że certyfikaty algorytmu SHA-256 są dozwolone tylko na maszynach mających .NET 4.5 lub nowszy.  
  
> [!WARNING]
> Począwszy od programu Visual Studio 2013 Update 3 to zadanie ma nowy podpisu, który pozwala na określenie wersji platformy docelowej dla pliku. Jesteś, zaleca się stosowanie nowa sygnatura wszędzie tam, gdzie to możliwe, ponieważ proces MSBuild używa algorytmu SHA-256 skróty, tylko wtedy, gdy platforma docelowa jest .NET 4.5 lub nowszej. Jeśli platformę docelową jest program .NET 4.0 lub poniżej, nie można używać skrótu SHA-256.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`CertificateThumbprint`|Wymagane `String` parametru.<br /><br /> Określa certyfikat do użycia podczas podpisywania. Ten certyfikat musi znajdować się w magazynie osobistym bieżącego użytkownika.|  
|`SigningTarget`|Wymagane <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br /> Określa pliki, aby zalogować się przy użyciu certyfikatu.|  
|`TimestampUrl`|Opcjonalnie `String` parametru.<br /><br /> Określa adres URL serwera sygnatur czasowych.|  
|`TargetFrameworkVersion`|Wersja .NET Framework, która jest używana dla elementu docelowego.|  
  
## <a name="remarks"></a>Uwagi  
 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisów, zobacz [klasa podstawowa zadania](../msbuild/task-base-class.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `SignFile` zadania do podpisywania plików określonych w `FilesToSign` elementu kolekcji za pomocą certyfikatu określonego przez `Certificate` właściwości.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <FileToSign Include="File.exe" />  
    </ItemGroup>  
    <PropertyGroup>  
        <Certificate>Cert.cer</Certificate>  
    </PropertyGroup>  
    <Target Name="Sign">  
        <SignFile  
            CertificateThumbprint="$(CertificateThumbprint)"  
            SigningTarget="@(FileToSign)"   
            TargetFrameworkVersion="v4.5" />  
    </Target>  
</Project>  
```  
  
> [!NOTE]
> Odcisk palca certyfikatu jest Skrót SHA-1 certyfikatu. Aby uzyskać więcej informacji, zobacz [uzyskać Skrót SHA-1 certyfikatu zaufanego głównego urzędu certyfikacji](https://msdn.microsoft.com/dd641990-9a88-4228-a245-017797131a87).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Exec` zadania do podpisywania plików określonych w `FilesToSign` elementu kolekcji za pomocą certyfikatu określonego przez `Certificate` właściwości. Służy to do podpisywania plików Instalatora Windows podczas procesu kompilacji.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <FileToSign Include="File.msi" />  
    </ItemGroup>  
    <PropertyGroup>  
        <Certificate>Cert.cer</Certificate>  
    </PropertyGroup>  
    <Target Name="Sign">  
        <Exec Command="signtool.exe sign /f CertFile /p Password "@(FileToSign)" "/>  
        <SignFile  
            CertificateThumbprint="$(CertificateThumbprint)"  
            SigningTarget="@(FileToSign)"   
            TargetFrameworkVersion="v4.0" />  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)   
 [Zadania](../msbuild/msbuild-tasks.md)
