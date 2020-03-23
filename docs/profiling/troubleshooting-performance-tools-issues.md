---
title: Rozwiązywanie problemów z narzędziami wydajności | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0b61cdf7-75b7-4abd-aff2-7bd997717626
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 514b910f2c19822dc821b8c9a52ae96b8aac80f0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778105"
---
# <a name="troubleshoot-performance-tools-issues"></a>Rozwiązywanie problemów z narzędziami wydajności
Podczas korzystania z narzędzi profilowania może wystąpić jeden z następujących problemów:

- [Żadne dane nie są zbierane przez narzędzia profilowania](#no-data-is-collected-by-the-profiling-tools)

- [Widoki wydajności i raporty wyświetlają numery nazw funkcji](#performance-views-and-reports-display-numbers-for-function-names)

## <a name="no-data-is-collected-by-the-profiling-tools"></a>Żadne dane nie są zbierane przez narzędzia profilowania
 Po profilu aplikacji, dane profilowania (.* vsp*) plik nie jest tworzony i otrzymasz następujące ostrzeżenie w oknie **wyjście** lub w oknie polecenia:

 PRF0025: Nie zebrano żadnych danych.

 Ten problem może być spowodowany przez kilka problemów:

- Proces, który został sprofilowany przy użyciu próbkowania lub .NET metoda pamięci uruchamia proces podrzędny, który staje się procesem, który wykonuje pracę aplikacji. Na przykład niektóre aplikacje odczytują wiersz polecenia, aby ustalić, czy zostały uruchomione jako aplikacja systemu Windows, czy jako aplikacja wiersza polecenia. Jeśli zażądano aplikacji systemu Windows, oryginalny proces uruchamia nowy proces skonfigurowany jako aplikacja systemu Windows, a następnie oryginalny proces kończy działanie. Ponieważ narzędzia profilowania nie zbierają automatycznie danych dla procesów podrzędnych, żadne dane nie są zbierane.

     Aby zebrać dane profilowania w tej sytuacji, dołącz profiler do procesu podrzędnego zamiast uruchamiania aplikacji z profilera. Aby uzyskać więcej informacji, zobacz [Jak: Dołączanie i odłączanie narzędzi wydajności do uruchamiania procesów](../profiling/how-to-attach-and-detach-performance-tools-to-running-processes.md) i [dołączania (VSPerfCmd)](../profiling/attach.md)

## <a name="performance-views-and-reports-display-numbers-for-function-names"></a>Widoki wydajności i raporty wyświetlają numery nazw funkcji
 Po profilu aplikacji, widzisz numery zamiast nazw funkcji w raportach i widokach.

 Ten problem jest spowodowany przez aparat analizy narzędzi profilowania nie może znaleźć . *pliki pdb,* które zawierają informacje o symbolu, które mapują informacje o kodzie źródłowym, takie nazwy funkcji i numery wierszy do skompilowanego pliku. Domyślnie kompilator tworzy plik . *pdb,* gdy plik aplikacji jest zbudowany. Odwołanie do katalogu lokalnego pliku . *plik pdb* jest przechowywany w skompilowanej aplikacji. Aparat analizy szuka w katalogu, do którego istnieje odwołanie dla . *pdb,* a następnie w pliku, który obecnie zawiera plik aplikacji. Jeśli plik . nie znaleziono pliku *pdb,* aparat analizy używa przesunięcia funkcji zamiast nazw funkcji.

 Problem można rozwiązać na jeden z dwóch sposobów:

- Znajdź plik . *plików pdb* i umieść je w tym samym katalogu co pliki aplikacji.

- Osadź informacje o symbolu w danych profilowania (.* vsp).* Aby uzyskać więcej informacji, zobacz [Zapisywanie informacji o symbolach z plikami danych wydajności](../profiling/saving-symbol-information-with-performance-data-files.md).

> [!NOTE]
> Aparat analizy wymaga, aby plik . plik *pdb* jest tą samą wersją co skompilowany plik aplikacji. A. plik *pdb* z wcześniejszej lub późniejszej kompilacji pliku aplikacji nie będzie działać.
