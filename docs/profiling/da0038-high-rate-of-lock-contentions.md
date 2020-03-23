---
title: 'DA0038: Wysoki wskaźnik rywalizacji o blokadę | Dokumenty firmy Microsoft'
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
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: d8e0218b01a162a3af8c35009bc8e733f5c386ef
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777505"
---
# <a name="da0038-high-rate-of-lock-contentions"></a>DA0038: Wysoki wskaźnik rywalizacji o blokadę

|||
|-|-|
|Identyfikator reguły|DA0038|
|Kategoria|Użycie programu .NET Framework|
|Metoda profilowania|Próbkowanie<br /><br /> Oprzyrządowanie<br /><br /> Pamięć .NET|
|Komunikat|Występuje wysoka szybkość rywalizacji blokady platformy .NET. Należy zbadać przyczynę tego rywalizacji blokady, uruchamiając profil współbieżności.|
|Typ reguły|Informacje|

 Podczas profilowania przy użyciu próbkowania, .NET pamięci lub metody rywalizacji o zasoby, należy zebrać co najmniej 25 próbek, aby wyzwolić tę regułę.

## <a name="cause"></a>Przyczyna
 Dane wydajności systemu, które są zbierane z danymi profilowania wskazuje, że znacznie wysoki wskaźnik rywalizacji blokady wystąpił podczas wykonywania aplikacji. Należy rozważyć profilowanie ponownie przy użyciu metody profilowania współbieżności, aby znaleźć przyczynę rywalizacji.

## <a name="rule-description"></a>Opis reguły
 Blokady są używane do ochrony krytycznych sekcji kodu, które muszą być wykonywane szeregowo przez jeden wątek naraz w aplikacji wielowątkowej. Program Microsoft .NET Common Language Run-time (CLR) zapewnia pełny zestaw synchronizacji i blokowania ilcie. Na przykład język C# obsługuje lock instrukcji (SyncLock w języku Visual Basic). Aplikacja zarządzana może wywołać Metody Monitor.Enter i Monitor.Exit w obszarze nazw System.Threading w celu bezpośredniego uzyskania i zwolnienia blokady. .NET Framework obsługuje dodatkową synchronizację i blokowanie wierzchołków, w tym klas, które obsługują muteksy, ReaderWriterLocks i Semafory. Aby uzyskać więcej informacji, zobacz [Omówienie ujegnienia synchronizacji](/dotnet/standard/threading/overview-of-synchronization-primitives) w przewodniku dla deweloperów platformy .NET Framework w witrynie sieci Web MSDN. Klasy .NET Framework są warstwowe na niższy poziom usług synchronizacji wbudowanych w system operacyjny Windows. Należą do nich krytyczne obiekty sekcji i wiele różnych funkcji sygnalizacji oczekiwania i zdarzeń. Aby uzyskać więcej informacji, zobacz sekcję [Synchronizacja](/windows/win32/sync/synchronization) w systemach Win32 i COM Development w bibliotece MSDN

 U podstaw klas .NET Framework i natywnych obiektów systemu Windows, które są używane do synchronizacji i blokowania są lokalizacje pamięci współużytkowanej, które muszą zostać zmienione za pomocą operacji zablokowanych. Zablokowane operacje używają instrukcji specyficznych dla sprzętu, które działają w lokalizacjach pamięci współużytkowanej, aby zmienić ich stan przy użyciu operacji niepodzielnych. Operacje niepodzielne są gwarantowane być spójne we wszystkich procesorach w komputerze. Blokady i WaitHandles są obiektami .NET, które automatycznie używają zablokowanych operacji podczas ich ustawiania lub resetowania. W aplikacji mogą istnieć inne struktury danych pamięci współużytkowanej, które również wymagają użycia zablokowanych operacji w celu zaktualizowanie w sposób bezpieczny dla wątków. Aby uzyskać więcej informacji, zobacz [Interlocked Operations](/dotnet/api/system.threading.interlocked) w sekcji .NET Framework biblioteki MSDN.

 Synchronizacja i blokowanie są mechanizmy używane w celu zapewnienia, że aplikacje wielowątkowe działają poprawnie. Każdy wątek aplikacji wielowątkowej jest niezależną jednostką wykonawczą, która jest zaplanowana niezależnie przez system operacyjny. Rywalizacja o blokadę występuje, gdy wątek, który próbuje uzyskać blokadę jest opóźniony, ponieważ inny wątek przytrzymuje blokadę.

 Zamki są często zagnieżdżone. Zagnieżdżanie występuje, gdy wątek wykonujący sekcję krytyczną wykonuje funkcję, która następnie wymaga innej blokady. Pewna ilość zagnieżdżania blokady jest nieunikniona. Sekcja krytyczna może wywołać metodę .NET Framework, która opiera się na blokadach, aby upewnić się, że jest bezpieczna dla wątków. Wywołanie z niektórych krytycznych sekcji w aplikacji do metody Framework, która również blokuje przy użyciu innego uchwytu blokady powoduje, że blokady do zagnieżdżenia. Zagnieżdżone warunki blokowania może prowadzić do problemów z wydajnością, które są notorycznie trudne do rozwikłania i naprawienia.

 Ta reguła jest uruchamiana, gdy pomiary wykonane podczas przebiegu profilowania wskazują, że istnieje zbyt duża ilość rywalizacji o blokadę. Rywalizacje blokady opóźniają wykonanie wątków oczekujących na blokadę. Nawet dość małe ilości rywalizacji blokady w testach jednostkowych lub w testach obciążenia uruchomionych na sprzęcie dolnej końca powinny być badane.

> [!NOTE]
> Gdy szybkość zgłoszonych rywalizacji blokady w danych profilowania jest zbyt wysoka, [DA0039: Bardzo wysoka szybkość blokady rywalizacji](../profiling/da0039-very-high-rate-of-lock-contentions.md) komunikat ostrzegawczy jest uruchamiany zamiast tego komunikatu informacyjnego.

## <a name="how-to-investigate-a-warning"></a>Jak zbadać ostrzeżenie
 Kliknij dwukrotnie wiadomość, aby przejść do widoku [Znaczniki](../profiling/marks-view.md) danych profilowania.  Znajdź kolumnę **.NET CLR LocksAndThreads\Contention Rate / sec.** Określ, czy istnieją określone fazy wykonywania programu, gdzie rywalizacja o blokadę jest cięższa niż inne fazy.

 Ta reguła jest uruchamiana tylko wtedy, gdy nie jest używany sposób profilowania współbieżności. Metoda profilowania współbieżności jest najlepszym narzędziem do diagnozowania problemów z wydajnością związanych z rywalizacją blokad w aplikacji. Zbieranie danych profilowania współbieżności, aby zrozumieć zachowanie blokowania aplikacji. Obejmuje to zrozumienie, które blokady są mocno twierdził, jak długo czas wykonywania wątku jest opóźnione oczekiwanie na blokady twierdził i jaki konkretny kod jest zaangażowany. Profile współbieżności zbiera dane na temat wszystkich rywalizacji blokady, w tym zachowanie blokowania natywnych obiektów systemu Windows, klas .NET Framework i innych bibliotek innych firm odwołania do aplikacji. Aby uzyskać informacje na temat profilowania współbieżności z [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE, zobacz Zbieranie danych [wątku i przetwarzania współbieżności](../profiling/collecting-thread-and-process-concurrency-data.md). Aby uzyskać łącza do informacji o profilowaniu współbieżności z wiersza polecenia, zobacz **Użyj metody współbieżności do zbierania rywalizacji o zasoby i danych aktywności wątku** sekcji [Użyj metod profilowania z wiersza polecenia](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md).
