---
title: Omówienie sesji wydajności | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778469"
---
# <a name="performance-session-overview"></a>Sesja wydajności — omówienie
W tym przeglądzie wyjaśniono podstawy profilowania. Deweloperzy, którzy są nowicjuszami [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] w pracy wydajności zobaczą, jak narzędzia profilowania mogą pomóc im szybko stać się produktywne i zwiększyć wydajność ich kodu. Deweloperzy, którzy mają doświadczenie w profilowaniu, mogą uzyskać przegląd określonych funkcji i procesów narzędzi profilowania.

 Narzędzia [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] profilowania ułatwiają identyfikowanie problemów z wydajnością w kodzie źródłowym i porównywanie wydajności możliwych rozwiązań. Kreatory narzędzi profilowania i ustawienia domyślne mogą dać natychmiastowy wgląd w wiele problemów z wydajnością. Funkcje i opcje narzędzi profilowania zapewniają dokładną kontrolę nad procesem profilowania. Ta kontrola obejmuje dokładne określanie wartości docelowej sekcji kodu, zbieranie informacji o chronometrażu na poziomie bloku oraz dołączanie dodatkowych danych o wydajności procesora i systemu do danych.

 Następujące kroki składają się na podstawowy proces korzystania z narzędzi profilowania:

1. Skonfiguruj sesję wydajności, określając metodę zbierania i dane, które chcesz zebrać.

2. Zbieranie danych profilowania przez uruchomienie aplikacji w sesji wydajności.

3. Analizowanie danych w celu zidentyfikowania problemu z wydajnością.

4. Modyfikowanie kodu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] w zintegrowanym środowisku programistycznym (IDE) w celu zwiększenia wydajności aplikacji kodu

5. Zbieranie danych profilowania na zmienionym kodzie i porównywanie danych profilowania oryginalnych i zmienionych danych.

6. Generowanie raportu, który dokumentuje wzrost wydajności.

   Aby pracować z informacjami dostarczonymi przez profilowanie, należy mieć informacje o symbolach dostępne dla plików binarnych, które mają być profilować, oraz dla plików binarnych systemu operacyjnego Windows.

## <a name="configure-the-performance-session"></a>Konfigurowanie sesji wydajności
 Aby skonfigurować sesję profilowania, wybierz metodę profilowania, której chcesz użyć, oraz dane, które chcesz zebrać. **Kreator wydajności** narzędzi profilowania może prowadzić użytkownika przez podstawową konfigurację, a strony właściwości Sesja wydajności umożliwiają dodanie dodatkowych opcji za pomocą stron właściwości Sesja wydajności:

- Metody profilowania obejmują próbkowanie, śledzenie i alokację pamięci.

- Wartości danych obejmują liczniki wydajności czasu, procesora i systemu operacyjnego oraz zdarzenia aplikacji, takie jak błędy stron i przejścia jądra.

  Można skonfigurować sesję wydajności [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] w projekcie jako część rozwiązania projektu lub profilu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dowolnych plików binarnych za pośrednictwem IDE. Można określić właściwości sesji na stronach właściwości Sesja wydajności lub użyć Kreatora profilowania.

## <a name="collect-profiling-data"></a>Zbieranie danych profilowania
 Należy rozpocząć zbieranie danych profilowania z **Eksploratora wydajności**. Można wstrzymać i wznowić profilowanie, aby ograniczyć ilość zbieranych danych. Można również dołączyć do procesu, który jest już uruchomiony.

 Jak tylko aplikacja zostanie uruchomiony, w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ide pojawi się okno Kontrola **zbierania danych.** W oknie **Kontrola zbierania danych** można profilować określone części aplikacji, wstrzymując i wznawiając proces zbierania. Można również użyć okna **Kontrola zbierania danych,** aby wstawić znaczniki do gromadzonych danych. Znaczniki są zdefiniowanymi przez użytkownika punktami danych, które są wyświetlane w widokach profilu i które mogą służyć do filtrowania danych profilowania.

 Po zamknięciu aplikacji docelowej narzędzia profilowania generuje plik danych profilowania (*.vsp) i [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wyświetla widok raportu podsumowania w IDE.

## <a name="analyze-the-data-and-identify-performance-issues"></a>Analizowanie danych i identyfikowanie problemów z wydajnością
 Po zakończeniu przebiegu profilowania dane są analizowane, a podsumowanie jest wyświetlane w oknach widoku **raport wydajności** narzędzi profilowania. Dane profilowania są zbierane dla stosu wywołań i poszczególnych funkcji aplikacji docelowej. Widoki raportu wyświetlają analizę wydajności dla zakresów danych procesów, wątków, modułów, funkcji i wierszy kodu źródłowego aplikacji. Wartości danych profilowania dla funkcji są następujące:

- Całkowity czas spędzony w funkcji i w funkcjach podrzędnych, które były wywoływane przez funkcję (wartości włącznie).

- Czas spędzony na wykonywaniu tylko kodu w funkcji (wartości wyłączne).

  Ponad dwanaście różnych widoków umożliwia analizowanie danych profilowania w najbardziej efektywny sposób. Wyświetl dostosowania umożliwiają filtrowanie i sortowanie danych w celu znalezienia funkcji, które mogą powodować problemy z wydajnością. Filtrowanie ścieżki aktywnej zapewnia natychmiastowe wyróżnianie najbardziej aktywnych ścieżek w widokach drzewa wywołań i modułu.

## <a name="modify-the-application-code"></a>Modyfikowanie kodu aplikacji
 Po odizolowaniu jednego lub więcej istotnych problemów z [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wydajnością, można zmodyfikować kod przy użyciu IDE, a następnie zbierać dane profilowania dla zmian.

## <a name="collect-profiling-data-again-and-compare-the-data-between-the-profiling-runs"></a>Zbierz ponownie dane profilowania i porównaj dane między przebiegami profilowania
 W widoku raportu porównawczego narzędzi profilowania jest wyświetlana różnica w wydajności modułu, funkcji lub linii między dwoma wybranymi plikami danych profilowania. Można określić wartości danych profilowania, które mają zostać porównane, a także przełączać się między widokiem porównania a widokami poszczególnych plików.

## <a name="generate-a-report-of-the-results"></a>Generowanie raportu z wyników
 Wiersze dowolnego widoku raportu o skuteczności można wklejać do wiadomości e-mail i arkuszy kalkulacyjnych, a także generować raporty zawierające dane dla jednego lub kilku widoków.

## <a name="see-also"></a>Zobacz też
- [Omówienia](../profiling/overviews-performance-tools.md)
- [Przewodnik: identyfikowanie problemów z wydajnością](beginners-guide-to-cpu-sampling.md)
