---
title: 'DA0038: Wysoki współczynnik rywalizacji o blokadę | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.38
- vs.performance.rules.DA0038
- vs.performance.DA0038
ms.assetid: ae0c8b2f-17b2-4f3d-a834-aa2f6371753b
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e2dad172ad21a57d406f0bb9ef9b42d0e27a13d6
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59667680"
---
# <a name="da0038-high-rate-of-lock-contentions"></a>DA0038: Wysoki współczynnik rywalizacji o blokadę
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby uzyskać najnowszą dokumentację programu Visual Studio, zobacz [DA0038: Wysoki współczynnik rywalizacji o blokadę](https://docs.microsoft.com/visualstudio/profiling/da0038-high-rate-of-lock-contentions).  
  
|||  
|-|-|  
|Identyfikator reguły|DA0038|  
|Kategoria|Sposób użycia programu .NET framework|  
|Metoda profilowania|Próbkowania<br /><br /> Oprzyrządowanie<br /><br /> Pamięć .NET|  
|Komunikat|Występuje wysoki współczynnik rywalizacji o blokadę platformy .NET. Zbadaj przyczynę tych rywalizacji, uruchamiając profil współbieżność.|  
|Typ reguły|Informacje|  
  
 Podczas profilowania za pomocą próbkowania pamięci platformy .NET i metod rywalizacji zasobów musi zebrać co najmniej 25 próbek do wyzwolenia tej reguły.  
  
## <a name="cause"></a>Przyczyna  
 Dane wydajności systemu, które są zbierane przy użyciu danych profilowania wskazuje znacznie wysoka liczba rywalizacji blokad, które wystąpiły podczas wykonywania aplikacji. Należy wziąć pod uwagę, profilowanie, aby znaleźć przyczynę rywalizacji ponownie, używając metoda profilowania współbieżności.  
  
## <a name="rule-description"></a>Opis reguły  
 Blokady są używane w celu ochrony krytycznych części kodu, który musi być wykonywane szeregowo jednego wątku w czasie w przypadku aplikacji wielowątkowych. Microsoft .NET wspólnego języka środowiska wykonawczego (języka wspólnego CLR) zapewnia pełny zestaw synchronizacji i blokowanie elementów podstawowych. Na przykład w języku C# obsługuje instrukcji "lock" (SyncLock w języku Visual Basic). Aplikacji zarządzanej może wywołać `Monitor.Enter` i `Monitor.Exit` metody system.Threading — przestrzeń nazw do nabywania i zwolnić blokady bezpośrednio. Program .NET Framework obsługuje dodatkowe synchronizacji i blokowania podstawowych, w tym klasy, które obsługują muteksy, ReaderWriterLocks i semafory. Aby uzyskać więcej informacji, zobacz [Przegląd podstawowych synchronizacji](http://go.microsoft.com/fwlink/?LinkId=177867) w przewodniku dewelopera .NET Framework w witrynie MSDN w sieci Web. Klas .NET Framework są nałożone na usługi synchronizacji niskiego poziomu, wbudowana w system operacyjny Windows. Obejmują one obiekty sekcję krytyczną wiele różnych oczekiwania i zdarzeń sygnalizowanie funkcji. Aby uzyskać więcej informacji, zobacz [synchronizacji](http://go.microsoft.com/fwlink/?LinkId=177869) sekcji Win32 i COM Programowanie w bibliotece MSDN  
  
 Podstawowe klasy .NET Framework i obiekty rodzime Windows, które są używane do synchronizacji i blokowania są lokalizacje pamięci współużytkowanej, które należy zmienić przy użyciu operacje blokowane. Zablokowana pula operacji zastosowania specyficzne dla sprzętu instrukcjami, które działają w lokalizacjach pamięci współużytkowanej na zmianę ich stanu przy użyciu niepodzielnych operacji. Niepodzielne operacje zapewniona jest spójny dla wszystkich procesorów w komputerze. Blokady i elementów WaitHandle są .NET obiektów, które automatycznie operacje blokowane podczas ustawiania lub resetowania. Mogą istnieć inne pamięci współużytkowanej struktury danych w aplikacji, która wymaga również użycia operacje blokowane w celu zaktualizowania w sposób bezpieczny dla wątków. Aby uzyskać więcej informacji, zobacz [operacji Blokowanej](http://go.microsoft.com/fwlink/?LinkId=177870) w .NET Framework w części biblioteki MSND  
  
 Synchronizacja i blokowanie to mechanizmy służące do zapewnienia poprawnie wykonywanie wielu wątków aplikacji. Każdy wątek aplikacji wielowątkowych to jednostki niezależne wykonywanie zaplanowanego niezależnie przez system operacyjny. Rywalizacja o blokady występuje, gdy wątek, który próbuje uzyskać blokadę jest opóźnione, ponieważ inny wątek jest z blokadą.  
  
 Często są zagnieżdżone blokad. Zagnieżdżanie występuje, gdy wątek wykonywania sekcję krytyczną wykonuje funkcję, która następnie wymaga innego blokady. Niektóre liczby zagnieżdżeń blokady jest nieuniknione. Twoja sekcja krytycznego może wywołać metody .NET Framework, która opiera się na blokady, aby upewnić się, że jest metodą o bezpiecznych wątkach. Wywołania niektórych sekcję krytyczną w aplikacji do metody Framework, który również blokuje przy użyciu dojścia blokady różne powoduje, że blokady zagnieździć. Zagnieżdżone warunki blokady może prowadzić do, które są bardzo trudne unravel i rozwiązywać problemy z wydajnością.  
  
 Ta reguła jest uruchamiana, gdy pomiarów dokonanych podczas uruchomienia profilowania wskazuje jest zbyt wysoki stopień Rywalizacja o blokady. Rywalizacji blokad opóźnienie wykonania wątków, które oczekują na blokadę. Należy zbadać nawet stosunkowo małe ilości Rywalizacja o blokady w testach jednostkowych lub w testach obciążenia uruchomione na dolnej sprzętowych zakończenia.  
  
> [!NOTE]
>  Po bardzo wysoka liczba rywalizacji blokad zgłoszone w danych profilowania [DA0039: Bardzo wysoki współczynnik rywalizacji o blokadę](../profiling/da0039-very-high-rate-of-lock-contentions.md) komunikat ostrzegawczy jest uruchamiany zamiast komunikat z informacjami.  
  
## <a name="how-to-investigate-a-warning"></a>Jak badać ostrzeżenie  
 Kliknij dwukrotnie komunikat, aby przejść do [znaczniki](../profiling/marks-view.md) widoku danych profilowania.  Znajdź **.NET CLR LocksAndThreads\Contention szybkość / sec** kolumny. Określa, czy określone faz wykonywania programu Rywalizacja o blokady w przypadku większych niż pozostałych faz.  
  
 Ta reguła jest uruchamiana tylko wtedy, gdy nie używasz metoda profilowania współbieżności. Metoda profilowania współbieżności to najlepsze narzędzie służące do diagnozowania problemów z wydajnością związanych z Rywalizacja o blokady w aplikacji. Zbieranie danych, aby zrozumieć zachowania blokującego aplikacji profilowania współbieżności. W tym opis blokad, które są silnie utrzymywał, ile czasu wykonywania wątków zostanie opóźnione, oczekiwania na blokady rywalizacją i jakie określonego kodu jest powiązana. Profile współbieżności zebranie danych dotyczących wszystkich rywalizacji blokad, w tym zachowania blokującego natywnych urządzeń Windows, klas .NET Framework i inne biblioteki innych firm odwołania do aplikacji. Aby uzyskać informacje dotyczące profilowania współbieżności z [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE, zobacz [danych współbieżności procesu i zbieranie wątku](../profiling/collecting-thread-and-process-concurrency-data.md). Aby uzyskać łącza do informacji o współbieżności profilowania z wiersza polecenia, zobacz **za pomocą metody współbieżności zbieranie rywalizacji o zasoby i dane o aktywności wątku** części [przy użyciu profilowania metody z Wiersz polecenia](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md).
