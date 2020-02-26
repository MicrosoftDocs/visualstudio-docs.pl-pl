---
title: SignFile — — zadanie | Microsoft Docs
ms.date: 11/04/2016
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 397366a7dac601cd11dc1c70efc352edf303a92e
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579584"
---
# <a name="signfile-task"></a>SignFile — zadanie

Podpisuje określony plik przy użyciu podanego certyfikatu.

## <a name="parameters"></a>Parametry

 W poniższej tabeli opisano parametry zadania `SignFile`.

 Należy pamiętać, że certyfikaty SHA-256 są dozwolone tylko na maszynach z platformą .NET 4,5 lub nowszym.

> [!WARNING]
> Począwszy od Visual Studio 2013 Update 3, to zadanie ma nowy podpis, który pozwala określić wersję platformy docelowej dla tego pliku. Zaleca się używanie nowej sygnatury wszędzie tam, gdzie jest to możliwe, ponieważ proces MSBuild używa skrótów SHA-256 tylko wtedy, gdy platformą docelową jest program .NET 4,5 lub nowszy. Jeśli platformą docelową jest program .NET 4,0 lub niższy, skrót SHA-256 nie zostanie użyty.

|Parametr|Opis|
|---------------|-----------------|
|`CertificateThumbprint`|Wymagany `String` parametr.<br /><br /> Określa certyfikat, który ma być używany do podpisywania. Ten certyfikat musi znajdować się w magazynie osobistym bieżącego użytkownika.|
|`SigningTarget`|Wymagany <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br /> Określa pliki do podpisania przy użyciu certyfikatu.|
|`TimestampUrl`|Opcjonalny parametr `String`.<br /><br /> Określa adres URL serwera sygnatury czasowej.|
|`TargetFrameworkVersion`|Wersja .NET Framework, która jest używana dla elementu docelowego.|

## <a name="remarks"></a>Uwagi

 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z klasy <xref:Microsoft.Build.Utilities.Task>. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [Klasa bazowa zadania](../msbuild/task-base-class.md).

## <a name="example"></a>Przykład

 Poniższy przykład używa zadania `SignFile` do podpisywania plików określonych w kolekcji elementów `FilesToSign` z certyfikatem określonym przez właściwość `Certificate`.

```xml
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
> Odcisk palca certyfikatu to skrót SHA-1 certyfikatu. Aby uzyskać więcej informacji, zobacz [Uzyskiwanie skrótu SHA-1 certyfikatu zaufanego głównego urzędu certyfikacji](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc733076\(v\=ws.10\)). W przypadku kopiowania i wklejania odcisku palca z szczegółów certyfikatu upewnij się, że nie dołączysz znaku dodatkowego (3F) niewidocznego, co może uniemożliwić `SignFile` odnajdywania certyfikatu.

## <a name="see-also"></a>Zobacz też
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
- [Zadania](../msbuild/msbuild-tasks.md)