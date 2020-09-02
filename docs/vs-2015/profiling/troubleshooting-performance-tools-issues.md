---
title: Rozwiązywanie problemów z narzędziami do oceny wydajności | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: troubleshooting
ms.assetid: 0b61cdf7-75b7-4abd-aff2-7bd997717626
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 575f17c641eb057dc01fb3302098bd9f8b47f9c5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64815511"
---
# <a name="troubleshooting-performance-tools-issues"></a>Rozwiązywanie problemów dotyczących narzędzi do oceny wydajności
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podczas korzystania z narzędzia profilowania może wystąpić jeden z następujących problemów:  
  
- [narzędzia profilowania nie zbiera żadnych danych.](#NoDataCollected)  
  
- [Widoki wydajności i raporty wyświetlają liczby dla nazw funkcji](#NoSymbols)  
  
## <a name="no-data-is-collected-by-the-profiling-tools"></a><a name="NoDataCollected"></a> narzędzia profilowania nie zbiera żadnych danych.  
 Po przetworzeniu profilu aplikacji plik danych profilowania (. vsp) nie zostanie utworzony, a w oknie danych wyjściowych zostanie wyświetlone następujące ostrzeżenie lub w oknie polecenia:  
  
 PRF0025: nie zebrano żadnych danych.  
  
 Przyczyną tego problemu może być kilka problemów:  
  
- Proces, który został profilowany przy użyciu próbkowania lub metoda pamięci .NET, uruchamia proces podrzędny, który jest procesem, który wykonuje działanie aplikacji. Na przykład niektóre aplikacje odczytują wiersz polecenia, aby określić, czy zostały one uruchomione jako aplikacja systemu Windows, czy jako aplikacja wiersza polecenia. Jeśli zażądano aplikacji systemu Windows, oryginalny proces uruchamia nowy proces skonfigurowany jako aplikacja systemu Windows, a następnie kończy działanie oryginalnego procesu. Ponieważ narzędzia profilowania nie zbiera automatycznie danych dla procesów podrzędnych, nie są zbierane żadne dane.  
  
     Aby zebrać dane profilowania w tej sytuacji, Dołącz profiler do procesu podrzędnego zamiast uruchamiania aplikacji za pomocą profilera. Aby uzyskać więcej informacji, zobacz [jak: dołączanie i odłączanie narzędzi wydajności do uruchomionych procesów](../profiling/how-to-attach-and-detach-performance-tools-to-running-processes.md) i [dołączanie (VSPerfCmd)](../profiling/attach.md)  
  
## <a name="performance-views-and-reports-display-numbers-for-function-names"></a><a name="NoSymbols"></a> Widoki wydajności i raporty wyświetlają liczby dla nazw funkcji  
 Po przeprowadzeniu profilu aplikacji zobaczysz liczby zamiast nazw funkcji w raportach i widokach.  
  
 Ten problem jest spowodowany przez aparat analizy narzędzia profilowania nie może znaleźć plików. pdb, które zawierają informacje o symbolach, które mapują informacje o kodzie źródłowym, takie jak nazwy funkcji i numery wierszy do skompilowanego pliku. Domyślnie kompilator tworzy plik. pdb podczas kompilowania pliku aplikacji. Odwołanie do katalogu lokalnego pliku. pdb jest przechowywane w skompilowanej aplikacji. Aparat analizy przegląda przywoływany katalog dla pliku. pdb, a następnie w pliku, który aktualnie zawiera plik aplikacji. Jeśli plik. pdb nie zostanie znaleziony, aparat analizy używa przesunięć funkcji zamiast nazw funkcji.  
  
 Problem można rozwiązać na jeden z dwóch sposobów:  
  
- Znajdź pliki. pdb i umieść je w tym samym katalogu, w którym znajdują się pliki aplikacji.  
  
- Osadź informacje o symbolach w pliku danych profilowania (. vsp). Aby uzyskać więcej informacji, zobacz [Zapisywanie informacji o symbolach przy użyciu plików danych dotyczących wydajności](../profiling/saving-symbol-information-with-performance-data-files.md).  
  
> [!NOTE]
> Aparat analizy wymaga, aby plik. pdb jest w tej samej wersji co plik skompilowanej aplikacji. Plik. pdb z wcześniejszej lub nowszej kompilacji pliku aplikacji nie będzie działał.
