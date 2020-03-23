---
title: Rozwiązywanie problemów z tworzeniem dzienników i tworzenie ich w przypadku problemów z budynkiem MSBuild
ms.date: 06/27/2019
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- msbuild logs"
author: corob-msft
ms.author: corob
manager: jillfra
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.description: Generate build logs for msbuild projects to collect helpful information when troubleshooting issues.
ms.openlocfilehash: 07b2c5e941d31ab1be853f9a89af94462329bdf2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77278810"
---
# <a name="troubleshoot-and-create-logs-for-msbuild-problems"></a>Rozwiązywanie problemów z tworzeniem dzienników i tworzenie ich w przypadku problemów z budynkiem MSBuild

Poniższe procedury mogą pomóc w diagnozowaniu problemów z kompilacją w projekcie programu Visual Studio i, jeśli to konieczne, utworzyć dziennik do wysłania do firmy Microsoft w celu zbadania.

## <a name="a-property-value-is-ignored"></a>Wartość właściwości jest ignorowana

Jeśli właściwość projektu wydaje się być ustawiona na określoną wartość, ale nie ma wpływu na kompilację, wykonaj następujące kroki:

1. Otwórz wiersz polecenia dewelopera programu Visual Studio, który odpowiada twojej wersji programu Visual Studio.
1. Uruchom następujące polecenie, po zastąpieniu wartości ścieżki rozwiązania, konfiguracji i nazwy projektu:

    ```cmd
    msbuild /p:SolutionDir="c:\MySolutionDir\";Configuration="MyConfiguration";Platform="Win32" /pp:out.xml MyProject.vcxproj
    ```

    To polecenie tworzy "wstępnie przetworzony" plik projektu msbuild (out.xml). Można wyszukać ten plik dla określonej właściwości, aby zobaczyć, gdzie jest zdefiniowany.

Ostatnia definicja właściwości jest to, co zużywa kompilacji. Jeśli właściwość jest ustawiona dwukrotnie, druga wartość zastępuje pierwszą. Ponadto MSBuild ocenia projekt w kilku przebiegów:

- PropertyGroups i import
- Itemdefinitiongroups
- Grupy elementów
- Obiekty docelowe

W związku z tym, biorąc pod uwagę następującą kolejność:

```xml
<PropertyGroup>
   <MyProperty>A</MyProperty>
</PropertyGroup>
<ItemGroup>
   <MyItems Include="MyFile.txt"/>
</ItemGroup>
<ItemDefinitionGroup>
  <MyItems>
      <MyMetadata>$(MyProperty)</MyMetadata>
  </MyItems>
</ItemDefinitionGroup>
<PropertyGroup>
   <MyProperty>B</MyProperty>
</PropertyGroup>
```

Wartość elementu "MyMetadata" dla elementu "MyFile.txt" zostanie oceniona na "B" podczas kompilacji (nie "A" i nie będzie pusta)

## <a name="incremental-build-is-building-more-than-it-should"></a>Przyrostowa budowa buduje więcej niż powinna

Jeśli MSBuild niepotrzebnie odbudowuje element projektu lub projektu, utwórz szczegółowy lub binarny dziennik kompilacji. Można wyszukiwać w dzienniku plik, który został zbudowany lub skompilowany niepotrzebnie. Dane wyjściowe wyglądają mniej więcej tak:

```output
  Task "CL"

  Using cached input dependency table built from:

  F:\test\Project1\Project1\Debug\Project1.tlog\CL.read.1.tlog

  Outputs for F:\TEST\PROJECT1\PROJECT1\PROJECT1.CPP:
  F:\TEST\PROJECT1\PROJECT1\DEBUG\PROJECT1.OBJ
  Project1.cpp will be compiled because F:\TEST\PROJECT1\PROJECT1\PROJECT1.H was modified at 6/5/2019 12:37:09 PM.

  Outputs for F:\TEST\PROJECT1\PROJECT1\PROJECT1.CPP:
  F:\TEST\PROJECT1\PROJECT1\DEBUG\PROJECT1.OBJ

  Write Tracking Logs:
  Debug\Project1.tlog\CL.write.1.tlog
```

Jeśli są budowane w visual studio IDE (ze szczegółową szczegółowością okna danych wyjściowych), **okno wyjściowe** wyświetla przyczynę, dla której każdy projekt nie jest aktualny:

```output
1>------ Up-To-Date check: Project: Project1, Configuration: Debug Win32 ------

1>Project is not up-to-date: build input 'f:\test\project1\project1\project1.h' was modified after the last build finished.
```

## <a name="create-a-binary-msbuild-log"></a>Tworzenie binarnego dziennika msbuild

1. Otwieranie wiersza polecenia dewelopera dla swojej wersji programu Visual Studio
1. W wierszu polecenia uruchom jedno z następujących poleceń. (Pamiętaj, aby użyć rzeczywistych wartości projektu i konfiguracji.

    ```cmd
    Msbuild /p:Configuration="MyConfiguration";Platform="x86" /bl MySolution.sln
    ```

    lub

    ```cmd
    Msbuild /p:/p:SolutionDir="c:\MySolutionDir\";Configuration="MyConfiguration";Platform="Win32" /bl MyProject.vcxproj
    ```

Plik Msbuild.binlog zostanie utworzony w katalogu, z którego uruchomiono msbuild. Można go wyświetlać i przeszukiwać za pomocą [przeglądarki dziennika msbuild structured .](http://www.msbuildlog.com/)

## <a name="create-a-detailed-log"></a>Tworzenie szczegółowego dziennika

1. W menu głównym programu Visual Studio przejdź do pozycji **Narzędzia** > **Opcje** > **projekty i rozwiązania kompilacji** >**i uruchamiania**.
1. Ustaw **msbuild projektu kompilacji szczegółowości** **na Szczegółowe** w obu polach kombi. Top jeden kontroluje kompilacji szczegółowości w **oknie danych wyjściowych,** a drugi \<kontroluje\>kompilacji szczegółowości w pliku .log projectname, który jest tworzony w katalogu pośredniego każdego projektu podczas kompilacji.
2. W wierszu polecenia dewelopera programu Visual Studio wprowadź jedno z tych poleceń, zastępując rzeczywistą ścieżkę i wartości konfiguracji:

    ```cmd
    Msbuild /p:Configuration="MyConfiguration";Platform="x86" /fl MySolution.sln
    ```

    lub

    ```cmd
    Msbuild /p:/p:SolutionDir="c:\MySolutionDir\";Configuration="MyConfiguration";Platform="Win32" /fl MyProject.vcxproj
    ```

    Plik Msbuild.log zostanie utworzony w katalogu, z którego uruchomiono msbuild.
