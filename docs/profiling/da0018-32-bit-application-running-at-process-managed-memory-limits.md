---
title: 'DA0018: 32-bitowa aplikacja uruchomiona przy limitach pamięci zarządzanych przez proces | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.18
- vs.performance.DA0018
- vs.performance.rules.DA0018
ms.assetid: 98eb2d96-f92f-42f9-915c-e5ac2330ffbf
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: d7bebd25f499131b4beda109ebb9ac468c2435b1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74780068"
---
# <a name="da0018-32-bit-application-running-at-process-managed-memory-limits"></a>DA0018: 32-bitowa aplikacja uruchomiona z limitami pamięci zarządzanych przez proces

|||
|-|-|
|Identyfikator reguły|DA0018|
|Kategoria|Użycie narzędzi profilowania|
|Metoda profilowania|Próbkowanie|
|Komunikat|Alokacje pamięci zarządzanej zbliżające się do domyślnego limitu dla procesu 32-bitowego. Aplikacja może być związana z pamięcią.|
|Typ reguły|Ostrzeżenie|

 Podczas profilowania przy użyciu próbkowania, .NET pamięci lub metody rywalizacji o zasoby, należy zebrać co najmniej 10 próbek, aby wyzwolić tę regułę.

## <a name="cause"></a>Przyczyna
 Dane systemowe zebrane podczas przebiegu profilowania wskazują, że sterty pamięci .NET Framework zbliżyły się do maksymalnego rozmiaru zarządzanych stert, które mogą osiągnąć w procesie 32-bitowym. Ten maksymalny rozmiar jest wartością domyślną. Jest on oparty na całkowitej ilości przestrzeni adresowej procesu, która może być alokowana dla bajtów prywatnych. Zgłoszona wartość jest maksymalną obserwowaną wartością stert, gdy proces profilowania był aktywny. Rozważ profilowanie ponownie przy użyciu metody profilowania pamięci .NET i optymalizacji użycia zasobów zarządzanych przez aplikację.

 Gdy rozmiar zarządzanych sterty podejście domyślny limit, proces automatycznego wyrzucania elementów bezużytecznych może być wywoływane częściej. Zwiększa to obciążenie związane z zarządzaniem pamięcią.

 Reguła jest uruchamiana tylko dla aplikacji 32-bitowych działających na komputerach 32-bitowych.

## <a name="rule-description"></a>Opis reguły
 Wspólny język microsoft .NET (CLR) zapewnia mechanizm automatycznego zarządzania pamięcią, który używa modułu zbierającego elementy bezużyteczne do odzyskiwania pamięci z obiektów, które aplikacja nie jest już używana. Moduł zbierający elementy bezużyteczne jest zorientowany na generowanie, przy założeniu, że wiele alokacji są krótkotrwałe. Zmienne lokalne, na przykład, powinny być krótkotrwałe. Nowo utworzone obiekty rozpoczynają się w generacji 0 (gen 0), a następnie przechodzą do generacji 1, gdy przetrwają uruchomienie wyrzucania elementów bezużytecznych, a na koniec przejście do generacji 2, jeśli aplikacja nadal ich używa.

 Obiekty zarządzane, które są większe niż 85 KB są przydzielane na stercie dużych obiektów, gdzie podlegają rzadziej wyrzucania elementów bezużytecznych i zagęszczania niż mniejsze obiekty. duże obiekty są zarządzane oddzielnie, ponieważ zakłada się, że są one bardziej trwałe i ponieważ mieszanie trwałych i dużych obiektów z często przydzielane mniejsze obiekty mogą powodować najgorzej rzutowane fragmentacji sterty.

 Ponieważ całkowity rozmiar zarządzanych stert zbliża się do domyślnego limitu, obciążenie związane z zarządzaniem pamięcią zwykle zwiększa się do punktu, w którym może zacząć wpływać na czas reakcji i skalowalności aplikacji.

## <a name="how-to-investigate-a-warning"></a>Jak zbadać ostrzeżenie
 Kliknij dwukrotnie wiadomość w oknie Lista błędów, aby przejść do widoku [Znaczniki.](../profiling/marks-view.md) Znajdź **.NET CLR\\Memory # Bajty we wszystkich kolumnach Sterty** i **# Całkowita liczba zatwierdzonych bajtów.** Określ, czy istnieją określone fazy wykonywania programu, w których alokacja pamięci zarządzanej jest cięższa niż inne fazy. Porównaj wartości **# Bajtów we wszystkich stert** kolumnach do szybkości wyrzucania elementów bezużytecznych zgłoszonych w **.NET CLR\\Memory # gen 0 Collections**, **.NET CLR Memory\\# of Gen 1 Collections**i **.NET CLR Memory\\# gen 2 Collections** kolumny, aby ustalić, czy wzorzec alokacji pamięci zarządzanej wpływa na szybkość wyrzucania elementów bezużytecznych.

 W aplikacji .NET Framework środowiska uruchomieniowego języka wspólnego ogranicza całkowity rozmiar zarządzanych stert do nieco mniej niż połowę maksymalnego rozmiaru części obszaru prywatnego przestrzeni adresowej procesu. W przypadku procesów 32-bitowych uruchomionych na komputerze 32-bitowym 2 GB reprezentuje górny limit prywatnej części przestrzeni adresowej procesu. Ponieważ całkowity rozmiar zarządzanych stert zaczyna zbliżać się do domyślnego limitu, obciążenie związane z zarządzaniem pamięcią może wzrosnąć, a wydajność aplikacji może się zmniejszyć.

 Jeśli nadmierne obciążenie pamięci zarządzanej jest problem, należy wziąć pod uwagę jedną z następujących opcji:

- optymalizacja wykorzystania zasobów pamięci zarządzanej przez aplikację

   — lub —

- podjęcie kroków w celu złagodzenia ograniczeń architektonicznych dotyczących maksymalnego rozmiaru pamięci wirtualnej dla procesu 32-bitowego

  Aby zoptymalizować użycie zasobów pamięci zarządzanej przez aplikację, należy zebrać dane alokacji pamięci zarządzanej w przebiegu profilowania alokacji pamięci .NET. Przejrzyj raporty [widoki danych pamięci .NET,](../profiling/dotnet-memory-data-views.md) aby zrozumieć wzorzec alokacji pamięci aplikacji.

  Użyj [widoku okres istnienia obiektu,](../profiling/object-lifetime-view.md) aby określić, które z obiektów danych programu są przeżywane do generacji, a następnie są odzyskiwane stamtąd.

  Użyj [widoku alokacji,](../profiling/dotnet-memory-allocations-view.md) aby określić ścieżkę wykonywania, która spowodowała te alokacje.

  Aby uzyskać więcej informacji na temat poprawy wydajności wyrzucania elementów bezużytecznych, zobacz .NET Framework artykuł techniczny, [Podstawowe modułu zbierającego elementy bezużyteczne i wskazówki dotyczące wydajności](/previous-versions/dotnet/articles/ms973837(v=msdn.10)) w witrynie sieci Web MSDN.

  Aby uzyskać ulgę architektoniczną od ograniczeń pamięci wirtualnej na rozmiar prywatnej części przestrzeni adresowej procesu, spróbuj uruchomić ten proces 32-bitowy na komputerze 64-bitowym.  Proces 32-bitowy na komputerze 64-bitowym może uzyskać do 4 GB prywatnej pamięci wirtualnej.

  64-bitowy proces uruchomiony na komputerze 64-bitowym może uzyskać do 8 TB pamięci wirtualnej. Należy rozważyć ponowne skompilowanie aplikacji do wykonania jako natywnej aplikacji 64-bitowej. Ta reguła służy wyłącznie do celów informacyjnych i może nie wymagać działań naprawczych.
