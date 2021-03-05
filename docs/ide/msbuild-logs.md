---
title: Rozwiązywanie problemów i Tworzenie dzienników dla programu MSBuild
description: Dowiedz się, jak można zdiagnozować problemy z kompilacją w projekcie programu Visual Studio i w razie potrzeby utworzyć dziennik do wysłania do firmy Microsoft w celu zbadania problemu.
ms.custom: SEO-VS-2020
ms.date: 02/08/2021
ms.technology: vs-ide-compile
ms.topic: troubleshooting
helpviewer_keywords:
- msbuild logs"
author: corob-msft
ms.author: corob
manager: jmartens
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.description: Generate build logs for msbuild projects to collect helpful information when troubleshooting issues.
ms.openlocfilehash: 3496eb5a0e8f699a994037ccc853a76e4f93e4ee
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102225218"
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
- Targets (Obiekty docelowe)

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

## <a name="create-a-binary-msbuild-log-at-the-command-prompt"></a>Utwórz binarny dziennik programu MSBuild w wierszu polecenia

1. Otwórz wiersz polecenia dla deweloperów dla używanej wersji programu Visual Studio

1. W wierszu polecenia Uruchom jedno z następujących poleceń. (Należy pamiętać, aby użyć rzeczywistego projektu i wartości konfiguracji):

   ```cmd
   Msbuild /p:Configuration="MyConfiguration";Platform="x86" /bl MySolution.sln
   ```

   lub

   ```cmd
   Msbuild /p:SolutionDir="c:\MySolutionDir\";Configuration="MyConfiguration";Platform="Win32" /bl MyProject.vcxproj
   ```

Plik *MSBuild. binlog* zostanie utworzony w katalogu, w którym uruchomiono program MSBuild.

## <a name="create-a-binary-msbuild-log-by-using-the-project-system-tools-extension"></a>Utwórz binarny dziennik MSBuild przy użyciu rozszerzenia narzędzi systemu projektu

1. Pobierz i zainstaluj [rozszerzenie narzędzi systemu projektu](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.ProjectSystemTools).

1. Po zainstalowaniu rozszerzenia niektóre nowe elementy pojawiają się w menu **Wyświetl**  >  **inne okna** .

   ![Inne menu systemu Windows](../ide/media/view-menu.png)

1. Wybierz pozycję **Wyświetl**  >  **inne**  >  **Rejestrowanie kompilacji** systemu Windows, aby wyświetlić okno **Rejestrowanie kompilacji** w programie Visual Studio. Wybierz ikonę pierwszego paska narzędzi, aby rozpocząć nagrywanie zarówno kompilacji zwykłych, jak i w czasie projektowania w systemie projektu.

   ![Okno rejestrowania kompilacji](../ide/media/build-logging-click-to-record.png)

1. Po zarejestrowaniu kompilacji zostanie ona wyświetlona w oknie rejestrowanie kompilacji. Kliknij prawym przyciskiem myszy element i wybierz polecenie **Zapisz dzienniki** w menu kontekstowym, aby zapisać plik *. binlog* .

   ![Menu kontekstowe rejestrowania kompilacji](../ide/media/build-logging-context-menu.png)

Pliki *. binlog* można wyświetlać i przeszukiwać za pomocą [podglądu dzienników strukturalnych programu MSBuild](http://www.msbuildlog.com/).

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

## <a name="see-also"></a>Zobacz też

- [Rozwiązywanie problemów z programem Visual Studio](/troubleshoot/visualstudio/welcome-visual-studio/)
