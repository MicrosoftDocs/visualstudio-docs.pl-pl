---
title: Rozwiązywanie problemów z narzędziami do oceny wydajności | Microsoft Docs
description: Poznaj różne sposoby rozwiązywania problemów z narzędziami wydajności, na przykład wtedy, gdy żadne dane nie są zbierane przez narzędzia profilowania.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0b61cdf7-75b7-4abd-aff2-7bd997717626
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: d079c2fbd41f6a3eff881a544e8b88c50938e3bf
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2021
ms.locfileid: "98722415"
---
# <a name="troubleshoot-performance-tools-issues"></a>Rozwiązywanie problemów z narzędziami do oceny wydajności
Podczas korzystania z narzędzia profilowania może wystąpić jeden z następujących problemów:

- [Narzędzia profilowania nie zbierają danych](#no-data-is-collected-by-the-profiling-tools)

- [Widoki wydajności i raporty wyświetlają liczby dla nazw funkcji](#performance-views-and-reports-display-numbers-for-function-names)

## <a name="no-data-is-collected-by-the-profiling-tools"></a>Narzędzia profilowania nie zbierają danych
 Po przeprowadzeniu profilu aplikacji dane profilowania (.*VSP*) nie został utworzony, a w oknie **danych wyjściowych** zostanie wyświetlone następujące ostrzeżenie lub w oknie polecenia:

 PRF0025: nie zebrano żadnych danych.

 Przyczyną tego problemu może być kilka problemów:

- Proces, który został profilowany przy użyciu próbkowania lub metoda pamięci .NET, uruchamia proces podrzędny, który jest procesem, który wykonuje działanie aplikacji. Na przykład niektóre aplikacje odczytują wiersz polecenia, aby określić, czy zostały one uruchomione jako aplikacja systemu Windows, czy jako aplikacja wiersza polecenia. Jeśli zażądano aplikacji systemu Windows, oryginalny proces uruchamia nowy proces skonfigurowany jako aplikacja systemu Windows, a następnie kończy działanie oryginalnego procesu. Ponieważ narzędzia profilowania nie zbiera automatycznie danych dla procesów podrzędnych, nie są zbierane żadne dane.

     Aby zebrać dane profilowania w tej sytuacji, Dołącz profiler do procesu podrzędnego zamiast uruchamiania aplikacji za pomocą profilera. Aby uzyskać więcej informacji, zobacz [jak: dołączanie i odłączanie narzędzi wydajności do uruchomionych procesów](../profiling/how-to-attach-and-detach-performance-tools-to-running-processes.md) i [dołączanie (VSPerfCmd)](../profiling/attach.md)

## <a name="performance-views-and-reports-display-numbers-for-function-names"></a>Widoki wydajności i raporty wyświetlają liczby dla nazw funkcji
 Po przeprowadzeniu profilu aplikacji zobaczysz liczby zamiast nazw funkcji w raportach i widokach.

 Ten problem jest spowodowany przez aparat analizy narzędzia profilowania nie może odnaleźć. pliki *PDB* zawierające informacje o symbolach, które mapują informacje o kodzie źródłowym, takie jak nazwy funkcji i numery wierszy do skompilowanego pliku. Domyślnie kompilator tworzy. plik *PDB* podczas kompilowania pliku aplikacji. Odwołanie do katalogu lokalnego. plik *PDB* jest przechowywany w skompilowanej aplikacji. Aparat analizy przegląda katalog, do którego się odwołuje. plik *PDB* , a następnie w pliku, który aktualnie zawiera plik aplikacji. Jeśli. nie znaleziono pliku *PDB* , aparat analizy używa przesunięć funkcji zamiast nazw funkcji.

 Problem można rozwiązać na jeden z dwóch sposobów:

- Znajdź. pliki *PDB* i umieścić je w tym samym katalogu, w którym znajdują się pliki aplikacji.

- Osadź informacje o symbolach w danych profilowania (.*VSP*). Aby uzyskać więcej informacji, zobacz [Zapisywanie informacji o symbolach przy użyciu plików danych dotyczących wydajności](../profiling/saving-symbol-information-with-performance-data-files.md).

> [!NOTE]
> Aparat analizy wymaga, aby. plik *PDB* jest taka sama jak wersja skompilowanego pliku aplikacji. Z. plik *PDB* z wcześniejszej lub nowszej kompilacji pliku aplikacji nie będzie działał.
