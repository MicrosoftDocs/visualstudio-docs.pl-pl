---
title: ResolveComReference — — zadanie | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ResolveComReference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, ResolveCOMReference task
- ResolveCOMReference task [MSBuild]
ms.assetid: c9bf5fcf-6453-40ea-b50f-a212adc3e9b5
caps.latest.revision: 29
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fc9ca34d8b8afc01787db594ffba5a1a36ec190e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64815494"
---
# <a name="resolvecomreference-task"></a>ResolveComReference — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Przyjmuje listę jednej lub więcej nazw bibliotek typów lub plików TLB i rozpoznaje te biblioteki typów do lokalizacji na dysku.  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry `ResolveCOMReference` zadania.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`DelaySign`|Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true` , umieszcza klucz publiczny w zestawie. Jeśli `false` , w pełni podpisuje zestaw.|  
|`EnvironmentVariables`|Opcjonalny `String[]` parametr.<br /><br /> Tablica par zmiennych środowiskowych, oddzielonych znakami równości. Te zmienne są przesyłane do zduplikowanego tlbimp.exe i aximp.exe oprócz lub selektywnego przesłaniania, zwykłego bloku środowiska.|  
|`ExecuteAsTool`|Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true` program uruchamia tlbimp.exe i aximp.exe z odpowiedniego platformy docelowej, aby wygenerować niezbędne zestawy otoki. Ten parametr umożliwia wiele elementów docelowych.|  
|`IncludeVersionInInteropName`|Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true` , wersja biblioteki typów zostanie uwzględniona w nazwie otoki. Wartość domyślna to `false`.|  
|`KeyContainer`|Opcjonalny `String` parametr.<br /><br /> Określa kontener, który posiada publiczny/prywatny<br /><br /> para kluczy.|  
|`KeyFile`|Opcjonalny `String` parametr.<br /><br /> Określa element, który zawiera publiczny/prywatny<br /><br /> para kluczy.|  
|`NoClassMembers`|Opcjonalny `Boolean` parametr.|  
|`ResolvedAssemblyReferences`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Określa rozwiązane odwołania do zestawu.|  
|`ResolvedFiles`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr wyjściowy.<br /><br /> Określa w pełni kwalifikowane pliki na dysku, które odpowiadają fizycznym lokalizacji bibliotek typów, które zostały dostarczone jako dane wejściowe tego zadania.|  
|`ResolvedModules`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.|  
|`SdkToolsPath`|Optional [ciąg] (<!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  -->konstruktora.<br /><br /> Jeśli `ExecuteAsTool` tak jest `true` , ten parametr musi być ustawiony na ścieżkę narzędzi zestawu SDK dla planowanej wersji platformy.|  
|`StateFile`|Opcjonalne <!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  --> konstruktora.<br /><br /> Określa plik pamięci podręcznej dla sygnatur czasowych składnika modelu COM. Jeśli nie istnieje, każde uruchomienie spowoduje ponowne wygenerowanie wszystkich otok.|  
|`TargetFrameworkVersion`|Opcjonalne <!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  --> konstruktora.<br /><br /> Określa wersję platformy docelowej projektu.<br /><br /> Wartość domyślna to `String.Empty`. oznacza to, że nie istnieje filtrowanie odwołań na podstawie platformy docelowej.|  
|`TargetProcessorArchitecture`|Opcjonalne <!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  --> konstruktora.<br /><br /> Określa preferowaną docelową architekturę procesora. Przekazanie do flagi tlbimp.exe/Machine po przetłumaczeniu.<br /><br /> Wartość parametru powinna być elementem członkowskim <xref:Microsoft.Build.Utilities.ProcessorArchitecture> .|  
|`TypeLibFiles`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Określa ścieżkę pliku biblioteki typów do odwołań COM. Elementy zawarte w tym parametrze mogą zawierać metadane elementu. Aby uzyskać więcej informacji, zobacz sekcję "metadane elementu TypeLibFiles" poniżej.|  
|`TypeLibNames`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Określa nazwy bibliotek typów do rozwiązania. Elementy zawarte w tym parametrze muszą zawierać metadane elementu. Aby uzyskać więcej informacji, zobacz sekcję "metadane elementu TypeLibNames" poniżej.|  
|`WrapperOutputDirectory`|Opcjonalny `String` parametr.<br /><br /> Lokalizacja na dysku, na którym znajduje się wygenerowany zestaw międzyoperacyjny. Jeśli nie określono metadanych tego elementu, zadanie używa ścieżki bezwzględnej katalogu, w którym znajduje się plik projektu.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="typelibnames-item-metadata"></a>Metadane elementu TypeLibNames  
 W poniższej tabeli opisano metadane elementu dostępne dla elementów przekazaną do `TypeLibNames` parametru.  
  
|Metadane|Opis|  
|--------------|-----------------|  
|`GUID`|Metadane wymaganego elementu.<br /><br /> Identyfikator GUID dla biblioteki typów. Jeśli nie określono metadanych tego elementu, zadanie zakończy się niepowodzeniem.|  
|`VersionMajor`|Metadane wymaganego elementu.<br /><br /> Główna wersja biblioteki typów. Jeśli nie określono metadanych tego elementu, zadanie zakończy się niepowodzeniem.|  
|`VersionMinor`|Metadane wymaganego elementu.<br /><br /> Wersja pomocnicza biblioteki typów. Jeśli nie określono metadanych tego elementu, zadanie zakończy się niepowodzeniem.|  
|`LocaleIdentifier`|Opcjonalne metadane elementu.<br /><br /> Identyfikator ustawień regionalnych (lub LCID) dla biblioteki typów. Jest to wartość 32-bitowa, która identyfikuje język ludzki preferowany przez użytkownika, region lub aplikację. Jeśli nie określono metadanych tego elementu, zadanie używa domyślnego identyfikatora ustawień regionalnych "0".|  
|`WrapperTool`|Opcjonalne metadane elementu.<br /><br /> Określa narzędzie otoki, które jest używane do generowania otoki zestawu dla tej biblioteki typów. Jeśli nie określono metadanych tego elementu, zadanie używa domyślnego narzędzia otoki "tlbimp". Dostępne, bez uwzględniania wielkości liter TypeLibs są następujące:<br /><br /> -   `Primary`: Użyj tego narzędzia otoki, jeśli chcesz użyć już wygenerowanego podstawowego zestawu międzyoperacyjnego dla składnika modelu COM. W przypadku korzystania z tego narzędzia otoki nie należy określać katalogu wyjściowego otoki, ponieważ spowoduje to niepowodzenie zadania.<br />-   `TLBImp`: Użyj tego narzędzia otoki, gdy chcesz wygenerować zestaw międzyoperacyjny dla składnika modelu COM.<br />-   `AXImp`: Użyj tego narzędzia otoki, gdy chcesz wygenerować zestaw międzyoperacyjny dla kontrolki ActiveX.|  
  
## <a name="typelibfiles-item-metadata"></a>Metadane elementu TypeLibFiles  
 W poniższej tabeli opisano metadane elementu dostępne dla elementów przekazaną do `TypeLibFiles` parametru.  
  
|Metadane|Opis|  
|--------------|-----------------|  
|`WrapperTool`|Opcjonalne metadane elementu.<br /><br /> Określa narzędzie otoki, które jest używane do generowania otoki zestawu dla tej biblioteki typów. Jeśli nie określono metadanych tego elementu, zadanie używa domyślnego narzędzia otoki "tlbimp". Dostępne, bez uwzględniania wielkości liter TypeLibs są następujące:<br /><br /> -   `Primary`: Użyj tego narzędzia otoki, jeśli chcesz użyć już wygenerowanego podstawowego zestawu międzyoperacyjnego dla składnika modelu COM. W przypadku korzystania z tego narzędzia otoki nie należy określać katalogu wyjściowego otoki, ponieważ spowoduje to niepowodzenie zadania.<br />-   `TLBImp`: Użyj tego narzędzia otoki, gdy chcesz wygenerować zestaw międzyoperacyjny dla składnika modelu COM.<br />-   `AXImp`: Użyj tego narzędzia otoki, gdy chcesz wygenerować zestaw międzyoperacyjny dla kontrolki ActiveX.|  
  
> [!NOTE]
> Im więcej informacji zapewniających unikatową identyfikację biblioteki typów, tym większe jest prawdopodobieństwo, że zadanie zostanie rozpoznane do prawidłowego pliku na dysku.  
  
## <a name="remarks"></a>Uwagi  
 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Utilities.Task> klasy. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [Klasa bazowa zadania](../msbuild/task-base-class.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Widoku](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
