---
title: MSBuild | Microsoft Docs
description: Dowiedz się, jak platforma Microsoft Build Engine (MSBuild) udostępnia plik projektu ze schematem XML, aby kontrolować kompilacje.
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
ms.openlocfilehash: dbf938e61cc1567beb682847821595f5ca6cc026
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905466"
---
# <a name="msbuild"></a>MSBuild

Microsoft Build Engine to platforma do kompilowania aplikacji. Ten aparat, który jest również znany jako MSBuild, zawiera schemat XML dla pliku projektu, który kontroluje, w jaki sposób platforma kompilacji przetwarza i tworzy oprogramowanie. Program Visual Studio używa programu MSBuild, ale MSBuild nie zależy od programu Visual Studio. Wywołując *msbuild.exe* w pliku projektu lub rozwiązania, można organizować i kompilować produkty w środowiskach, w których nie zainstalowano programu Visual Studio.

 Program Visual Studio używa programu MSBuild do ładowania i kompilowania projektów zarządzanych. Pliki projektu w programie Visual Studio (*. csproj*, *. vbproj*, *. vcxproj* i inne) zawierają kod XML programu MSBuild, który jest wykonywany podczas kompilowania projektu przy użyciu środowiska IDE. Projekty programu Visual Studio zaimportują wszystkie niezbędne ustawienia i procesy kompilacji, aby wykonywać typowe prace programistyczne, ale można je rozbudować lub zmodyfikować z poziomu programu Visual Studio lub za pomocą edytora XML.

 Aby uzyskać informacje na temat programu MSBuild dla języka C++, zobacz [MSBuild (C++)](/cpp/build/msbuild-visual-cpp).

 Poniższe przykłady ilustrują, kiedy można uruchamiać kompilacje przez wywoływanie MSBuild z wiersza polecenia zamiast środowiska IDE programu Visual Studio.

- Program Visual Studio nie jest zainstalowany. ([Pobierz program MSBuild bez programu Visual Studio](https://visualstudio.microsoft.com/downloads/?q=build+tools)).

- Chcesz użyć 64-bitowej wersji programu MSBuild. Ta wersja programu MSBuild jest zwykle zbędna, ale umożliwia MSBuild dostęp do większej ilości pamięci.

- Chcesz uruchomić kompilację w wielu procesach. Można jednak użyć IDE, aby osiągnąć ten sam wynik w projektach w językach C++ i C#.

- Chcesz zmodyfikować system kompilacji. Na przykład możesz chcieć włączyć następujące akcje:

  - Przetwarzaj wstępnie pliki przed osiągnięciem kompilatora.

  - Skopiuj dane wyjściowe kompilacji do innego miejsca.

  - Twórz skompresowane pliki na podstawie danych wyjściowych kompilacji.

  - Wykonaj krok przetwarzania końcowego. Na przykład możesz chcieć oznaczyć zestaw przy użyciu innej wersji.

Można napisać kod w środowisku IDE programu Visual Studio, ale uruchamiać kompilacje przy użyciu programu MSBuild. Alternatywnie można skompilować kod w środowisku IDE na komputerze deweloperskim, ale uruchomić program MSBuild z wiersza polecenia, aby skompilować kod, który jest zintegrowany z wielu deweloperów. Do kompilowania projektów .NET Core można także użyć [interfejsu wiersza polecenia (CLI) platformy .NET Core](/dotnet/core/tools/), który używa programu MSBuild.

> [!NOTE]
> Za pomocą Azure Pipelines można automatycznie kompilować, testować i wdrażać aplikację. System kompilacji może automatycznie uruchamiać kompilacje, gdy deweloperzy ewidencjonują kod (na przykład w ramach strategii ciągłej integracji) lub zgodnie z harmonogramem (na przykład w przypadku nocnej kompilacji testu weryfikacyjnego). Azure Pipelines kompiluje kod przy użyciu programu MSBuild. Aby uzyskać więcej informacji, zobacz [Azure Pipelines](/azure/devops/pipelines/index?view=vsts&preserve-view=true).

Ten artykuł zawiera omówienie programu MSBuild. Aby zapoznać się z samouczkiem wprowadzającym, zobacz [Przewodnik: korzystanie z programu MSBuild](../msbuild/walkthrough-using-msbuild.md).

## <a name="use-msbuild-at-a-command-prompt"></a>Korzystanie z programu MSBuild w wierszu polecenia

 Aby uruchomić program MSBuild w wierszu polecenia, Przekaż plik projektu do *MSBuild.exe*, wraz z odpowiednimi opcjami wiersza polecenia. Opcje wiersza polecenia umożliwiają ustawianie właściwości, wykonywanie określonych elementów docelowych i ustawianie innych opcji kontrolujących proces kompilacji. Na przykład, można użyć następującej składni wiersza polecenia do skompilowania pliku *webproj. proj* z `Configuration` właściwością ustawioną na `Debug` .

```cmd
MSBuild.exe MyProj.proj -property:Configuration=Debug
```

 Aby uzyskać więcej informacji na temat opcji wiersza polecenia programu MSBuild, zobacz informacje dotyczące [wiersza polecenia](../msbuild/msbuild-command-line-reference.md).

> [!IMPORTANT]
> Przed pobraniem projektu należy określić wiarygodność kodu.

## <a name="project-file"></a>Plik projektu

 MSBuild używa formatu pliku projektu opartego na języku XML, który jest prosty i rozszerzalny. Format pliku projektu programu MSBuild pozwala deweloperom opisać elementy, które mają zostać skompilowane, a także jak mają być skompilowane dla różnych systemów operacyjnych i konfiguracji. Ponadto format pliku projektu umożliwia deweloperom tworzenie reguł kompilacji wielokrotnego użytku, które można umieścić w osobnych plikach, dzięki czemu kompilacje mogą być wykonywane spójnie w różnych projektach w produkcie.

 W poniższych sekcjach opisano niektóre podstawowe elementy formatu pliku projektu programu MSBuild. Aby zapoznać się z samouczkiem dotyczącym tworzenia podstawowego pliku projektu, zobacz [Przewodnik: Tworzenie pliku projektu MSBuild od podstaw](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md).

### <a name="properties"></a><a name="BKMK_Properties"></a> Właściwości

 Właściwości reprezentują pary klucz/wartość, których można użyć do konfigurowania kompilacji. Właściwości są deklarowane przez utworzenie elementu, który ma nazwę właściwości jako element podrzędny elementu [Właściwości](../msbuild/propertygroup-element-msbuild.md) . Na przykład poniższy kod tworzy właściwość o nazwie `BuildDir` , która ma wartość `Build` .

```xml
<PropertyGroup>
    <BuildDir>Build</BuildDir>
</PropertyGroup>
```

 Właściwość można definiować warunkowo, umieszczając `Condition` atrybut w elemencie. Zawartość elementów warunkowych jest ignorowana, jeśli warunek nie zostanie spełniony `true` . W poniższym przykładzie `Configuration` element jest zdefiniowany, jeśli nie został jeszcze zdefiniowany.

```xml
<Configuration  Condition=" '$(Configuration)' == '' ">Debug</Configuration>
```

 Do właściwości można odwoływać się w całym pliku projektu przy użyciu składni $ ( \<PropertyName> ). Na przykład można odwołać się do właściwości w poprzednich przykładach przy użyciu `$(BuildDir)` i `$(Configuration)` .

 Aby uzyskać więcej informacji na temat właściwości, zobacz [Właściwości programu MSBuild](../msbuild/msbuild-properties.md).

### <a name="items"></a><a name="BKMK_Items"></a> Produktów

 Elementy są wejściami do systemu kompilacji i zazwyczaj reprezentują pliki. Elementy są pogrupowane w typy elementów na podstawie nazw elementów zdefiniowanych przez użytkownika. Te typy elementów mogą służyć jako parametry zadań, które wykorzystują poszczególne elementy do wykonywania kroków procesu kompilacji.

 Elementy są zadeklarowane w pliku projektu przez utworzenie elementu, który ma nazwę typu elementu jako element podrzędny elementu [Item](../msbuild/itemgroup-element-msbuild.md) . Na przykład poniższy kod tworzy typ elementu o nazwie `Compile` , który zawiera dwa pliki.

```xml
<ItemGroup>
    <Compile Include = "file1.cs"/>
    <Compile Include = "file2.cs"/>
</ItemGroup>
```

 Do typów elementów można się odwoływać w całym pliku projektu przy użyciu składni @ ( \<ItemType> ). Na przykład typ elementu w przykładzie może być przywoływany za pomocą `@(Compile)` .

 W programie MSBuild nazwy elementów i atrybutów są rozróżniane wielkości liter. Jednak nazwy właściwości, elementów i metadanych nie są. W poniższym przykładzie jest tworzony typ elementu `Compile` , `comPile` , lub jakakolwiek inna odmiana przypadku, a typ elementu to wartość "jeden. cs; dwa. cs".

```xml
<ItemGroup>
  <Compile Include="one.cs" />
  <comPile Include="two.cs" />
</ItemGroup>
```

 Elementy mogą być deklarowane przy użyciu symboli wieloznacznych i mogą zawierać dodatkowe metadane dla bardziej zaawansowanych scenariuszy kompilacji. Aby uzyskać więcej informacji o elementach, zobacz [Items](../msbuild/msbuild-items.md).

### <a name="tasks"></a><a name="BKMK_Tasks"></a> Widoku

 Zadania są jednostkami kodu wykonywalnego, które są używane przez projekty MSBuild do wykonywania operacji kompilacji. Na przykład zadanie może kompilować pliki wejściowe lub uruchomić narzędzie zewnętrzne. Zadania mogą być ponownie używane i mogą być współużytkowane przez różnych deweloperów w różnych projektach.

 Logika wykonywania zadania jest zapisywana w kodzie zarządzanym i mapowana na MSBuild przy użyciu elementu [UsingTask](../msbuild/usingtask-element-msbuild.md) . Można napisać własne zadanie, tworząc typ zarządzany, który implementuje <xref:Microsoft.Build.Framework.ITask> interfejs. Aby uzyskać więcej informacji o sposobach pisania zadań, zobacz [Zapisywanie zadań](../msbuild/task-writing.md).

 Program MSBuild zawiera typowe zadania, które można modyfikować zgodnie z wymaganiami. Przykłady to [copy](../msbuild/copy-task.md), które kopiuje pliki, [MakeDir](../msbuild/makedir-task.md), które tworzą katalogi, i [CSC](../msbuild/csc-task.md), które kompilują pliki kodu źródłowego języka Visual C#. Listę dostępnych zadań wraz z informacjami o użyciu zawiera temat [Dokumentacja zadania](../msbuild/msbuild-task-reference.md).

 Zadanie jest wykonywane w pliku projektu programu MSBuild przez utworzenie elementu, który ma nazwę zadania jako elementu podrzędnego elementu [docelowego](../msbuild/target-element-msbuild.md) . Zadania zwykle akceptują parametry, które są przenoszone jako atrybuty elementu. Zarówno właściwości programu MSBuild, jak i elementy mogą być używane jako parametry. Na przykład poniższy kod wywołuje zadanie [MakeDir](../msbuild/makedir-task.md) i przekazuje jego wartość `BuildDir` właściwości, która została zadeklarowana w poprzednim przykładzie.

```xml
<Target Name="MakeBuildDirectory">
    <MakeDir  Directories="$(BuildDir)" />
</Target>
```

 Aby uzyskać więcej informacji o zadaniach, zobacz [zadania](../msbuild/msbuild-tasks.md).

### <a name="targets"></a><a name="BKMK_Targets"></a> Celach

 Kieruje zadania grupy w określonej kolejności i uwidacznia sekcje pliku projektu jako punkty wejścia do procesu kompilacji. Elementy docelowe są często pogrupowane w sekcje logiczne, aby zwiększyć czytelność i umożliwić rozszerzanie. Rozdzielenie kroków kompilacji na elementy docelowe umożliwia wywołanie jednej części procesu kompilacji z innych elementów docelowych bez kopiowania tej sekcji kodu do każdego obiektu docelowego. Na przykład, jeśli kilka punktów wejścia do procesu kompilacji wymaga skompilowania odwołań, można utworzyć obiekt docelowy, który kompiluje odwołania, a następnie uruchomić ten element docelowy z każdego punktu wejścia, gdzie jest to wymagane.

 Elementy docelowe są zadeklarowane w pliku projektu za pomocą elementu [Target](../msbuild/target-element-msbuild.md) . Na przykład poniższy kod tworzy obiekt docelowy o nazwie `Compile` , który następnie wywołuje zadanie [CSC](../msbuild/csc-task.md) , które ma listę elementów zadeklarowaną we wcześniejszym przykładzie.

```xml
<Target Name="Compile">
    <Csc Sources="@(Compile)" />
</Target>
```

 W bardziej zaawansowanych scenariuszach obiekty docelowe mogą służyć do opisywania relacji między sobą i wykonywania analizy zależności, aby można było pominąć całe sekcje procesu kompilacji, jeśli ten element docelowy jest aktualny. Aby uzyskać więcej informacji o obiektach docelowych, zobacz [targets](../msbuild/msbuild-targets.md).

## <a name="build-logs"></a>Dzienniki kompilacji

 Błędy kompilacji, ostrzeżenia i komunikaty można rejestrować w konsoli lub innym urządzeniu wyjściowym. Aby uzyskać więcej informacji, zobacz [Uzyskiwanie dzienników kompilacji](../msbuild/obtaining-build-logs-with-msbuild.md) i [Logowanie w programie MSBuild](../msbuild/logging-in-msbuild.md).

## <a name="use-msbuild-in-visual-studio"></a>Korzystanie z programu MSBuild w programie Visual Studio

 Program Visual Studio używa formatu pliku projektu programu MSBuild do przechowywania informacji o kompilacji projektów zarządzanych. Ustawienia projektu, które są dodawane lub zmieniane za pomocą interfejsu programu Visual Studio, są uwzględniane w temacie *. \* plik PROJ* wygenerowany dla każdego projektu. Program Visual Studio używa hostowanego wystąpienia programu MSBuild do kompilowania projektów zarządzanych. Oznacza to, że zarządzany projekt może być skompilowany w Visual Studio lub w wierszu polecenia (nawet jeśli program Visual Studio nie jest zainstalowany), a wyniki będą takie same.

 Aby zapoznać się z samouczkiem dotyczącym korzystania z programu MSBuild w programie Visual Studio, zobacz [Przewodnik: używanie programu MSBuild](../msbuild/walkthrough-using-msbuild.md).

## <a name="multitargeting"></a><a name="BKMK_Multitargeting"></a> Wielowersyjności kodu

 Za pomocą programu Visual Studio można skompilować aplikację do uruchamiania na jednej z kilku różnych wersji .NET Framework. Na przykład można skompilować aplikację do uruchamiania na .NET Framework 2,0 na platformie 32-bitowej i można skompilować tę samą aplikację do uruchamiania na .NET Framework 4,5 na platformie 64-bitowej. Możliwość kompilowania do więcej niż jednej struktury ma nazwę wiele obiektów docelowych.

 Oto niektóre korzyści wynikające z użycia:

- Można opracowywać aplikacje przeznaczone dla wcześniejszych wersji .NET Framework, na przykład wersje 2,0, 3,0 i 3,5.

- Możesz określić platformę docelową inną niż .NET Framework, na przykład Silverlight.

- Można wskazać *Profil platformy*, który jest wstępnie zdefiniowanym podzbiorem platformy docelowej.

- Jeśli dodatek Service Pack dla bieżącej wersji .NET Framework jest wydawany, można go określić jako docelowy.

- Gwarantujemy, że aplikacja używa tylko funkcji dostępnych w środowisku docelowym i platformie.

Aby uzyskać więcej informacji, zobacz wiele [obiektów docelowych](../msbuild/msbuild-multitargeting-overview.md).

## <a name="see-also"></a>Zobacz też

| Tytuł | Opis |
| - | - |
| [Przewodnik: Tworzenie pliku projektu MSBuild od zera](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md) | Pokazuje, jak utworzyć podstawowy plik projektu przyrostowo, używając tylko edytora tekstu. |
| [Przewodnik: Korzystanie z programu MSBuild](../msbuild/walkthrough-using-msbuild.md) | Wprowadza bloki konstrukcyjne programu MSBuild i pokazuje, jak pisać, manipulować i debugować projekty MSBuild bez zamykania środowiska IDE programu Visual Studio. |
| [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md) | Przedstawia cztery bloki konstrukcyjne MSBuild: Properties, Items, targets i Tasks. |
| [Elementy](../msbuild/msbuild-items.md) | Opisuje ogólne koncepcje związane z formatem pliku programu MSBuild oraz sposób dopasowania elementów do siebie. |
| [właściwości programu MSBuild](../msbuild/msbuild-properties.md) | Wprowadza właściwości i kolekcje właściwości. Właściwości to pary klucz/wartość, których można użyć do konfigurowania kompilacji. |
| [Targets (Obiekty docelowe)](../msbuild/msbuild-targets.md) | Wyjaśnia, w jaki sposób grupować zadania w określonej kolejności i włączać sekcje procesu kompilacji do wywołania w wierszu polecenia. |
| [Zadania](../msbuild/msbuild-tasks.md) | Pokazuje, jak utworzyć jednostkę kodu wykonywalnego, która może być używana przez program MSBuild do wykonywania niepodzielnych operacji kompilacji. |
| [Warunki](../msbuild/msbuild-conditions.md) | Omawia, w jaki sposób używać `Condition` atrybutu w elemencie MSBuild. |
| [Pojęcia zaawansowane](../msbuild/msbuild-advanced-concepts.md) | Przedstawia operacje wsadowe, wykonywanie transformacji, wieloadresowe i inne zaawansowane techniki. |
| [Logowanie w programie MSBuild](../msbuild/logging-in-msbuild.md) | Opisuje, jak rejestrować zdarzenia, komunikaty i błędy kompilacji. |
| [Jak program MSBuild kompiluje projekty](build-process-overview.md) | Opisuje proces kompilacji wewnętrznej używany w programie MSBuild |
| [Dodatkowe zasoby](https://social.msdn.microsoft.com/forums/vstudio/home?forum=msbuild) | Wyświetla listę zasobów społeczności i pomocy technicznej, aby uzyskać więcej informacji na temat programu MSBuild. |

## <a name="reference"></a>Dokumentacja

- [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)\
 Linki do tematów zawierających informacje referencyjne.

- [Słownik](msbuild-glossary.md)\
 Definiuje typowe warunki MSBuild.
