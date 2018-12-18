---
title: Sesja wydajności — omówienie | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Profiling Tools, performance session
- performance sessions
ms.assetid: 35752f95-a57a-4def-b64d-cf4899669e99
caps.latest.revision: 40
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b71f507e783552e066d41fe74e63fbc6b6146338
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51750044"
---
# <a name="performance-session-overview"></a>Sesja wydajności — Omówienie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym omówieniu przedstawiono podstawowe informacje profilowania. Zobaczą deweloperzy, którzy dopiero wydajności pracy sposób, w jaki [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Profiling Tools może pomóc im szybko stać się wydajność i zwiększyć wydajność swój kod. Deweloperzy, którzy doświadczenie w profilowania można zapoznać się z określonych funkcji narzędzi profilowania i procesów.  
  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Narzędzia profilowania pomagają zidentyfikować problemy z wydajnością w kodzie źródłowym i porównać wydajność możliwych rozwiązań. Profilowanie kreatorów narzędzia i ustawienia domyślne daje natychmiastowy wgląd w wiele problemów z wydajnością. Funkcje i opcje Profiling Tools zapewniają dokładną kontrolę nad procesem profilowania. Ten formant obejmuje dokładne wartości docelowej sekcji kodu, zbieranie informacji o czasie na poziomie bloku i włączenia dodatkowe dane dotyczące wydajności procesora i systemu w danych.  
  
 Poniższe kroki tworzą proces basic przy użyciu narzędzi profilowania:  
  
1. Konfigurowanie sesji wydajności, określając metod zbierania i dane, które mają być zbierane.  
  
2. Zbieranie danych profilowania, uruchamiając aplikację w sesji wydajności.  
  
3. Analizowanie danych, aby zidentyfikować problem z wydajnością.  
  
4. Modyfikowanie kodu w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zintegrowanego środowiska programistycznego (IDE) do zwiększa wydajność aplikacji, kodu  
  
5. Zbieranie danych profilowania na zmiany kodu i porównywanie danych profilowania, oryginalnym i zmienionych danych.  
  
6. Generowanie raportu, która dokumentuje wzrost wydajności.  
  
   Aby pracować z informacjami, które są dostarczane przez profilowanie, powinny mieć informacji o symbolach dostępna dla plików binarnych, które chcesz przeprowadzić profilowanie, jak i dla danych binarnych systemu operacyjnego Windows.  
  
## <a name="configure-the-performance-session"></a>Konfigurowanie sesji wydajności  
 Aby skonfigurować sesję profilowania, wybierz metody profilowania, którego chcesz używać i dane, które mają być zbierane. Narzędzia profilowania **kreatora wydajności** mogą ukierunkować za pomocą konfiguracji podstawowej oraz na stronach właściwości sesji wydajności można użyć, aby dodać więcej opcji:  
  
- Metody profilowania to próbkowania, śledzenie i alokacji pamięci.  
  
- Dane obejmują czas procesora i liczniki wydajności systemu operacyjnego i aplikacji zdarzenia, takie jak błędy stron i przejścia jądra.  
  
  Możesz skonfigurować sesję pomiaru wydajności w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projektu jako część rozwiązania projektu lub dowolne dane binarne, przy użyciu profilu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE. Można określić właściwości sesji na stronach właściwości sesji wydajności, lub można użyć Kreatora profilowania.  
  
## <a name="collect-profiling-data"></a>Zbieranie danych profilowania  
 Rozpocznij zbierania danych z profilowania **Eksplorator wydajności**. Można wstrzymać i wznowić profilowanie, aby ograniczyć ilość zbieranych danych. Można także dołączyć do procesu, który jest już uruchomiony.  
  
 Zaraz po uruchomieniu aplikacji program **kontroli zbierania danych** okno pojawia się w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE. Z **kontroli zbierania danych** oknie określonych części aplikacji można profilować, wstrzymywanie i wznawianie procesu zbierania. Można również użyć **kontroli zbierania danych** okna i wstaw znaczniki w dane, które są zbierane. Znaczniki są punkty danych zdefiniowanych przez użytkownika, które są wyświetlane w widokach profilu i który może służyć do filtrowania danych profilowania.  
  
 Podczas zamykania aplikacji docelowej, Profiling Tools generuje plik danych profilowania (*.vsp) i wyświetla widok raport z podsumowaniem w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE.  
  
## <a name="analyze-the-data-and-identify-performance-issues"></a>Analizowanie danych i zidentyfikować problemy z wydajnością  
 Po zakończeniu przebiegu profilowania te dane są analizowane i w narzędziach profilowania zostanie wyświetlone podsumowanie **raport dotyczący wydajności** wyświetlania systemu windows. Dane profilowania są zbierane dla stosu wywołań i poszczególnych funkcji w aplikacji docelowej. Raport widoków wyświetlanie analizy wydajności zakresy danych procesy, wątki, modułów, funkcji i wierszy kodu źródłowego aplikacji. Dane profilowania wartości dla funkcji są następujące:  
  
- Całkowity czas spędzony w funkcji i funkcji podrzędnych, które zostały wywołane przez funkcję (wartości włącznie).  
  
- Czas, jaki był poświęcony na wykonywanie tylko kod w funkcji (wyłączne wartości).  
  
  Ponad 12 różne widoki umożliwiają analizowanie danych profilowania w najbardziej efektywny sposób. Dostosowania widoków umożliwiają filtrowanie i sortowanie danych znajdują się funkcje, które mogą być przyczyną problemów z wydajnością. Filtrowanie gorącej ścieżki zawiera wyróżnienie najbardziej aktywnych ścieżek w widokach drzewo wywołań i moduł.  
  
## <a name="modify-the-application-code"></a>Modyfikowanie kodu aplikacji  
 Po izolowanych jeden lub więcej problemów z wydajnością istotne, można zmodyfikować kod za pomocą [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE, a następnie zbieranie danych profilowania dla zmiany.  
  
## <a name="collect-profiling-data-again-and-compare-the-data-between-the-profiling-runs"></a>Zbieranie danych profilowania ponownie i porównywanie danych między tras profilowania  
 Porównanie narzędzi profilowania widoku raportu jest wyświetlana różnica w module, funkcji lub wiersza wydajności między dwoma wybranych plików danych profilowania. Można określić profilowania wartości danych, które mają być porównane, można przełączać się między widoku porównania i widoki pojedynczych plików.  
  
## <a name="generate-a-report-of-the-results"></a>Generowanie raportu z wynikami  
 Wiersze dowolny widok raportu wydajności można wkleić do wiadomości e-mail i arkuszy kalkulacyjnych i można generować raporty, które zawierają dane dla jednego lub wielu widoków.  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie](../profiling/overviews-performance-tools.md)   
 [Przewodnik: identyfikowanie problemów z wydajnością](../profiling/walkthrough-identifying-performance-problems.md)



