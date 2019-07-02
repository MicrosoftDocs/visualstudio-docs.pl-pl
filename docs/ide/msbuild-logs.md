---
title: Rozwiązywanie problemów i twórz dzienniki na potrzeby problemów programu MSBuild
ms.date: 06/27/2019
ms.topic: conceptual
helpviewer_keywords:
- msbuild logs"
author: mikeblome
ms.author: mblome
manager: jillfra
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.description: Generate build logs for msbuild projects to collect helpful information when troubleshooting issues.
ms.openlocfilehash: c3db56ac7ea60ce88beae6698c974ac91373ed00
ms.sourcegitcommit: 6f7a740750b2cd17ea2275c3d046caebc9782917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/02/2019
ms.locfileid: "67518239"
---
# <a name="troubleshoot-and-create-logs-for-msbuild-problems"></a>Rozwiązywanie problemów i twórz dzienniki na potrzeby problemów programu MSBuild

Poniższe procedury ułatwia diagnozowanie problemów kompilacji w projekcie programu Visual Studio, a jeśli to konieczne, tworzy plik dziennika, aby wysłać do firmy Microsoft w celu zbadania problemu.

## <a name="a-property-value-is-ignored"></a>Wartość właściwości jest ignorowane.

Jeśli właściwość projektu wydaje się być równa określonej wartości, ale nie ma wpływu na kompilację, wykonaj następujące kroki:

1. Otwórz program Visual Studio wiersza polecenia dewelopera odpowiadający Twojej wersji programu Visual Studio.
1. Uruchom następujące polecenie, po podstawieniu wartości dla ścieżka rozwiązania, konfiguracji i nazwa projektu:

    ```cmd
    msbuild /p:SolutionDir="c:\MySolutionDir\";Configuration="MyConfiguration";Platform="Win32" /pp:out.xml MyProject.vcxproj
    ```

    To polecenie tworzy plik projektu msbuild "wstępnie przetworzony" (out.xml). Możesz wyszukiwać tego pliku dla konkretnej właściwości zobaczyć, w którym jest zdefiniowana.

Ostatnia definicja właściwości jest zużywa kompilacji. Jeśli właściwość jest ustawiona, dwa razy, druga wartość zastępuje pierwszy. Program MSBuild oblicza również, projekt w kilku przebiegów:

- PropertyGroups i Importy
- ItemDefinitionGroups
- ItemGroups
- Obiekty docelowe

W związku z tym podane w następującej kolejności:

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

Wartość "MyMetadata" dla elementu "Mójplik.txt" zostaną ocenione "B" podczas kompilacji (nie "A" i nie jest pusty)

## <a name="incremental-build-is-building-more-than-it-should"></a>Tworzy więcej niż powinien kompilacja przyrostowa

Jeśli program MSBuild jest niepotrzebnie ponownie skompilować projektu lub elementu projektu, tworzy plik dziennika kompilacji szczegółowe lub binarne. Można przeszukiwać dziennik dla pliku, który został skompilowany lub niepotrzebnie skompilowany. Dane wyjściowe wyglądają następująco:

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

Jeśli tworzysz w środowisku IDE programu Visual Studio (przy użyciu szczegółowych danych wyjściowych okna poziom szczegółowości), **okno danych wyjściowych** Wyświetla przyczyny, dlaczego każdy projekt jest nieaktualny:

```output
1>------ Up-To-Date check: Project: Project1, Configuration: Debug Win32 ------

1>Project is not up-to-date: build input 'f:\test\project1\project1\project1.h' was modified after the last build finished.
```

## <a name="create-a-binary-msbuild-log"></a>Tworzy plik dziennika msbuild binarne

1. Otwórz wiersz polecenia dla deweloperów dla używanej wersji programu Visual Studio
1. W wierszu polecenia Uruchom jedno z następujących poleceń. (Pamiętaj, aby użyć rzeczywistych wartości projektu i konfiguracji.):

    ```cmd
    Msbuild /p:Configuration="MyConfiguration";Platform="x86" /bl MySolution.sln
    ```

    lub

    ```cmd
    Msbuild /p:/p:SolutionDir="c:\MySolutionDir\";Configuration="MyConfiguration";Platform="Win32" /bl MyProject.vcxproj
    ```

Plik Msbuild.binlog zostanie utworzony w katalogu, w którym uruchomiono program MSBuild z. Można przeglądać i przeszukiwać je za pomocą [ze strukturą Podgląd dziennika Msbuild](http://www.msbuildlog.com/).

## <a name="create-a-detailed-log"></a>Tworzenie szczegółowego dziennika

1. W menu głównym programu Visual Studio, przejdź do **narzędzia** > **opcje** > **projekty i rozwiązania** >**kompilacji i uruchom**.
1. Ustaw **poziom szczegółowości kompilacji projektu programu Msbuild** do **szczegółowe** w obu polach kombi. Formanty górnej jeden kompilacja poziom szczegółowości w **okno danych wyjściowych** i drugi określa poziom szczegółowości w \<projectname\>pliku log, który jest tworzony w katalogu pośrednim każdego projektu podczas Kompilacja.
1. Z wiersza polecenia dla deweloperów programu Visual Studio wprowadź jedną z tych poleceń, zastępując rzeczywistych wartości ścieżki i konfiguracji:

    ```cmd
    Msbuild /p:Configuration="MyConfiguration";Platform="x86" /fl MySolution.sln 
    ```

    lub

    ```cmd
    Msbuild /p:/p:SolutionDir="c:\MySolutionDir\";Configuration="MyConfiguration";Platform="Win32" /fl MyProject.vcxproj
    ```

    Plik Msbuild.log zostanie utworzony w katalogu, w którym uruchomiono program msbuild z.
