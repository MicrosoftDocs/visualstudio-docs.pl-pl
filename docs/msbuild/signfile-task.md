---
title: Zadanie Pliku logowania | Dokumenty firmy Microsoft
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
ms.openlocfilehash: ee018b42fc23b0a520b510235117cb74729fd4b6
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094514"
---
# <a name="signfile-task"></a>SignFile — zadanie

Podpisuje określony plik przy użyciu określonego certyfikatu.

## <a name="parameters"></a>Parametry

 W poniższej tabeli `SignFile` opisano parametry zadania.

 Należy zauważyć, że certyfikaty SHA-256 są dozwolone tylko na komputerach z .NET 4.5 lub nowszym.

> [!WARNING]
> Począwszy od programu Visual Studio 2013 Update 3, to zadanie ma nowy podpis, który umożliwia określenie docelowej wersji struktury dla pliku. Zachęcamy do korzystania z nowego podpisu, gdy jest to możliwe, ponieważ proces MSBuild używa skrótów SHA-256 tylko wtedy, gdy struktura docelowa jest .NET 4.5 lub wyższa. Jeśli struktura docelowa jest .NET 4.0 lub poniżej, sha-256 mieszania nie będzie używany.

|Parametr|Opis|
|---------------|-----------------|
|`CertificateThumbprint`|Wymagany parametr interfejsu `String`.<br /><br /> Określa certyfikat do podpisywania. Ten certyfikat musi znajdować się w magazynie osobistym bieżącego użytkownika.|
|`SigningTarget`|Wymagany parametr interfejsu <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Określa pliki do podpisania za pomocą certyfikatu.|
|`TimestampUrl`|Parametr `String` opcjonalny.<br /><br /> Określa adres URL serwera znaczników czasu.|
|`TargetFrameworkVersion`|Wersja programu .NET Framework, która jest używana dla obiektu docelowego.|

## <a name="remarks"></a>Uwagi

 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisów, zobacz [Klasa podstawowa zadania](../msbuild/task-base-class.md).

## <a name="example"></a>Przykład

 Poniższy przykład używa `SignFile` zadania do podpisania plików `FilesToSign` określonych w kolekcji `CertificateThumbprint` towarów z certyfikatem określonym przez właściwość.

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
> Odcisk palca certyfikatu jest skrótem SHA-1 certyfikatu. Aby uzyskać więcej informacji, zobacz [Uzyskiwanie skrótu SHA-1 zaufanego certyfikatu głównego urzędu certyfikacji](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc733076\(v\=ws.10\)). Jeśli kopiujesz i wklejasz odcisk palca ze szczegółów certyfikatu, upewnij się, że nie `SignFile` zawierasz niewidocznego znaku dodatkowego (3F), który może uniemożliwić znalezienie certyfikatu.

## <a name="see-also"></a>Zobacz też

- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
- [Zadania](../msbuild/msbuild-tasks.md)