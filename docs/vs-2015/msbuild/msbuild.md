---
title: MSBuild | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, about MSBuild
- MSBuild, overview
ms.assetid: e39f13f7-1e1d-4435-95ca-0c222bca071c
caps.latest.revision: 62
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7ac637c478b5bb105b48abeb1d0ec074122e3dda
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68739689"
---
# <a name="msbuild"></a>MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuildengine](../includes/vstecmsbuildengine-md.md)]To platforma do kompilowania aplikacji. Ten aparat, który jest również znany jako MSBuild, zawiera schemat XML dla pliku projektu, który kontroluje, w jaki sposób platforma kompilacji przetwarza i tworzy oprogramowanie. Program Visual Studio używa programu MSBuild, ale nie jest zależny od Visual Studio. Wywołując msbuild.exe w pliku projektu lub rozwiązania, można organizować i kompilować produkty w środowiskach, w których nie zainstalowano programu Visual Studio.  
  
 Program Visual Studio używa programu MSBuild do ładowania i kompilowania projektów zarządzanych. Pliki projektu w programie Visual Studio (. csproj,. vbproj, vcxproj i inne) zawierają kod XML programu MSBuild, który jest wykonywany podczas kompilowania projektu przy użyciu środowiska IDE. Projekty programu Visual Studio zaimportują wszystkie niezbędne ustawienia i procesy kompilacji, aby wykonywać typowe prace programistyczne, ale można je rozbudować lub zmodyfikować z poziomu programu Visual Studio lub za pomocą edytora XML.  
  
 Aby uzyskać informacje na temat programu MSBuild for C++, zobacz [MSBuild (Visual C++)](https://msdn.microsoft.com/library/7a1be7ff-0312-4669-adf2-5f5bf507d560).  
  
 Poniższe przykłady ilustrują, kiedy można uruchamiać kompilacje przy użyciu wiersza polecenia programu MSBuild zamiast środowiska IDE programu Visual Studio.  
  
- Program Visual Studio nie jest zainstalowany.  
  
- Chcesz użyć 64-bitowej wersji programu MSBuild. Ta wersja programu MSBuild jest zwykle zbędna, ale umożliwia MSBuild dostęp do większej ilości pamięci.  
  
- Chcesz uruchomić kompilację w wielu procesach. Można jednak użyć IDE, aby osiągnąć ten sam wynik w projektach w językach C++ i C#.  
  
- Chcesz zmodyfikować system kompilacji. Na przykład możesz chcieć włączyć następujące akcje:  
  
  - Przetwarzaj wstępnie pliki przed osiągnięciem kompilatora.  
  
  - Skopiuj dane wyjściowe kompilacji do innego miejsca.  
  
  - Twórz skompresowane pliki na podstawie danych wyjściowych kompilacji.  
  
  - Wykonaj krok przetwarzania końcowego. Na przykład możesz chcieć oznaczyć zestaw przy użyciu innej wersji.  
  
  Można napisać kod w środowisku IDE programu Visual Studio, ale uruchamiać kompilacje przy użyciu programu MSBuild. Alternatywnie można skompilować kod w środowisku IDE na komputerze deweloperskim, ale używać wiersza polecenia programu MSBuild do kompilowania kodu, który jest zintegrowany z wielu deweloperów.  
  
> [!NOTE]
> Możesz użyć Team Foundation Build, aby automatycznie kompilować, testować i wdrażać aplikację. System kompilacji może automatycznie uruchamiać kompilacje, gdy deweloperzy ewidencjonują kod (na przykład w ramach strategii ciągłej integracji) lub zgodnie z harmonogramem (na przykład w przypadku nocnej kompilacji testu weryfikacyjnego). Team Foundation Build kompiluje kod przy użyciu programu MSBuild. Aby uzyskać więcej informacji, zobacz [Kompilowanie aplikacji](/azure/devops/pipelines/index).  
  
 Ten temat zawiera omówienie programu MSBuild. Aby zapoznać się z samouczkiem wprowadzającym, zobacz [Przewodnik: korzystanie z programu MSBuild](../msbuild/walkthrough-using-msbuild.md).  
  
 **W tym temacie**  
  
- [Korzystanie z programu MSBuild w wierszu polecenia](#BKMK_CommandPrompt)  
  
- [Plik projektu](#BKMK_ProjectFile)  
  
  - [Właściwości](#BKMK_Properties)  

  - [Elementy](#BKMK_Items)  

  - [Zadania](#BKMK_Tasks)  

  - [Targets (Obiekty docelowe)](#BKMK_Targets)  

- [Dzienniki kompilacji](#BKMK_BuildLogs)  
  
- [Korzystanie z programu MSBuild w programie Visual Studio](#BKMK_VisualStudio)  
  
- [Wielowersyjności kodu](#BKMK_Multitargeting)  
  
## <a name="using-msbuild-at-a-command-prompt"></a><a name="BKMK_CommandPrompt"></a> Korzystanie z programu MSBuild w wierszu polecenia  
 Aby uruchomić z [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] wiersza polecenia, Przekaż plik projektu do MSBuild.exe, wraz z odpowiednimi opcjami wiersza polecenia. Opcje wiersza polecenia umożliwiają ustawianie właściwości, wykonywanie określonych elementów docelowych i ustawianie innych opcji kontrolujących proces kompilacji. Na przykład, można użyć następującej składni wiersza polecenia do skompilowania pliku `MyProj.proj` z `Configuration` właściwością ustawioną na `Debug` .  
  
```  
MSBuild.exe MyProj.proj /property:Configuration=Debug  
```  
  
 Aby uzyskać więcej informacji na temat [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] opcji wiersza polecenia, zobacz informacje dotyczące [wiersza polecenia](../msbuild/msbuild-command-line-reference.md).  
  
> [!IMPORTANT]
> Przed pobraniem projektu należy określić wiarygodność kodu.  
  
## <a name="project-file"></a><a name="BKMK_ProjectFile"></a> Plik projektu  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] używa formatu pliku projektu opartego na języku XML, który jest prosty i rozszerzalny. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]Format pliku projektu umożliwia deweloperom Opisywanie elementów, które mają zostać skompilowane, a także sposób ich kompilowania w różnych systemach operacyjnych i konfiguracjach. Ponadto format pliku projektu umożliwia deweloperom tworzenie reguł kompilacji wielokrotnego użytku, które można umieścić w osobnych plikach, dzięki czemu kompilacje mogą być wykonywane spójnie w różnych projektach w produkcie.  
  
 W poniższych sekcjach opisano niektóre podstawowe elementy [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] formatu pliku projektu. Aby zapoznać się z samouczkiem dotyczącym tworzenia podstawowego pliku projektu, zobacz [Przewodnik: Tworzenie pliku projektu MSBuild od podstaw](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md).  
  
### <a name="properties"></a><a name="BKMK_Properties"></a> Aœciwoœci  
 Właściwości reprezentują pary klucz/wartość, których można użyć do konfigurowania kompilacji. Właściwości są deklarowane przez utworzenie elementu, który ma nazwę właściwości jako element podrzędny elementu [Właściwości](../msbuild/propertygroup-element-msbuild.md) . Na przykład poniższy kod tworzy właściwość o nazwie `BuildDir` , która ma wartość `Build` .  
  
```  
<PropertyGroup>  
    <BuildDir>Build</BuildDir>  
</PropertyGroup>  
```  
  
 Właściwość można definiować warunkowo, umieszczając `Condition` atrybut w elemencie. Zawartość elementów warunkowych jest ignorowana, jeśli warunek nie zostanie spełniony `true` . W poniższym przykładzie `Configuration` element jest zdefiniowany, jeśli nie został jeszcze zdefiniowany.  
  
```  
<Configuration  Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
```  
  
 Do właściwości można odwoływać się w całym pliku projektu przy użyciu składni $ (*PropertyName*). Na przykład można odwołać się do właściwości w poprzednich przykładach przy użyciu `$(BuildDir)` i `$(Configuration)` .  
  
 Aby uzyskać więcej informacji na temat właściwości, zobacz [Właściwości programu MSBuild](msbuild-properties1.md).  
  
### <a name="items"></a><a name="BKMK_Items"></a> Produktów  
 Elementy są wejściami do systemu kompilacji i zazwyczaj reprezentują pliki. Elementy są pogrupowane w typy elementów na podstawie nazw elementów zdefiniowanych przez użytkownika. Te typy elementów mogą służyć jako parametry zadań, które wykorzystują poszczególne elementy do wykonywania kroków procesu kompilacji.  
  
 Elementy są zadeklarowane w pliku projektu przez utworzenie elementu, który ma nazwę typu elementu jako element podrzędny elementu [Item](../msbuild/itemgroup-element-msbuild.md) . Na przykład poniższy kod tworzy typ elementu o nazwie `Compile` , który zawiera dwa pliki.  
  
```  
<ItemGroup>  
    <Compile Include = "file1.cs"/>  
    <Compile Include = "file2.cs"/>  
</ItemGroup>  
```  
  
 Do typów elementów można się odwoływać w całym pliku projektu przy użyciu składni @ (*ItemType*). Na przykład typ elementu w przykładzie może być przywoływany za pomocą `@(Compile)` .  
  
 W programie MSBuild nazwy elementów i atrybutów są rozróżniane wielkości liter. Jednak nazwy właściwości, elementów i metadanych nie są. W poniższym przykładzie jest tworzony typ elementu `Compile` , `comPile` , lub jakakolwiek inna odmiana przypadku, a typ elementu to wartość "jeden. cs; dwa. cs".  
  
```  
<ItemGroup>  
  <Compile Include="one.cs" />  
  <comPile Include="two.cs" />  
</ItemGroup>  
```  
  
 Elementy mogą być deklarowane przy użyciu symboli wieloznacznych i mogą zawierać dodatkowe metadane dla bardziej zaawansowanych scenariuszy kompilacji. Aby uzyskać więcej informacji o elementach, zobacz [Items](../msbuild/msbuild-items.md).  
  
### <a name="tasks"></a><a name="BKMK_Tasks"></a> Widoku  
 Zadania są jednostkami kodu wykonywalnego, które są [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] używane przez projekty do wykonywania operacji kompilacji. Na przykład zadanie może kompilować pliki wejściowe lub uruchomić narzędzie zewnętrzne. Zadania mogą być ponownie używane i mogą być współużytkowane przez różnych deweloperów w różnych projektach.  
  
 Logika wykonywania zadania jest zapisywana w kodzie zarządzanym i mapowana na [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] przy użyciu elementu [UsingTask](../msbuild/usingtask-element-msbuild.md) . Można napisać własne zadanie, tworząc typ zarządzany, który implementuje <xref:Microsoft.Build.Framework.ITask> interfejs. Aby uzyskać więcej informacji o sposobach pisania zadań, zobacz [Zapisywanie zadań](../msbuild/task-writing.md).  
  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] obejmuje typowe zadania, które można zmodyfikować zgodnie z wymaganiami.  Przykłady to [copy](../msbuild/copy-task.md), które kopiuje pliki, [MakeDir](../msbuild/makedir-task.md), które tworzą katalogi, i [CSC](../msbuild/csc-task.md), które kompilują pliki kodu źródłowego języka Visual C#. Listę dostępnych zadań wraz z informacjami o użyciu zawiera temat [Dokumentacja zadania](../msbuild/msbuild-task-reference.md).  
  
 Zadanie jest wykonywane w [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] pliku projektu przez utworzenie elementu, który ma nazwę zadania jako elementu podrzędnego elementu [docelowego](../msbuild/target-element-msbuild.md) . Zadania zwykle akceptują parametry, które są przenoszone jako atrybuty elementu. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]Właściwości i elementy mogą być używane jako parametry. Na przykład poniższy kod wywołuje zadanie [MakeDir](../msbuild/makedir-task.md) i przekazuje jego wartość `BuildDir` właściwości, która została zadeklarowana w poprzednim przykładzie.  
  
```  
<Target Name="MakeBuildDirectory">  
    <MakeDir  Directories="$(BuildDir)" />  
</Target>  
```  
  
 Aby uzyskać więcej informacji o zadaniach, zobacz [zadania](../msbuild/msbuild-tasks.md).  
  
### <a name="targets"></a><a name="BKMK_Targets"></a> Celach  
 Kieruje zadania grupy w określonej kolejności i uwidacznia sekcje pliku projektu jako punkty wejścia do procesu kompilacji. Elementy docelowe są często pogrupowane w sekcje logiczne, aby zwiększyć czytelność i umożliwić rozszerzanie. Rozdzielenie kroków kompilacji na elementy docelowe umożliwia wywołanie jednej części procesu kompilacji z innych elementów docelowych bez kopiowania tej sekcji kodu do każdego obiektu docelowego. Na przykład, jeśli kilka punktów wejścia do procesu kompilacji wymaga skompilowania odwołań, można utworzyć obiekt docelowy, który kompiluje odwołania, a następnie uruchomić ten element docelowy z każdego punktu wejścia, gdzie jest to wymagane.  
  
 Elementy docelowe są zadeklarowane w pliku projektu za pomocą elementu [Target](../msbuild/target-element-msbuild.md) . Na przykład poniższy kod tworzy obiekt docelowy o nazwie `Compile` , który następnie wywołuje zadanie [CSC](../msbuild/csc-task.md) , które ma listę elementów zadeklarowaną we wcześniejszym przykładzie.  
  
```  
<Target Name="Compile">  
    <Csc Sources="@(Compile)" />  
</Target>  
```  
  
 W bardziej zaawansowanych scenariuszach obiekty docelowe mogą służyć do opisywania relacji między sobą i wykonywania analizy zależności, aby można było pominąć całe sekcje procesu kompilacji, jeśli ten element docelowy jest aktualny. Aby uzyskać więcej informacji o obiektach docelowych, zobacz [targets](../msbuild/msbuild-targets.md).  
  
## <a name="build-logs"></a><a name="BKMK_BuildLogs"></a> Dzienniki kompilacji  
 Błędy kompilacji, ostrzeżenia i komunikaty można rejestrować w konsoli lub innym urządzeniu wyjściowym. Aby uzyskać więcej informacji, zobacz [Uzyskiwanie dzienników kompilacji](../msbuild/obtaining-build-logs-with-msbuild.md) i [Logowanie w programie MSBuild](../msbuild/logging-in-msbuild.md).  
  
## <a name="using-msbuild-in-visual-studio"></a><a name="BKMK_VisualStudio"></a> Korzystanie z programu MSBuild w programie Visual Studio  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] program używa [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] formatu pliku projektu do przechowywania informacji o kompilacji projektów zarządzanych. Ustawienia projektu, które są dodawane lub zmieniane za pomocą [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] interfejsu, są odzwierciedlane w pliku proj. *, który jest generowany dla każdego projektu. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] program używa hostowanego wystąpienia programu [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] do kompilowania projektów zarządzanych. Oznacza to, że zarządzany projekt może być wbudowany [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] lub w wierszu polecenia (nawet jeśli [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nie jest zainstalowany), a wyniki będą takie same.  
  
 Aby zapoznać się z samouczkiem dotyczącym korzystania z programu MSBuild w programie Visual Studio, zobacz [Przewodnik: używanie programu MSBuild](../msbuild/walkthrough-using-msbuild.md).  
  
## <a name="multitargeting"></a><a name="BKMK_Multitargeting"></a> Wielowersyjności kodu  
 Za pomocą programu Visual Studio można skompilować aplikację do uruchamiania na jednej z kilku różnych wersji .NET Framework. Na przykład można skompilować aplikację do uruchamiania na .NET Framework 2,0 na platformie 32-bitowej i można skompilować tę samą aplikację do uruchamiania na .NET Framework 4,5 na platformie 64-bitowej. Możliwość kompilowania do więcej niż jednej struktury ma nazwę wiele obiektów docelowych.  
  
 Oto niektóre korzyści wynikające z użycia:  
  
- Można opracowywać aplikacje przeznaczone dla wcześniejszych wersji .NET Framework, na przykład wersje 2,0, 3,0 i 3,5.  
  
- Możesz określić platformę docelową inną niż .NET Framework, na przykład Silverlight.  
  
- Można wskazać *Profil platformy*, który jest wstępnie zdefiniowanym podzbiorem platformy docelowej.  
  
- Jeśli dodatek Service Pack dla bieżącej wersji .NET Framework jest wydawany, można go wskazać.  
  
- Gwarantujemy, że aplikacja używa tylko funkcji dostępnych w środowisku docelowym i platformie.  
  
  Aby uzyskać więcej informacji, zobacz wiele [obiektów docelowych](../msbuild/msbuild-multitargeting-overview.md).  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Przewodnik: Tworzenie pliku projektu MSBuild od podstaw](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)|Pokazuje, jak utworzyć podstawowy plik projektu przyrostowo, używając tylko edytora tekstu.|  
|[Przewodnik: Korzystanie z programu MSBuild](../msbuild/walkthrough-using-msbuild.md)|Wprowadza bloki konstrukcyjne programu MSBuild i pokazuje, jak pisać, manipulować i debugować projekty MSBuild bez zamykania środowiska IDE programu Visual Studio.|  
|[Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)|Przedstawia cztery bloki konstrukcyjne MSBuild: Properties, Items, targets i Tasks.|  
|[Elementy](../msbuild/msbuild-items.md)|Opisuje ogólne pojęcia związane z [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] formatem pliku oraz sposób dopasowania fragmentów.|  
|[Właściwości programu MSBuild](msbuild-properties1.md)|Wprowadza właściwości i kolekcje właściwości. Właściwości to pary klucz/wartość, których można użyć do konfigurowania kompilacji.|  
|[Targets (Obiekty docelowe)](../msbuild/msbuild-targets.md)|Wyjaśnia, w jaki sposób grupować zadania w określonej kolejności i włączać sekcje procesu kompilacji do wywołania w wierszu polecenia.|  
|[Zadania](../msbuild/msbuild-tasks.md)|Pokazuje, jak utworzyć jednostkę kodu wykonywalnego, która może być używana przez program [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] do wykonywania niepodzielnych operacji kompilacji.|  
|[Warunki](../msbuild/msbuild-conditions.md)|Omawia, w jaki sposób używać `Condition` atrybutu w elemencie MSBuild.|  
|[Pojęcia zaawansowane](../msbuild/msbuild-advanced-concepts.md)|Przedstawia operacje wsadowe, wykonywanie transformacji, wieloadresowe i inne zaawansowane techniki.|  
|[Logowanie w programie MSBuild](../msbuild/logging-in-msbuild.md)|Opisuje, jak rejestrować zdarzenia, komunikaty i błędy kompilacji.|  
|[Dodatkowe zasoby](../msbuild/additional-msbuild-resources.md)|Wyświetla listę zasobów społeczności i pomocy technicznej, aby uzyskać więcej informacji na temat programu MSBuild.|  
  
## <a name="reference"></a>Tematy pomocy  
 [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)  
 Linki do tematów zawierających informacje referencyjne.  
  
 Słownik  
 Definiuje typowe warunki MSBuild.
