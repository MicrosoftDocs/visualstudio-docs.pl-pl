---
title: FXC — zadanie | Microsoft Docs
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
- MSBuild (C++), FXC task
- FXC task (MSBuild (C++))
author: corob-msft
ms.author: corob
ms.workload:
- multiple
ms.openlocfilehash: 67958a1a1ebb2ff382d0896e2fbaec6105c0c785
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "77279285"
---
# <a name="fxc-task"></a>FXC, zadanie

Użyj kompilatorów modułu cieniującego HLSL w procesie kompilacji.

## <a name="parameters"></a>Parametry

W poniższej tabeli opisano parametry zadania **fxc** .

|Parametr|Opis|
|---------------|-----------------|
|**AdditionalIncludeDirectories**|Opcjonalny parametr **String []** .<br/><br/>Określa co najmniej jeden katalog do dodania do ścieżki dołączania; Oddzielaj średnikami, jeśli więcej niż jeden.<br/><br/>Użyj polecenia `/I[path]`.|
|**AdditionalOptions**|Opcjonalny parametr **ciągu** .|
|**AllResourcesBound**|Opcjonalny parametr **bool** .<br/><br/>Kompilator zakłada, że wszystkie zasoby, które mogą odwoływać się do programu do cieniowania, są powiązane i są w dobrym stanie na czas trwania wykonywania programu do cieniowania. Dostępne dla modelu modułu cieniującego 5,1 lub nowszego.<br/><br/>Użyj polecenia `/all_resources_bound`.|
|**AssemblerOutput**|Opcjonalny parametr **ciągu** .<br/><br/>Określa zawartość pliku wyjściowego języka asemblera.<br/><br/>Użyj polecenia `/Fc, /Fx`.<br/><br/>**Nolisting**<br/>**AssemblyCode**, użyj `Fc` .<br/>**AssemblyCodeAndHex**, użyj `Fx` .|
|**AssemblerOutputFile**|Opcjonalny parametr **ciągu** .<br/><br/>Określa nazwę pliku dla pliku listy kodu zestawu.|
|**CompileD2DCustomEffect**|Opcjonalny parametr **bool** .<br/><br/>Kompiluj niestandardowy efekt Direct2D, który zawiera cieniowanie pikseli. Nie należy używać dla efektu niestandardowego wierzchołka ani obliczeń.|
|**ConsumeExportFile**|Opcjonalny parametr **ciągu** .|
|**DisableOptimizations**|Opcjonalny parametr **bool** .<br/><br/>Wyłącz optymalizacje.<br/><br/>`/Od` oznacza `/Gfp` , że dane wyjściowe nie mogą być identyczne z `/Od /Gfp` .|
|**EnableDebuggingInformation**|Opcjonalny parametr **bool** .<br/><br/>Włącz informacje debugowania.|
|**EnableUnboundedDescriptorTables**|Opcjonalny parametr **bool** .<br/><br/>Informowanie kompilatora, że program wykorzystujący cieniowanie może zawierać deklarację tablicy zasobów z nieograniczonym zakresem. Dostępne dla modelu modułu cieniującego 5,1 lub nowszego.<br/><br/>Użyj polecenia `/enable_unbounded_descriptor_tables`.|
|**EntryPointName**|Opcjonalny parametr **ciągu** .<br/><br/>Określa nazwę punktu wejścia dla programu do cieniowania.<br/><br/>Użyj polecenia `/E[name]`.|
|**GenerateExportFile**|Opcjonalny parametr **ciągu** .|
|**GenerateExportShaderProfile**|Opcjonalny parametr **ciągu** .|
|**HeaderFileOutput**|Opcjonalny parametr **ciągu** .<br/><br/>Określa nazwę pliku nagłówkowego zawierającego kod obiektu.<br/><br/>Użyj polecenia `/Fh [name]`.|
|**ObjectFileOutput**|Opcjonalny parametr **ciągu** .<br/><br/>Określa nazwę pliku obiektu.<br/><br/>Użyj polecenia `/Fo [name]`.|
|**PreprocessorDefinitions**|Opcjonalny parametr **String []** .<br/><br/>Definiuje symbole przetwarzania wstępnego dla pliku źródłowego.|
|**SetRootSignature**|Opcjonalny parametr **ciągu** .<br/><br/>Dołącz podpis główny do kodu bajtowego modułu cieniującego. Dostępne dla modelu modułu cieniującego 5,0 lub nowszego.<br/><br/>Użyj polecenia `/setrootsignature`.|
|**ShaderModel**|Opcjonalny parametr **ciągu** .<br/><br/>Określa model programu do cieniowania. Niektóre typy cieniowania mogą być używane tylko z najnowszymi modelami programu do cieniowania.<br/><br/>Użyj polecenia `/T [type]_[model]`.|
|**Program do cieniowania**|Opcjonalny parametr **ciągu** .<br/><br/>Określa typ cieniowania.<br/><br/>Użyj polecenia `/T [type]_[model]`.<br/><br/>**Efekt**, użyj `fx` .<br/>**Wierzchołek**, użyj `vs` .<br/>**Piksel**, użyj `ps` .<br/>**Geometria**, użyj `gs` .<br/>**Kadłub**, użyj `hs` .<br/>**Domena**, użyj `ds` .<br/>**Obliczenia**, użycie `cs` .<br/>**Biblioteka**, użyj `lib` .<br/>**RootSignature**, Generuj obiekt sygnatury głównej.|
|**Element źródłowy**|Wymagany parametr **ITaskItem** .|
|**SuppressStartupBanner**|Opcjonalny parametr **bool** .<br/><br/>Pomija wyświetlanie transparentu startowego i komunikatu informacyjnego.<br/><br/>Użyj polecenia `/nologo`.|
|**Katalog trackerlogdirectory**|Opcjonalny parametr **ciągu** .|
|**TreatWarningAsError**|Opcjonalny parametr **bool** .<br/><br/>Traktuje wszystkie ostrzeżenia kompilatora jako błędy.<br/><br/>W przypadku nowego projektu najlepiej jest używać go `/WX` we wszystkich kompilacjach; rozpoznanie wszystkich ostrzeżeń zapewni najmniejszą możliwą trudną do znalezienia wady kodu.|
|**nazwa_zmiennej**|Opcjonalny parametr **ciągu** .<br/><br/>Określa nazwę zmiennej w pliku nagłówkowym.<br/><br/>Użyj polecenia `/Vn [name]`.|

## <a name="see-also"></a>Zobacz też

[Dokumentacja zadań](../msbuild/msbuild-task-reference.md)