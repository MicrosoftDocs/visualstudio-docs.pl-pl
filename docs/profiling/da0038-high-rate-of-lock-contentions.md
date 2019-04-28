---
title: 'DA0038: Wysoki współczynnik rywalizacji o blokadę | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.38
- vs.performance.rules.DA0038
- vs.performance.DA0038
ms.assetid: ae0c8b2f-17b2-4f3d-a834-aa2f6371753b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ba95cde967f428717be852dad785233eb96cb290
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63444884"
---
# <a name="da0038-high-rate-of-lock-contentions"></a>DA0038: Wysoki współczynnik rywalizacji blokad

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
 Blokady są używane w celu ochrony krytycznych części kodu, który musi być wykonywane szeregowo jednego wątku w czasie w przypadku aplikacji wielowątkowych. Microsoft .NET wspólnego języka środowiska wykonawczego (języka wspólnego CLR) zapewnia pełny zestaw synchronizacji i blokowanie elementów podstawowych. Na przykład w języku C# obsługuje instrukcji "lock" (SyncLock w języku Visual Basic). Aplikacji zarządzanej można wywołać metody Monitor.Enter i Monitor.Exit w przestrzeni nazw System.Threading nabywania i zwolnić blokady bezpośrednio. Program .NET Framework obsługuje dodatkowe synchronizacji i blokowania podstawowych, w tym klasy, które obsługują muteksy, ReaderWriterLocks i semafory. Aby uzyskać więcej informacji, zobacz [Przegląd podstawowych synchronizacji](http://go.microsoft.com/fwlink/?LinkId=177867) w przewodniku dewelopera .NET Framework w witrynie MSDN w sieci Web. Klas .NET Framework są nałożone na usług o niższym poziomie synchronizacji wbudowana w system operacyjny Windows. Obejmują one obiekty sekcję krytyczną wiele różnych oczekiwania i zdarzeń sygnalizowanie funkcji. Aby uzyskać więcej informacji, zobacz [synchronizacji](http://go.microsoft.com/fwlink/?LinkId=177869) sekcji Win32 i COM Programowanie w bibliotece MSDN

 Podstawowe klasy .NET Framework i obiekty rodzime Windows, które są używane do synchronizacji i blokowania są lokalizacje pamięci współużytkowanej, które należy zmienić przy użyciu operacje blokowane. Zablokowana pula operacji zastosowania specyficzne dla sprzętu instrukcjami, które działają w lokalizacjach pamięci współużytkowanej na zmianę ich stanu przy użyciu niepodzielnych operacji. Niepodzielne operacje zapewniona jest spójny dla wszystkich procesorów w komputerze. Blokady i elementów WaitHandle są .NET obiektów, które automatycznie operacje blokowane podczas ustawiania lub resetowania. Mogą istnieć inne pamięci współużytkowanej struktury danych w aplikacji, która wymaga również użycia operacje blokowane w celu zaktualizowania w sposób bezpieczny dla wątków. Aby uzyskać więcej informacji, zobacz [operacji Blokowanej](http://go.microsoft.com/fwlink/?LinkId=177870) w .NET Framework w części biblioteki MSDN Library.

 Synchronizacja i blokowanie to mechanizmy służące do zapewnienia poprawnie wykonywanie wielu wątków aplikacji. Każdy wątek aplikacji wielowątkowych to jednostki niezależne wykonywanie zaplanowanego niezależnie przez system operacyjny. Rywalizacja o blokady występuje, gdy wątek, który próbuje uzyskać blokadę jest opóźnione, ponieważ inny wątek jest z blokadą.

 Często są zagnieżdżone blokad. Zagnieżdżanie występuje, gdy wątek wykonywania sekcję krytyczną wykonuje funkcję, która następnie wymaga innego blokady. Niektóre liczby zagnieżdżeń blokady jest nieuniknione. Twoja sekcja krytycznego może wywołać metody .NET Framework, która opiera się na blokady, aby upewnić się, że jest metodą o bezpiecznych wątkach. Wywołania niektórych sekcję krytyczną w aplikacji do metody Framework, który również blokuje przy użyciu dojścia blokady różne powoduje, że blokady zagnieździć. Zagnieżdżone warunki blokady może prowadzić do, które są bardzo trudne unravel i rozwiązywać problemy z wydajnością.

 Ta reguła jest uruchamiana, gdy pomiarów dokonanych podczas uruchomienia profilowania wskazuje jest zbyt wysoki stopień Rywalizacja o blokady. Rywalizacji blokad opóźnienie wykonania wątków, które oczekują na blokadę. Należy zbadać nawet stosunkowo małe ilości Rywalizacja o blokady w testach jednostkowych lub w testach obciążenia uruchomione na dolnej sprzętowych zakończenia.

> [!NOTE]
> Po bardzo wysoka liczba rywalizacji blokad zgłoszone w danych profilowania [DA0039: Bardzo wysoki współczynnik rywalizacji o blokadę](../profiling/da0039-very-high-rate-of-lock-contentions.md) komunikat ostrzegawczy jest uruchamiany zamiast komunikat z informacjami.

## <a name="how-to-investigate-a-warning"></a>Jak badać ostrzeżenie
 Kliknij dwukrotnie komunikat, aby przejść do [znaczniki](../profiling/marks-view.md) widoku danych profilowania.  Znajdź **.NET CLR LocksAndThreads\Contention szybkość / sec** kolumny. Określa, czy określone faz wykonywania programu Rywalizacja o blokady w przypadku większych niż pozostałych faz.

 Ta reguła jest uruchamiana tylko wtedy, gdy nie używasz metoda profilowania współbieżności. Metoda profilowania współbieżności to najlepsze narzędzie służące do diagnozowania problemów z wydajnością związanych z Rywalizacja o blokady w aplikacji. Zbieranie danych, aby zrozumieć zachowania blokującego aplikacji profilowania współbieżności. W tym opis blokad, które są silnie utrzymywał, ile czasu wykonywania wątków zostanie opóźnione, oczekiwania na blokady rywalizacją i jakie określonego kodu jest powiązana. Współbieżność profile zbiera dane na wszystkich zablokować rywalizacji, w tym zachowania blokującego natywnych urządzeń Windows, klas .NET Framework i inne biblioteki innych firm aplikacji odwołania. Aby uzyskać informacje dotyczące profilowania współbieżności z [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE, zobacz [zbierania danych współbieżności procesu i wątku](../profiling/collecting-thread-and-process-concurrency-data.md). Aby uzyskać łącza do informacji o współbieżności profilowania z wiersza polecenia, zobacz **zbierania danych zasobów rywalizacji o zasoby i wątku działania przy użyciu metody współbieżności** części [korzystanie z metod profilowania z Wiersz polecenia](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md).