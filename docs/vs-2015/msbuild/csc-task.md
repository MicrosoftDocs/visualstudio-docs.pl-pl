---
title: CSC — zadanie | Microsoft Docs
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
ms.openlocfilehash: e0dd27fe64982e77872e37ec01dbdb71a0a141ae
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65694098"
---
# <a name="csc-task"></a>Csc — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zawija CSC.exe i tworzy pliki wykonywalne (. exe), biblioteki dołączane dynamicznie (pliki. dll) lub moduły kodu (pliki. module). Aby uzyskać więcej informacji na temat CSC.exe, zobacz [Opcje kompilatora języka C#](https://msdn.microsoft.com/library/d3403556-1816-4546-a782-e8223a772e44).  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry `Csc` zadania.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`AdditionalLibPaths`|Opcjonalny `String[]` parametr.<br /><br /> Określa dodatkowe katalogi do wyszukiwania odwołań. Aby uzyskać więcej informacji, zobacz [/lib (opcje kompilatora C#)](https://msdn.microsoft.com/library/b0efcc88-e8aa-4df4-a00b-8bdef70b7673).|  
|`AddModules`|Opcjonalny `String` parametr.<br /><br /> Określa co najmniej jeden moduł, który ma być częścią zestawu. Aby uzyskać więcej informacji, zobacz [/addmodule (opcje kompilatora C#)](https://msdn.microsoft.com/library/ed604546-0dc2-4bd4-9a3e-610a8d973e58).|  
|`AllowUnsafeBlocks`|Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true` , kompiluje kod, który używa słowa kluczowego [UNSAFE](https://msdn.microsoft.com/library/7e818009-1c6e-4b9e-b769-3728a01586a0) . Aby uzyskać więcej informacji, zobacz [/unsafe (opcje kompilatora C#)](https://msdn.microsoft.com/library/fdb77ed9-da03-45bd-bb7f-250704da1bcc).|  
|`ApplicationConfiguration`|Opcjonalny `String` parametr.<br /><br /> Określa plik konfiguracyjny aplikacji zawierający ustawienia powiązania zestawu.|  
|`BaseAddress`|Opcjonalny `String` parametr.<br /><br /> Określa preferowany adres podstawowy, z którego ma zostać załadowana Biblioteka DLL. Domyślny adres podstawowy dla biblioteki DLL jest ustawiany przez [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] środowisko uruchomieniowe języka wspólnego. Aby uzyskać więcej informacji, zobacz [/BaseAddress (opcje kompilatora C#)](https://msdn.microsoft.com/library/ce13c965-dfe4-4433-94f5-63b476e3a608).|  
|`CheckForOverflowUnderflow`|Opcjonalny `Boolean` parametr.<br /><br /> Określa, czy arytmetyczne liczby całkowite, które przepływają granice typu danych, powodują wyjątek w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [/Checked (opcje kompilatora C#)](https://msdn.microsoft.com/library/fb7475d3-e6a6-4e6d-b86c-69e7a74c854b).|  
|`CodePage`|Opcjonalny `Int32` parametr.<br /><br /> Określa stronę kodową, która ma być używana dla wszystkich plików kodu źródłowego w kompilacji. Aby uzyskać więcej informacji, zobacz [/CodePage (opcje kompilatora C#)](https://msdn.microsoft.com/library/75942989-b69a-4308-90a0-840c73d2c478).|  
|`DebugType`|Opcjonalny `String` parametr.<br /><br /> Określa typ debugowania. `DebugType` może być `full` lub `pdbonly` . Wartość domyślna to `full` , co umożliwia dołączenie debugera do działającego programu. Określanie `pdbonly` umożliwia debugowanie kodu źródłowego, gdy program jest uruchamiany w debugerze, ale wyświetla tylko asembler, gdy uruchomiony program jest podłączony do debugera.<br /><br /> Ten parametr zastępuje `EmitDebugInformation` parametr.<br /><br /> Aby uzyskać więcej informacji, zobacz [/debug (opcje kompilatora C#)](https://msdn.microsoft.com/library/e2b48c07-01bc-45cc-a52c-92e9085eb969).|  
|`DefineConstants`|Opcjonalny `String` parametr.<br /><br /> Definiuje symbole preprocesora. Aby uzyskać więcej informacji, zobacz [/define (opcje kompilatora C#)](https://msdn.microsoft.com/library/f17d7b4d-82d0-4133-8563-68cced1cac6e).|  
|`DelaySign`|Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true` , określa, że chcesz użyć w pełni podpisanego zestawu. Jeśli `false` , określa, że chcesz umieścić klucz publiczny w zestawie.<br /><br /> Ten parametr nie ma żadnego efektu, chyba że jest używany z `KeyFile` `KeyContainer` parametrem or.<br /><br /> Aby uzyskać więcej informacji, zobacz [/delaysign (opcje kompilatora C#)](https://msdn.microsoft.com/library/bcb058eb-2933-4e7f-b356-5c941db4de75).|  
|`DisabledWarnings`|Opcjonalny `String` parametr.<br /><br /> Określa listę ostrzeżeń, które mają zostać wyłączone. Aby uzyskać więcej informacji, zobacz [/nowarn (opcje kompilatora C#)](https://msdn.microsoft.com/library/6dcbc5e8-ae67-4566-9df3-f63cfdd9c4e4).|  
|`DocumentationFile`|Opcjonalny `String` parametr.<br /><br /> Przetwarza komentarze dokumentacji do pliku XML. Aby uzyskać więcej informacji, zobacz [/doc (opcje kompilatora C#)](https://msdn.microsoft.com/library/849eea59-c936-4311-bad8-d07404480f2a).|  
|`EmitDebugInformation`|Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true` zadanie generuje informacje o debugowaniu i umieszcza je w pliku bazy danych programu (. pdb). Jeśli `false` zadanie nie emituje żadnych informacji debugowania. Wartość domyślna to `false`. Aby uzyskać więcej informacji, zobacz [/debug (opcje kompilatora C#)](https://msdn.microsoft.com/library/e2b48c07-01bc-45cc-a52c-92e9085eb969).|  
|`ErrorReport`|Opcjonalny `String` parametr.<br /><br /> Zapewnia wygodny sposób zgłaszania wewnętrznego błędu języka C# do firmy Microsoft. Ten parametr może mieć wartość `prompt` , `send` , lub `none` . Jeśli parametr jest ustawiony na `prompt` , zostanie wyświetlony monit, gdy wystąpi wewnętrzny błąd kompilatora. Monit umożliwia elektroniczne wysyłanie raportu o usterce do firmy Microsoft. Jeśli parametr jest ustawiony na `send` , raport o usterce jest wysyłany automatycznie. Jeśli parametr jest ustawiony na `none` , błąd jest raportowany tylko w danych wyjściowych kompilatora. Wartość domyślna to `none`. Aby uzyskać więcej informacji, zobacz [/errorreport (opcje kompilatora C#)](https://msdn.microsoft.com/library/bd0e7493-b79d-4369-9c3f-ba26ebdfbedf).|  
|`FileAlignment`|Opcjonalny `Int32` parametr.<br /><br /> Określa rozmiar sekcji w pliku wyjściowym. Aby uzyskać więcej informacji, zobacz [/filealign (opcje kompilatora C#)](https://msdn.microsoft.com/library/15cf1c98-3798-4ced-9f08-60619308a073).|  
|`GenerateFullPaths`|Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true` , określa ścieżkę bezwzględną do pliku w danych wyjściowych kompilatora. Jeśli `false` , określa nazwę pliku. Wartość domyślna to `false`. Aby uzyskać więcej informacji, zobacz [/fullpaths (opcje kompilatora C#)](https://msdn.microsoft.com/library/d2a5f857-cbb2-430b-879c-d648aaf0b8c4).|  
|`KeyContainer`|Opcjonalny `String` parametr.<br /><br /> Określa nazwę kontenera klucza kryptograficznego. Aby uzyskać więcej informacji, zobacz [/KEYCONTAINER (opcje kompilatora C#)](https://msdn.microsoft.com/library/b3982b6d-2382-4f7e-bebd-ce98eaa30763).|  
|`KeyFile`|Opcjonalny `String` parametr.<br /><br /> Określa nazwę pliku zawierającego klucz kryptograficzny. Aby uzyskać więcej informacji, zobacz [/keyfile (opcje kompilatora C#)](https://msdn.microsoft.com/library/0815f9de-ace4-4e98-b4c6-13c55dea40c2).|  
|`LangVersion`|Opcjonalny `String` parametr.<br /><br /> Określa wersję języka do użycia. Aby uzyskać więcej informacji, zobacz [/langversion (opcje kompilatora C#)](https://msdn.microsoft.com/library/3fb00b05-a0ff-4782-b313-13a4c0f62d94).|  
|`LinkResources`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Tworzy łącze do [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] zasobu w pliku wyjściowym; plik zasobu nie jest umieszczany w pliku wyjściowym.<br /><br /> Elementy przesłane do tego parametru mogą zawierać opcjonalne wpisy metadanych o nazwach `LogicalName` i `Access` . `LogicalName` odpowiada `identifier` parametrowi `/linkresource` przełącznika i `Access` odpowiada `accessibility-modifier` parametrowi. Aby uzyskać więcej informacji, zobacz [/linkresource (opcje kompilatora C#)](https://msdn.microsoft.com/library/440c26c2-77c1-4811-a0a3-57cce3f5fc96).|  
|`MainEntryPoint`|Opcjonalny `String` parametr.<br /><br /> Określa lokalizację `Main` metody. Aby uzyskać więcej informacji, zobacz [/Main (opcje kompilatora C#)](https://msdn.microsoft.com/library/975cf4d5-36ac-4530-826c-4aad0c7f2049).|  
|`ModuleAssemblyName`|Opcjonalny `String` parametr.<br /><br /> Określa nazwę zestawu, którego częścią ma być ten moduł.|  
|`NoConfig`|Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true` , instruuje kompilator, aby nie kompilować z plikiem CSC. rsp. Aby uzyskać więcej informacji, zobacz [/noconfig (opcje kompilatora C#)](https://msdn.microsoft.com/library/cd26967e-e494-4c8c-b5c9-af13b2f78b2e).|  
|`NoLogo`|Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true` , pomija wyświetlanie informacji transparentu kompilatora. Aby uzyskać więcej informacji, zobacz [/nologo (opcje kompilatora C#)](https://msdn.microsoft.com/library/426afb36-a8fb-469d-9c45-a35d9512557c).|  
|`NoStandardLib`|Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true` , program zapobiega importowaniu mscorlib.dll, który definiuje całą przestrzeń nazw System. Użyj tego parametru, jeśli chcesz zdefiniować lub utworzyć własną przestrzeń nazw systemu i obiekty. Aby uzyskać więcej informacji, zobacz [/nostdlib (opcje kompilatora C#)](https://msdn.microsoft.com/library/ec197989-fa49-4725-a455-e06b551eb65f).|  
|`NoWin32Manifest`|Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true` nie, nie dołączaj domyślnego manifestu Win32.|  
|`Optimize`|Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true` , włącza optymalizacje. Jeśli `false` , wyłącza optymalizacje. Aby uzyskać więcej informacji, zobacz [/Optimize (opcje kompilatora C#)](https://msdn.microsoft.com/library/6dd5b6f2-cd1d-4593-a9f4-1c2ed9404ca0).|  
|`OutputAssembly`|Opcjonalny `String` parametr wyjściowy.<br /><br /> Określa nazwę pliku wyjściowego. Aby uzyskać więcej informacji, zobacz [/out (opcje kompilatora C#)](https://msdn.microsoft.com/library/70d91d01-7bd2-4aea-ba8b-4e9807e9caa5).|  
|`PdbFile`|Opcjonalny `String` parametr.<br /><br /> Określa nazwę pliku informacji o debugowaniu. Nazwa domyślna to nazwa pliku wyjściowego z rozszerzeniem. pdb.|  
|`Platform`|Opcjonalny `String` parametr.<br /><br /> Określa platformę procesora, do której ma być przeznaczony plik wyjściowy. Ten parametr może mieć wartość `x86` , `x64` , lub `anycpu` . Wartość domyślna to `anycpu`. Aby uzyskać więcej informacji, zobacz [/platform (opcje kompilatora C#)](https://msdn.microsoft.com/library/c290ff5e-47f4-4a85-9bb3-9c2525b0be04).|  
|`References`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Powoduje, że zadanie importuje informacje o typie publicznym z określonych elementów do bieżącego projektu. Aby uzyskać więcej informacji, zobacz [/Reference (opcje kompilatora C#)](https://msdn.microsoft.com/library/8d13e5b0-abf6-4c46-bf71-2daf2cd0a6c4).<br /><br /> Możesz określić [!INCLUDE[csprcs](../includes/csprcs-md.md)] alias odwołania w [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] pliku, dodając metadane `Aliases` do oryginalnego elementu "odwołanie". Na przykład, aby ustawić alias "LS1" w następującym wierszu polecenia CSC:<br /><br /> `csc /r:LS1=MyCodeLibrary.dll /r:LS2=MyCodeLibrary2.dll *.cs`<br /><br /> Użyj:<br /><br /> `<Reference Include="MyCodeLibrary"> <Aliases>LS1</Aliases> </Reference>`|  
|`Resources`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Osadza [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] zasób w pliku wyjściowym.<br /><br /> Elementy przesłane do tego parametru mogą zawierać opcjonalne wpisy metadanych o nazwach `LogicalName` i `Access` . `LogicalName` odpowiada `identifier` parametrowi `/resource` przełącznika i `Access` odpowiada `accessibility-modifier` parametrowi. Aby uzyskać więcej informacji, zobacz [/Resource (opcje kompilatora C#)](https://msdn.microsoft.com/library/5212666e-98ab-47e4-a497-b5545ab15c7f).|  
|`ResponseFiles`|Opcjonalny `String` parametr.<br /><br /> Określa plik odpowiedzi zawierający polecenia dla tego zadania. Aby uzyskać więcej informacji, zobacz [@ (Określ plik odpowiedzi)](https://msdn.microsoft.com/library/dda4fa9f-a02c-400f-8b6a-d58834e13d7f).|  
|`Sources`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Określa co najmniej jeden [!INCLUDE[csprcs](../includes/csprcs-md.md)] plik źródłowy.|  
|`TargetType`|Opcjonalny `String` parametr.<br /><br /> Określa format pliku wyjściowego. Ten parametr może mieć wartość `library` , która tworzy bibliotekę kodu, `exe` która tworzy aplikację konsolową, `module` która tworzy moduł lub `winexe` tworzy program systemu Windows. Wartość domyślna to `library`. Aby uzyskać więcej informacji, zobacz [/Target (opcje kompilatora C#)](https://msdn.microsoft.com/library/a18bbd8e-bbf7-49e7-992c-717d0eb1f76f).|  
|`TreatWarningsAsErrors`|Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true` , traktuje wszystkie ostrzeżenia jako błędy. Aby uzyskać więcej informacji, zobacz [/warnaserror (opcje kompilatora C#)](https://msdn.microsoft.com/library/04680ec3-08d6-4e2e-a274-38310e10e33c).|  
|`UseHostCompilerIfAvailable`|Opcjonalny `Boolean` parametr.<br /><br /> Instruuje zadanie, aby używało obiektu kompilatora w procesie, jeśli jest dostępny. Używane tylko przez [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|  
|`Utf8Output`|Opcjonalny `Boolean` parametr.<br /><br /> Rejestruje dane wyjściowe kompilatora przy użyciu kodowania UTF-8. Aby uzyskać więcej informacji, zobacz [/utf8output (opcje kompilatora C#)](https://msdn.microsoft.com/library/27ff7381-c281-45d7-b2eb-1ad644b1354e).|  
|`WarningLevel`|Opcjonalny `Int32` parametr.<br /><br /> Określa poziom ostrzeżeń dla kompilatora, który ma być wyświetlany. Aby uzyskać więcej informacji, zobacz [/warn (opcje kompilatora C#)](https://msdn.microsoft.com/library/5f80ff59-4991-4382-9f9a-77da18446e71).|  
|`WarningsAsErrors`|Opcjonalny `String` parametr.<br /><br /> Określa listę ostrzeżeń, które mają być traktowane jako błędy. Aby uzyskać więcej informacji, zobacz [/warnaserror (opcje kompilatora C#)](https://msdn.microsoft.com/library/04680ec3-08d6-4e2e-a274-38310e10e33c).<br /><br /> Ten parametr zastępuje `TreatWarningsAsErrors` parametr.|  
|`WarningsNotAsErrors`|Opcjonalny `String` parametr.<br /><br /> Określa listę ostrzeżeń, które nie są traktowane jako błędy. Aby uzyskać więcej informacji, zobacz [/warnaserror (opcje kompilatora C#)](https://msdn.microsoft.com/library/04680ec3-08d6-4e2e-a274-38310e10e33c).<br /><br /> Ten parametr jest przydatny tylko wtedy, gdy `TreatWarningsAsErrors` parametr jest ustawiony na `true` .|  
|`Win32Icon`|Opcjonalny `String` parametr.<br /><br /> Wstawia plik ICO w zestawie, który zapewnia plikowi wyjściowemu żądany wygląd w Eksploratorze plików. Aby uzyskać więcej informacji, zobacz [/win32icon (opcje kompilatora C#)](https://msdn.microsoft.com/library/756d9b6d-ab07-41b7-ba58-5bd88f711138).|  
|`Win32Manifest`|Opcjonalny `String` parametr.<br /><br /> Określa manifest Win32, który ma zostać uwzględniony.|  
|`Win32Resource`|Opcjonalny `String` parametr.<br /><br /> Wstawia plik zasobów Win32 (. res) do pliku wyjściowego. Aby uzyskać więcej informacji, zobacz [/win32res (opcje kompilatora C#)](https://msdn.microsoft.com/library/3c33f750-6948-4c7e-a27e-bef98f77255b).|  
  
## <a name="remarks"></a>Uwagi  
 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z `Microsoft.Build.Tasks.ManagedCompiler` klasy, która dziedziczy z klasy <xref:Microsoft.Build.Tasks.ToolTaskExtension> , która sama dziedziczy z <xref:Microsoft.Build.Utilities.ToolTask> klasy. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [ToolTaskExtension Base Class](../msbuild/tooltaskextension-base-class.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa `Csc` zadania do kompilowania pliku wykonywalnego z plików źródłowych w `Compile` kolekcji elementów.  
  
```  
<CSC  
    Sources="@(Compile)"  
    OutputAssembly="$(AppName).exe"  
    EmitDebugInformation="true" />  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)   
 [Zadania](../msbuild/msbuild-tasks.md)
