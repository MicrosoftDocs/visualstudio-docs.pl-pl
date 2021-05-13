---
title: MsBuild | Microsoft Docs
description: Dowiedz się, jak platforma Microsoft Build Engine (MSBuild) udostępnia plik projektu ze schematem XML do sterowania kompilacjami.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, about MSBuild
- MSBuild, overview
ms.assetid: e39f13f7-1e1d-4435-95ca-0c222bca071c
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 372fc5c81b963cbb8e46cab689713e476fcfff7d
ms.sourcegitcommit: 9cb0097c33755a3e5cbadde3b0a6e9e76cee727d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2021
ms.locfileid: "109848282"
---
# <a name="msbuild"></a>MSBuild

Ta Microsoft Build Engine to platforma do tworzenia aplikacji. Ten aparat, znany również jako MSBuild, udostępnia schemat XML dla pliku projektu, który kontroluje sposób procesów i kompilacji oprogramowania przez platformę kompilacji. Visual Studio korzysta z programu MSBuild, ale nie zależy od Visual Studio. Za pomocą wywołania *msbuild.exe* pliku projektu lub rozwiązania można orkiestrować i kompilować produkty w środowiskach, Visual Studio nie są zainstalowane.

 Visual Studio używa programu MSBuild do ładowania i kompilowania projektów zarządzanych. Pliki projektu w programie Visual Studio *(pliki csproj,* *vbproj,* *vcxproj* i inne) zawierają kod XML programu MSBuild, który jest wykonywany podczas kompilowania projektu przy użyciu środowiska IDE. Visual Studio importują wszystkie niezbędne ustawienia i procesy kompilacji do typowych prac programistacyjnych, ale można je rozszerzać lub modyfikować z poziomu programu Visual Studio lub za pomocą edytora XML.

 Aby uzyskać informacje o programie MSBuild dla języka C++, [zobacz MSBuild (C++)](/cpp/build/msbuild-visual-cpp).

 W poniższych przykładach pokazano, kiedy można uruchamiać kompilacje, inicjując program MSBuild z wiersza polecenia zamiast Visual Studio IDE.

- Visual Studio nie jest zainstalowana. (Pobierz[program MSBuild bez Visual Studio](https://visualstudio.microsoft.com/downloads/?q=build+tools).)

- Chcesz użyć 64-bitowej wersji programu MSBuild. Ta wersja programu MSBuild jest zwykle niepotrzebna, ale umożliwia programowi MSBuild dostęp do większej ilości pamięci.

- Chcesz uruchomić kompilację w wielu procesach. Można jednak użyć środowiska IDE, aby osiągnąć ten sam wynik w projektach w językach C++ i C#.

- Chcesz zmodyfikować system kompilacji. Można na przykład włączyć następujące akcje:

  - Przetwarzaj wstępnie pliki, zanim dotrą do kompilatora.

  - Skopiuj dane wyjściowe kompilacji do innego miejsca.

  - Tworzenie skompresowanych plików z danych wyjściowych kompilacji.

  - Wykonaj krok przetwarzania po przetwarzaniu. Na przykład możesz chcieć sygnaturę zestawu z inną wersją.

Możesz napisać kod w Visual Studio IDE, ale uruchamiać kompilacje przy użyciu programu MSBuild. Innym rozwiązaniem jest skompilowanie kodu w idee na komputerze dewelopera, ale uruchomienie programu MSBuild z wiersza polecenia w celu skompilowania kodu zintegrowanego przez wielu deweloperów. Do kompilowania projektów .NET Core można również użyć interfejsu wiersza polecenia [.NET Core,](/dotnet/core/tools/)który używa programu MSBuild.

> [!NOTE]
> Za pomocą Azure Pipelines można automatycznie kompilować, testować i wdrażać aplikację. System kompilacji może automatycznie uruchamiać kompilacje, gdy deweloperzy zaewidencjują kod (na przykład w ramach strategii ciągłej integracji) lub zgodnie z harmonogramem (na przykład nocnej kompilacji testu weryfikacyjnego kompilacji). Azure Pipelines kompiluje kod przy użyciu programu MSBuild. Aby uzyskać więcej informacji, zobacz [Azure Pipelines](/azure/devops/pipelines/index?view=vsts&preserve-view=true).

Ten artykuł zawiera omówienie programu MSBuild. Aby uzyskać samouczek wprowadzający, zobacz [Przewodnik: korzystanie z programu MSBuild.](../msbuild/walkthrough-using-msbuild.md)

## <a name="use-msbuild-at-a-command-prompt"></a>Używanie programu MSBuild w wierszu polecenia

 Aby uruchomić program MSBuild w wierszu polecenia, przekaż plik projektu doMSBuild.exe *,* wraz z odpowiednimi opcjami wiersza polecenia. Opcje wiersza polecenia umożliwiają ustawianie właściwości, wykonywanie określonych obiektów docelowych i ustawianie innych opcji, które kontrolują proces kompilacji. Na przykład użyj następującej składni wiersza polecenia, aby skompilować plik *MyProj.proj* z `Configuration` właściwością ustawioną na `Debug` .

```cmd
MSBuild.exe MyProj.proj -property:Configuration=Debug
```

 Aby uzyskać więcej informacji na temat opcji wiersza polecenia programu MSBuild, zobacz [Informacje o wierszu polecenia](../msbuild/msbuild-command-line-reference.md).

> [!IMPORTANT]
> Przed pobraniem projektu należy określić wiarygodność kodu.

## <a name="project-file"></a>Plik projektu

 Program MSBuild używa formatu pliku projektu opartego na języku XML, który jest prosty i rozszerzalny. Format pliku projektu MSBuild umożliwia deweloperom opisywanie elementów, które mają zostać sbudowaną, a także sposób ich budowania dla różnych systemów operacyjnych i konfiguracji. Ponadto format pliku projektu umożliwia deweloperom tworzenie reguł kompilacji wielokrotnego użytku, które można uwzględniać w oddzielnych plikach, dzięki czemu kompilacje mogą być wykonywane spójnie w różnych projektach produktu.

 W poniższych sekcjach opisano niektóre podstawowe elementy formatu pliku projektu MSBuild. Aby uzyskać samouczek dotyczący tworzenia podstawowego pliku projektu, zobacz [Przewodnik: tworzenie pliku projektu MSBuild od podstaw.](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)

### <a name="properties"></a><a name="BKMK_Properties"></a> Właściwości

 Właściwości reprezentują pary klucz/wartość, których można użyć do konfigurowania kompilacji. Właściwości są deklarowane przez utworzenie elementu o nazwie właściwości jako elementu podrzędnego elementu [PropertyGroup.](../msbuild/propertygroup-element-msbuild.md) Na przykład poniższy kod tworzy właściwość o nazwie `BuildDir` , która ma wartość `Build` .

```xml
<PropertyGroup>
    <BuildDir>Build</BuildDir>
</PropertyGroup>
```

 Właściwość można zdefiniować warunkowo, umieszczając `Condition` atrybut w elemencie . Zawartość elementów warunkowych jest ignorowana, chyba że warunek ma wartość `true` . W poniższym przykładzie `Configuration` element jest definiowany, jeśli nie został jeszcze zdefiniowany.

```xml
<Configuration  Condition=" '$(Configuration)' == '' ">Debug</Configuration>
```

 Odwołania do właściwości można odwoływać się w całym pliku projektu przy użyciu składni $( \<PropertyName> ). Na przykład można odwoływać się do właściwości w poprzednich przykładach przy użyciu `$(BuildDir)` i `$(Configuration)` .

 Aby uzyskać więcej informacji na temat właściwości, zobacz [Właściwości programu MSBuild.](../msbuild/msbuild-properties.md)

### <a name="items"></a><a name="BKMK_Items"></a> Elementy

 Elementy są wejściami do systemu kompilacji i zazwyczaj reprezentują pliki. Elementy są grupowane w typy elementów na podstawie nazw elementów zdefiniowanych przez użytkownika. Te typy elementów mogą służyć jako parametry dla zadań, które używają poszczególnych elementów do wykonywania kroków procesu kompilacji.

 Elementy są deklarowane w pliku projektu przez utworzenie elementu o nazwie typu elementu jako elementu podrzędnego [elementu ItemGroup.](../msbuild/itemgroup-element-msbuild.md) Na przykład poniższy kod tworzy typ elementu o nazwie `Compile` , który zawiera dwa pliki.

```xml
<ItemGroup>
    <Compile Include = "file1.cs"/>
    <Compile Include = "file2.cs"/>
</ItemGroup>
```

 Odwołania do typów elementów można odwoływać się w całym pliku projektu przy użyciu składni @( \<ItemType> ). Na przykład typ elementu w przykładzie zostanie przywołyny przy użyciu elementu `@(Compile)` .

 W programie MSBuild w nazwach elementów i atrybutów jest wielkość liter. Nie są to jednak nazwy właściwości, elementów i metadanych. Poniższy przykład tworzy typ elementu , lub dowolną inną odmianę przypadku i nadaje elementowi wartość `Compile` `comPile` "one.cs;two.cs".

```xml
<ItemGroup>
  <Compile Include="one.cs" />
  <Compile Include="two.cs" />
</ItemGroup>
```

 Elementy mogą być deklarowane przy użyciu symboli wieloznacznych i mogą zawierać dodatkowe metadane dla bardziej zaawansowanych scenariuszy kompilacji. Aby uzyskać więcej informacji na temat elementów, zobacz [Items](../msbuild/msbuild-items.md).

### <a name="tasks"></a><a name="BKMK_Tasks"></a> Zadania

 Zadania to jednostki kodu wykonywalnego, których projekty MSBuild używają do wykonywania operacji kompilacji. Na przykład zadanie może skompilować pliki wejściowe lub uruchomić zewnętrzne narzędzie. Zadania mogą być ponownie używane i mogą być współużytkowane przez różnych deweloperów w różnych projektach.

 Logika wykonywania zadania jest zapisywana w kodzie zarządzanym i mapowana do programu MSBuild przy użyciu [elementu UsingTask.](../msbuild/usingtask-element-msbuild.md) Możesz napisać własne zadanie, tworzenie zarządzanego typu, który implementuje <xref:Microsoft.Build.Framework.ITask> interfejs. Aby uzyskać więcej informacji na temat pisania zadań, zobacz [Task writing](../msbuild/task-writing.md).

 Program MSBuild zawiera typowe zadania, które można modyfikować, aby odpowiadały Twoim potrzebom. Przykłady [to Copy](../msbuild/copy-task.md), który kopiuje pliki, [MakeDir](../msbuild/makedir-task.md), który tworzy katalogi, i [Csc](../msbuild/csc-task.md), który kompiluje pliki kodu źródłowego Visual C#. Aby uzyskać listę dostępnych zadań wraz z informacjami o użyciu, zobacz [Task reference (Informacje o zadaniu).](../msbuild/msbuild-task-reference.md)

 Zadanie jest wykonywane w pliku projektu MSBuild przez utworzenie elementu, który ma nazwę zadania jako element podrzędny [elementu target.](../msbuild/target-element-msbuild.md) Zadania zwykle akceptują parametry, które są przekazywane jako atrybuty elementu. Właściwości i elementy programu MSBuild mogą być używane jako parametry. Na przykład poniższy kod wywołuje zadanie [MakeDir](../msbuild/makedir-task.md) i przekazuje do niego wartość właściwości, `BuildDir` która została zadeklarowana we wcześniejszym przykładzie.

```xml
<Target Name="MakeBuildDirectory">
    <MakeDir  Directories="$(BuildDir)" />
</Target>
```

 Aby uzyskać więcej informacji na temat zadań, zobacz [Zadania](../msbuild/msbuild-tasks.md).

### <a name="targets"></a><a name="BKMK_Targets"></a> Cele

 Obiekty docelowe grupują zadania w określonej kolejności i uwidoczniają sekcje pliku projektu jako punkty wejścia do procesu kompilacji. Obiekty docelowe są często pogrupowane w sekcje logiczne w celu zwiększenia czytelności i umożliwienia rozszerzania. Podział kroków kompilacji na obiekty docelowe umożliwia wywołanie jednego elementu procesu kompilacji z innych obiektów docelowych bez kopiowania tej sekcji kodu do każdego elementu docelowego. Jeśli na przykład kilka punktów wejścia do procesu kompilacji wymaga skompilowania odwołań, możesz utworzyć element docelowy, który tworzy odwołania, a następnie uruchomić ten element docelowy z każdego punktu wejścia, w którym jest to wymagane.

 Elementy docelowe są deklarowane w pliku projektu przy użyciu [elementu Target.](../msbuild/target-element-msbuild.md) Na przykład poniższy kod tworzy element docelowy o nazwie , który następnie wywołuje zadanie Csc, które ma listę elementów zadeklarowaną `Compile` we wcześniejszym [](../msbuild/csc-task.md) przykładzie.

```xml
<Target Name="Compile">
    <Csc Sources="@(Compile)" />
</Target>
```

 W bardziej zaawansowanych scenariuszach obiekty docelowe mogą służyć do opisywania relacji między sobą i analizowania zależności, aby można było pominąć całe sekcje procesu kompilacji, jeśli ten element docelowy jest aktualny. Aby uzyskać więcej informacji na temat obiektów docelowych, zobacz [Targets ( Cele).](../msbuild/msbuild-targets.md)

## <a name="build-logs"></a>Dzienniki kompilacji

 Błędy kompilacji, ostrzeżenia i komunikaty można rejestrować w konsoli lub innym urządzeniu wyjściowym. Aby uzyskać więcej informacji, zobacz Obtaining build logs and Logging in MSBuild (Uzyskiwanie [dzienników kompilacji](../msbuild/obtaining-build-logs-with-msbuild.md) i [rejestrowanie w programie MSBuild).](../msbuild/logging-in-msbuild.md)

## <a name="use-msbuild-in-visual-studio"></a>Używanie programu MSBuild w programie Visual Studio

 Visual Studio format pliku projektu MSBuild jest używany do przechowywania informacji o kompilacji dotyczących zarządzanych projektów. Ustawienia projektu, które są dodawane lub zmieniane przy użyciu interfejsu Visual Studio są odzwierciedlane w *. \* plik proj* generowany dla każdego projektu. Visual Studio używa hostowanych wystąpień programu MSBuild do kompilowania projektów zarządzanych. Oznacza to, że projekt zarządzany może być wbudowany Visual Studio wiersza polecenia (nawet jeśli Visual Studio nie jest zainstalowany), a wyniki będą identyczne.

 Aby uzyskać samouczek dotyczący używania programu MSBuild w programie Visual Studio, zobacz [Przewodnik: korzystanie z programu MSBuild.](../msbuild/walkthrough-using-msbuild.md)

## <a name="multitargeting"></a><a name="BKMK_Multitargeting"></a> Wieloadążeń

 Za pomocą Visual Studio można skompilować aplikację do uruchamiania w dowolnej z kilku wersji .NET Framework. Na przykład można skompilować aplikację do uruchamiania w programie .NET Framework 2.0 na platformie 32-bitowej, a tę samą aplikację można skompilować do uruchomienia na platformie .NET Framework 4.5 na platformie 64-bitowej. Możliwość kompilowania do więcej niż jednej struktury nosi nazwę wielotarkowania.

 Oto niektóre z zalet wielowątkowania:

- Można tworzyć aplikacje, które są docelowe dla wcześniejszych wersji .NET Framework, na przykład w wersjach 2.0, 3.0 i 3.5.

- Można kierować do platform innych niż .NET Framework, na przykład Silverlight.

- Można wybrać profil *struktury*, który jest wstępnie zdefiniowanym podzbiorem struktury docelowej.

- Jeśli dodatek Service Pack dla bieżącej wersji .NET Framework został wydany, można go ukierunkować.

- Wielopozysłowy gwarantuje, że aplikacja używa tylko funkcji dostępnych w docelowej platformie i platformie.

Aby uzyskać więcej informacji, zobacz [Multitargeting](../msbuild/msbuild-multitargeting-overview.md).

## <a name="see-also"></a>Zobacz też

| Tytuł | Opis |
| - | - |
| [Przewodnik: Tworzenie pliku projektu MSBuild od zera](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md) | Pokazuje, jak przyrostowo tworzyć podstawowy plik projektu przy użyciu tylko edytora tekstów. |
| [Przewodnik: Korzystanie z programu MSBuild](../msbuild/walkthrough-using-msbuild.md) | Wprowadzenie do bloków konstrukcyjnych programu MSBuild i pokazuje, jak pisać, manipulować i debugować projekty MSBuild bez zamykania Visual Studio IDE. |
| [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md) | Przedstawia cztery bloki konstrukcyjne programu MSBuild: właściwości, elementy, elementy docelowe i zadania. |
| [Elementy](../msbuild/msbuild-items.md) | W tym artykule opisano ogólne pojęcia związane z formatem pliku MSBuild oraz sposób dopasowania tych elementów do siebie. |
| [właściwości programu MSBuild](../msbuild/msbuild-properties.md) | Wprowadza właściwości i kolekcje właściwości. Właściwości to pary klucz/wartość, których można użyć do konfigurowania kompilacji. |
| [Targets (Obiekty docelowe)](../msbuild/msbuild-targets.md) | Wyjaśnia, jak grupować zadania w określonej kolejności i umożliwić wywoływanie sekcji procesu kompilacji w wierszu polecenia. |
| [Zadania](../msbuild/msbuild-tasks.md) | Pokazuje, jak utworzyć jednostkę kodu wykonywalnego, która może być używana przez program MSBuild do wykonywania niepodzielnych operacji kompilacji. |
| [Warunki](../msbuild/msbuild-conditions.md) | W tym artykule omówiono sposób `Condition` używania atrybutu w elemencie MSBuild. |
| [Pojęcia zaawansowane](../msbuild/msbuild-advanced-concepts.md) | Przedstawia przetwarzanie wsadowe, wykonywanie przekształceń, wielotargeting i inne zaawansowane techniki. |
| [Logowanie w programie MSBuild](../msbuild/logging-in-msbuild.md) | Opisuje sposób rejestrować zdarzenia kompilacji, komunikaty i błędy. |
| [Jak program MSBuild kompiluje projekty](build-process-overview.md) | Opisuje wewnętrzny proces kompilacji używany w programie MSBuild |
| [Dodatkowe zasoby](https://social.msdn.microsoft.com/forums/vstudio/home?forum=msbuild) | Wyświetla listę zasobów społeczności i pomocy technicznej, aby uzyskać więcej informacji na temat programu MSBuild. |

## <a name="reference"></a>Odwołanie

- [Odwołanie do programu MSBuild](../msbuild/msbuild-reference.md)\
 Linki do tematów zawierających informacje referencyjne.

- [Słownik entry](msbuild-glossary.md)\
 Definiuje typowe terminy msbuild.
