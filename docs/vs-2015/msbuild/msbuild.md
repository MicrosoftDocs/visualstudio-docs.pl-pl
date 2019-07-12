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
ms.openlocfilehash: 13029e05e4f29e532918562afd2fee520b387464
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67821627"
---
# <a name="msbuild"></a>MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuildengine](../includes/vstecmsbuildengine-md.md)] To platforma do tworzenia aplikacji. Ten aparat, który jest również znany jako MSBuild, dostarcza schemat XML pliku projektu, który kontroluje, jak platforma kompilacji przetwarza i tworzy oprogramowanie. Program Visual Studio używa MSBuild, ale go nie są zależne od programu Visual Studio. Za pomocą wywołania msbuild.exe w pliku projektu lub rozwiązania, można organizować i kompilować produkty w środowiskach, w których nie zainstalowano programu Visual Studio.  
  
 Visual Studio używa MSBuild do ładowania i kompilacji projektów zarządzanych. Pliki projektu w programie Visual Studio (.csproj, .vbproj, vcxproj i inne) zawierają kod MSBuild XML, który jest wykonywany, gdy tworzysz projekt za pomocą IDE. Zaimportuj wszystkie niezbędne ustawienia projektów programu Visual Studio, a procesy typowe dla pracy deweloperów kompilacji, ale można rozszerzyć lub zmodyfikować je z poziomu programu Visual Studio lub za pomocą edytora XML.  
  
 Aby uzyskać informacje dotyczące programu MSBuild dla języka C++, zobacz [MSBuild (Visual C++)](https://msdn.microsoft.com/library/7a1be7ff-0312-4669-adf2-5f5bf507d560).  
  
 Poniższe przykłady ilustrują, kiedy można uruchamiać kompilacje przy użyciu wiersza polecenia MSBuild zamiast Visual Studio IDE.  
  
- Nie zainstalowano programu Visual Studio.  
  
- Chcesz użyć 64-bitowej wersji programu MSBuild. Ta wersja programu MSBuild jest zazwyczaj zbędna, ale pozwala MSBuild na dostęp do większej ilości pamięci.  
  
- Chcesz uruchomić kompilację w wielu procesach. Jednak można użyć środowiska IDE, aby osiągnąć ten sam wynik w projektach w językach C++ i C#.  
  
- Chcesz zmodyfikować system kompilacji. Na przykład możesz chcieć umożliwić następujące działania:  
  
  - Przetwórz wstępnie pliki, zanim dotrą do kompilatora.  
  
  - Skopiuj skompilowane pliki w inne miejsce.  
  
  - Stwórz skompresowane pliki z wyjścia kompilacji.  
  
  - Wykonaj krok przetwarzania końcowego. Na przykład możesz chcieć sygnatury zestaw z innej wersji.  
  
  Można napisać kod w środowisku IDE programu Visual Studio, ale uruchamiać kompilacje przy użyciu programu MSBuild. Jako inną alternatywę można skompilować kod w środowisku IDE na komputerze deweloperskim, ale użyj wiersza polecenia MSBuild do kompilowania kodu, który jest zintegrowany z wielu deweloperów.  
  
> [!NOTE]
> Team Foundation Build służy do automatycznego kompilowania, testowania i wdrażania aplikacji. System kompilacji można automatycznie uruchamiać kompilacje, gdy deweloperzy ewidencjonują kod (na przykład, jako część strategii ciągłej integracji) lub według harmonogramu (na przykład nocna kompilacja Test weryfikacji kompilacji). Team Foundation Build kompiluje kod przy użyciu programu MSBuild. Aby uzyskać więcej informacji, zobacz [skompilować aplikację](https://msdn.microsoft.com/library/a971b0f9-7c28-479d-a37b-8fd7e27ef692).  
  
 Ten temat zawiera omówienie programu MSBuild. Aby uzyskać Samouczek wprowadzający, zobacz [instruktażu: Korzystanie z programu MSBuild](../msbuild/walkthrough-using-msbuild.md).  
  
 **W tym temacie**  
  
- [Korzystanie z programu MSBuild w wierszu polecenia](#BKMK_CommandPrompt)  
  
- [Plik projektu](#BKMK_ProjectFile)  
  
  - [Właściwości](#BKMK_Properties)  

  - [Elementy](#BKMK_Items)  

  - [Zadania](#BKMK_Tasks)  

  - [Docelowe elementy](#BKMK_Targets)  

- [Kompilacja dzienników](#BKMK_BuildLogs)  
  
- [Korzystanie z programu MSBuild w programie Visual Studio](#BKMK_VisualStudio)  
  
- [Wielowersyjność kodu](#BKMK_Multitargeting)  
  
## <a name="BKMK_CommandPrompt"></a> Korzystanie z programu MSBuild w wierszu polecenia  
 Aby uruchomić [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] w wierszu polecenia, Przekaż plik projektu do MSBuild.exe, wraz z odpowiednimi opcjami wiersza polecenia. Opcje wiersza polecenia umożliwiają ustawianie właściwości, wykonywanie określonych obiektów docelowych i ustaw inne opcje, które sterują procesem kompilacji. Na przykład można użyć następującej składni wiersza polecenia do tworzenia pliku `MyProj.proj` z `Configuration` właściwością `Debug`.  
  
```  
MSBuild.exe MyProj.proj /property:Configuration=Debug  
```  
  
 Aby uzyskać więcej informacji na temat [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] opcji wiersza polecenia, zobacz [odwołanie do wiersza polecenia](../msbuild/msbuild-command-line-reference.md).  
  
> [!IMPORTANT]
> Przed pobierania projektu Ustal wiarygodność kodu.  
  
## <a name="BKMK_ProjectFile"></a> Plik projektu  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] używa formatu pliku projektu opartego na języku XML, który jest bardzo prosty i rozszerzalny. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] Formatu pliku projektu umożliwia deweloperom opisywanie elementów, które mają być tworzone, a także, jak są one tworzone dla różnych systemów operacyjnych i konfiguracji. Ponadto format pliku projektu umożliwia deweloperom tworzenie kompilacji wielokrotnego użytku reguł, które mogą być umieszczane w osobnych plikach, tak aby kompilacje mogły być wykonywane konsekwentnie między różnymi projektami w produkcie.  
  
 W poniższych sekcjach opisano niektóre z podstawowych elementów [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] formatu pliku projektu. Samouczek dotyczący sposobu tworzenia podstawowego pliku projektu, zobacz [instruktażu: Tworzenie pliku projektu MSBuild od zera](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md).  
  
### <a name="BKMK_Properties"></a> Właściwości  
 Właściwości reprezentują pary klucz/wartość, które mogą służyć do konfigurowania kompilacji. Właściwości deklaruje się poprzez utworzenie elementu zawierającego nazwę właściwości jako element podrzędny elementu [PropertyGroup](../msbuild/propertygroup-element-msbuild.md) elementu. Na przykład, poniższy kod tworzy właściwość o nazwie `BuildDir` wartością `Build`.  
  
```  
<PropertyGroup>  
    <BuildDir>Build</BuildDir>  
</PropertyGroup>  
```  
  
 Można zdefiniować właściwość warunkowo przez umieszczenie `Condition` atrybutu w elemencie. Zawartość elementów warunkowych jest ignorowana, chyba, że warunek to `true`. W poniższym przykładzie `Configuration` jest zdefiniowany element, jeśli jeszcze nie został zdefiniowany.  
  
```  
<Configuration  Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
```  
  
 Właściwości można się odwoływać w całym pliku projektu przy użyciu składni $(*PropertyName*). Na przykład, można się odwoływać do właściwości w poprzednich przykładach za pomocą `$(BuildDir)` i `$(Configuration)`.  
  
 Aby uzyskać więcej informacji o właściwościach, zobacz [właściwości programu MSBuild](msbuild-properties1.md).  
  
### <a name="BKMK_Items"></a> Elementy  
 Elementy to wejścia do systemu kompilacji i zazwyczaj reprezentują pliki. Elementy są grupowane w typy elementów, na podstawie nazw elementów zdefiniowanych przez użytkownika. Te typy elementów może służyć jako parametry dla zadań, które używają poszczególnych elementów, aby wykonać kroki procesu kompilacji.  
  
 Elementy deklaruje się w pliku projektu, tworząc element, który ma nazwę typu elementu jako element podrzędny elementu [ItemGroup](../msbuild/itemgroup-element-msbuild.md) elementu. Na przykład, poniższy kod tworzy typ elementu o nazwie `Compile`, który zawiera dwa pliki.  
  
```  
<ItemGroup>  
    <Compile Include = "file1.cs"/>  
    <Compile Include = "file2.cs"/>  
</ItemGroup>  
```  
  
 Typy elementów można odwoływać się w całym pliku projektu przy użyciu składni @(*ItemType*). Na przykład typ elementu w przykładzie będzie używane odwołanie za pomocą `@(Compile)`.  
  
 W programie MSBuild nazw elementów i atrybutów jest rozróżniana wielkość liter. Jednak nazwy właściwości, elementów i metadanych nie są. Poniższy przykład tworzy typ elementu `Compile`, `comPile`, lub inne zmiany wielkości liter i daje typowi elementu wartość "one.cs;two.cs".  
  
```  
<ItemGroup>  
  <Compile Include="one.cs" />  
  <comPile Include="two.cs" />  
</ItemGroup>  
```  
  
 Elementy mogą być deklarowane przy użyciu symboli wieloznacznych i mogą zawierać dodatkowe metadane dla bardziej zaawansowanych scenariuszy kompilacji. Aby uzyskać więcej informacji na temat elementów, zobacz [elementów](../msbuild/msbuild-items.md).  
  
### <a name="BKMK_Tasks"></a> Zadania  
 Zadania to jednostki kodu wykonywalnego, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] projektów służy do wykonywania operacji kompilacji. Na przykład zadanie może skompilować pliki wejściowe lub uruchomić narzędzie zewnętrzne. Zadania mogą zostać ponownie użyte i mogą być współdzielone przez różnych deweloperów w różnych projektach.  
  
 Logika wykonania zadania jest zapisywana w kodzie zarządzanym i mapowana do [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] przy użyciu [UsingTask](../msbuild/usingtask-element-msbuild.md) elementu. Można napisać własne zadanie, tworząc typ zarządzany, który implementuje <xref:Microsoft.Build.Framework.ITask> interfejsu. Aby uzyskać więcej informacji na temat pisania zadań, zobacz [wpisywanie zadania](../msbuild/task-writing.md).  
  
 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] zawiera typowe zadania, które można dostosować do własnych wymagań.  Należą do nich [kopiowania](../msbuild/copy-task.md), który kopiuje pliki, [MakeDir](../msbuild/makedir-task.md), który tworzy katalogi, i [Csc](../msbuild/csc-task.md), który kompiluje pliki kodu źródłowego języka Visual C#. Aby uzyskać listę dostępnych zadań wraz z informacji o użyciu, zobacz [odwołanie do zadania](../msbuild/msbuild-task-reference.md).  
  
 Zadanie jest wykonywane w [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] pliku projektu poprzez utworzenie elementu zawierającego nazwę zadania jako element podrzędny elementu [docelowej](../msbuild/target-element-msbuild.md) elementu. Zadania zazwyczaj akceptują parametry, które są przekazywane jako atrybuty elementu. Zarówno [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] właściwości i elementy, które mogą być używane jako parametry. Na przykład, poniższy kod wywoła [MakeDir](../msbuild/makedir-task.md) zadań, a następnie przekazuje jej wartość `BuildDir` właściwości, który został zadeklarowany we wcześniejszym przykładzie.  
  
```  
<Target Name="MakeBuildDirectory">  
    <MakeDir  Directories="$(BuildDir)" />  
</Target>  
```  
  
 Aby uzyskać więcej informacji o zadaniach, zobacz [zadania](../msbuild/msbuild-tasks.md).  
  
### <a name="BKMK_Targets"></a> Obiekty docelowe  
 Obiekty docelowe grupują zadania w określonej kolejności i udostępniają sekcje pliku projektu jako punkty wejścia do procesu kompilacji. Obiekty docelowe często są pogrupowane w logiczne sekcje, aby zwiększyć czytelność i pozwolić na rozbudowę. Podział kroków kompilacji na obiekty docelowe pozwala wywołać jeden fragment procesu kompilacji z innych obiektów docelowych bez kopiowania tej sekcji kodu do każdego obiektu docelowego. Na przykład jeśli wiele punktów wejścia do procesu kompilacji wymaga wbudowania odwołań, można utworzyć obiekt docelowy, który tworzy odwołania i następnie uruchomić obiekt docelowy z każdego punktu wejścia, gdzie jest to wymagane.  
  
 Obiekty docelowe są deklarowane w pliku projektu za pomocą [docelowej](../msbuild/target-element-msbuild.md) elementu. Na przykład, poniższy kod tworzy obiekt docelowy o nazwie `Compile`, która następnie wywołuje metodę [Csc](../msbuild/csc-task.md) zadanie, które ma element listy zadeklarowany we wcześniejszym przykładzie.  
  
```  
<Target Name="Compile">  
    <Csc Sources="@(Compile)" />  
</Target>  
```  
  
 W bardziej zaawansowanych scenariuszach obiekty docelowe może służyć do opisywania relacji między sobą i przeprowadzać analizę zależności, tak aby całe sekcje procesu kompilacji może zostać pominięta, jeżeli ten obiekt docelowy jest aktualny. Aby uzyskać więcej informacji na temat elementów docelowych, zobacz [cele](../msbuild/msbuild-targets.md).  
  
## <a name="BKMK_BuildLogs"></a> Kompilacja dzienników  
 Możesz rejestrować błędy kompilacji, ostrzeżenia i komunikaty na konsoli lub innym urządzeniu wyjściowym. Aby uzyskać więcej informacji, zobacz [uzyskiwanie dzienników kompilacji](../msbuild/obtaining-build-logs-with-msbuild.md) i [logowanie w programie MSBuild](../msbuild/logging-in-msbuild.md).  
  
## <a name="BKMK_VisualStudio"></a> Korzystanie z programu MSBuild w programie Visual Studio  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] używa [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] formatu pliku projektu do przechowywania informacji tworzenia zarządzanych projektów. Ustawienia projektu, które są dodane lub zmienione za pomocą [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] interfejsu są odzwierciedlane. * proj pliku, który jest generowany dla każdego projektu. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] używa hostowanej instancji [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] do tworzenia projektów zarządzanych. Oznacza to, że zarządzanego projektu mogą być wbudowane [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] lub w wierszu polecenia (nawet wtedy, gdy [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nie jest zainstalowany), a wyniki będą identyczne.  
  
 Samouczek dotyczący sposobu użycia MSBuild w programie Visual Studio, zobacz [instruktażu: Korzystanie z programu MSBuild](../msbuild/walkthrough-using-msbuild.md).  
  
## <a name="BKMK_Multitargeting"></a> Wielowersyjności kodu w programie  
 Za pomocą programu Visual Studio, można kompilować aplikację do uruchamiania w jednej z kilku różnych wersji programu .NET Framework. Na przykład można kompilować aplikacje do uruchamiania na .NET Framework 2.0 na platformie 32-bitowe i można kompilować tej samej aplikacji do uruchamiania na .NET Framework 4.5 na platformie 64-bitowej. Możliwość kompilowania do więcej niż jednej struktury jest lub multitargeting.  
  
 Oto niektóre korzyści wynikające z wielowersyjności:  
  
- Można tworzyć aplikacje przeznaczone dla wcześniejszych wersji programu .NET Framework, na przykład wersji 2.0, 3.0 i 3.5.  
  
- Można wskazać platform innych niż .NET Framework, na przykład Silverlight.  
  
- Możesz wybrać docelową *profil framework*, czyli uprzednio zdefiniowany podzbiór platformy docelowej.  
  
- Jeśli z dodatkiem Service pack dla bieżącej wersji programu .NET Framework jest zwalniana, można go wykorzystać.  
  
- Wielowersyjność gwarantuje, że aplikacja używa tylko funkcjonalności, która jest dostępna w platformę docelową i platformy.  
  
  Aby uzyskać więcej informacji, zobacz [Wielowersyjność](../msbuild/msbuild-multitargeting-overview.md).  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Przewodnik: tworzenie pliku projektu MSBuild od zera](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)|Przedstawia sposób tworzenia podstawowego pliku projektu przyrostowo, używając tylko tekst edytora.|  
|[Przewodnik: korzystanie z programu MSBuild](../msbuild/walkthrough-using-msbuild.md)|Wprowadza bloki konstrukcyjne programu MSBuild i pokazuje, jak napisać, modyfikowania i debugowania projektów programu MSBuild bez zamykania środowiska IDE programu Visual Studio.|  
|[Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)|Przedstawia cztery bloki konstrukcyjne MSBuild: właściwości, elementów, obiektów docelowych i zadań.|  
|[Elementy](../msbuild/msbuild-items.md)|Opisuje ogólne pojęcia [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] plik formatu i sposób dopasowywania.|  
|[Właściwości programu MSBuild](msbuild-properties1.md)|Wprowadza właściwości i kolekcje właściwości. Właściwości to pary klucz/wartość, które mogą być używane do konfigurowania kompilacji.|  
|[Docelowe elementy](../msbuild/msbuild-targets.md)|Wyjaśnia, jak grupować zadania razem w określonej kolejności i włączyć sekcje procesu kompilacji, który ma być wywoływana w wierszu polecenia.|  
|[Zadania](../msbuild/msbuild-tasks.md)|Pokazuje, jak utworzyć jednostkę kodu wykonywalnego, który może być używany przez [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] do wykonywania niepodzielnych operacji kompilacji.|  
|[Warunki](../msbuild/msbuild-conditions.md)|W tym artykule omówiono sposób używania `Condition` atrybutu w elemencie programu MSBuild.|  
|[Pojęcia zaawansowane](../msbuild/msbuild-advanced-concepts.md)|Przedstawia przetwarzanie wsadowe, wykonywanie przekształceń, wielowersyjność i inne zaawansowane techniki.|  
|[Logowanie w programie MSBuild](../msbuild/logging-in-msbuild.md)|Opisuje sposób rejestrowania zdarzeń kompilacji, wiadomości i błędy.|  
|[Dodatkowe zasoby](../msbuild/additional-msbuild-resources.md)|Wyświetla listę zasobów społeczności i pomocy technicznej, aby uzyskać więcej informacji na temat programu MSBuild.|  
  
## <a name="reference"></a>Tematy pomocy  
 [Odwołanie do narzędzia MSBuild](../msbuild/msbuild-reference.md)  
 Zawiera łącza do tematów, które zawierają informacje odniesienia.  
  
 Słownik  
 Definiuje typowe terminy programu MSBuild.
