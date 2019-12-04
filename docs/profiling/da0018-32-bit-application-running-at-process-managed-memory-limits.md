---
title: DA0018:32-bitowa aplikacja uruchomiona w limitach pamięci zarządzanej przez proces | Microsoft Docs
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
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74780068"
---
# <a name="da0018-32-bit-application-running-at-process-managed-memory-limits"></a>DA0018:32-bitowa aplikacja działająca w granicach pamięci zarządzanej przez proces

|||
|-|-|
|Identyfikator zasady|DA0018|
|Kategoria|Użycie narzędzia profilowania|
|Metoda profilowania|Sond|
|Komunikat|Alokacje pamięci zarządzanej zbliżają się do domyślnego limitu dla procesu 32-bitowego. Twoja aplikacja może być powiązana z pamięcią.|
|Typ reguły|Ostrzeżenie|

 Podczas profilowania przy użyciu metod pobierania próbek, pamięci .NET lub rywalizacji o zasoby należy zebrać co najmniej 10 próbek, aby wyzwolić tę regułę.

## <a name="cause"></a>Przyczyna
 Dane systemowe zebrane podczas przebiegu profilowania wskazują, że sterty pamięci .NET Framework zbliżają się do maksymalnego rozmiaru sterty zarządzanej w procesie 32-bitowym. Ten maksymalny rozmiar jest wartością domyślną. Jest on oparty na łącznej ilości przestrzeni adresowej procesu, która może zostać przypisana do bajtów prywatnych. Raportowana wartość to maksymalna obserwowana wartość sterty, gdy profilowany proces był aktywny. Rozważ ponowne przeprowadzenie profilowania przy użyciu metody profilowania pamięci platformy .NET i zoptymalizowanie użycia zasobów zarządzanych przez aplikację.

 Gdy rozmiar sterty zarządzanej zbliża się do domyślnego limitu, proces automatycznego odzyskiwania pamięci może być niezależny. Zwiększa to obciążenie zarządzania pamięcią.

 Reguła jest uruchamiana tylko dla aplikacji 32-bitowych działających na komputerach 32-bitowych.

## <a name="rule-description"></a>Opis reguły
 Microsoft .NET Common Language Time (CLR) zapewnia automatyczny mechanizm zarządzania pamięcią, który używa modułu wyrzucania elementów bezużytecznych do odzyskiwania pamięci z obiektów, które nie są już używane przez aplikację. Moduł wyrzucania elementów bezużytecznych jest oparty na generacji, w oparciu o założenie, że wiele alokacji jest krótkoterminowych. Zmienne lokalne, na przykład, powinny być krótkotrwałe. Nowo utworzone obiekty rozpoczynają się w generacji 0 (Gen 0), a następnie postępować w generacji 1, gdy zajmują się uruchomieniem odzyskiwania pamięci, a wreszcie przechodzą do generacji 2, jeśli aplikacja nadal używa tych danych.

 Obiekty zarządzane o rozmiarze większym niż 85 KB są przydzielane na stercie dużego obiektu, gdzie podlegają mniej częstemu wyrzucaniu elementów bezużytecznych i kompaktowania niż mniejsze obiekty. duże obiekty są zarządzane oddzielnie, ponieważ zakłada się, że są one bardziej trwałe i ponieważ mieszanie trwałych i dużych obiektów z często przydzielonymi mniejszymi obiektami może spowodować powstanie fragmentacji rzutowania sterty.

 Ponieważ całkowity rozmiar sterty zarządzanej zbliża się do domyślnego limitu, obciążenie związane z zarządzaniem pamięcią zwykle zwiększa się do momentu, w którym można zacząć wpływać na czas odpowiedzi i skalowalność aplikacji.

## <a name="how-to-investigate-a-warning"></a>Jak zbadać ostrzeżenie
 Kliknij dwukrotnie komunikat w oknie Lista błędów, aby przejść do widoku [znaczniki](../profiling/marks-view.md) . Znajdź **pamięć środowiska CLR programu .net\\liczba bajtów we wszystkich stertach** i kolumnach **# całkowita liczba bajtów zadeklarowanych** . Ustal, czy istnieją określone fazy wykonywania programu, w których alokacja pamięci zarządzanej jest większa niż w przypadku innych faz. Porównaj wartości **w kolumnie # Bytes we wszystkich stertach** z szybkością wyrzucania elementów bezużytecznych raportowaną w **pamięci programu .NET CLR\\# kolekcji gen 0**, **pamięci środowiska .NET CLR\\# kolekcji Gen 1**i **programu .NET CLR Memory\\# kolekcji generacji 2** kolumn, aby określić, czy wzorzec alokacji pamięci zarządzanej ma wpływ na szybkość wyrzucania elementów bezużytecznych.

 W aplikacji .NET Framework środowisko uruchomieniowe języka wspólnego ogranicza łączny rozmiar sterty zarządzanej do niemniejszej niż jedna połowa maksymalnego rozmiaru obszaru adresów procesu. W przypadku procesów 32-bitowych uruchomionych na komputerze 32-bitowym 2 GB reprezentuje górny limit prywatnej części przestrzeni adresowej procesu. Ponieważ łączny rozmiar sterty zarządzanej zbliża się do limitu domyślnego, obciążenie pamięci może zwiększyć się i może obniżyć wydajność aplikacji.

 Jeśli nadmierne obciążenie pamięci zarządzanej jest problemem, należy wziąć pod uwagę jedną z następujących opcji:

- Optymalizowanie użycia zasobów pamięci zarządzanej przez aplikację

   lub

- podejmowanie kroków w celu zwolnienia ograniczeń architektury dla maksymalnego rozmiaru pamięci wirtualnej dla procesu 32-bitowego

  W celu zoptymalizowania użycia zasobów pamięci zarządzanej przez aplikację należy zebrać dane alokacji pamięci zarządzanej w ramach przebiegu profilowania pamięci platformy .NET. Przejrzyj raporty dotyczące [widoków danych pamięci .NET](../profiling/dotnet-memory-data-views.md) , aby zrozumieć wzorzec alokacji pamięci aplikacji.

  [Widok okresu istnienia obiektów](../profiling/object-lifetime-view.md) umożliwia określenie, które obiekty danych programu są wykorzystywane do generacji, a następnie odzyskiwane z tego miejsca.

  [Widok alokacje](../profiling/dotnet-memory-allocations-view.md) służy do określania ścieżki wykonywania, która spowodowała te przydziały.

  Aby uzyskać więcej informacji o ulepszaniu wydajności odzyskiwania pamięci, zobacz artykuł techniczny .NET Framework, [podstawowe informacje dotyczące modułu wyrzucania elementów bezużytecznych i wskazówki dotyczące wydajności](/previous-versions/dotnet/articles/ms973837(v=msdn.10)) w witrynie MSDN w sieci Web.

  Aby uzyskać ulgi architektury z ograniczeń pamięci wirtualnej na rozmiar prywatnej części przestrzeni adresowej procesu, spróbuj uruchomić ten proces 32-bitowy na komputerze 64-bitowym.  Proces 32-bitowy na komputerze 64-bitowym może uzyskać do 4 GB prywatnej pamięci wirtualnej.

  Proces 64-bitowy uruchomiony na komputerze 64-bitowym może uzyskać do 8 TB pamięci wirtualnej. Rozważ ponowne skompilowanie aplikacji, aby wykonać ją jako natywną aplikację 64-bitową. Ta reguła służy tylko do celów informacyjnych i może nie wymagać czynności naprawczych.
