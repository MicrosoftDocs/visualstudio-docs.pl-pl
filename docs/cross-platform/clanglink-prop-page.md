---
title: Clang właściwości konsolidatora (Android C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 10/23/2017
ms.technology: vs-ide-mobile
ms.topic: conceptual
ms.assetid: 66e88848-116c-4eb0-bc57-183394d35b57
author: corob
ms.author: mblome
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
ms.openlocfilehash: 16dcb7ff5925f341fc78b57f1d9a4f011a27d576
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62815780"
---
# <a name="clang-linker-properties-android-c"></a>Clang właściwości konsolidatora (Android C++)

Właściwość | Opis | Opcje
--- | ---| ---
Plik wyjściowy | Opcja przesłania domyślną nazwę i lokalizację programu tworzonego przez konsolidatora. (-o)
Pokaż postęp | Drukuje wiadomości dotyczące postępu konsolidatora.
Wersja | -Version — opcja nakazuje konsolidatorowi umieszczenie numeru wersji w nagłówku pliku wykonywalnego.
Włącz pełne dane wyjściowe | Verbose — opcja nakazuje konsolidatorowi wysyłanie pełnych komunikatów na potrzeby debugowania.
Włącz konsolidację przyrostową | Ta opcja nakazuje konsolidatorowi włączenie konsolidowania przyrostowego.
Ścieżka wyszukiwania biblioteki udostępnionej | Umożliwia użytkownikowi Wypełnianie ścieżki wyszukiwania biblioteki udostępnionej.
Dodatkowe katalogi biblioteki | Umożliwia użytkownikowi przesłanianie ścieżki środowiskowej biblioteki. (-L folder).
Raport nierozpoznanych odwołań do symboli | Włączenie tej opcji będzie zgłaszać nierozpoznanych odwołań do symboli.
Optymalizacja pod kątem użycia pamięci | Optymalizuj pod kątem użycia pamięci przez kątem tabel symboli, zgodnie z potrzebami.
Ignoruj określone biblioteki domyślne | Określa jedną lub więcej nazw bibliotek domyślnych do zignorowania.
Wymuszaj odwołania do symboli | Symbol wymuszania do można wpisać w pliku wyjściowym jako niezdefiniowanego symbolu.
Informacje o symbolach debugera | Informacje o symbolach w pliku danych wyjściowych debugera. | **Uwzględnij wszystkie**<br>**Pomiń niepotrzebne symbole na potrzeby przetwarzania relokacji**<br>**Pomiń informacje o symbolach debugera tylko**<br>**Pomiń wszystkie informacje o symbolach**<br>
Informacje o symbolach debugera pakietu | Usuń informacje o symbolach debugera przed pakowania.  Kopię oryginalny plik binarny będzie służyć do debugowania.
Nazwa pliku mapy | Opcja Map nakazuje konsolidatorowi utworzenie pliku mapy o nazwie określonej przez użytkownika.
Oznacz zmienne tylko do odczytu po relokacji | Ta opcja oznacza zmienne jako tylko do odczytu po relokacji.
Włącz natychmiastowe powiązanie funkcji | Ta opcja oznacza obiekt do natychmiastowego powiązania funkcji.
Wymagaj stosu wykonywalnego | Ta opcja oznacza dane wyjściowe jako niewymagające stosu wykonywalnego.
Całe archiwum | Całe archiwum używa całego kodu ze źródeł i zależności dodatkowych.
Dodatkowe opcje | Dodatkowe opcje.
{1&gt;Dodatkowe zależności&lt;1} | Określa dodatkowe elementy do dodania do wiersza polecenia konsolidacji.
Zależności biblioteki | Ta opcja umożliwia określenie dodatkowych bibliotek, które mają zostać dodane do wiersza polecenia konsolidatora. Dodatkowe biblioteki zostaną dodane w celu uruchomienia wiersza polecenia konsolidatora z *lib* i kończyć się znakiem *.a* lub *SO* rozszerzenia.  (-lFILE)
