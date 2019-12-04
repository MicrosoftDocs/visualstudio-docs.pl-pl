---
title: Przegląd sesji wydajności | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools, performance session
- performance sessions
ms.assetid: 35752f95-a57a-4def-b64d-cf4899669e99
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: e7b23a7cbefeace19a3deaa5c1bfc05580081d39
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74778469"
---
# <a name="performance-session-overview"></a>Sesja wydajności — omówienie
W tym omówieniu wyjaśniono podstawowe informacje dotyczące profilowania. Deweloperzy, którzy są nowością w pracy, zobaczą, jak narzędzia profilowania [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] mogą pomóc im szybko i zwiększyć wydajność kodu. Deweloperzy znający profilowanie mogą uzyskać przegląd określonych funkcji i procesów narzędzia profilowania.

 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] narzędzia profilowania ułatwia identyfikowanie problemów z wydajnością w kodzie źródłowym i porównanie wydajności możliwych rozwiązań. Kreatory narzędzia profilowania i ustawienia domyślne mogą dać natychmiastowy wgląd w wiele problemów z wydajnością. Funkcje i opcje narzędzia profilowania zapewniają dokładną kontrolę nad procesem profilowania. Ta kontrolka obejmuje precyzyjne kierowanie sekcji kodu, zbieranie informacji o chronometrażu na poziomie bloku oraz uwzględnianie dodatkowych danych dotyczących procesora i wydajności systemu w danych.

 Poniższe kroki składają się na podstawowy proces przy użyciu narzędzia profilowania:

1. Skonfiguruj sesję wydajności, określając metodę kolekcji i dane, które mają być zbierane.

2. Zbieranie danych profilowania przez uruchomienie aplikacji w sesji wydajności.

3. Analizuj dane, aby zidentyfikować problem z wydajnością.

4. Zmodyfikuj kod w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zintegrowanego środowiska programistycznego (IDE), aby zwiększyć wydajność aplikacji w kodzie

5. Zbierz dane profilowania dla zmienionego kodu i Porównaj dane profilowania oryginalnych i zmienionych danych.

6. Generowanie raportu, który dokumentuje wzrost wydajności.

   Aby można było korzystać z informacji dostarczanych przez profilowanie, należy uzyskać informacje o symbolach dla plików binarnych, które mają być profilowe, oraz dla plików binarnych systemu operacyjnego Windows.

## <a name="configure-the-performance-session"></a>Konfigurowanie sesji wydajności
 Aby skonfigurować sesję profilowania, wybierz metodę profilowania, która ma być używana, oraz dane, które mają być zbierane. **Kreator wydajności** narzędzia profilowania może przeprowadzić Cię przez konfigurację podstawową i można użyć stron właściwości sesji wydajności, aby dodać więcej opcji:

- Metody profilowania obejmują próbkowanie, śledzenie i alokację pamięci.

- Wartości danych obejmują licznik czasu, procesora i wydajności systemu operacyjnego oraz zdarzenia aplikacji, takie jak błędy stron i przejścia jądra.

  Sesję wydajności można skonfigurować w projekcie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] jako część rozwiązania projektu lub profilować dowolne pliki binarne za pomocą [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE. Właściwości sesji można określić na stronie właściwości sesji wydajności. można też użyć Kreatora profilowania.

## <a name="collect-profiling-data"></a>Zbieranie danych profilowania
 Możesz rozpocząć zbieranie danych profilowania z **Eksplorator wydajności**. Można wstrzymywać i wznawiać profilowanie, aby ograniczyć ilość zbieranych danych. Możesz również dołączyć do procesu, który jest już uruchomiony.

 Gdy tylko aplikacja zostanie uruchomiona, okno **Kontrola zbierania danych** zostanie wyświetlone w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE. Z okna **Kontrola zbierania danych** można profilować konkretne części aplikacji przez wstrzymywanie i wznawianie procesu kolekcjonowania. Możesz również użyć okna **Kontrola zbierania danych** , aby wstawić znaczniki do zbieranych danych. Znaczniki to zdefiniowane przez użytkownika punkty danych, które są wyświetlane w widokach profilów i mogą służyć do filtrowania danych profilowania.

 Gdy aplikacja docelowa zostanie ZAMKNIĘTA, narzędzia profilowania generuje plik danych profilowania (*. vsp) i wyświetla widok raportu podsumowania w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE.

## <a name="analyze-the-data-and-identify-performance-issues"></a>Analizowanie danych i identyfikowanie problemów z wydajnością
 Po zakończeniu przebiegu profilowania dane są analizowane, a podsumowanie jest wyświetlane w oknach widoku **raportu wydajności** narzędzia profilowania. Dane profilowania są zbierane dla stosu wywołań i poszczególnych funkcji aplikacji docelowej. Widoki raportów wyświetlają analizę wydajności dla zakresów danych procesów, wątków, modułów, funkcji i wierszy kodu źródłowego aplikacji. Profilowania wartości danych dla funkcji są następujące:

- Całkowity czas spędzony w funkcji i w funkcjach podrzędnych, które zostały wywołane przez funkcję (wartości włącznie).

- Czas spędzony na wykonywaniu tylko kodu w funkcji (wartości wyłączne).

  Ponad dwanaście różnych widoków umożliwia analizowanie danych profilowania w najbardziej efektywny sposób. Widok dostosowania umożliwia filtrowanie i sortowanie danych w celu znalezienia funkcji, które mogą powodować problemy z wydajnością. Filtrowanie ścieżek aktywnych umożliwia natychmiastowe wyróżnienie najbardziej aktywnych ścieżek w drzewie wywołań i w widokach modułów.

## <a name="modify-the-application-code"></a>Modyfikowanie kodu aplikacji
 Po odizolowaniu jednego lub kilku odpowiednich problemów z wydajnością można zmodyfikować kod przy użyciu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE, a następnie zebrać dane profilowania dla zmian.

## <a name="collect-profiling-data-again-and-compare-the-data-between-the-profiling-runs"></a>Zbierz ponownie dane profilowania i Porównaj dane między uruchomieniami profilowania
 Widok raportu porównania narzędzia profilowania przedstawia różnice w zakresie wydajności modułu, funkcji lub linii między dwoma wybranymi plikami danych profilowania. Możesz określić wartości danych profilowania, które chcesz porównać, i można przełączać się między widokiem porównania i widokami poszczególnych plików.

## <a name="generate-a-report-of-the-results"></a>Generowanie raportu dotyczącego wyników
 Możesz wkleić wiersze dowolnego widoku raportu wydajności do wiadomości e-mail i arkuszy kalkulacyjnych, a także generować raporty zawierające dane dla jednego lub wielu widoków.

## <a name="see-also"></a>Zobacz także
- [Omówienia](../profiling/overviews-performance-tools.md)
- [Przewodnik: identyfikowanie problemów z wydajnością](beginners-guide-to-cpu-sampling.md)
