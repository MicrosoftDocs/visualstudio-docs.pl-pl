---
title: MSBuild | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, about MSBuild
- MSBuild, overview
ms.assetid: e39f13f7-1e1d-4435-95ca-0c222bca071c
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c2387526860b7d6da136a72cf83727f6714e2e52
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633073"
---
# <a name="msbuild"></a>MSBuild

Aparat kompilacji firmy Microsoft to platforma do tworzenia aplikacji. Ten aparat, który jest również znany jako MSBuild, zapewnia schemat XML dla pliku projektu, który kontroluje sposób tworzenia platformy przetwarza i tworzy oprogramowanie. Visual Studio używa MSBuild, ale MSBuild nie zależy od programu Visual Studio. Wywołując *msbuild.exe* w pliku projektu lub rozwiązania, można aranżować i tworzyć produkty w środowiskach, w których program Visual Studio nie jest zainstalowany.

 Visual Studio używa MSBuild do ładowania i tworzenia zarządzanych projektów. Pliki projektu w programie Visual Studio (*.csproj*, *.vbproj*, *.vcxproj*i inne) zawierają kod XML MSBuild, który jest wykonywany podczas tworzenia projektu przy użyciu IDE. Projekty programu Visual Studio importują wszystkie niezbędne ustawienia i procesy kompilacji do wykonywania typowych prac rozwojowych, ale można rozszerzyć lub zmodyfikować je z poziomu programu Visual Studio lub za pomocą edytora XML.

 Aby uzyskać informacje o MSBuild dla języka C++, zobacz [MSBuild (C++)](/cpp/build/msbuild-visual-cpp).

 Poniższe przykłady ilustrują, kiedy można uruchomić kompilacje przez wywołanie MSBuild z wiersza polecenia zamiast środowiska IDE programu Visual Studio.

- Visual Studio nie jest zainstalowany. (Pobierz[MSBuild bez programu Visual Studio).](https://visualstudio.microsoft.com/downloads/?q=build+tools)

- Chcesz użyć 64-bitowej wersji programu MSBuild. Ta wersja MSBuild jest zwykle niepotrzebne, ale umożliwia MSBuild dostęp do większej ilości pamięci.

- Chcesz uruchomić kompilację w wielu procesach. Jednak można użyć IDE do osiągnięcia tego samego wyniku w projektach w językach C++ i C#.

- Chcesz zmodyfikować system kompilacji. Na przykład można włączyć następujące akcje:

  - Wstępnie przetwarza pliki, zanim dotrą do kompilatora.

  - Skopiuj dane wyjściowe kompilacji w inne miejsce.

  - Tworzenie skompresowanych plików z wyjść kompilacji.

  - Wykonaj etap przetwarzania końcowego. Na przykład można stemplować zestaw z inną wersją.

Można napisać kod w programie Visual Studio IDE, ale uruchomić kompilacje przy użyciu MSBuild. Jako inną alternatywę można utworzyć kod w IDE na komputerze deweloperskim, ale uruchomić MSBuild z wiersza polecenia do tworzenia kodu, który jest zintegrowany z wielu deweloperów. Można również użyć [interfejsu wiersza polecenia .NET Core (CLI),](/dotnet/core/tools/)który używa MSBuild, do tworzenia projektów .NET Core.

> [!NOTE]
> Za pomocą usługi Azure Pipelines można automatycznie kompilować, testować i wdrażać aplikację. System kompilacji można automatycznie uruchamiać kompilacje, gdy deweloperzy zaewidencjonować kod (na przykład jako część strategii ciągłej integracji) lub zgodnie z harmonogramem (na przykład co noc kompilacji testu weryfikacji kompilacji). Usługa Azure Potoki kompiluje kod przy użyciu msbuild. Aby uzyskać więcej informacji, zobacz [Potoki platformy Azure](/azure/devops/pipelines/index?view=vsts).

Ten artykuł zawiera omówienie msbuild. Aby zapoznać się z samouczkiem wprowadzającym, zobacz [Przewodnik: Korzystanie z usługi MSBuild](../msbuild/walkthrough-using-msbuild.md).

## <a name="use-msbuild-at-a-command-prompt"></a>Używanie programu MSBuild w wierszu polecenia

 Aby uruchomić program MSBuild w wierszu polecenia, przekaż plik projektu do *pliku MSBuild.exe*wraz z odpowiednimi opcjami wiersza polecenia. Opcje wiersza polecenia umożliwiają ustawianie właściwości, wykonywanie określonych obiektów docelowych i ustawianie innych opcji sterujących procesem kompilacji. Na przykład do zbudowania pliku *MyProj.proj* z właściwością ustawioną `Configuration` na `Debug`.

```cmd
MSBuild.exe MyProj.proj -property:Configuration=Debug
```

 Aby uzyskać więcej informacji o opcjach wiersza polecenia MSBuild, zobacz [Odwołanie do wiersza polecenia](../msbuild/msbuild-command-line-reference.md).

> [!IMPORTANT]
> Przed pobraniem projektu należy określić wiarygodność kodu.

## <a name="project-file"></a>Plik projektu

 MSBuild używa formatu pliku projektu opartego na języku XML, który jest prosty i rozszerzalny. Format pliku projektu MSBuild umożliwia deweloperom opisanie elementów, które mają zostać zbudowane, a także sposób ich budowy dla różnych systemów operacyjnych i konfiguracji. Ponadto format pliku projektu umożliwia deweloperom tworzenie reguł kompilacji wielokrotnegoużytnia, które można uwzględnić w oddzielnych plikach, dzięki czemu kompilacje mogą być wykonywane konsekwentnie w różnych projektach w produkcie.

 W poniższych sekcjach opisano niektóre podstawowe elementy formatu pliku projektu MSBuild. Aby zapoznać się z samouczkiem na temat tworzenia podstawowego pliku projektu, zobacz [Przewodnik: Tworzenie pliku projektu MSBuild od podstaw](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md).

### <a name="properties"></a><a name="BKMK_Properties"></a>Właściwości

 Właściwości reprezentują pary klucz/wartość, które mogą służyć do konfigurowania kompilacji. Właściwości są deklarowane przez utworzenie elementu, który ma nazwę właściwości jako element podrzędny [PropertyGroup](../msbuild/propertygroup-element-msbuild.md) elementu. Na przykład poniższy kod tworzy `BuildDir` właściwość o `Build`nazwie, która ma wartość .

```xml
<PropertyGroup>
    <BuildDir>Build</BuildDir>
</PropertyGroup>
```

 Właściwość można zdefiniować warunkowo, umieszczając `Condition` atrybut w elemencie. Zawartość elementów warunkowych jest ignorowana, chyba `true`że warunek zostanie obliczony na . W poniższym przykładzie `Configuration` element jest zdefiniowany, jeśli nie został jeszcze zdefiniowany.

```xml
<Configuration  Condition=" '$(Configuration)' == '' ">Debug</Configuration>
```

 Właściwości można odwoływać się w całym pliku projektu przy\<użyciu składni $( PropertyName>). Na przykład można odwoływać się do właściwości w `$(BuildDir)` `$(Configuration)`poprzednich przykładach za pomocą i .

 Aby uzyskać więcej informacji o właściwościach, zobacz [WŁAŚCIWOŚCI MSBuild](../msbuild/msbuild-properties.md).

### <a name="items"></a><a name="BKMK_Items"></a>Elementy

 Elementy są dane wejściowe do systemu kompilacji i zazwyczaj reprezentują pliki. Elementy są grupowane w typy elementów na podstawie nazw elementów zdefiniowanych przez użytkownika. Te typy elementów mogą służyć jako parametry dla zadań, które używają poszczególnych elementów do wykonywania kroków procesu kompilacji.

 Elementy są deklarowane w pliku projektu przez utworzenie elementu, który ma nazwę typu elementu jako element podrzędny [itemGroup](../msbuild/itemgroup-element-msbuild.md) elementu. Na przykład poniższy kod tworzy `Compile`typ elementu o nazwie , który zawiera dwa pliki.

```xml
<ItemGroup>
    <Compile Include = "file1.cs"/>
    <Compile Include = "file2.cs"/>
</ItemGroup>
```

 Typy elementów można odwoływać się w całym pliku\<projektu przy użyciu składni @( ItemType>). Na przykład typ elementu w przykładzie będzie `@(Compile)`się odwoływać za pomocą programu .

 W MSBuild nazwy elementów i atrybutów są rozróżniane. Jednak nazwy właściwości, elementów i metadanych nie są. Poniższy przykład tworzy `Compile`typ `comPile`towaru , lub dowolną inną odmianę przypadku i nadaje typowi elementu wartość "one.cs;two.cs".

```xml
<ItemGroup>
  <Compile Include="one.cs" />
  <comPile Include="two.cs" />
</ItemGroup>
```

 Elementy mogą być zadeklarowane przy użyciu symboli wieloznacznych i może zawierać dodatkowe metadane dla bardziej zaawansowanych scenariuszy kompilacji. Aby uzyskać więcej informacji o towarach, zobacz [Elementy](../msbuild/msbuild-items.md).

### <a name="tasks"></a><a name="BKMK_Tasks"></a>Zadania

 Zadania są jednostkami kodu wykonywalnego, które projekty MSBuild używają do wykonywania operacji kompilacji. Na przykład zadanie może skompilować pliki wejściowe lub uruchomić narzędzie zewnętrzne. Zadania mogą być ponownie za pomocą wielu ekscyt i mogą być współużytkowane przez różnych deweloperów w różnych projektach.

 Logika wykonywania zadania jest zapisywana w kodzie zarządzanym i mapowana na MSBuild przy użyciu [UsingTask](../msbuild/usingtask-element-msbuild.md) element. Można napisać własne zadanie, tworząc typ zarządzany, <xref:Microsoft.Build.Framework.ITask> który implementuje interfejs. Aby uzyskać więcej informacji na temat pisania zadań, zobacz [Pisanie zadań](../msbuild/task-writing.md).

 MSBuild zawiera typowe zadania, które można modyfikować zgodnie z wymaganiami. Przykładami są [Kopiuj](../msbuild/copy-task.md), który kopiuje pliki, [MakeDir](../msbuild/makedir-task.md), który tworzy katalogi, i [Csc](../msbuild/csc-task.md), który kompiluje pliki kodu źródłowego języka Visual C#. Aby uzyskać listę dostępnych zadań wraz z informacjami o użyciu, zobacz [Odwołanie do zadania](../msbuild/msbuild-task-reference.md).

 Zadanie jest wykonywane w pliku projektu MSBuild przez utworzenie elementu, który ma nazwę zadania jako element podrzędny elementu [target.](../msbuild/target-element-msbuild.md) Zadania zazwyczaj akceptują parametry, które są przekazywane jako atrybuty elementu. Właściwości MSBuild i elementy mogą służyć jako parametry. Na przykład następujący kod wywołuje [makedir](../msbuild/makedir-task.md) zadania i przekazuje `BuildDir` go wartość właściwości, która została zadeklarowana we wcześniejszym przykładzie.

```xml
<Target Name="MakeBuildDirectory">
    <MakeDir  Directories="$(BuildDir)" />
</Target>
```

 Aby uzyskać więcej informacji o zadaniach, zobacz [Zadania](../msbuild/msbuild-tasks.md).

### <a name="targets"></a><a name="BKMK_Targets"></a>Cele

 Cele grupowania zadań razem w określonej kolejności i uwidaczniają sekcje pliku projektu jako punkty wejścia w procesie kompilacji. Obiekty docelowe są często pogrupowane w sekcje logiczne, aby zwiększyć czytelność i umożliwić jej rozszerzenie. Podział kroków kompilacji na obiekty docelowe umożliwia wywołanie jednego fragmentu procesu kompilacji z innych obiektów docelowych bez kopiowania tej sekcji kodu do każdego obiektu docelowego. Na przykład jeśli kilka punktów wejścia do procesu kompilacji wymagają odwołań do utworzenia, można utworzyć obiekt docelowy, który tworzy odwołania, a następnie uruchomić ten cel z każdego punktu wejścia, gdzie jest to wymagane.

 Obiekty docelowe są deklarowane w pliku projektu przy użyciu elementu [target.](../msbuild/target-element-msbuild.md) Na przykład poniższy kod tworzy `Compile`obiekt docelowy o nazwie , który następnie wywołuje zadanie [Csc,](../msbuild/csc-task.md) które ma listę elementów, która została zadeklarowana we wcześniejszym przykładzie.

```xml
<Target Name="Compile">
    <Csc Sources="@(Compile)" />
</Target>
```

 W bardziej zaawansowanych scenariuszach obiekty docelowe mogą służyć do opisywania relacji między sobą i wykonywania analizy zależności, dzięki czemu można pominąć całe sekcje procesu kompilacji, jeśli ten obiekt docelowy jest aktualny. Aby uzyskać więcej informacji o celach, zobacz [Cele](../msbuild/msbuild-targets.md).

## <a name="build-logs"></a>Tworzenie dzienników

 Można rejestrować błędy kompilacji, ostrzeżenia i komunikaty do konsoli lub innego urządzenia wyjściowego. Aby uzyskać więcej informacji, zobacz [Uzyskiwanie dzienników kompilacji](../msbuild/obtaining-build-logs-with-msbuild.md) i [rejestrowanie w programie MSBuild](../msbuild/logging-in-msbuild.md).

## <a name="use-msbuild-in-visual-studio"></a>Używanie usługi MSBuild w programie Visual Studio

 Visual Studio używa formatu pliku projektu MSBuild do przechowywania informacji kompilacji o projektach zarządzanych. Ustawienia projektu, które są dodawane lub zmieniane przy użyciu interfejsu programu Visual Studio, są odzwierciedlane w *pliku .\* proj,* który jest generowany dla każdego projektu. Visual Studio używa hostowanego wystąpienia MSBuild do tworzenia zarządzanych projektów. Oznacza to, że zarządzany projekt może być zbudowany w programie Visual Studio lub w wierszu polecenia (nawet jeśli program Visual Studio nie jest zainstalowany), a wyniki będą identyczne.

 Aby zapoznać się z samouczkiem na temat używania usługi MSBuild w programie Visual Studio, zobacz [Instruktaż: Korzystanie z usługi MSBuild](../msbuild/walkthrough-using-msbuild.md).

## <a name="multitargeting"></a><a name="BKMK_Multitargeting"></a>Wielotargowe

 Za pomocą programu Visual Studio, można skompilować aplikację do uruchomienia w dowolnej z kilku wersji programu .NET Framework. Na przykład można skompilować aplikację do uruchomienia na platformie .NET Framework 2.0 na platformie 32-bitowej i można skompilować tę samą aplikację do uruchomienia na platformie .NET Framework 4.5 na platformie 64-bitowej. Możliwość kompilowania do więcej niż jednej struktury nosi nazwę multitargeting.

 Oto niektóre z zalet multitargetingu:

- Można tworzyć aplikacje, które są przeznaczone dla wcześniejszych wersji programu .NET Framework, na przykład wersje 2.0, 3.0 i 3.5.

- Można kierować struktury inne niż .NET Framework, na przykład Silverlight.

- Można kierować *profil struktury*, który jest wstępnie zdefiniowany podzbiór struktury docelowej.

- Jeśli dodatek Service Pack dla bieżącej wersji programu .NET Framework zostanie wydany, można go kierować.

- Multitargeting gwarantuje, że aplikacja używa tylko funkcje, które są dostępne w ramach docelowej i platformy.

Aby uzyskać więcej informacji, zobacz [Multitargeting](../msbuild/msbuild-multitargeting-overview.md).

## <a name="see-also"></a>Zobacz też

| Tytuł | Opis |
| - | - |
| [Przewodnik: Tworzenie pliku projektu MSBuild od podstaw](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md) | Pokazuje, jak tworzyć podstawowy plik projektu przyrostowo, używając tylko edytora tekstu. |
| [Przewodnik: Używanie programu MSBuild](../msbuild/walkthrough-using-msbuild.md) | Przedstawia bloki konstrukcyjne MSBuild i pokazuje, jak pisać, manipulować i debugować projekty MSBuild bez zamykania środowiska IDE programu Visual Studio. |
| [Koncepcje MSBuild](../msbuild/msbuild-concepts.md) | Przedstawia cztery bloki konstrukcyjne MSBuild: właściwości, elementy, obiekty docelowe i zadania. |
| [Items](../msbuild/msbuild-items.md) | Opisuje ogólne pojęcia dotyczące formatu pliku MSBuild i jak elementy pasują do siebie. |
| [Właściwości MSBuild](../msbuild/msbuild-properties.md) | Wprowadza właściwości i kolekcje właściwości. Właściwości są pary klucz/wartość, które mogą służyć do konfigurowania kompilacji. |
| [Cele](../msbuild/msbuild-targets.md) | W tym artykule wyjaśniono, jak grupować zadania w określonej kolejności i włączać sekcje procesu kompilacji, które mają być wywoływane w wierszu polecenia. |
| [Zadania](../msbuild/msbuild-tasks.md) | Pokazuje, jak utworzyć jednostkę kodu wykonywalnego, który może być używany przez MSBuild do wykonywania operacji kompilacji niepodzielnej. |
| [Warunki](../msbuild/msbuild-conditions.md) | W tym artykule `Condition` omówiono sposób używania atrybutu w elemencie MSBuild. |
| [Pojęcia zaawansowane](../msbuild/msbuild-advanced-concepts.md) | Przedstawia przetwarzanie wsadowe, wykonywanie przekształceń, multitargeting i inne zaawansowane techniki. |
| [Logowanie w programie MSBuild](../msbuild/logging-in-msbuild.md) | W tym artykule opisano sposób rejestrowania zdarzeń kompilacji, komunikatów i błędów. |
| [Zasoby dodatkowe](https://social.msdn.microsoft.com/forums/vstudio/home?forum=msbuild) | Wyświetla listę zasobów społeczności i pomocy technicznej, aby uzyskać więcej informacji na temat MSBuild. |

## <a name="reference"></a>Dokumentacja

- [Odwołanie do budynku MSBuild](../msbuild/msbuild-reference.md)\
 Łącza do tematów zawierających informacje referencyjne.

- [Słownik entry](msbuild-glossary.md)\
 Definiuje typowe terminy MSBuild.
