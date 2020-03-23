---
title: Zadanie FXC | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77279285"
---
# <a name="fxc-task"></a>Zadanie FXC

Użyj kompilatorów modułów cieniowania HLSL w procesie kompilacji.

## <a name="parameters"></a>Parametry

W poniższej tabeli opisano parametry zadania **FXC.**

|Parametr|Opis|
|---------------|-----------------|
|**DodatkoweInobserwająKatary**|Opcjonalny **parametr string[].**<br/><br/>Określa jeden lub więcej katalogów do dodania do ścieżki dołączania; od siebie średnikami, jeśli więcej niż jeden.<br/><br/>Użyj witryny `/I[path]`.|
|**Dodatkoweopcje**|Opcjonalny parametr **ciągu.**|
|**AllResourcesBound (Wszystkie źródła:**|Opcjonalny parametr **bool.**<br/><br/>Kompilator zakłada, że wszystkie zasoby, które moduł cieniujący może odwołać są powiązane i są w dobrym stanie na czas wykonywania modułu cieniującego. Dostępne dla shader model 5.1 i powyżej.<br/><br/>Użyj witryny `/all_resources_bound`.|
|**AkceserOutput**|Opcjonalny parametr **ciągu.**<br/><br/>Określa zawartość pliku wyjściowego języka zestawu.<br/><br/>Użyj witryny `/Fc, /Fx`.<br/><br/>**NoListing (NoListing)**<br/>**AssemblyCode**, `Fc`użyj .<br/>**AssemblyCodeAndHex**, `Fx`użyj .|
|**Plik akceseraOutput**|Opcjonalny parametr **ciągu.**<br/><br/>Określa nazwę pliku z listą kodu zestawu.|
|**KompilacjaD2DCustomEffect**|Opcjonalny parametr **bool.**<br/><br/>Skompiluj niestandardowy efekt Direct2D zawierający moduły cieniowania pikseli. Nie należy używać dla wierzchołka lub obliczenia efektu niestandardowego.|
|**ConsumeExportFile (Plik eksplikatry**|Opcjonalny parametr **ciągu.**|
|**Wyłączenie aptyzowania**|Opcjonalny parametr **bool.**<br/><br/>Wyłącz optymalizacje.<br/><br/>`/Od`sugeruje, `/Gfp` że wyjście może `/Od /Gfp`nie być identyczne z .|
|**Włączinformację budowania**|Opcjonalny parametr **bool.**<br/><br/>Włącz informacje debugowania.|
|**Włącz NiezwolnioneTables deskryptora**|Opcjonalny parametr **bool.**<br/><br/>Poinformuj kompilator, że moduł cieniujący może zawierać deklarację tablicy zasobów z niezwiązanym zakresem. Dostępne dla shader model 5.1 i powyżej.<br/><br/>Użyj witryny `/enable_unbounded_descriptor_tables`.|
|**Nazwa punktu wejścia**|Opcjonalny parametr **ciągu.**<br/><br/>Określa nazwę punktu wejścia modułu cieniującego.<br/><br/>Użyj witryny `/E[name]`.|
|**Generowanie pliku przedprzemytem**|Opcjonalny parametr **ciągu.**|
|**Generowanieprofilu szyderów**|Opcjonalny parametr **ciągu.**|
|**HeaderFileOutput (Plik nagłówka)**|Opcjonalny parametr **ciągu.**<br/><br/>Określa nazwę pliku nagłówka zawierającego kod obiektu.<br/><br/>Użyj witryny `/Fh [name]`.|
|**ObjectFileOutput (Plik obiektu)**|Opcjonalny parametr **ciągu.**<br/><br/>Określa nazwę pliku obiektu.<br/><br/>Użyj witryny `/Fo [name]`.|
|**Definicje przedtwarze**|Opcjonalny **parametr string[].**<br/><br/>Definiuje symbole przetwarzania wstępnego dla pliku źródłowego.|
|**Podpis SetRoot**|Opcjonalny parametr **ciągu.**<br/><br/>Dołącz podpis główny do kodu bajtowego modułu cieniującego. Dostępne dla shader model 5.0 i powyżej.<br/><br/>Użyj witryny `/setrootsignature`.|
|**Moduł cieniujący**|Opcjonalny parametr **ciągu.**<br/><br/>Określa model modułu cieniującego. Niektórych typów modułów cieniującego można używać tylko z najnowszymi modelami modułów cieniującego.<br/><br/>Użyj witryny `/T [type]_[model]`.|
|**Typ modułu cieniującego**|Opcjonalny parametr **ciągu.**<br/><br/>Określa typ modułu cieniującego.<br/><br/>Użyj witryny `/T [type]_[model]`.<br/><br/>**Efekt**, `fx`użyj .<br/>**Wierzchołek**, użyj `vs`.<br/>**Piksel**, `ps`użyj .<br/>**Geometria**, `gs`użyj .<br/>**Kadłub**, `hs`użyj .<br/>**Domena** `ds`, użyj .<br/>**Oblicz ,** `cs`użyj .<br/>**Biblioteka** `lib`, użyj .<br/>**RootSignature**, wygeneruj główny obiekt podpisu.|
|**Źródła**|Wymagany parametr **ITaskItem.**|
|**SuppressStartupBanner (SuppressStartupBanner)**|Opcjonalny parametr **bool.**<br/><br/>Pomija wyświetlanie banera startowego i komunikatu informacyjnego.<br/><br/>Użyj witryny `/nologo`.|
|**TrackerLogDirectory (TrackerLogDirectory)**|Opcjonalny parametr **ciągu.**|
|**TreatWarningAsError**|Opcjonalny parametr **bool.**<br/><br/>Traktuje wszystkie ostrzeżenia kompilatora jako błędy.<br/><br/>W przypadku nowego projektu najlepiej jest `/WX` użyć we wszystkich kompilacjach; rozwiązanie wszystkich ostrzeżeń zapewni jak najmniej trudnych do znalezienia wad kodu.|
|**nazwa_zmiennej**|Opcjonalny parametr **ciągu.**<br/><br/>Określa nazwę nazwy zmiennej w pliku nagłówka.<br/><br/>Użyj witryny `/Vn [name]`.|

## <a name="see-also"></a>Zobacz też

[Odwołanie do zadania](../msbuild/msbuild-task-reference.md)