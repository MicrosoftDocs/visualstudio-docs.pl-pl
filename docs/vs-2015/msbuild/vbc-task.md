---
title: VBC — zadanie | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Vbc
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Vbc task [MSBuild]
- MSBuild, Vbc task
ms.assetid: 595278b1-2782-4577-b1ba-b4b5ab5625a3
caps.latest.revision: 22
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6edc8b246055dcd8efdb32f4118f81a535635d55
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65683829"
---
# <a name="vbc-task"></a>Vbc — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zawija vbc.exe, które tworzą pliki wykonywalne (. exe), biblioteki dołączane dynamicznie (dll) lub moduły kodu (. module). Aby uzyskać więcej informacji na vbc.exe, zobacz [Visual Basic kompilator wiersza polecenia](https://msdn.microsoft.com/library/6b57c444-50c7-4b88-8f59-ed65cff5e05c).  
  
## <a name="parameters"></a>Parametry  
 W poniższej tabeli opisano parametry `Vbc` zadania.  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`AdditionalLibPaths`|Opcjonalny `String[]` parametr.<br /><br /> Określa dodatkowe foldery, w których mają być wyszukiwane zestawy określone w atrybucie References.|  
|`AddModules`|Opcjonalny `String[]` parametr.<br /><br /> Powoduje, że kompilator udostępnił wszystkie informacje o typie z określonych plików dla aktualnie kompilowanego projektu. Ten parametr odnosi się do przełącznika [/addmodule](https://msdn.microsoft.com/library/fb4b89d4-4926-4f20-868d-427fa28497b2) kompilatora vbc.exe.|  
|`BaseAddress`|Opcjonalny `String` parametr.<br /><br /> Określa adres podstawowy biblioteki DLL. Ten parametr odnosi się do przełącznika [/BaseAddress](https://msdn.microsoft.com/library/c982bcf2-46e5-47a2-bc8f-a5cc32b7dc47) kompilatora vbc.exe.|  
|`CodePage`|Opcjonalny `Int32` parametr.<br /><br /> Określa stronę kodową, która ma być używana dla wszystkich plików kodu źródłowego w kompilacji. Ten parametr odnosi się do przełącznika [/CodePage](https://msdn.microsoft.com/library/be36ec33-6800-4505-838c-4124564f5cc9) kompilatora vbc.exe.|  
|`DebugType`|Opcjonalny `String[]` parametr.<br /><br /> Powoduje, że kompilator generuje informacje o debugowaniu. Ten parametr może mieć następujące wartości:<br /><br /> -   `full`<br />-   `pdbonly`<br /><br /> Wartość domyślna to `full` , co umożliwia dołączenie debugera do działającego programu. Wartość zezwala na `pdbonly` Debugowanie kodu źródłowego, gdy program jest uruchamiany w debugerze, ale wyświetla kod języka asemblera tylko wtedy, gdy uruchomiony program jest dołączony do debugera. Aby uzyskać więcej informacji, zobacz [/debug (Visual Basic)](https://msdn.microsoft.com/library/c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2).|  
|`DefineConstants`|Opcjonalny `String[]` parametr.<br /><br /> Definiuje warunkowe stałe kompilatora. Pary symbol/wartość są oddzielone średnikami i są określone za pomocą następującej składni:<br /><br /> *symbol1* `=` *wartość1* `;` *symbol2* `=` *wartość2*<br /><br /> Ten parametr odnosi się do przełącznika [/define](https://msdn.microsoft.com/library/f735c57d-1cf9-4f2f-a26f-0de630fd4077) kompilatora vbc.exe.|  
|`DelaySign`|Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true` , zadanie umieszcza klucz publiczny w zestawie. Jeśli `false` , zadanie w pełni podpisuje zestaw. Wartość domyślna to `false` . Ten parametr nie ma żadnego efektu, chyba że jest używany z `KeyFile` parametrem lub `KeyContainer` parametrem. Ten parametr odnosi się do przełącznika [/delaysign](https://msdn.microsoft.com/library/c76e61a4-1884-4252-9fb2-377f99caa690) kompilatora vbc.exe.|  
|`DisabledWarnings`|Opcjonalny `String` parametr.<br /><br /> Pomija określone ostrzeżenia. Wystarczy określić część liczbową identyfikatora ostrzeżenia. Wiele ostrzeżeń jest rozdzielonych średnikami. Ten parametr odnosi się do przełącznika [/nowarn](https://msdn.microsoft.com/library/7ebf2106-0652-4fdc-bf60-70fc86465d83) kompilatora vbc.exe.|  
|`DocumentationFile`|Opcjonalny `String` parametr.<br /><br /> Przetwarza komentarze dokumentacji do określonego pliku XML. Ten parametr zastępuje `GenerateDocumentation` atrybut. Aby uzyskać więcej informacji, zobacz [/doc](https://msdn.microsoft.com/library/5fc32ec9-a149-4648-994c-a8d0cccd0a65).|  
|`EmitDebugInformation`|Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true` zadanie generuje informacje o debugowaniu i umieszcza je w pliku. pdb. Aby uzyskać więcej informacji, zobacz [/debug (Visual Basic)](https://msdn.microsoft.com/library/c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2).|  
|`ErrorReport`|Opcjonalny `String` parametr.<br /><br /> Określa, w jaki sposób zadanie ma raportować wewnętrzne błędy kompilatora. Ten parametr może mieć następujące wartości:<br /><br /> -   `prompt`<br />-   `send`<br />-   `none`<br /><br /> Jeśli `prompt` jest określony i wystąpi wewnętrzny błąd kompilatora, użytkownik zostanie poproszony o wybranie opcji wheter w celu wysłania danych błędu do firmy Microsoft.<br /><br /> Jeśli `send` jest określona i wystąpi wewnętrzny błąd kompilatora, zadanie wysyła dane błędu do firmy Microsoft.<br /><br /> Wartość domyślna to `none` , która raportuje błędy tylko w danych wyjściowych.<br /><br /> Ten parametr odnosi się do przełącznika [/errorreport](https://msdn.microsoft.com/library/a7fe83a2-a6d8-460c-8dad-79a8f433f501) kompilatora vbc.exe.|  
|`FileAlignment`|Opcjonalny `Int32` parametr.<br /><br /> Określa w bajtach, gdzie należy wyrównać sekcje pliku wyjściowego. Ten parametr może mieć następujące wartości:<br /><br /> -   `512`<br />-   `1024`<br />-   `2048`<br />-   `4096`<br />-   `8192`<br /><br /> Ten parametr odnosi się do przełącznika [/filealign](https://msdn.microsoft.com/library/cc61ec3d-ad38-4b28-9659-099d73cad099) kompilatora vbc.exe.|  
|`GenerateDocumentation`|Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true` , program generuje informacje dokumentacji i umieszcza je w pliku XML z nazwą pliku wykonywalnego lub biblioteki tworzonego przez zadanie. Aby uzyskać więcej informacji, zobacz [/doc](https://msdn.microsoft.com/library/5fc32ec9-a149-4648-994c-a8d0cccd0a65).|  
|`Imports`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Importuje przestrzenie nazw z określonych kolekcji elementów. Ten parametr odnosi się do przełącznika [/Imports —](https://msdn.microsoft.com/library/9a93fb53-c080-497b-bf9b-441022dbbc39) kompilatora vbc.exe.|  
|`KeyContainer`|Opcjonalny `String` parametr.<br /><br /> Określa nazwę kontenera klucza kryptograficznego. Ten parametr corresonds do przełącznika [/keycontainer](https://msdn.microsoft.com/library/6a9bc861-1752-4db1-9f64-b5252f0482cc) kompilatora vbc.exe.|  
|`KeyFile`|Opcjonalny `String` parametr.<br /><br /> Określa nazwę pliku zawierającego klucz kryptograficzny. Aby uzyskać więcej informacji, zobacz [/KeyFile](https://msdn.microsoft.com/library/ffa82a4b-517a-4c6c-9889-5bae7b534bb8).|  
|`LangVersion`|Optional [ciąg] (<!-- TODO: review code entity reference <xref:assetId:///String?qualifyHint=False&amp;autoUpgrade=True>  -->konstruktora.<br /><br /> Określa wersję języka ("9" lub "10").|  
|`LinkResources`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Tworzy łącze do zasobu .NET Framework w pliku wyjściowym; plik zasobu nie jest umieszczany w pliku wyjściowym. Ten parametr odnosi się do przełącznika [/linkresource](https://msdn.microsoft.com/library/cf4dcad8-17b7-404c-9184-29358aa05b15) kompilatora vbc.exe.|  
|`MainEntryPoint`|Opcjonalny `String` parametr.<br /><br /> Określa klasę lub moduł, który zawiera `Sub Main` procedurę. Ten parametr corresonds do przełącznika [/Main](https://msdn.microsoft.com/library/83fc339d-6652-415d-b205-b5133319b5b0) kompilatora vbc.exe.|  
|`ModuleAssemblyName`|Opcjonalny `String` parametr.<br /><br /> Określa zestaw, który jest częścią tego modułu.|  
|`NoConfig`|Opcjonalny `Boolean` parametr.<br /><br /> Określa, że kompilator nie powinien używać pliku VBC. rsp. Ten parametr odnosi się do parametru [/noconfig](https://msdn.microsoft.com/library/a7405067-bd21-4171-adf4-a126fa3ad6c3) kompilatora vbc.exe.|  
|`NoLogo`|Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true` , pomija wyświetlanie informacji transparentu kompilatora. Ten parametr odnosi się do przełącznika [/nologo](https://msdn.microsoft.com/library/25ef54b6-d676-4639-a2d2-a747a158bc07) kompilatora vbc.exe.|  
|`NoStandardLib`|Opcjonalny `Boolean` parametr.<br /><br /> Powoduje, że kompilator nie odwołuje się do bibliotek standardowych. Ten parametr odnosi się do przełącznika [/nostdlib](https://msdn.microsoft.com/library/140381b8-dc96-4ad5-ae11-792c9ed0be4d) kompilatora vbc.exe.|  
|`NoVBRuntimeReference`|Opcjonalny `Boolean` parametr.<br /><br /> Tylko do użytku wewnętrznego. Jeśli ma wartość true, uniemożliwia automatyczne odwołanie do Microsoft.VisualBasic.dll..|  
|`NoWarnings`|Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true` , zadanie pomija wszystkie ostrzeżenia. Aby uzyskać więcej informacji, zobacz [/nowarn](https://msdn.microsoft.com/library/7ebf2106-0652-4fdc-bf60-70fc86465d83).|  
|`Optimize`|Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true` , włącza optymalizacje kompilatora. Ten parametr odnosi się do przełącznika [/Optimize](https://msdn.microsoft.com/library/fcba4a97-3622-4b87-a891-0f77deab4998) kompilatora vbc.exe.|  
|`OptionCompare`|Opcjonalny `String` parametr.<br /><br /> Określa sposób, w jaki są wykonywane porównania ciągów. Ten parametr może mieć następujące wartości:<br /><br /> -   `binary`<br />-   `text`<br /><br /> Wartość `binary` określa, że zadanie używa porównywania ciągów binarnych. Wartość `text` określa, że zadanie używa porównania ciągów tekstowych. Wartość domyślna tego parametru to `binary` . Ten parametr odnosi się do przełącznika [/optioncompare —](https://msdn.microsoft.com/library/7237b766-b44d-4cc5-9a3c-885348a7d9e4) kompilatora vbc.exe.|  
|`OptionExplicit`|Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true` wymagana jest jawna deklaracja zmiennych. Ten parametr odnosi się do przełącznika [/optionexplicit —](https://msdn.microsoft.com/library/5d296ab3-bafe-4c4d-9887-78f162ed86c7) kompilatora vbc.exe.|  
|`OptionInfer`|Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true` , zezwala na wnioskowanie o typie zmiennych.|  
|`OptionStrict`|Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true` , zadanie wymusza ścisłą semantykę typu w celu ograniczenia niejawnych konwersji typów. Ten parametr odnosi się do przełącznika [/optionstrict —](https://msdn.microsoft.com/library/c7b10086-0fa4-49db-b3c8-4ae0db5957da) kompilatora vbc.exe.|  
|`OptionStrictType`|Opcjonalny `String` parametr.<br /><br /> Określa, który semantyczny typ ma generować ostrzeżenie. Obecnie obsługiwana jest tylko wartość "Custom". Ten parametr odnosi się do przełącznika [/optionstrict —](https://msdn.microsoft.com/library/c7b10086-0fa4-49db-b3c8-4ae0db5957da) kompilatora vbc.exe.|  
|`OutputAssembly`|Opcjonalny `String` parametr wyjściowy.<br /><br /> Określa nazwę pliku wyjściowego. Ten parametr odnosi się do przełącznika [/out](https://msdn.microsoft.com/library/9f148c15-0909-4cb8-a2db-777f8a8b45ae) kompilatora vbc.exe.|  
|`Platform`|Opcjonalny `String` parametr.<br /><br /> Określa platformę procesora, do której ma być przeznaczony plik wyjściowy. Ten parametr może mieć wartość `x86` , `x64` , `Itanium` , lub `anycpu` . Wartość domyślna to `anycpu`. Ten parametr odnosi się do przełącznika [/platform](https://msdn.microsoft.com/library/f9bc61e6-e854-4ae1-87b9-d6244de23fd1) kompilatora vbc.exe.|  
|`References`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Powoduje, że zadanie importuje informacje o typie publicznym z określonych elementów do bieżącego projektu. Ten parametr odnosi się do przełącznika [/Reference](https://msdn.microsoft.com/library/66bdfced-bbf6-43d1-a554-bc0990315737) kompilatora vbc.exe.|  
|`RemoveIntegerChecks`|Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true` , wyłącza sprawdzanie błędów przepełnienia liczby całkowitej. Wartość domyślna to `false`. Ten parametr odnosi się do przełącznika [/removeintchecks —](https://msdn.microsoft.com/library/c1835bd5-1e38-4fba-bd2f-6984774765d4) kompilatora vbc.exe.|  
|`Resources`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Osadza zasób .NET Framework w pliku wyjściowym. Ten parametr odnosi się do przełącznika [/Resource](https://msdn.microsoft.com/library/eee2f227-91f2-4f2b-a9d6-1c51c5320858) kompilatora vbc.exe.|  
|`ResponseFiles`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Określa plik odpowiedzi zawierający polecenia dla tego zadania. Ten parametr odpowiada opcji [@ (Określ plik odpowiedzi)](https://msdn.microsoft.com/library/a6847eaa-e5f9-4303-9421-45b55484b9ca) kompilatora vbc.exe.|  
|`RootNamespace`|Opcjonalny `String` parametr.<br /><br /> Określa główną przestrzeń nazw dla wszystkich deklaracji typu. Ten parametr odnosi się do przełącznika [/RootNamespace —](https://msdn.microsoft.com/library/e9245edf-6bef-420d-a7c7-324117752783) kompilatora vbc.exe.|  
|`SdkPath`|Opcjonalny `String` parametr.<br /><br /> Określa lokalizację mscorlib.dll i microsoft.visualbasic.dll. Ten parametr odnosi się do przełącznika [/SdkPath](https://msdn.microsoft.com/library/fec8a3f1-b791-4a37-8af7-344859f8212d) kompilatora vbc.exe.|  
|`Sources`|Opcjonalny <xref:Microsoft.Build.Framework.ITaskItem> `[]` parametr.<br /><br /> Określa co najmniej jeden [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] plik źródłowy.|  
|`TargetCompactFramework`|Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true` , zadanie jest celem [!INCLUDE[Compact](../includes/compact-md.md)] . Ten przełącznik odpowiada przełącznikowi [/netcf —](https://msdn.microsoft.com/library/db7cfa59-c315-401c-a59b-0daf355343d6) kompilatora vbc.exe.|  
|`TargetType`|Opcjonalny `String` parametr.<br /><br /> Określa format pliku wyjściowego. Ten parametr może mieć wartość `library` , która tworzy bibliotekę kodu, `exe` która tworzy aplikację konsolową, `module` która tworzy moduł lub `winexe` tworzy program systemu Windows. Wartość domyślna to `library`. Ten parametr odnosi się do przełącznika [/Target](https://msdn.microsoft.com/library/e0954147-548b-461f-9c4b-a8f88845616c) kompilatora vbc.exe.|  
|`Timeout`|Opcjonalny `Int32` parametr.<br /><br /> Określa ilość czasu (w milisekundach), po upływie którego plik wykonywalny zadania zostanie zakończony. Wartość domyślna to `Int.MaxValue` , co oznacza, że nie ma limitu czasu.|  
|`ToolPath`|Opcjonalny `String` parametr.<br /><br /> Określa lokalizację, z której zadanie będzie ładować podstawowy plik wykonywalny (vbc.exe). Jeśli ten parametr nie jest określony, zadanie używa ścieżki instalacji zestawu SDK odpowiadającej wersji platformy, która jest uruchomiona [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] .|  
|`TreatWarningsAsErrors`|Opcjonalny `Boolean` parametr.<br /><br /> Jeśli `true` wszystkie ostrzeżenia są traktowane jako błędy. Aby uzyskać więcej informacji, zobacz [/warnaserror (Visual Basic)](https://msdn.microsoft.com/library/49819f1d-a1bd-4201-affe-5afe6d9712e1).|  
|`UseHostCompilerIfAvailable`|Opcjonalny `Boolean` parametr.<br /><br /> Instruuje zadanie, aby używało obiektu kompilatora w procesie, jeśli jest dostępny. Używane tylko przez [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|  
|`Utf8Output`|Opcjonalny `Boolean` parametr.<br /><br /> Rejestruje dane wyjściowe kompilatora przy użyciu kodowania UTF-8. Ten parametr odnosi się do przełącznika [/utf8output](https://msdn.microsoft.com/library/8ab36b1e-027a-49ac-85b4-f48997d9e4d6) kompilatora vbc.exe.|  
|`Verbosity`|Opcjonalny `String` parametr.<br /><br /> Określa poziom szczegółowości danych wyjściowych kompilatora. Poziom szczegółowości może być `Quiet` `Normal` (wartość domyślna), lub `Verbose` .|  
|`WarningsAsErrors`|Opcjonalny `String` parametr.<br /><br /> Określa listę ostrzeżeń, które mają być traktowane jako błędy. Aby uzyskać więcej informacji, zobacz [/warnaserror (Visual Basic)](https://msdn.microsoft.com/library/49819f1d-a1bd-4201-affe-5afe6d9712e1).<br /><br /> Ten parametr zastępuje `TreatWarningsAsErrors` parametr.|  
|`WarningsNotAsErrors`|Opcjonalny `String` parametr.<br /><br /> Określa listę ostrzeżeń, które nie są traktowane jako błędy. Aby uzyskać więcej informacji, zobacz [/warnaserror (Visual Basic)](https://msdn.microsoft.com/library/49819f1d-a1bd-4201-affe-5afe6d9712e1).<br /><br /> Ten parametr jest przydatny tylko wtedy, gdy `TreatWarningsAsErrors` parametr jest ustawiony na `true` .|  
|`Win32Icon`|Opcjonalny `String` parametr.<br /><br /> Wstawia plik ICO w zestawie, który zapewnia plikowi wyjściowemu żądany wygląd w Eksploratorze plików. Ten parametr odnosi się do przełącznika [/win32icon](https://msdn.microsoft.com/library/aecaab01-9353-46c5-941c-6edabd4eff92) kompilatora vbc.exe.|  
|`Win32Resources`|Opcjonalny `String` parametr.<br /><br /> Wstawia plik zasobów Win32 (. res) do pliku wyjściowego. Ten parametr odnosi się do przełącznika [/win32resource —](https://msdn.microsoft.com/library/e226946d-19ce-4cc9-91f5-aed24f77aa2b) kompilatora vbc.exe.|  
  
## <a name="remarks"></a>Uwagi  
 Oprócz parametrów wymienionych powyżej, to zadanie dziedziczy parametry z <xref:Microsoft.Build.Tasks.ToolTaskExtension> klasy, która sama dziedziczy z <xref:Microsoft.Build.Utilities.ToolTask> klasy. Aby zapoznać się z listą tych dodatkowych parametrów i ich opisów, zobacz [ToolTaskExtension Base Class](../msbuild/tooltaskextension-base-class.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kompiluje [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] projekt.  
  
```  
<VBC  
   Sources="@(sources)"  
   Resources="strings.resources"  
   Optimize="true"  
   OutputAssembly="out.exe"/>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator wiersza polecenia Visual Basic](https://msdn.microsoft.com/library/6b57c444-50c7-4b88-8f59-ed65cff5e05c)   
 [Widoku](../msbuild/msbuild-tasks.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
