---
title: Generatedeploymentmanifest — zadanie | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GenerateDeploymentManifest
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GenerateDeploymentManifest task
- GenerateDeploymentManifest task [MSBuild]
ms.assetid: 0734ebda-734d-49c4-9642-8d9d919d45fd
caps.latest.revision: 32
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6f0c13e5ea8778ca91c30383287aaad6e965bb65
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59665847"
---
# <a name="generatedeploymentmanifest-task"></a>GenerateDeploymentManifest — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Generuje [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifest wdrożenia. A [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifest wdrożenia w tym artykule opisano wdrażanie aplikacji przez określenie unikatowej tożsamości wdrożenia, identyfikujące cech wdrażania, takie jak instalowanie lub tryb online, określenie aplikacji zaktualizuj ustawienia i lokalizacje, aktualizacji i wskazanie odpowiedniego [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifestu aplikacji.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry `GenerateDeploymentManifest` zadania.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`AssemblyName`|Opcjonalnie `String` parametru.<br /><br /> Określa `Name` pole tożsamości zestawu wygenerowanego manifestu. Jeśli ten parametr nie jest określony, nazwa wynika z `EntryPoint` lub `InputManifest` parametrów. Jeśli nazwa nie można wywnioskować, zadanie wyrzuca błąd.|  
|`AssemblyVersion`|Opcjonalnie `String` parametru.<br /><br /> Określa `Version` pole tożsamości zestawu wygenerowanego manifestu. Jeśli nie określono tego parametru, zadanie używa wartości "1.0.0.0".|  
|`CreateDesktopShortcut`|Opcjonalnie `Boolean` parametru.<br /><br /> W przypadku opcji true, tworzona jest ikona na pulpicie podczas instalacji aplikacji ClickOnce.|  
|`DeploymentUrl`|Opcjonalnie `String` parametru.<br /><br /> Określa lokalizację aktualizacji dla aplikacji. Jeśli ten parametr nie jest określony, lokalizacja aktualizacji nie jest zdefiniowana dla aplikacji. Jednak jeśli `UpdateEnabled` parametr jest `true`, należy określić zaktualizowaną lokalizację. Określona wartość powinna być w pełni kwalifikowany adres URL lub ścieżką UNC.|  
|`Description`|Opcjonalnie `String` parametru.<br /><br /> Określa opcjonalny opis dla aplikacji.|  
|`DisallowUrlActivation`|Opcjonalnie `Boolean` parametru.<br /><br /> Określa, czy aplikacja powinna zostać uruchomiona automatycznie po otwarciu go przy użyciu adresu URL. Jeśli ten parametr jest `true`, aplikację można uruchomić tylko z Start menu. Wartość domyślna tego parametru to `false`. Wejście to stosuje się tylko wtedy, gdy `Install` wartość parametru jest `true`.|  
|`EntryPoint`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Wskazuje punkt wejścia dla wygenerowanego zestawu manifestu. Aby uzyskać [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifestu wdrażania, dane wejściowe określają [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifestu aplikacji.<br /><br /> W [!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)], [generateapplicationmanifest — zadanie](../msbuild/generateapplicationmanifest-task.md) wymagane `EntryPoint` do generowania manifestu aplikacji. (Zestaw lub manifesty macierzyste nie wymagają `EntryPoint`.) Wymóg ten był stosowany z powodu błędu kompilacji: "MSB3185: Punkt wejścia nie jest określony dla manifestu."<br /><br /> [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] nie wystawia tego błędu podczas `EntryPoint` zadanie nie zostanie określony. Zamiast tego \<customhostspecified — > tag jest wstawiany jako element podrzędny elementu \<Punkt_wejścia > tagu, na przykład:<br /><br /> `<entryPoint xmlns="urn:schemas-`<br /><br /> `microsoft-com:asm.v2">`<br /><br /> `<co.v1:customHostSpecified />`<br /><br /> `</entryPoint>`<br /><br /> Za pomocą poniższej procedury, można dodać zależności DLL do manifestu aplikacji:<br /><br /> 1.  Rozpoznaj odwołania zestawu z wywołaniem <xref:Microsoft.Build.Tasks.ResolveAssemblyReference>.<br />2.  Przekazać dane wyjściowe poprzedniego zadania i samego montażu do <xref:Microsoft.Build.Tasks.ResolveManifestFiles>.<br />3.  Przekazać zależności za pomocą `Dependencies` parametr <xref:Microsoft.Build.Tasks.GenerateApplicationManifest>.|  
|`ErrorReportUrl`|(Opcjonalne [String]<!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  -->) parametr.<br /><br /> Określa adres URL strony sieci Web, która jest wyświetlana w oknach dialogowych podczas instalacji ClickOnce.|  
|`InputManifest`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br /> Wskazuje dokument danych wejściowych XML, która będzie służyć jako podstawa do generatora manifestu. Dzięki temu dane strukturalnych, takich jak niestandardowe definicje manifestu są odzwierciedlane w manifeście danych wyjściowych. Element główny dokumentu XML musi być zbiorem węzła trustinfo w obszarze nazw asmv1.|  
|`Install`|Opcjonalnie `Boolean` parametru.<br /><br /> Określa, czy aplikacja jest zainstalowaną aplikacją lub aplikacją tylko w trybie online. Jeśli ten parametr jest `true`, aplikacja zostanie zainstalowana w menu Start użytkownika i może zostać usunięty przez za pomocą okna dialogowego Dodaj lub usuń programy. Jeśli ten parametr jest `false`, aplikacja jest przeznaczona do użytku online ze strony sieci Web. Wartość domyślna tego parametru to `true`.|  
|`MapFileExtensions`|Opcjonalnie `Boolean` parametru.<br /><br /> Określa, czy mapowanie rozszerzenia nazwy pliku .deploy jest używane. Jeśli ten parametr jest `true`, każdy plik programu jest publikowany z rozszerzeniem nazwy pliku .deploy. Ta opcja jest przydatna dla zabezpieczeń serwera sieci Web ograniczyć liczbę rozszerzeń nazw plików, które muszą być odblokowane, żeby umożliwić [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] wdrożenia aplikacji. Wartość domyślna tego parametru to `false`.|  
|`MaxTargetPath`|Opcjonalnie `String` parametru.<br /><br /> Określa maksymalną dozwoloną długość ścieżki pliku w [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] wdrożenia aplikacji. Jeśli ten parametr jest określony, długość każdej ścieżki pliku w aplikacji jest sprawdzana względem tego limitu. Wszystkie elementy, które przekraczają limit spowodują ostrzeżenia kompilacji. Jeśli wejście to nie jest określona lub jest równe zeru, żadne sprawdzanie nie jest przeprowadzane.|  
|`MinimumRequiredVersion`|Opcjonalnie `String` parametru.<br /><br /> Określa, czy użytkownik może pominąć tę aktualizację. Jeśli użytkownik ma wersję, która jest mniejsza niż minimalna wymagana, nie będzie on możliwość pominąć tę aktualizację. Te dane wejściowe ma zastosowanie tylko jeśli wartość `Install` parametr `true`.|  
|`OutputManifest`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> parametru.<br /><br /> Określa nazwę utworzonego wyjściowego pliku manifestu. Jeśli ten parametr nie jest określony, nazwa pliku wyjściowego wynika z tożsamości wygenerowanego manifestu.|  
|`Platform`|Opcjonalnie `String` parametru.<br /><br /> Określa platformę docelową aplikacji. Ten parametr może mieć następujące wartości:<br /><br /> -   `AnyCPU`<br />-   `x86`<br />-   `x64`<br />-   `Itanium`<br /><br /> Wartość domyślna to `AnyCPU`.|  
|`Product`|Opcjonalnie `String` parametru.<br /><br /> Określa nazwę aplikacji. Jeśli ten parametr nie jest określony, nazwa wynika z tożsamości wygenerowanego manifestu. Nazwa ta jest używaną nazwą skrótu w Start menu i jest częścią nazwy, która pojawia się w oknie dialogowym Dodaj lub usuń programy.|  
|`Publisher`|Opcjonalnie `String` parametru.<br /><br /> Określa wydawcę aplikacji. Jeśli ten parametr nie jest określony, nazwa wynika z zarejestrowanego użytkownika lub tożsamości wygenerowanego manifestu. Nazwa ta jest używaną nazwą folderu, w Start menu i jest częścią nazwy, która pojawia się w oknie dialogowym Dodaj lub usuń programy.|  
|`SuiteNamel`|Opcjonalnie `String` parametru.<br /><br /> Określa nazwę folderu, w menu Start, w którym znajduje się aplikacja po wdrażania ClickOnce.|  
|`SupportUrl`|Opcjonalnie `String` parametru.<br /><br /> Określa łącze, które pojawia się w oknie dialogowym Dodaj lub usuń programy w aplikacji. Określona wartość powinna być w pełni kwalifikowany adres URL lub ścieżką UNC.|  
|`TargetCulture`|Opcjonalnie `String` parametru.<br /><br /> Identyfikuje kulturę aplikacji i określa `Language` pole tożsamości zestawu wygenerowanego manifestu. Jeśli ten parametr nie jest określony, zakłada się, że aplikacja jest kulturowo niezmienna.|  
|`TrustUrlParameters`|Opcjonalnie `Boolean` parametru.<br /><br /> Określa, czy parametry ciągu zapytania URL powinny być udostępnione do aplikacji. Wartość domyślna tego parametru to `false`, co oznacza, że parametry nie będą dostępne dla aplikacji.|  
|`UpdateEnabled`|Opcjonalnie `Boolean` parametru.<br /><br /> Wskazuje, czy aplikacja jest włączona dla aktualizacji. Wartość domyślna tego parametru to `false`. Ten parametr ma zastosowanie tylko jeśli wartość `Install` parametr `true`.|  
|`UpdateInterval`|Opcjonalnie `Int32` parametru.<br /><br /> Określa interwał aktualizacji dla aplikacji. Wartość domyślna tego parametru to zero. Ten parametr ma zastosowanie tylko jeśli wartości `Install` i `UpdateEnabled` parametry są zarówno `true`.|  
|`UpdateMode`|Opcjonalnie `String` parametru.<br /><br /> Określa, czy aktualizacje powinny być sprawdzane na pierwszym planie, zanim aplikacja jest uruchomiona lub jest uruchomiona w tle jako aplikacja. Ten parametr może mieć następujące wartości:<br /><br /> -   `Foreground`<br />-   `Background`<br /><br /> Wartość domyślna tego parametru to `Background`. Ten parametr ma zastosowanie tylko jeśli wartości `Install` i `UpdateEnabled` parametry są zarówno `true`.|  
|`UpdateUnit`|Opcjonalnie `String` parametru.<br /><br /> Określa jednostki dla `UpdateInterval` parametru. Ten parametr może mieć następujące wartości:<br /><br /> -   `Hours`<br />-   `Days`<br />-   `Weeks`<br /><br /> Ten parametr ma zastosowanie tylko jeśli wartości `Install` i `UpdateEnabled` parametry są zarówno `true`.|  
  
## <a name="remarks"></a>Uwagi  
 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.GenerateManifestBase> klasa, która sama dziedziczy <xref:Microsoft.Build.Utilities.Task> klasy. Aby uzyskać listę parametrów klasy zadanie, zobacz [klasa podstawowa zadania](../msbuild/task-base-class.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zadania](../msbuild/msbuild-tasks.md)   
 [Generateapplicationmanifest — zadanie](../msbuild/generateapplicationmanifest-task.md)   
 [Signfile — zadanie](../msbuild/signfile-task.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
