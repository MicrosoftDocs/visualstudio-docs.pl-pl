---
title: Rozwiązywanie problemów i Tworzenie dzienników dla programu MSBuild
ms.date: 06/27/2019
ms.technology: vs-ide-compile
ms.topic: troubleshooting
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
ms.openlocfilehash: ae91f7b9c90f0b06c449d26f67fe4fcc3434518e
ms.sourcegitcommit: f27084e64c79e6428746a20dda92795df996fb31
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85768701"
---
# <a name="troubleshoot-and-create-logs-for-msbuild-problems"></a>Rozwiązywanie problemów i Tworzenie dzienników dla programu MSBuild

Poniższe procedury mogą pomóc zdiagnozować problemy z kompilacją w projekcie programu Visual Studio i w razie potrzeby utworzyć dziennik do wysłania do firmy Microsoft w celu zbadania problemu.

## <a name="a-property-value-is-ignored"></a>Wartość właściwości jest ignorowana.

Jeśli właściwość projektu jest ustawiona na określoną wartość, ale nie ma wpływu na kompilację, wykonaj następujące kroki:

1. Otwórz wiersz polecenia dla deweloperów programu Visual Studio, który odnosi się do używanej wersji programu Visual Studio.
1. Uruchom następujące polecenie po podpisaniu wartości dla ścieżki rozwiązania, konfiguracji i nazwy projektu:

    ```cmd
    msbuild /p:SolutionDir="c:\MySolutionDir\";Configuration="MyConfiguration";Platform="Win32" /pp:out.xml MyProject.vcxproj
    ```

    To polecenie tworzy "wstępnie przetworzony plik projektu programu MSBuild (out.xml). Możesz wyszukać ten plik pod kątem konkretnej właściwości, aby zobaczyć, gdzie jest zdefiniowana.

Ostatnią definicją właściwości jest to, czego używa kompilacja. Jeśli właściwość jest ustawiona dwukrotnie, druga wartość zastępuje pierwszy. Ponadto MSBuild ocenia projekt w kilku przebiegach:

- PropertyGroups i Importy
- ItemDefinitionGroups
- ItemGroups
- Obiekty docelowe

W związku z tym w następującej kolejności:

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

Wartość "metadanych" dla elementu "MyFile.txt" zostanie oceniona jako "B" podczas kompilacji (nie "A", a nie puste)

## <a name="incremental-build-is-building-more-than-it-should"></a>Kompilacja przyrostowa kompiluje więcej niż powinien

Jeśli program MSBuild niepotrzebnie ponownie kompiluje projekt lub element projektu, Utwórz szczegółowy lub binarny dziennik kompilacji. Możesz wyszukać w dzienniku plik, który został zbudowany lub skompilowany niepotrzebnie. Dane wyjściowe wyglądają następująco:

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

W przypadku kompilowania w środowisku IDE programu Visual Studio (ze szczegółowym ustawieniem szczegółowości okna danych wyjściowych) **okno dane wyjściowe** Wyświetla przyczynę nieaktualności poszczególnych projektów:

```output
1>------ Up-To-Date check: Project: Project1, Configuration: Debug Win32 ------

1>Project is not up-to-date: build input 'f:\test\project1\project1\project1.h' was modified after the last build finished.
```

## <a name="create-a-binary-msbuild-log"></a>Tworzenie binarnego dziennika programu MSBuild

1. Otwórz wiersz polecenia dla deweloperów dla używanej wersji programu Visual Studio
1. W wierszu polecenia Uruchom jedno z następujących poleceń. (Należy pamiętać, aby użyć rzeczywistego projektu i wartości konfiguracji):

    ```cmd
    Msbuild /p:Configuration="MyConfiguration";Platform="x86" /bl MySolution.sln
    ```

    lub

    ```cmd
    Msbuild /p:/p:SolutionDir="c:\MySolutionDir\";Configuration="MyConfiguration";Platform="Win32" /bl MyProject.vcxproj
    ```

Plik MSBuild. binlog zostanie utworzony w katalogu, w którym uruchomiono program MSBuild. Można je wyświetlić i przeszukać przy użyciu [podglądu dzienników struktury programu MSBuild](http://www.msbuildlog.com/).

## <a name="create-a-detailed-log"></a>Tworzenie szczegółowego dziennika

1. Z menu głównego programu Visual Studio wybierz kolejno pozycje **Narzędzia**  >  **Opcje**  >  **projekty i rozwiązania**  > **kompilacja i uruchomienie**.
1. Ustaw **poziom szczegółowości kompilacji projektu programu MSBuild** na **szczegółowy** w obu polach kombi. Kontrolka Top 1 kompiluje poziom szczegółowości w **okno dane wyjściowe** , a druga kontrola w \<projectname\> pliku dziennika, który jest tworzony w katalogu pośrednim projektu podczas kompilacji.
2. W wierszu polecenia programu Visual Studio Developer wprowadź jedno z tych poleceń, zastępując rzeczywistą ścieżkę i wartości konfiguracji:

    ```cmd
    Msbuild /p:Configuration="MyConfiguration";Platform="x86" /fl MySolution.sln
    ```

    lub

    ```cmd
    Msbuild /p:/p:SolutionDir="c:\MySolutionDir\";Configuration="MyConfiguration";Platform="Win32" /fl MyProject.vcxproj
    ```

    Plik MSBuild. log zostanie utworzony w katalogu, w którym uruchomiono program MSBuild.
