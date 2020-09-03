---
title: GenerateDeploymentManifest — — zadanie | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149598"
---
# <a name="generatedeploymentmanifest-task"></a>GenerateDeploymentManifest — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Generuje [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifest wdrożenia. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]Manifest wdrożenia opisuje wdrożenie aplikacji przez zdefiniowanie unikatowej tożsamości dla wdrożenia, zidentyfikowanie cech wdrożenia, takich jak instalacja lub tryb online, określanie ustawień aktualizacji aplikacji i lokalizacji aktualizacji oraz wskazanie odpowiedniego [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifestu aplikacji.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry `GenerateDeploymentManifest` zadania.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`AssemblyName`|Opcjonalny `String` parametr.<br /><br /> Określa `Name` pole tożsamości zestawu dla wygenerowanego manifestu. Jeśli ten parametr nie jest określony, nazwa jest wywnioskowana z `EntryPoint` `InputManifest` parametrów lub. Jeśli nie można wywnioskować nazwy, zadanie zgłosi błąd.|  
|`AssemblyVersion`|Opcjonalny `String` parametr.<br /><br /> Określa `Version` pole tożsamości zestawu dla wygenerowanego manifestu. Jeśli ten parametr nie jest określony, zadanie używa wartości "1.0.0.0".|  
|`CreateDesktopShortcut`|Opcjonalny `Boolean` parametr.<br /><br /> W przypadku wartości true na pulpicie zostanie utworzona ikona podczas instalacji aplikacji ClickOnce.|  
|`DeploymentUrl`|Opcjonalny `String` parametr.<br /><br /> Określa lokalizację aktualizacji aplikacji. Jeśli ten parametr nie jest określony, nie zdefiniowano lokalizacji aktualizacji dla aplikacji. Jeśli jednak `UpdateEnabled` parametr ma wartość `true` , należy określić lokalizację aktualizacji. Określona wartość powinna być w pełni kwalifikowanym adresem URL lub ścieżką UNC.|  
|`Description`|Opcjonalny `String` parametr.<br /><br /> Określa opcjonalny opis aplikacji.|  
|`DisallowUrlActivation`|Opcjonalny `Boolean` parametr.<br /><br /> Określa, czy aplikacja powinna być uruchamiana automatycznie podczas otwierania przy użyciu adresu URL. Jeśli ten parametr ma wartość `true` , aplikacja może zostać uruchomiona tylko z menu Start. Wartość domyślna tego parametru to `false` . Dane wejściowe są stosowane tylko wtedy, gdy `Install` wartość parametru to `true` .|  
|`EntryPoint`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Wskazuje punkt wejścia dla wygenerowanego zestawu manifestu. W przypadku [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifestu wdrożenia dane wejściowe określają [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] manifest aplikacji.<br /><br /> W programie [!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)] [zadanie GenerateApplicationManifest —](../msbuild/generateapplicationmanifest-task.md) wymagało `EntryPoint` wygenerowania manifestu aplikacji. (Zestaw lub manifesty natywne nie wymagają `EntryPoint` .) To wymaganie zostało wymuszone z powodu błędu kompilacji: "MSB3185: EntryPoint nie został określony dla manifestu".<br /><br /> [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] nie wystawia tego błędu, jeśli `EntryPoint` nie określono parametru zadania. Zamiast tego \<customHostSpecified> tag jest wstawiany jako element podrzędny \<entryPoint> tagu, na przykład:<br /><br /> `<entryPoint xmlns="urn:schemas-`<br /><br /> `microsoft-com:asm.v2">`<br /><br /> `<co.v1:customHostSpecified />`<br /><br /> `</entryPoint>`<br /><br /> Zależności bibliotek DLL można dodać do manifestu aplikacji, wykonując następujące czynności:<br /><br /> 1. Rozwiąż odwołania do zestawów za pomocą wywołania metody <xref:Microsoft.Build.Tasks.ResolveAssemblyReference> .<br />2. Przekaż dane wyjściowe poprzedniego zadania i samego zestawu do programu <xref:Microsoft.Build.Tasks.ResolveManifestFiles> .<br />3. Przekaż zależności przy użyciu `Dependencies` parametru do <xref:Microsoft.Build.Tasks.GenerateApplicationManifest> .|  
|`ErrorReportUrl`|Optional [ciąg] (<!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  -->konstruktora.<br /><br /> Określa adres URL strony sieci Web, która jest wyświetlana w oknach dialogowych podczas instalacji ClickOnce.|  
|`InputManifest`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br /> Wskazuje wejściowy dokument XML, który ma stanowić podstawę dla generatora manifestów. Dzięki temu dane strukturalne, takie jak niestandardowe definicje manifestu, zostaną odzwierciedlone w manifeście danych wyjściowych. Element główny w dokumencie XML musi być węzłem zestawu w przestrzeni nazw asmv1.|  
|`Install`|Opcjonalny `Boolean` parametr.<br /><br /> Określa, czy aplikacja jest zainstalowaną aplikacją, czy tylko w trybie online. Jeśli ten parametr ma wartość `true` , aplikacja zostanie zainstalowana w menu Start użytkownika i będzie można ją usunąć za pomocą okna dialogowego Dodawanie lub usuwanie programów. Jeśli ten parametr ma wartość `false` , aplikacja jest przeznaczona do użycia w trybie online ze strony sieci Web. Wartość domyślna tego parametru to `true` .|  
|`MapFileExtensions`|Opcjonalny `Boolean` parametr.<br /><br /> Określa, czy jest używane Mapowanie rozszerzenia nazwy pliku. deploy. Jeśli ten parametr to `true` , każdy plik programu jest publikowany z rozszerzeniem nazwy pliku. deploy. Ta opcja jest przydatna do zabezpieczenia serwera sieci Web, aby ograniczyć liczbę rozszerzeń nazw plików, które muszą być odblokowane w celu włączenia [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] wdrażania aplikacji. Wartość domyślna tego parametru to `false` .|  
|`MaxTargetPath`|Opcjonalny `String` parametr.<br /><br /> Określa maksymalną dozwoloną długość ścieżki pliku we [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] wdrożeniu aplikacji. Jeśli ten parametr jest określony, długość każdej ścieżki pliku w aplikacji jest sprawdzana względem tego limitu. Wszystkie elementy, które przekraczają limit, spowodują ostrzeżenie dotyczące kompilacji. Jeśli nie określono tego parametru wejściowego lub wartość jest równa zero, sprawdzanie nie jest wykonywane.|  
|`MinimumRequiredVersion`|Opcjonalny `String` parametr.<br /><br /> Określa, czy użytkownik może pominąć aktualizację. Jeśli użytkownik ma wersję, która jest mniejsza niż wymagana minimum, nie będzie mieć opcji pomijania aktualizacji. Te dane wejściowe są stosowane tylko wtedy, gdy wartość `Install` parametru to `true` .|  
|`OutputManifest`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> parametr.<br /><br /> Określa nazwę wygenerowanego pliku manifestu wyjściowego. Jeśli ten parametr nie jest określony, nazwa pliku wyjściowego jest wywnioskowana z tożsamości wygenerowanego manifestu.|  
|`Platform`|Opcjonalny `String` parametr.<br /><br /> Określa platformę docelową aplikacji. Ten parametr może mieć następujące wartości:<br /><br /> -   `AnyCPU`<br />-   `x86`<br />-   `x64`<br />-   `Itanium`<br /><br /> Wartość domyślna to `AnyCPU`.|  
|`Product`|Opcjonalny `String` parametr.<br /><br /> Określa nazwę aplikacji. Jeśli ten parametr nie jest określony, nazwa jest wywnioskowana z tożsamości wygenerowanego manifestu. Ta nazwa jest używana jako nazwa skrótu w menu Start i jest częścią nazwy, która pojawia się w oknie dialogowym Dodaj lub usuń programy.|  
|`Publisher`|Opcjonalny `String` parametr.<br /><br /> Określa wydawcę aplikacji. Jeśli ten parametr nie jest określony, nazwa zostanie wywnioskowana z zarejestrowanego użytkownika lub tożsamość wygenerowanego manifestu. Ta nazwa jest używana jako nazwa folderu w menu Start i jest częścią nazwy, która pojawia się w oknie dialogowym Dodaj lub usuń programy.|  
|`SuiteNamel`|Opcjonalny `String` parametr.<br /><br /> Określa nazwę folderu w menu Start, w którym znajduje się aplikacja po wdrożeniu ClickOnce.|  
|`SupportUrl`|Opcjonalny `String` parametr.<br /><br /> Określa łącze, które pojawia się w oknie dialogowym Dodaj lub usuń programy dla aplikacji. Określona wartość powinna być w pełni kwalifikowanym adresem URL lub ścieżką UNC.|  
|`TargetCulture`|Opcjonalny `String` parametr.<br /><br /> Identyfikuje kulturę aplikacji i określa `Language` pole tożsamości zestawu dla wygenerowanego manifestu. Jeśli ten parametr nie jest określony, zakłada się, że aplikacja ma niezmienną kulturę.|  
|`TrustUrlParameters`|Opcjonalny `Boolean` parametr.<br /><br /> Określa, czy parametry ciągu zapytania URL mają być dostępne dla aplikacji. Wartość domyślna tego parametru to `false` , co oznacza, że parametry nie będą dostępne dla aplikacji.|  
|`UpdateEnabled`|Opcjonalny `Boolean` parametr.<br /><br /> Wskazuje, czy aplikacja jest włączona dla aktualizacji. Wartość domyślna tego parametru to `false` . Ten parametr ma zastosowanie tylko wtedy, gdy wartość `Install` parametru to `true` .|  
|`UpdateInterval`|Opcjonalny `Int32` parametr.<br /><br /> Określa interwał aktualizacji aplikacji. Wartość domyślna tego parametru to zero. Ten parametr ma zastosowanie tylko wtedy, gdy wartości `Install` `UpdateEnabled` parametrów i `true` .|  
|`UpdateMode`|Opcjonalny `String` parametr.<br /><br /> Określa, czy aktualizacje mają być sprawdzane na pierwszym planie przed uruchomieniem aplikacji, czy w tle, gdy aplikacja jest uruchomiona. Ten parametr może mieć następujące wartości:<br /><br /> -   `Foreground`<br />-   `Background`<br /><br /> Wartość domyślna tego parametru to `Background` . Ten parametr ma zastosowanie tylko wtedy, gdy wartości `Install` `UpdateEnabled` parametrów i `true` .|  
|`UpdateUnit`|Opcjonalny `String` parametr.<br /><br /> Określa jednostki dla `UpdateInterval` parametru. Ten parametr może mieć następujące wartości:<br /><br /> -   `Hours`<br />-   `Days`<br />-   `Weeks`<br /><br /> Ten parametr ma zastosowanie tylko wtedy, gdy wartości `Install` `UpdateEnabled` parametrów i `true` .|  
  
## <a name="remarks"></a>Uwagi  
 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.GenerateManifestBase> klasy, która sama dziedziczy z <xref:Microsoft.Build.Utilities.Task> klasy. Aby zapoznać się z listą parametrów klasy Task, zobacz [Klasa bazowa zadania](../msbuild/task-base-class.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Widoku](../msbuild/msbuild-tasks.md)   
 [GenerateApplicationManifest —, zadanie](../msbuild/generateapplicationmanifest-task.md)   
 [SignFile —, zadanie](../msbuild/signfile-task.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
