---
title: Rozwiązywanie problemów z wydajnością problemy dotyczące narzędzi | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0b61cdf7-75b7-4abd-aff2-7bd997717626
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 93e9f75ad953ff9c6cd08e8eb78bcfbf01542223
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51787929"
---
# <a name="troubleshooting-performance-tools-issues"></a>Rozwiązywanie problemów z wydajnością problemy dotyczące narzędzi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Może wystąpić jeden z następujących problemów, korzystając z narzędzi profilowania:  
  
-   [Żadne dane nie są zbierane za pomocą narzędzi profilowania](#NoDataCollected)  
  
-   [Wydajność widoków i raportów wyświetlania liczb dla nazwy funkcji](#NoSymbols)  
  
##  <a name="NoDataCollected"></a> Żadne dane nie są zbierane za pomocą narzędzi profilowania  
 Po użytkownik profil aplikacji, nie utworzono pliku danych (Vsp) profilowania i w oknie danych wyjściowych lub w oknie wiersza polecenia, pojawia się następujące ostrzeżenie:  
  
 PRF0025: Zebrano żadnych danych.  
  
 Ten problem może być spowodowany kilka problemów:  
  
-   Proces, która była profilowana przy użyciu pobierania próbek lub .NET — metoda pamięci rozpoczyna się proces podrzędny, która staje się proces, który wykonuje pracę aplikacji. Na przykład niektóre aplikacje odczytać wiersza polecenia, aby ustalić, czy zostały uruchomione jako aplikacji Windows lub aplikacji wiersza polecenia. Jeśli zażądano aplikacji Windows, proces oryginalnego uruchamia nowy proces, skonfigurowany jako aplikacji Windows, a następnie kończy działanie pierwotny proces. Ponieważ Profiling Tools nie automatycznego zbierania danych dla procesów podrzędnych, są zbierane żadne dane.  
  
     Do zbierania danych profilowania w takiej sytuacji, należy dołączyć profiler do procesu podrzędnego, zamiast uruchamiania aplikacji przy użyciu profilera. Aby uzyskać więcej informacji, zobacz [porady: dołączanie i odłączanie narzędzi do oceny wydajności uruchomione procesy](../profiling/how-to-attach-and-detach-performance-tools-to-running-processes.md) i [Attach (VSPerfCmd)](../profiling/attach.md)  
  
##  <a name="NoSymbols"></a> Wydajność widoków i raportów wyświetlania liczb dla nazwy funkcji  
 Po użytkownik profil aplikacji, można wyświetlić numery zamiast nazwy funkcji w raportach i widokach.  
  
 Ten problem jest spowodowany przez aparat analizy Profiling Tools nie będzie w stanie znaleźć pliki .pdb, które zawierają informacje o symbolach, mapująca informacji dotyczących kodu źródłowego, takie nazwy i numery wierszy na skompilowanych plików. Domyślnie kompilator tworzy plik .pdb podczas kompilowania pliku aplikacji. Odwołanie do katalogu lokalnego pliku .pdb jest przechowywany w skompilowanej aplikacji. Aparat analizy wyszukuje w bieżącym katalogu odwołania dla pliku .pdb, a następnie w pliku zawierającego plik aplikacji. Jeśli nie ma pliku .pdb, aparat analizy używa przesunięcia funkcji zamiast nazwy funkcji.  
  
 W rozwiązaniu problemu w jeden z dwóch sposobów:  
  
-   Znajdź pliki .pdb i umieść je w tym samym katalogu co pliki aplikacji.  
  
-   Osadzanie informacji o symbolach w pliku danych (Vsp) profilowania. Aby uzyskać więcej informacji, zobacz [zapisywanie informacji o symbolach w plików danych dotyczących wydajności](../profiling/saving-symbol-information-with-performance-data-files.md).  
  
> [!NOTE]
>  Aparat analizy wymaga pliku .pdb zgodnej z wersją pliku skompilowanej aplikacji. Plik .pdb z wcześniejszych lub nowszej kompilacji pliku aplikacji nie będzie działać.



