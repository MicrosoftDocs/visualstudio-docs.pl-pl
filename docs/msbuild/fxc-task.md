---
title: Zadanie FXC | Dokumentacja firmy Microsoft
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.fxc
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (Visual C++), FXC task
- FXC task (MSBuild (Visual C++))
author: mikeblome
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: 65819f1625477effab024055828301b26ab5804a
ms.sourcegitcommit: d78821f8c353e0102b1554719f549f32dffac71b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/27/2019
ms.locfileid: "58515168"
---
# <a name="fxc-task"></a>Zadanie FXC

W procesie kompilacji, należy użyć kompilatorów programu do cieniowania HLSL.

## <a name="parameters"></a>Parametry

W poniższej tabeli opisano parametry **FXC** zadania.

|Parametr|Opis|
|---------------|-----------------|
|**AdditionalIncludeDirectories**|Opcjonalnie **string []** parametru.<br/><br/>Określa jeden lub więcej katalogów do dodania do ścieżki dołączenia; Oddziel przy użyciu średnikami, jeśli istnieje więcej niż jedna.<br/><br/>Użyj `/I[path]`.|
|**AdditionalOptions**|Opcjonalnie **ciąg** parametru.|
|**AllResourcesBound**|Opcjonalnie **bool** parametru.<br/><br/>Kompilator zakłada, że wszystkie zasoby, które mogą odwoływać się do modułu cieniującego są powiązane i są w dobrym stanie w czasie trwania operacji wykonywania programu do cieniowania. Dostępne dla modelu modułu cieniującego 5.1 i nowszych.<br/><br/>Użyj `/all_resources_bound`.|
|**AssemblerOutput**|Opcjonalnie **ciąg** parametru.<br/><br/>Określa zawartość pliku wyjściowego języka asemblera.<br/><br/>Użyj `/Fc, /Fx`.<br/><br/>**NoListing**<br/>**AssemblyCode**, użyj `Fc`.<br/>**AssemblyCodeAndHex**, użyj `Fx`.|
|**AssemblerOutputFile**|Opcjonalnie **ciąg** parametru.<br/><br/>Określa nazwę pliku, plik listingu z kodem asemblera.|
|**CompileD2DCustomEffect**|Opcjonalnie **bool** parametru.<br/><br/>Kompiluj niestandardowy efekt Direct2D i zawiera programów do cieniowania pikseli. Na użytek wierzchołek lub nie obliczenia niestandardowego efektu.|
|**ConsumeExportFile**|Opcjonalnie **ciąg** parametru.|
|**DisableOptimizations**|Opcjonalnie **bool** parametru.<br/><br/>Wyłącz optymalizacje.<br/><br/>`/Od` oznacza `/Gfp` jednak wynik może nie być taka sama jak `/Od /Gfp`.|
|**EnableDebuggingInformation**|Opcjonalnie **bool** parametru.<br/><br/>Włącz informacje debugowania.|
|**EnableUnboundedDescriptorTables**|Opcjonalnie **bool** parametru.<br/><br/>Informuje kompilator, że program cieniujący może zawierać deklarację tablicy zasobów z zakresem niepowiązanych. Dostępne dla modelu modułu cieniującego 5.1 i nowszych.<br/><br/>Użyj `/enable_unbounded_descriptor_tables`.|
|**EntryPointName**|Opcjonalnie **ciąg** parametru.<br/><br/>Określa nazwę punktu wejścia dla programu do cieniowania.<br/><br/>Użyj `/E[name]`.|
|**GenerateExportFile**|Opcjonalnie **ciąg** parametru.|
|**GenerateExportShaderProfile**|Opcjonalnie **ciąg** parametru.|
|**HeaderFileOutput**|Opcjonalnie **ciąg** parametru.<br/><br/>Określa nazwę pliku nagłówkowego, zawierającego kod obiektu.<br/><br/>Użyj `/Fh [name]`.|
|**ObjectFileOutput**|Opcjonalnie **ciąg** parametru.<br/><br/>Określa nazwę pliku obiektu.<br/><br/>Użyj `/Fo [name]`.|
|**PreprocessorDefinitions**|Opcjonalnie **string []** parametru.<br/><br/>Definiuje symbole przetwarzania wstępnego dla pliku źródłowego.|
|**SetRootSignature**|Opcjonalnie **ciąg** parametru.<br/><br/>Dołącz podpis głównego do kodu bajtowego programu cieniującego. Dostępne dla modelu modułu cieniującego 5.0 i nowszych.<br/><br/>Użyj `/setrootsignature`.|
|**ShaderModel**|Opcjonalnie **ciąg** parametru.<br/><br/>Określa model cieniowania. Niektóre typy cieniowania należy używać tylko z najnowszymi modelami cieniowania.<br/><br/>Użyj `/T [type]_[model]`.|
|**ShaderType**|Opcjonalnie **ciąg** parametru.<br/><br/>Określa typ programu do cieniowania.<br/><br/>Użyj `/T [type]_[model]`.<br/><br/>**Efekt**, użyj `fx`.<br/>**Wierzchołek**, użyj `vs`.<br/>**Piksel**, użyj `ps`.<br/>**Geometria**, użyj `gs`.<br/>**Kadłuba**, użyj `hs`.<br/>**Domeny**, użyj `ds`.<br/>**Obliczenia**, użyj `cs`.<br/>**Biblioteka**, użyj `lib`.<br/>**RootSignature**, Generuj obiekt sygnatury głównej.|
|**Element źródłowy**|Wymagane **ITaskItem** parametru.|
|**SuppressStartupBanner**|Opcjonalnie **bool** parametru.<br/><br/>Pomija wyświetlanie komunikat transparentu i informacje o uruchamiania.<br/><br/>Użyj `/nologo`.|
|**TrackerLogDirectory**|Opcjonalnie **ciąg** parametru.|
|**TreatWarningAsError**|Opcjonalnie **bool** parametru.<br/><br/>Traktuje wszystkie ostrzeżenia kompilatora jako błędy.<br/><br/>Dla nowego projektu może być najlepiej użyć `/WX` we wszystkich kompilacjach; rozwiązanie wszystkich ostrzeżeń zapewni najmniejszą liczbą wad możliwe kodu twardych do znalezienia.|
|**VariableName**|Opcjonalnie **ciąg** parametru.<br/><br/>Określa nazwę zmiennej w pliku nagłówkowym.<br/><br/>Użyj `/Vn [name]`.|

## <a name="see-also"></a>Zobacz także

[Odwołanie do zadania](../msbuild/msbuild-task-reference.md)