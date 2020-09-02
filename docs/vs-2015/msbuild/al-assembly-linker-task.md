---
title: AL (Konsolidator zestawu) — zadanie | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#AL
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- AL task [MSBuild]
- MSBuild, AL task
ms.assetid: 2ddefbf2-5662-4d55-99a6-ac383bf44560
caps.latest.revision: 25
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 85fb11429822d49d1a86697d9480f3a8ab0759de
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65684693"
---
# <a name="al-assembly-linker-task"></a>AL (Assembly Linker) — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zadanie AL otacza AL.exe, narzędzia, które jest dystrybuowane z [!INCLUDE[winsdklong](../includes/winsdklong-md.md)] . To narzędzie konsolidatora zestawu służy do tworzenia zestawu z manifestem z co najmniej jednego pliku, który jest modułem lub plikami zasobów. Kompilatory i środowiska programistyczne mogą już zapewnić te możliwości, więc często nie jest konieczne bezpośrednie używanie tego zadania. Konsolidator zestawu jest najbardziej przydatny dla deweloperów, którzy chcą utworzyć pojedynczy zestaw z wielu plików składników, takich jak te, które mogą być tworzone na podstawie programowania w języku mieszanym. To zadanie nie łączy modułów w pojedynczy plik zestawu; poszczególne moduły muszą być nadal dystrybuowane i dostępne w celu poprawnego załadowania zestawu. Aby uzyskać więcej informacji na AL.exe, zobacz [Al.exe (Konsolidator zestawu)](https://msdn.microsoft.com/library/b5382965-0053-47cf-b92f-862860275a01).  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry `AL` zadania.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`AlgorithmID`|Opcjonalny `String` parametr.<br /><br /> Określa algorytm wyznaczania wartości skrótu dla wszystkich plików w wieloplikowym zestawie z wyjątkiem pliku, który zawiera manifest zestawu. Aby uzyskać więcej informacji, zobacz dokumentację `/algid` opcji w [Al.exe (Konsolidator zestawu)](https://msdn.microsoft.com/library/b5382965-0053-47cf-b92f-862860275a01).|  
|`BaseAddress`|Opcjonalny `String` parametr.<br /><br /> Określa adres, pod którym zostanie załadowana Biblioteka DLL na komputerze użytkownika w czasie wykonywania. Aplikacje ładują się szybciej, jeśli określisz adres podstawowy bibliotek DLL, zamiast zezwalać systemowi operacyjnemu na przeniesienie bibliotek DLL w przestrzeni procesu. Ten parametr odpowiada opcji/Base [address] w [Al.exe (Konsolidator zestawu)](https://msdn.microsoft.com/library/b5382965-0053-47cf-b92f-862860275a01).|  
|`CompanyName`|Opcjonalny `String` parametr.<br /><br /> Określa ciąg dla `Company` pola w zestawie. Aby uzyskać więcej informacji, zobacz dokumentację `/comp[any]` opcji w [Al.exe (Konsolidator zestawu)](https://msdn.microsoft.com/library/b5382965-0053-47cf-b92f-862860275a01).|  
|`Configuration`|Opcjonalny `String` parametr.<br /><br /> Określa ciąg dla `Configuration` pola w zestawie. Aby uzyskać więcej informacji, zobacz dokumentację `/config[uration]` opcji w [Al.exe (Konsolidator zestawu)](https://msdn.microsoft.com/library/b5382965-0053-47cf-b92f-862860275a01).|  
|`Copyright`|Opcjonalny `String` parametr.<br /><br /> Określa ciąg dla `Copyright` pola w zestawie. Aby uzyskać więcej informacji, zobacz dokumentację `/copy[right]` opcji w [Al.exe (Konsolidator zestawu)](https://msdn.microsoft.com/library/b5382965-0053-47cf-b92f-862860275a01).|  
|`Culture`|Opcjonalny `String` parametr.<br /><br /> Określa ciąg kultury do skojarzenia z zestawem. Aby uzyskać więcej informacji, zobacz dokumentację `/c[ulture]` opcji w [Al.exe (Konsolidator zestawu)](https://msdn.microsoft.com/library/b5382965-0053-47cf-b92f-862860275a01).|  
|`DelaySign`|Opcjonalny `Boolean` parametr.<br /><br /> `true` Aby umieścić tylko klucz publiczny w zestawie; `false` Aby w pełni podpisać zestaw. Aby uzyskać więcej informacji, zobacz dokumentację `/delay[sign]` opcji w [Al.exe (Konsolidator zestawu)](https://msdn.microsoft.com/library/b5382965-0053-47cf-b92f-862860275a01).|  
|`Description`|Opcjonalny `String` parametr.<br /><br /> Określa ciąg dla `Description` pola w zestawie. Aby uzyskać więcej informacji, zobacz dokumentację `/descr[iption]` opcji w [Al.exe (Konsolidator zestawu)](https://msdn.microsoft.com/library/b5382965-0053-47cf-b92f-862860275a01).|  
|`EmbedResources`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Osadza określone zasoby w obrazie zawierającym manifest zestawu. To zadanie kopiuje zawartość pliku zasobów do obrazu. Elementy przesłane do tego parametru mogą zawierać opcjonalne metadane dołączone do nich `LogicalName` i `Access` . `LogicalName`Metadane są używane do określania wewnętrznego identyfikatora dla zasobu.  `Access`Metadane można ustawić tak, aby `private` zasób nie był widoczny dla innych zestawów. Aby uzyskać więcej informacji, zobacz dokumentację `/embed[resource]` opcji w [Al.exe (Konsolidator zestawu)](https://msdn.microsoft.com/library/b5382965-0053-47cf-b92f-862860275a01).|  
|`EvidenceFile`|Opcjonalny `String` parametr.<br /><br /> Osadza określony plik w zestawie z nazwą zasobu `Security.Evidence` .<br /><br /> Nie można używać `Security.Evidence` do zwykłych zasobów. Ten parametr odpowiada `/e[vidence]` opcji w [Al.exe (Konsolidator zestawu)](https://msdn.microsoft.com/library/b5382965-0053-47cf-b92f-862860275a01).|  
|`ExitCode`|Opcjonalny `Int32` wyjściowy parametr tylko do odczytu.<br /><br /> Określa kod zakończenia dostarczony przez wykonane polecenie.|  
|`FileVersion`|Opcjonalny `String` parametr.<br /><br /> Określa ciąg dla `File Version` pola w zestawie. Aby uzyskać więcej informacji, zobacz dokumentację `/fileversion` opcji w [Al.exe (Konsolidator zestawu)](https://msdn.microsoft.com/library/b5382965-0053-47cf-b92f-862860275a01).|  
|`Flags`|Opcjonalny `String` parametr.<br /><br /> Określa wartość dla `Flags` pola w zestawie. Aby uzyskać więcej informacji, zobacz dokumentację `/flags` opcji w [Al.exe (Konsolidator zestawu)](https://msdn.microsoft.com/library/b5382965-0053-47cf-b92f-862860275a01).|  
|`GenerateFullPaths`|Opcjonalny `Boolean` parametr.<br /><br /> Powoduje, że zadanie używa ścieżki bezwzględnej dla wszystkich plików, które są raportowane w komunikacie o błędzie. Ten parametr odpowiada `/fullpaths` opcji w [Al.exe (Konsolidator zestawu)](https://msdn.microsoft.com/library/b5382965-0053-47cf-b92f-862860275a01).|  
|`KeyContainer`|Opcjonalny `String` parametr.<br /><br /> Określa kontener zawierający parę kluczy. Zestaw zostanie podpisany (należy nadać mu silną nazwę) przez wstawienie klucza publicznego do manifestu zestawu. Następnie zadanie spowoduje podpisywanie końcowego zestawu przy użyciu klucza prywatnego. Aby uzyskać więcej informacji, zobacz dokumentację `/keyn[ame]` opcji w [Al.exe (Konsolidator zestawu)](https://msdn.microsoft.com/library/b5382965-0053-47cf-b92f-862860275a01).|  
|`KeyFile`|Opcjonalny `String` parametr.<br /><br /> Określa plik, który zawiera parę kluczy lub tylko klucz publiczny do podpisywania zestawu. Kompilator wstawia klucz publiczny w manifeście zestawu, a następnie podpisuje ostateczny zestaw przy użyciu klucza prywatnego. Aby uzyskać więcej informacji, zobacz dokumentację `/keyf[ile]` opcji w [Al.exe (Konsolidator zestawu)](https://msdn.microsoft.com/library/b5382965-0053-47cf-b92f-862860275a01).|  
|`LinkResources`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Łączy określone pliki zasobów z zestawem. Zasób stał się częścią zestawu, ale plik nie jest kopiowany. Elementy przesłane do tego parametru mogą zawierać opcjonalne metadane o nazwie `LogicalName` , `Target` i `Access` . `LogicalName`Metadane są używane do określania wewnętrznego identyfikatora dla zasobu. `Target`Metadane mogą określać ścieżkę i nazwę pliku, do którego zadanie kopiuje plik, po którym kompiluje ten nowy plik do zestawu. `Access`Metadane można ustawić tak, aby `private` zasób nie był widoczny dla innych zestawów. Aby uzyskać więcej informacji, zobacz dokumentację `/link[resource]` opcji w [Al.exe (Konsolidator zestawu)](https://msdn.microsoft.com/library/b5382965-0053-47cf-b92f-862860275a01).|  
|`MainEntryPoint`|Opcjonalny `String` parametr.<br /><br /> Określa w pełni kwalifikowaną nazwę (*Class. Method*) metody, która ma być używana jako punkt wejścia podczas konwertowania modułu do pliku wykonywalnego. Ten parametr odpowiada `/main` opcji w [Al.exe (Konsolidator zestawu)](https://msdn.microsoft.com/library/b5382965-0053-47cf-b92f-862860275a01).|  
|`OutputAssembly`|Wymagany <xref:Microsoft.Build.Framework.ITaskItem> parametr wyjściowy.<br /><br /> Określa nazwę pliku wygenerowanego przez to zadanie. Ten parametr odpowiada `/out` opcji w [Al.exe (Konsolidator zestawu)](https://msdn.microsoft.com/library/b5382965-0053-47cf-b92f-862860275a01).|  
|`Platform`|Opcjonalny `String` parametr.<br /><br /> Ogranicza platformę, na której można uruchomić ten kod; musi mieć jedną z wartości `x86` , `Itanium` , `x64` , lub `anycpu` . Wartość domyślna to `anycpu`. Ten parametr odpowiada `/platform` opcji w [Al.exe (Konsolidator zestawu)](https://msdn.microsoft.com/library/b5382965-0053-47cf-b92f-862860275a01).|  
|`ProductName`|Opcjonalny `String` parametr.<br /><br /> Określa ciąg dla `Product` pola w zestawie. Aby uzyskać więcej informacji, zobacz dokumentację `/prod[uct]` opcji w [Al.exe (Konsolidator zestawu)](https://msdn.microsoft.com/library/b5382965-0053-47cf-b92f-862860275a01).|  
|`ProductVersion`|Opcjonalny `String` parametr.<br /><br /> Określa ciąg dla `ProductVersion` pola w zestawie. Aby uzyskać więcej informacji, zobacz dokumentację `/productv[ersion]` opcji w [Al.exe (Konsolidator zestawu)](https://msdn.microsoft.com/library/b5382965-0053-47cf-b92f-862860275a01).|  
|`ResponseFiles`|Opcjonalny `String[]` parametr.<br /><br /> Określa pliki odpowiedzi, które zawierają dodatkowe opcje do przekazania do konsolidatora zestawu.|  
|`SdkToolsPath`|Opcjonalny `String` parametr.<br /><br /> Określa ścieżkę do narzędzi zestawu SDK, takich jak resgen.exe.|  
|`SourceModules`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Jeden lub więcej modułów do skompilowania w zestawie. Moduły zostaną wyświetlone w manifeście zestawu, który będzie nadal musiał być dystrybuowany i dostępny w celu załadowania zestawu. Elementy przesłane do tego parametru mogą mieć dodatkowe metadane o nazwie `Target` , który określa ścieżkę i nazwę pliku, do którego zadanie kopiuje plik, po czym kompiluje ten nowy plik do zestawu. Aby uzyskać więcej informacji, zobacz dokumentację dotyczącą [Al.exe (Konsolidator zestawu)](https://msdn.microsoft.com/library/b5382965-0053-47cf-b92f-862860275a01). Ten parametr odnosi się do listy modułów, które są przesyłane do Al.exe bez określonego przełącznika.|  
|`TargetType`|Opcjonalny `String` parametr.<br /><br /> Określa format pliku wyjściowego: `library` (Biblioteka kodu), `exe` (Aplikacja konsolowa) lub `win` (aplikacja oparta na systemie Windows). Wartość domyślna to `library`. Ten parametr odpowiada `/t[arget]` opcji w [Al.exe (Konsolidator zestawu)](https://msdn.microsoft.com/library/b5382965-0053-47cf-b92f-862860275a01).|  
|`TemplateFile`|Opcjonalny `String` parametr.<br /><br /> Określa zestaw, z którego mają dziedziczyć wszystkie metadane zestawu, z wyjątkiem pola kultura. Określony zestaw musi mieć silną nazwę.<br /><br /> Zestaw utworzony przy użyciu `TemplateFile` parametru będzie zestawem satelickim. Ten parametr odpowiada `/template` opcji w [Al.exe (Konsolidator zestawu)](https://msdn.microsoft.com/library/b5382965-0053-47cf-b92f-862860275a01).|  
|`Timeout`|Opcjonalny `Int32` parametr.<br /><br /> Określa ilość czasu (w milisekundach), po upływie którego plik wykonywalny zadania zostanie zakończony. Wartość domyślna to `Int.MaxValue` , co oznacza, że nie ma limitu czasu.|  
|`Title`|Opcjonalny `String` parametr.<br /><br /> Określa ciąg dla `Title` pola w zestawie. Aby uzyskać więcej informacji, zobacz dokumentację `/title` opcji w [Al.exe (Konsolidator zestawu)](https://msdn.microsoft.com/library/b5382965-0053-47cf-b92f-862860275a01).|  
|`ToolPath`|Opcjonalny `String` parametr.<br /><br /> Określa lokalizację, z której zadanie będzie ładować podstawowy plik wykonywalny (Al.exe). Jeśli ten parametr nie jest określony, zadanie używa ścieżki instalacji zestawu SDK odpowiadającej wersji platformy, która jest uruchomiona [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] .|  
|`Trademark`|Opcjonalny `String` parametr.<br /><br /> Określa ciąg dla `Trademark` pola w zestawie. Aby uzyskać więcej informacji, zobacz dokumentację `/trade[mark]` opcji w [Al.exe (Konsolidator zestawu)](https://msdn.microsoft.com/library/b5382965-0053-47cf-b92f-862860275a01).|  
|`Version`|Opcjonalny `String` parametr.<br /><br /> Określa informacje o wersji tego zestawu. Format ciągu to *główna. pomocnicza. kompilacja. poprawka*. Wartość domyślna to 0. Aby uzyskać więcej informacji, zobacz dokumentację `/v[ersion]` opcji w [Al.exe (Konsolidator zestawu)](https://msdn.microsoft.com/library/b5382965-0053-47cf-b92f-862860275a01).|  
|`Win32Icon`|Opcjonalny `String` parametr.<br /><br /> Wstawia plik .ico do zestawu. Plik .ico nadaje plikowi wyjściowemu pożądany wygląd w Eksploratorze plików. Ten parametr odpowiada `/win32icon` opcji w [Al.exe (Konsolidator zestawu)](https://msdn.microsoft.com/library/b5382965-0053-47cf-b92f-862860275a01).|  
|`Win32Resource`|Opcjonalny `String` parametr.<br /><br /> Wstawia zasób Win32 (plik .res) do pliku wyjściowego. Aby uzyskać więcej informacji, zobacz dokumentację `/win32res` opcji w [Al.exe (Konsolidator zestawu)](https://msdn.microsoft.com/library/b5382965-0053-47cf-b92f-862860275a01).|  
  
## <a name="remarks"></a>Uwagi  
 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.ToolTaskExtension> klasy, która sama dziedziczy z <xref:Microsoft.Build.Utilities.ToolTask> klasy. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [ToolTaskExtension Base Class](../msbuild/tooltaskextension-base-class.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy zestaw z określonymi opcjami.  
  
```  
<AL  
    EmbedResources="@(EmbeddedResource)"  
    Culture="%(EmbeddedResource.Culture)"  
    TemplateFile="@(IntermediateAssembly)"  
    KeyContainer="$(KeyContainerName)"  
    KeyFile="$(KeyOriginatorFile)"  
    DelaySign="$(DelaySign)"  
  
    OutputAssembly=  
       "%(EmbeddedResource.Culture)\$(TargetName).resources.dll">  
  
    <Output TaskParameter="OutputAssembly"  
        ItemName="SatelliteAssemblies"/>  
</AL>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)   
 [Zadania](../msbuild/msbuild-tasks.md)
