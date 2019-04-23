---
title: Rozwiązywanie problemów z wydajnością problemy dotyczące narzędzi | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0b61cdf7-75b7-4abd-aff2-7bd997717626
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9d6487f4a6021f36cecd490504075cdba2ac2293
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60061388"
---
# <a name="troubleshoot-performance-tools-issues"></a>Narzędzia do rozwiązywania problemów z wydajnością
Może wystąpić jeden z następujących problemów, korzystając z narzędzi profilowania:

- [Żadne dane nie są zbierane za pomocą narzędzi profilowania](#no-data-is-collected-by-the-profiling-tools)

- [Raportach i widokach wydajności wyświetlane numery nazwy funkcji](#performance-views-and-reports-display-numbers-for-function-names)

## <a name="no-data-is-collected-by-the-profiling-tools"></a>Żadne dane nie są zbierane za pomocą narzędzi profilowania
 Po profil aplikacji, danych profilowania (. *Vsp*) plików nie jest tworzony i pojawia się następujące ostrzeżenie w **dane wyjściowe** oknie lub w oknie wiersza polecenia:

 PRF0025: Zebrano żadnych danych.

 Ten problem może być spowodowany kilka problemów:

- Proces, która była profilowana przy użyciu pobierania próbek lub .NET — metoda pamięci rozpoczyna się proces podrzędny, która staje się proces, który wykonuje pracę aplikacji. Na przykład niektóre aplikacje odczytać wiersza polecenia, aby ustalić, czy zostały uruchomione jako aplikacji Windows lub aplikacji wiersza polecenia. Jeśli zażądano aplikacji Windows, proces oryginalnego uruchamia nowy proces, skonfigurowany jako aplikacji Windows, a następnie kończy działanie pierwotny proces. Ponieważ Profiling Tools nie automatycznego zbierania danych dla procesów podrzędnych, są zbierane żadne dane.

     Do zbierania danych profilowania w takiej sytuacji, należy dołączyć profiler do procesu podrzędnego, zamiast uruchamiania aplikacji przy użyciu profilera. Aby uzyskać więcej informacji, zobacz [jak: Dołączanie i odłączanie narzędzi wydajności do uruchomionych procesów](../profiling/how-to-attach-and-detach-performance-tools-to-running-processes.md) i [Attach (VSPerfCmd)](../profiling/attach.md)

## <a name="performance-views-and-reports-display-numbers-for-function-names"></a>Raportach i widokach wydajności wyświetlane numery nazwy funkcji
 Po użytkownik profil aplikacji, można wyświetlić numery zamiast nazwy funkcji w raportach i widokach.

 Ten problem jest spowodowany przez aparat analizy Profiling Tools nie będzie w stanie znaleźć. *pdb* pliki, które zawierają informacje o symbolach, że mapy źródła informacji o kodzie, takie nazwy i numery wierszy przeznaczonych do skompilowanych plików. Domyślnie, kompilator utworzy. *pdb* plików podczas kompilowania pliku aplikacji. Odwołanie do katalogu lokalnego. *pdb* plik jest przechowywany w skompilowanej aplikacji. Aparat analizy wyszukuje w bieżącym katalogu dla odwołania. *pdb* pliku, a następnie w pliku, który obecnie zawiera pliku aplikacji. Jeśli. *pdb* plik nie zostanie znaleziony, aparat analizy używa przesunięcia funkcji zamiast nazwy funkcji.

 W rozwiązaniu problemu w jeden z dwóch sposobów:

- Znajdź. *pdb* pliki i umieścić je w tym samym katalogu co pliki aplikacji.

- Osadzanie informacji o symbolach w danych profilowania (. *Vsp*) pliku. Aby uzyskać więcej informacji, zobacz [zapisywanie informacji o symbolach wydajności pliki danych](../profiling/saving-symbol-information-with-performance-data-files.md).

> [!NOTE]
>  Aparat analizy wymaga. *pdb* plik jest w tej samej wersji co plik skompilowanej aplikacji. ELEMENT. *pdb* pliku z wcześniejszych lub nowszej kompilacji pliku aplikacji nie będą działać.