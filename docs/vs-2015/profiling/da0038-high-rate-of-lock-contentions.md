---
title: 'DA0038: wysoki współczynnik rywalizacji o blokadę | Microsoft Docs'
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
ms.openlocfilehash: e3f96303d69d394f3e24021ddea530d44a8ab718
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300079"
---
# <a name="da0038-high-rate-of-lock-contentions"></a>DA0038: Wysoka liczba rywalizacji blokad
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby uzyskać najnowszą dokumentację programu Visual Studio, zobacz [DA0038: wysoka liczba rywalizacji o blokadę](https://docs.microsoft.com/visualstudio/profiling/da0038-high-rate-of-lock-contentions).  
  
|||  
|-|-|  
|Identyfikator zasady|DA0038|  
|Kategoria|Użycie .NET Framework|  
|Metoda profilowania|Sond<br /><br /> Oprzyrządowanie<br /><br /> Pamięć platformy .NET|  
|Komunikat|Występuje wysoki współczynnik rywalizacji o blokadę platformy .NET. Sprawdź przyczynę rywalizacji o blokadę, uruchamiając profil współbieżności.|  
|Typ reguły|Informacje|  
  
 Podczas profilowania przy użyciu metod próbkowania, pamięci .NET lub rywalizacji o zasoby należy zebrać co najmniej 25 próbek, aby wyzwolić tę regułę.  
  
## <a name="cause"></a>Przyczyna  
 Dane wydajności systemu zbierane z danymi profilowania wskazują, że podczas wykonywania aplikacji wystąpiła znacznie duża liczba rywalizacji blokad. Rozważ ponowne przeprowadzenie profilowania przy użyciu metody profilowania współbieżności, aby znaleźć przyczynę rywalizacji.  
  
## <a name="rule-description"></a>Opis reguły  
 Blokady są używane do ochrony krytycznych sekcji kodu, które muszą być wykonywane sekwencyjnie przez jeden wątek na raz w aplikacji wielowątkowej. Microsoft .NET Common Language Run-Time (CLR) zawiera pełny zestaw synchronizacji i blokowania elementów podstawowych. Na przykład C# język obsługuje instrukcję Lock (SyncLock w Visual Basic). Aplikacja zarządzana może wywoływać metody `Monitor.Enter` i `Monitor.Exit` w przestrzeni nazw System. Threading, aby bezpośrednio uzyskać i zwolnić blokadę. .NET Framework obsługuje dodatkowe synchronizacje i blokowanie elementów pierwotnych, w tym klas, które obsługują muteksy, ReaderWriterLocks i semafory. Aby uzyskać więcej informacji, zobacz [Omówienie elementów pierwotnych synchronizacji](https://go.microsoft.com/fwlink/?LinkId=177867) w podręczniku .NET Framework dewelopera w witrynie MSDN w sieci Web. Klasy .NET Framework są przydzielone warstwami za pośrednictwem usług synchronizacji niższego poziomu wbudowanych w system operacyjny Windows. Obejmują one krytyczne obiekty sekcji i wiele różnych funkcji oczekiwania i sygnalizacji zdarzeń. Aby uzyskać więcej informacji, zobacz sekcję [Synchronizacja](https://go.microsoft.com/fwlink/?LinkId=177869) w temacie programowanie Win32 i com w bibliotece MSDN.  
  
 Podstawową klasą .NET Framework i natywnych obiektów systemu Windows, które są używane na potrzeby synchronizacji i blokowania, są lokalizacje pamięci udostępnionej, które należy zmienić przy użyciu operacji zablokowanych. Operacje wykonywane w sposób nieblokowany wykorzystują instrukcje specyficzne dla sprzętu, które działają w lokalizacjach udostępnionych pamięci, aby zmienić ich stan przy użyciu operacji niepodzielnych. Operacje niepodzielne są gwarantowane dla wszystkich procesorów na komputerze. Blokady i elementy WaitHandle są obiektami .NET, które automatycznie używają operacji zablokowanych, gdy są one ustawione lub resetowane. W aplikacji mogą istnieć inne struktury danych pamięci współdzielonej, które wymagają, aby można było je aktualizować w sposób bezpieczny dla wątków. Aby uzyskać więcej informacji, zobacz sekcję [operacje zablokowane](https://go.microsoft.com/fwlink/?LinkId=177870) w sekcji .NET Framework biblioteki MSND  
  
 Synchronizacja i blokowanie to mechanizmy stosowane w celu zapewnienia poprawnego wykonywania aplikacji wielowątkowych. Każdy wątek aplikacji wielowątkowej jest niezależną jednostką wykonywania zaplanowaną niezależnie od systemu operacyjnego. Rywalizacja o blokady występuje zawsze, gdy wątek próbujący uzyskać blokadę jest opóźniony, ponieważ inny wątek utrzymuje blokadę.  
  
 Blokady są często zagnieżdżone. Zagnieżdżanie występuje, gdy wątek wykonujący sekcję krytyczną wykonuje funkcję, która następnie wymaga innej blokady. Nie będzie możliwe uniknięcie zagnieżdżenia blokady. Sekcja krytyczna może wywoływać metodę .NET Framework, która opiera się na blokadach, aby upewnić się, że jest bezpieczna wątkowo. Wywołanie z pewnej krytycznej sekcji w aplikacji do metody struktury, która również jest blokowana przy użyciu innego uchwytu blokady, powoduje, że blokady są zagnieżdżane. Zagnieżdżone warunki blokowania mogą prowadzić do problemów z wydajnością, które są wielowątkowy bardzo trudne do Unravel i naprawy.  
  
 Ta zasada jest wyzwalana, gdy pomiary wykonywane podczas przebiegu profilowania wskazują, że występuje nadmierna ilość rywalizacji o blokadę. Zablokuj rywalizacje opóźniają wykonywanie wątków, które oczekują na blokadę. Nawet dość małe ilości zawartości blokady w testach jednostkowych lub testach obciążenia działających na niższym sprzęcie powinien zostać zbadany.  
  
> [!NOTE]
> Gdy częstotliwość zgłaszania rywalizacji o blokady w danych profilowania jest nadmiernie wysoka, komunikat ostrzegawczy [DA0039: bardzo wysoka liczba rywalizacji blokad](../profiling/da0039-very-high-rate-of-lock-contentions.md) jest uruchamiany zamiast tego komunikatu informacji.  
  
## <a name="how-to-investigate-a-warning"></a>Jak zbadać ostrzeżenie  
 Kliknij dwukrotnie komunikat, aby przejść do widoku [znaczniki](../profiling/marks-view.md) danych profilowania.  Znajdź kolumnę **LocksAndThreads\Contention/s środowiska .NET CLR** . Ustal, czy istnieją określone fazy wykonywania programu, w których rywalizacja o blokady jest grubsza niż w przypadku innych faz.  
  
 Ta zasada jest uruchamiana tylko wtedy, gdy nie używasz metody profilowania współbieżności. Metoda profilowania współbieżności jest najlepszym narzędziem używanym do diagnozowania problemów z wydajnością związanych z zablokowaniem rywalizacji w aplikacji. Zbieraj dane profilowania współbieżności, aby zrozumieć zachowanie blokowania aplikacji. Dotyczy to również informacji o tym, które blokady są silnie ograniczone, jak długo czas wykonywania wątku jest opóźniony w odczekaniu na ograniczone blokady i jaki konkretny kod jest implicated. Profile współbieżności zbierają dane dotyczące wszystkich rywalizacji blokad, w tym zachowania blokowania natywnych obiektów systemu Windows, klas .NET Framework i innych bibliotek innych firm, do których odwołuje się aplikacja. Aby uzyskać informacje na temat profilowania współbieżności z [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE, zobacz [zbieranie danych współbieżności wątków i procesów](../profiling/collecting-thread-and-process-concurrency-data.md). Aby uzyskać linki do informacji na temat profilowania współbieżności z wiersza polecenia, zobacz sekcję **using metody współbieżności, aby zebrać dane rywalizacji o zasoby i aktywność wątku** w temacie [using metody profilowania z wiersza polecenia](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md).
