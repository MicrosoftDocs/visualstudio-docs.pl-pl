---
title: CSC — zadanie | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Csc
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Csc task [MSBuild]
- MSBuild, Csc task
ms.assetid: d8c19b36-f5ca-484b-afa6-8ff3b90e103a
caps.latest.revision: 30
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2d69d19e43ae2e94382e32ba6579f55cecb2efca
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59659491"
---
# <a name="csc-task"></a>Csc — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Opakowuje CSC.exe i tworzy pliki wykonywalne (pliki .exe), bibliotek dołączanych dynamicznie (pliki .dll) lub modułów kodu (.netmodule pliki). Aby uzyskać więcej informacji na temat CSC.exe, zobacz [opcje kompilatora C#](http://msdn.microsoft.com/library/d3403556-1816-4546-a782-e8223a772e44).  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry `Csc` zadania.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`AdditionalLibPaths`|Opcjonalnie `String[]` parametru.<br /><br /> Określa dodatkowe katalogi do wyszukiwania odwołań. Aby uzyskać więcej informacji, zobacz [/lib (opcje kompilatora C#)](http://msdn.microsoft.com/library/b0efcc88-e8aa-4df4-a00b-8bdef70b7673).|  
|`AddModules`|Opcjonalnie `String` parametru.<br /><br /> Określa jeden lub wiele modułów jako część zestawu. Aby uzyskać więcej informacji, zobacz [/addmodule (opcje kompilatora C#)](http://msdn.microsoft.com/library/ed604546-0dc2-4bd4-9a3e-610a8d973e58).|  
|`AllowUnsafeBlocks`|Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, kompiluje kod, który używa [niebezpieczne](http://msdn.microsoft.com/library/7e818009-1c6e-4b9e-b769-3728a01586a0) — słowo kluczowe. Aby uzyskać więcej informacji, zobacz [/ unsafe (opcje kompilatora C#)](http://msdn.microsoft.com/library/fdb77ed9-da03-45bd-bb7f-250704da1bcc).|  
|`ApplicationConfiguration`|Opcjonalnie `String` parametru.<br /><br /> Określa plik konfiguracyjny aplikacji zawierający ustawienia powiązania zestawu.|  
|`BaseAddress`|Opcjonalnie `String` parametru.<br /><br /> Określa preferowany adres podstawowy, w którym można załadować biblioteki DLL. Domyślny adres podstawowy dla biblioteki DLL jest ustawiana przez [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] środowiska uruchomieniowego języka wspólnego. Aby uzyskać więcej informacji, zobacz [/baseAddress (opcje kompilatora C#)](http://msdn.microsoft.com/library/ce13c965-dfe4-4433-94f5-63b476e3a608).|  
|`CheckForOverflowUnderflow`|Opcjonalnie `Boolean` parametru.<br /><br /> Określa, czy liczba całkowita arytmetyczny, który przepełnienie granic o typie danych powoduje wyjątek w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [/ checked (opcje kompilatora C#)](http://msdn.microsoft.com/library/fb7475d3-e6a6-4e6d-b86c-69e7a74c854b).|  
|`CodePage`|Opcjonalnie `Int32` parametru.<br /><br /> Określa stronę kodową do użycia dla wszystkich plikach kodu źródłowego w kompilacji. Aby uzyskać więcej informacji, zobacz [/CODEPAGE (opcje kompilatora C#)](http://msdn.microsoft.com/library/75942989-b69a-4308-90a0-840c73d2c478).|  
|`DebugType`|Opcjonalnie `String` parametru.<br /><br /> Określa typ debugowania. `DebugType` może być `full` lub `pdbonly`. Wartość domyślna to `full`, co pozwala debuger dołączony do uruchomionego programu. Określanie `pdbonly` umożliwia źródła debugowania kodu, gdy program jest uruchomiony w debugerze, ale są wyświetlane tylko asemblera, gdy uruchomiony program jest dołączony do debugera.<br /><br /> Ten parametr zastępuje `EmitDebugInformation` parametru.<br /><br /> Aby uzyskać więcej informacji, zobacz [/Debug (opcje kompilatora C#)](http://msdn.microsoft.com/library/e2b48c07-01bc-45cc-a52c-92e9085eb969).|  
|`DefineConstants`|Opcjonalnie `String` parametru.<br /><br /> Definiuje symbole preprocesora. Aby uzyskać więcej informacji, zobacz [/ define (opcje kompilatora C#)](http://msdn.microsoft.com/library/f17d7b4d-82d0-4133-8563-68cced1cac6e).|  
|`DelaySign`|Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, określa, że chcesz, aby podpisać zestaw całkowicie. Jeśli `false`, określa, że chcesz tylko umieścić klucz publiczny w zestawie.<br /><br /> Ten parametr jest ignorowany, chyba że używany z `KeyFile` lub `KeyContainer` parametru.<br /><br /> Aby uzyskać więcej informacji, zobacz [/DelaySign (opcje kompilatora C#)](http://msdn.microsoft.com/library/bcb058eb-2933-4e7f-b356-5c941db4de75).|  
|`DisabledWarnings`|Opcjonalnie `String` parametru.<br /><br /> Określa listę ostrzeżeń, które mają zostać wyłączone. Aby uzyskać więcej informacji, zobacz [/nowarn (opcje kompilatora C#)](http://msdn.microsoft.com/library/6dcbc5e8-ae67-4566-9df3-f63cfdd9c4e4).|  
|`DocumentationFile`|Opcjonalnie `String` parametru.<br /><br /> Przetwarza komentarze dokumentacji do pliku XML. Aby uzyskać więcej informacji, zobacz [/doc (opcje kompilatora C#)](http://msdn.microsoft.com/library/849eea59-c936-4311-bad8-d07404480f2a).|  
|`EmitDebugInformation`|Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, zadanie generuje informacje o debugowaniu i umieszcza je w pliku bazy danych (PDB) programu. Jeśli `false`, zadanie emituje żadnych informacji debugowania. Wartość domyślna to `false`. Aby uzyskać więcej informacji, zobacz [/Debug (opcje kompilatora C#)](http://msdn.microsoft.com/library/e2b48c07-01bc-45cc-a52c-92e9085eb969).|  
|`ErrorReport`|Opcjonalnie `String` parametru.<br /><br /> Zapewnia wygodny sposób, aby zgłosić błąd wewnętrzny C# do firmy Microsoft. Ten parametr może mieć wartość `prompt`, `send`, lub `none`. Jeśli parametr jest ustawiony na `prompt`, zostanie wyświetlony monit, gdy wystąpi błąd wewnętrzny kompilatora. Monit umożliwia elektronicznie Wyślij raport o usterce do firmy Microsoft. Jeśli parametr jest ustawiony na `send`, raport o usterce są wysyłane automatycznie. Jeśli parametr jest ustawiony na `none`, tylko w tekst wyjściowy kompilatora zgłaszany jest błąd. Wartość domyślna to `none`. Aby uzyskać więcej informacji, zobacz [/errorreport (opcje kompilatora C#)](http://msdn.microsoft.com/library/bd0e7493-b79d-4369-9c3f-ba26ebdfbedf).|  
|`FileAlignment`|Opcjonalnie `Int32` parametru.<br /><br /> Określa rozmiar sekcji w pliku wyjściowym. Aby uzyskać więcej informacji, zobacz [/filealign (opcje kompilatora C#)](http://msdn.microsoft.com/library/15cf1c98-3798-4ced-9f08-60619308a073).|  
|`GenerateFullPaths`|Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, określa bezwzględną ścieżkę do pliku w danych wyjściowych kompilatora. Jeśli `false`, określa nazwę pliku. Wartość domyślna to `false`. Aby uzyskać więcej informacji, zobacz [/fullpaths (opcje kompilatora C#)](http://msdn.microsoft.com/library/d2a5f857-cbb2-430b-879c-d648aaf0b8c4).|  
|`KeyContainer`|Opcjonalnie `String` parametru.<br /><br /> Określa nazwę kontenera kluczy kryptograficznych. Aby uzyskać więcej informacji, zobacz [/KeyContainer (opcje kompilatora C#)](http://msdn.microsoft.com/library/b3982b6d-2382-4f7e-bebd-ce98eaa30763).|  
|`KeyFile`|Opcjonalnie `String` parametru.<br /><br /> Określa nazwę pliku zawierającego klucz kryptograficzny. Aby uzyskać więcej informacji, zobacz [/KeyFile (opcje kompilatora C#)](http://msdn.microsoft.com/library/0815f9de-ace4-4e98-b4c6-13c55dea40c2).|  
|`LangVersion`|Opcjonalnie `String` parametru.<br /><br /> Określa wersję języka. Aby uzyskać więcej informacji, zobacz [/langversion (opcje kompilatora C#)](http://msdn.microsoft.com/library/3fb00b05-a0ff-4782-b313-13a4c0f62d94).|  
|`LinkResources`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Tworzy łącze do [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] zasobu w pliku wyjściowym; plik zasobu nie zostanie umieszczony w pliku wyjściowym.<br /><br /> Pozycji przekazanych do tego parametru może zawierać wpisy opcjonalne metadane, o nazwie `LogicalName` i `Access`. `LogicalName` odnosi się do `identifier` parametru `/linkresource` przełączyć, i `Access` odpowiada `accessibility-modifier` parametru. Aby uzyskać więcej informacji, zobacz [/linkresource (opcje kompilatora C#)](http://msdn.microsoft.com/library/440c26c2-77c1-4811-a0a3-57cce3f5fc96).|  
|`MainEntryPoint`|Opcjonalnie `String` parametru.<br /><br /> Określa lokalizację `Main` metody. Aby uzyskać więcej informacji, zobacz [/main (opcje kompilatora C#)](http://msdn.microsoft.com/library/975cf4d5-36ac-4530-826c-4aad0c7f2049).|  
|`ModuleAssemblyName`|Opcjonalnie `String` parametru.<br /><br /> Określa nazwę zestawu, który będzie należeć tego modułu.|  
|`NoConfig`|Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, informuje kompilator, nie można skompilować przy użyciu pliku csc.rsp. Aby uzyskać więcej informacji, zobacz [/noconfig (opcje kompilatora C#)](http://msdn.microsoft.com/library/cd26967e-e494-4c8c-b5c9-af13b2f78b2e).|  
|`NoLogo`|Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, Pomija wyświetlanie informacji o transparencie kompilatora. Aby uzyskać więcej informacji, zobacz [/nologo (opcje kompilatora C#)](http://msdn.microsoft.com/library/426afb36-a8fb-469d-9c45-a35d9512557c).|  
|`NoStandardLib`|Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, uniemożliwia Importuj biblioteki mscorlib.dll, która określa całą przestrzeń nazw System. Użyj tego parametru, jeśli chcesz zdefiniować lub tworzyć własne systemową przestrzenią nazw i obiektów. Aby uzyskać więcej informacji, zobacz [/nostdlib (opcje kompilatora C#)](http://msdn.microsoft.com/library/ec197989-fa49-4725-a455-e06b551eb65f).|  
|`NoWin32Manifest`|Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, nie dołączaj domyślny manifest Win32.|  
|`Optimize`|Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, włącza optymalizacje. Jeśli `false`, wyłącza optymalizacje. Aby uzyskać więcej informacji, zobacz [/ optimize (opcje kompilatora C#)](http://msdn.microsoft.com/library/6dd5b6f2-cd1d-4593-a9f4-1c2ed9404ca0).|  
|`OutputAssembly`|Opcjonalnie `String` parametr wyjściowy.<br /><br /> Określa nazwę pliku wyjściowego. Aby uzyskać więcej informacji, zobacz [/out (opcje kompilatora C#)](http://msdn.microsoft.com/library/70d91d01-7bd2-4aea-ba8b-4e9807e9caa5).|  
|`PdbFile`|Opcjonalnie `String` parametru.<br /><br /> Określa nazwę pliku informacji debugowania. Domyślną nazwą jest nazwa pliku wyjściowego z rozszerzeniem .pdb.|  
|`Platform`|Opcjonalnie `String` parametru.<br /><br /> Określa platformę procesora, który ma zostać użyty przez plik wyjściowy. Ten parametr może mieć wartość `x86`, `x64`, lub `anycpu`. Wartość domyślna to `anycpu`. Aby uzyskać więcej informacji, zobacz [/platform (opcje kompilatora C#)](http://msdn.microsoft.com/library/c290ff5e-47f4-4a85-9bb3-9c2525b0be04).|  
|`References`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Powoduje, że zadanie zaimportować informacje typu publicznego z określonych elementów do bieżącego projektu. Aby uzyskać więcej informacji, zobacz [/Reference (opcje kompilatora C#)](http://msdn.microsoft.com/library/8d13e5b0-abf6-4c46-bf71-2daf2cd0a6c4).<br /><br /> Można określić [!INCLUDE[csprcs](../includes/csprcs-md.md)] odwołania aliasu w [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] pliku, dodając metadanych `Aliases` do oryginalnego elementu "Odwołanie". Na przykład można ustawić aliasu "LS1" w wierszu polecenia następujące CSC:<br /><br /> `csc /r:LS1=MyCodeLibrary.dll /r:LS2=MyCodeLibrary2.dll *.cs`<br /><br /> należy użyć:<br /><br /> `<Reference Include="MyCodeLibrary"> <Aliases>LS1</Aliases> </Reference>`|  
|`Resources`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Osadza [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] zasobów do pliku wyjściowego.<br /><br /> Pozycji przekazanych do tego parametru może zawierać wpisy opcjonalne metadane, o nazwie `LogicalName` i `Access`. `LogicalName` odnosi się do `identifier` parametru `/resource` przełączyć, i `Access` odpowiada `accessibility-modifier` parametru. Aby uzyskać więcej informacji, zobacz [/Resource (opcje kompilatora C#)](http://msdn.microsoft.com/library/5212666e-98ab-47e4-a497-b5545ab15c7f).|  
|`ResponseFiles`|Opcjonalnie `String` parametru.<br /><br /> Określa plik odpowiedzi, który zawiera polecenia służące do tego zadania. Aby uzyskać więcej informacji, zobacz [@ (Określ plik odpowiedzi)](http://msdn.microsoft.com/library/dda4fa9f-a02c-400f-8b6a-d58834e13d7f).|  
|`Sources`|Opcjonalnie <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametru.<br /><br /> Określa co najmniej jeden [!INCLUDE[csprcs](../includes/csprcs-md.md)] plików źródłowych.|  
|`TargetType`|Opcjonalnie `String` parametru.<br /><br /> Określa format pliku wyjściowego. Ten parametr może mieć wartości `library`, tworzy bibliotekę kodu `exe`, tworzy aplikacji konsoli, `module`, co powoduje utworzenie modułu, lub `winexe`, która tworzy Windows program. Wartość domyślna to `library`. Aby uzyskać więcej informacji, zobacz [/TARGET (opcje kompilatora C#)](http://msdn.microsoft.com/library/a18bbd8e-bbf7-49e7-992c-717d0eb1f76f).|  
|`TreatWarningsAsErrors`|Opcjonalnie `Boolean` parametru.<br /><br /> Jeśli `true`, traktuje wszystkie ostrzeżenia jako błędy. Aby uzyskać więcej informacji, zobacz [/warnaserror (opcje kompilatora C#)](http://msdn.microsoft.com/library/04680ec3-08d6-4e2e-a274-38310e10e33c).|  
|`UseHostCompilerIfAvailable`|Opcjonalnie `Boolean` parametru.<br /><br /> Powoduje, że zadanie używa obiektu wewnątrzprocesowego kompilatora, jeśli jest dostępny. Używany wyłącznie przez [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|  
|`Utf8Output`|Opcjonalnie `Boolean` parametru.<br /><br /> Kompilator dzienniki danych wyjściowych przy użyciu kodowania UTF-8. Aby uzyskać więcej informacji, zobacz [/utf8output (opcje kompilatora C#)](http://msdn.microsoft.com/library/27ff7381-c281-45d7-b2eb-1ad644b1354e).|  
|`WarningLevel`|Opcjonalnie `Int32` parametru.<br /><br /> Określa poziom ostrzeżeń kompilatora do wyświetlenia. Aby uzyskać więcej informacji, zobacz [/ warn (opcje kompilatora C#)](http://msdn.microsoft.com/library/5f80ff59-4991-4382-9f9a-77da18446e71).|  
|`WarningsAsErrors`|Opcjonalnie `String` parametru.<br /><br /> Określa listę ostrzeżeń do traktowania jako błędy. Aby uzyskać więcej informacji, zobacz [/warnaserror (opcje kompilatora C#)](http://msdn.microsoft.com/library/04680ec3-08d6-4e2e-a274-38310e10e33c).<br /><br /> Ten parametr zastępuje `TreatWarningsAsErrors` parametru.|  
|`WarningsNotAsErrors`|Opcjonalnie `String` parametru.<br /><br /> Określa listę ostrzeżeń, które nie są traktowane jako błędy. Aby uzyskać więcej informacji, zobacz [/warnaserror (opcje kompilatora C#)](http://msdn.microsoft.com/library/04680ec3-08d6-4e2e-a274-38310e10e33c).<br /><br /> Ten parametr jest przydatna, jeśli `TreatWarningsAsErrors` parametr ma wartość `true`.|  
|`Win32Icon`|Opcjonalnie `String` parametru.<br /><br /> Wstawia plik .ico w zestawie, który nadaje plikowi wyjściowemu pożądany wygląd w Eksploratorze plików. Aby uzyskać więcej informacji, zobacz [/win32icon (opcje kompilatora C#)](http://msdn.microsoft.com/library/756d9b6d-ab07-41b7-ba58-5bd88f711138).|  
|`Win32Manifest`|Opcjonalnie `String` parametru.<br /><br /> Określa manifest Win32 do uwzględnienia.|  
|`Win32Resource`|Opcjonalnie `String` parametru.<br /><br /> Wstawia plik zasobów (.res) Win32 w pliku wyjściowym. Aby uzyskać więcej informacji, zobacz [/win32res (opcje kompilatora C#)](http://msdn.microsoft.com/library/3c33f750-6948-4c7e-a27e-bef98f77255b).|  
  
## <a name="remarks"></a>Uwagi  
 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z `Microsoft.Build.Tasks.ManagedCompiler` klasy, która dziedziczy po elemencie <xref:Microsoft.Build.Tasks.ToolTaskExtension> klasa, która sama dziedziczy <xref:Microsoft.Build.Utilities.ToolTask> klasy. Aby uzyskać listę tych dodatkowych parametrów i ich opisów, zobacz [tooltaskextension — klasa bazowa](../msbuild/tooltaskextension-base-class.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Csc` zadanie, aby skompilować plik wykonywalny przy użyciu plików źródłowych w `Compile` elementu kolekcji.  
  
```  
<CSC  
    Sources="@(Compile)"  
    OutputAssembly="$(AppName).exe"  
    EmitDebugInformation="true" />  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)   
 [Zadania](../msbuild/msbuild-tasks.md)
