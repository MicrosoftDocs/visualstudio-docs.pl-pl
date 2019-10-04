---
title: Właściwości konsolidatora Clang ( C++Android) | Microsoft Docs
ms.custom: ''
ms.date: 10/23/2017
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 66e88848-116c-4eb0-bc57-183394d35b57
author: corob-msft
ms.author: corob
manager: jillfra
f1_keywords:
- VC.Project.VCLinkerTool.OutputFile
- VC.Project.VCLinkerTool.ShowProgress
- VC.Project.VCLinkerTool.Version
- VC.Project.VCLinkerTool.VerboseOutput
- VC.Project.VCLinkerTool.IncrementalLink
- VC.Project.VCLinkerTool.SharedLibrarySearchPath
- VC.Project.VCLinkerTool.AdditionalLibraryDirectories
- VC.Project.VCLinkerTool.UnresolvedReferences
- VC.Project.VCLinkerTool.OptimizeForMemory
- VC.Project.VCLinkerTool.IgnoreDefaultLibraryNames
- VC.Project.VCLinkerTool.ForceSymbolReferences
- VC.Project.VCLinkerTool.ForceFileOutput
- VC.Project.VCLinkerTool.OmitDebuggerSymbolInformation
- VC.Project.VCLinkerTool.GenerateMapFile
- VC.Project.VCLinkerTool.Relocation
- VC.Project.VCLinkerTool.FunctionBinding
- VC.Project.VCLinkerTool.NoExecStackRequired
- VC.Project.WholeArchive
- VC.Project.AdditionalOptionsPage
- VC.Project.VCLinkerTool.AdditionalDependencies
- VC.Project.VCLinkerTool.LibraryDependencies
ms.workload:
- xplat-cplusplus
ms.openlocfilehash: e8f138b6c496f9dec32ad44dbdfa2064dd639990
ms.sourcegitcommit: 6ae0a289f1654dec63b412bfa22035511a2ef5ad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2019
ms.locfileid: "71950684"
---
# <a name="clang-linker-properties-android-c"></a>Właściwości konsolidatora Clang ( C++Android)

Właściwość | Opis | Decyzji
--- | ---| ---
Plik wyjściowy | Opcja zastępuje domyślną nazwę i lokalizację programu tworzonego przez konsolidatora. (-o)
Pokaż postęp | Drukuje wiadomości dotyczące postępu konsolidatora.
Version | Opcja-Version nakazuje konsolidatorowi umieszczenie numeru wersji w nagłówku pliku wykonywalnego.
Włącz pełne dane wyjściowe | Opcja-verbose nakazuje konsolidatorowi wyprowadzanie pełnych komunikatów na potrzeby debugowania.
Włącz konsolidację przyrostową | Opcja nakazuje konsolidatorowi włączenie konsolidacji przyrostowej.
Ścieżka wyszukiwania biblioteki udostępnionej | Zezwala użytkownikowi na wypełnienie ścieżki wyszukiwania biblioteki udostępnionej.
Dodatkowe katalogi biblioteki | Zezwala użytkownikowi na przesłanianie ścieżki biblioteki środowiskowej. (-L folder).
Zgłoś nierozpoznane odwołania do symboli | Ta opcja po włączeniu spowoduje zgłoszenie nierozpoznanych odwołań do symboli.
Optymalizuj pod kątem użycia pamięci | Optymalizuj pod kątem użycia pamięci przez odczytanie tabel symboli stosownie do potrzeb.
Ignoruj określone biblioteki domyślne | Określa co najmniej jedną nazwę bibliotek domyślnych do zignorowania.
Wymuszaj odwołania do symboli | Wymuś wprowadzenie symbolu w pliku wyjściowym jako niezdefiniowanego symbolu.
Informacje o symbolach debugera | Informacje o symbolach debugera z pliku wyjściowego. | **Uwzględnij wszystko**<br>**Pomiń niepotrzebne symbole na potrzeby przetwarzania relokacji**<br>**Pomiń tylko informacje o symbolach debugera**<br>**Pomiń wszystkie informacje o symbolach**<br>
Informacje o symbolach debugera pakietów | Rozpakuj informacje o symbolach debugera przed opakowaniem.  Kopia oryginalnego pliku binarnego zostanie użyta do debugowania.
Nazwa pliku mapy | Opcja map nakazuje konsolidatorowi utworzenie pliku mapy o nazwie określonej przez użytkownika.
Oznacz zmienne jako tylko do odczytu po relokacji | Ta opcja oznacza zmienne jako tylko do odczytu po relokacji.
Włącz natychmiastowe powiązanie funkcji | Ta opcja oznacza obiekt do natychmiastowego powiązania funkcji.
Wymagaj stosu wykonywalnego | Ta opcja oznacza dane wyjściowe jako niewymagające stosu wykonywalnego.
Całe archiwum | Całe archiwum używa całego kodu ze źródeł i dodatkowych zależności.
Opcje dodatkowe | Opcje dodatkowe.
{1&gt;Dodatkowe zależności&lt;1} | Określa dodatkowe elementy do dodania do wiersza polecenia konsolidacji.
Zależności biblioteki | Ta opcja umożliwia określenie dodatkowych bibliotek, które mają zostać dodane do wiersza polecenia konsolidatora. Dodatkowe biblioteki zostaną dodane na końcu wiersza polecenia konsolidatora z *biblioteki lib* i kończyć z rozszerzeniem. *a* lub *.*  (-lFILE)
