---
title: Podstawowy zestaw reguł poprawności dla zarządzanego kodu
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 631f0daf-1d42-4c90-a7dc-1a6a9de64c93
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 8f48b2d60feb9743529de8ed80b80365ffb815d1
ms.sourcegitcommit: 08c144d290da373df841f04fc799e3133540a541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2019
ms.locfileid: "72534600"
---
# <a name="basic-correctness-rules-rule-set-for-managed-code"></a>Podstawowy zestaw reguł poprawności dla zarządzanego kodu

Zestaw reguł prawidłowości podstawowych reguł poprawności koncentruje się na błędach logiki i często występujących pomyłek w korzystaniu z interfejsów API platformy. Podstawowe reguły poprawności obejmują reguły z zestawu reguł [zarządzanych zalecanych reguł](managed-recommended-rules-rule-set-for-managed-code.md) .

Poniższa tabela zawiera opis wszystkich reguł w zestawie reguł poprawności podstawowych firmy Microsoft.

|Reguła|Opis|
|----------|-----------------|
|[CA1001](../code-quality/ca1001.md)|Typy, do których należą pola możliwe do likwidacji, powinny być możliwe do likwidacji|
|[CA1009](../code-quality/ca1009.md)|Poprawnie deklaruj procedury obsługi zdarzeń|
|[CA1016](../code-quality/ca1016.md)|Oznacz zestawy atrybutem AssemblyVersion|
|[CA1033](../code-quality/ca1033.md)|Metody interfejsu powinny móc zostać wywołane przez typy podrzędne|
|[CA1049](../code-quality/ca1049.md)|Typy, do których należą natywne zasoby, powinny być możliwe do likwidacji|
|[CA1060](../code-quality/ca1060.md)|Przenieś metody P/Invoke do klasy NativeMethods|
|[CA1061](../code-quality/ca1061.md)|Nie ukrywaj metod klasy bazowej|
|[CA1063](../code-quality/ca1063.md)|Poprawnie zaimplementuj interfejs IDisposable|
|[CA1065](../code-quality/ca1065.md)|Nie wywołuj wyjątków w nieoczekiwanych lokalizacjach|
|[CA1301](../code-quality/ca1301.md)|Unikaj duplikowania akceleratorów|
|[CA1400](../code-quality/ca1400.md)|Punkty wejścia P/Invoke powinny istnieć|
|[CA1401](../code-quality/ca1401.md)|Elementy P/Invoke nie powinny być widoczne|
|[CA1403](../code-quality/ca1403.md)|Typy z automatycznym układem nie powinny być widoczne dla modelu COM|
|[CA1404](../code-quality/ca1404.md)|Wywołaj metodę GetLastError bezpośrednio po elemencie P/Invoke|
|[CA1405](../code-quality/ca1405.md)|Typy podstawowe typów widocznych dla modelu COM powinny być widoczne dla modelu COM|
|[CA1410](../code-quality/ca1410.md)|Metody rejestracji modelu COM powinny mieć swoje odpowiedniki|
|[CA1415](../code-quality/ca1415.md)|Poprawnie zadeklaruj elementy P/Invoke|
|[CA1821](../code-quality/ca1821.md)|Usuwaj puste finalizatory|
|[CA1900](../code-quality/ca1900.md)|Pola typu wartości powinny być przenośne|
|[CA1901](../code-quality/ca1901.md)|Deklaracje metody P/Invoke powinny być przenośne|
|[CA2002](../code-quality/ca2002.md)|Nie blokuj obiektów o słabej tożsamości|
|[CA2100](../code-quality/ca2100.md)|Sprawdź zapytania SQL pod kątem luk w zabezpieczeniach|
|[CA2101](../code-quality/ca2101.md)|Określ kierowanie dla argumentów ciągu P/Invoke|
|[CA2108](../code-quality/ca2108.md)|Przejrzyj zabezpieczenia deklaratywne dla typów wartości|
|[CA2111](../code-quality/ca2111.md)|Wskaźniki nie powinny być widoczne|
|[CA2112](../code-quality/ca2112.md)|Zabezpieczone typy nie powinny ujawniać pól|
|[CA2114](../code-quality/ca2114.md)|Zabezpieczenie metody powinno być nadzbiorem typu|
|[CA2116](../code-quality/ca2116.md)|Metody z atrybutem APTCA powinny wywoływać tylko metody z atrybutem APTCA|
|[CA2117](../code-quality/ca2117.md)|Typy z atrybutem APTCA powinny rozszerzać tylko typy podstawowe z atrybutem APTCA|
|[CA2122](../code-quality/ca2122.md)|Nie ujawniaj pośrednio metod żądaniami LinkDemand|
|[CA2123](../code-quality/ca2123.md)|Przesłonięcia żądań konsolidacji powinny być identyczne z podstawowymi|
|[CA2124](../code-quality/ca2124.md)|Opakuj podatne na przejęcie klauzule finally w zewnętrzny blok try|
|[CA2126](../code-quality/ca2126.md)|Żądania LinkDemand dla typu wymagają żądań dziedziczenia|
|[CA2131](../code-quality/ca2131.md)|Typy krytyczne pod względem zabezpieczeń nie mogą brać udziału w określaniu równoważności typów|
|[CA2132](../code-quality/ca2132.md)|Konstruktory domyślne muszą być co najmniej tak krytyczne jak konstruktory domyślne typu podstawowego|
|[CA2133](../code-quality/ca2133.md)|Delegaci muszą być powiązani z metodami ze spójną przezroczystością|
|[CA2134](../code-quality/ca2134.md)|Metody muszą zachowywać spójną przezroczystość podczas nadpisywania metod bazowych|
|[CA2137](../code-quality/ca2137.md)|Metody przezroczyste muszą zawierać tylko weryfikowalny język pośredni|
|[CA2138](../code-quality/ca2138.md)|Metody przezroczyste nie mogą wywoływać metod z atrybutem SuppressUnmanagedCodeSecurity|
|[CA2140](../code-quality/ca2140.md)|Kod przezroczysty nie może przywoływać elementów krytycznych pod względem zabezpieczeń|
|[CA2141](../code-quality/ca2141.md)|Metody przezroczyste nie mogą spełniać LinkDemands|
|[CA2146](../code-quality/ca2146.md)|Typy muszą być co najmniej tak krytyczne jak ich typy i interfejsy podstawowe|
|[CA2147](../code-quality/ca2147.md)|Metody przezroczyste nie mogą używać asercji zabezpieczeń|
|[CA2149](../code-quality/ca2149.md)|Metody przezroczyste nie mogą wywoływać kodu natywnego|
|[CA2200](../code-quality/ca2200.md)|Ponowie zgłoś wyjątek, aby zachować szczegóły stosu|
|[CA2202](../code-quality/ca2202.md)|Nie likwiduj obiektów wielokrotnie|
|[CA2207](../code-quality/ca2207.md)|Pola statyczne typu wartości inicjuj bezpośrednio|
|[CA2212](../code-quality/ca2212.md)|Nie oznaczaj składników usługi atrybutem WebMethod|
|[CA2213](../code-quality/ca2213.md)|Pola możliwe do likwidacji należy likwidować|
|[CA2214](../code-quality/ca2214.md)|Nie wywołuj w konstruktorach metod, które można przesłaniać|
|[CA2216](../code-quality/ca2216.md)|Typy możliwe do likwidacji powinny deklarować finalizator|
|[CA2220](../code-quality/ca2220.md)|Finalizatory powinny wywoływać finalizator klasy bazowej|
|[CA2229](../code-quality/ca2229.md)|Zaimplementuj konstruktory serializacji|
|[CA2231](../code-quality/ca2231.md)|Przeciążaj operator równości w przypadku przesłaniania metody ValueType.Equals|
|[CA2232](../code-quality/ca2232.md)|Oznacz punkty wejścia modelu Windows Forms atrybutem STAThread|
|[CA2235](../code-quality/ca2235.md)|Oznacz wszystkie pola nieprzeznaczone do serializacji|
|[CA2236](../code-quality/ca2236.md)|Wywołuj metody klasy bazowej dla typów ISerializable|
|[CA2237](../code-quality/ca2237.md)|Oznacz typy ISerializable atrybutem SerializableAttribute|
|[CA2238](../code-quality/ca2238.md)|Poprawnie implementuj metody serializacji|
|[CA2240](../code-quality/ca2240.md)|Poprawnie zaimplementuj interfejs ISerializable|
|[CA2241](../code-quality/ca2241.md)|Podaj poprawne argumenty metod formatowania|
|[CA2242](../code-quality/ca2242.md)|Poprawnie testuj nie-liczby (NaN)|
|[CA1008](../code-quality/ca1008.md)|Typy wyliczeniowe powinny mieć wartość zero|
|[CA1013](../code-quality/ca1013.md)|Przeciążaj operator równości w przypadku przeciążania operatorów dodawania i odejmowania|
|[CA1303](../code-quality/ca1303.md)|Nie przekazuj literałów jako zlokalizowanych parametrów|
|[CA1308](../code-quality/ca1308.md)|Normalizuj ciągi do postaci zapisanej wielkimi literami|
|[CA1806](../code-quality/ca1806.md)|Nie ignoruj wyników metod|
|[CA1816](../code-quality/ca1816.md)|Poprawnie wywołaj metodę GC.SuppressFinalize|
|[CA1819](../code-quality/ca1819.md)|Właściwości nie powinny zwracać tablic|
|[CA1820](../code-quality/ca1820.md)|Testuj obecność pustych ciągów przy użyciu długości ciągu|
|[CA1903](../code-quality/ca1903.md)|Używaj tylko interfejsu API platformy docelowej|
|[CA2004](../code-quality/ca2004.md)|Usuń wywołania funkcji GC.KeepAlive|
|[CA2006](../code-quality/ca2006.md)|Używaj klasy SafeHandle w celu hermetyzacji zasobów natywnych|
|[CA2102](../code-quality/ca2102.md)|Przechwytuj wyjątki bez atrybutu CLSCompliant w ogólnych procedurach obsługi|
|[CA2104](../code-quality/ca2104.md)|Nie deklaruj modyfikowalnych typów referencyjnych tylko do odczytu|
|[CA2105](../code-quality/ca2105.md)|Pola tablicy nie powinny być tylko do odczytu|
|[CA2106](../code-quality/ca2106.md)|Zabezpiecz asercje|
|[CA2115](../code-quality/ca2115.md)|Wywołaj funkcję GC.KeepAlive w przypadku korzystania z zasobów natywnych|
|[CA2119](../code-quality/ca2119.md)|Pieczętuj metody, które spełniają wymagania interfejsów prywatnych|
|[CA2120](../code-quality/ca2120.md)|Zabezpiecz konstruktory serializacji|
|[CA2121](../code-quality/ca2121.md)|Konstruktory statyczne powinny być prywatne|
|[CA2130](../code-quality/ca2130.md)|Stałe krytyczne pod względem zabezpieczeń powinny być przezroczyste|
|[CA2205](../code-quality/ca2205.md)|Użyj zarządzanych odpowiedników funkcji API Win32|
|[CA2215](../code-quality/ca2215.md)|Metody Dispose powinny wywoływać metodę Dispose klasy bazowej|
|[CA2221](../code-quality/ca2221.md)|Finalizatory powinny być chronione|
|[CA2222](../code-quality/ca2222.md)|Nie obniżaj dziedziczonej widoczności składowych|
|[CA2223](../code-quality/ca2223.md)|Składowe powinny różnić się nie tylko zwracanym typem|
|[CA2224](../code-quality/ca2224.md)|Przesłaniaj metodę equals w przypadku przeciążania operatora równości|
|[CA2226](../code-quality/ca2226.md)|Operatory powinny mieć symetryczne przeciążenia|
|[CA2227](../code-quality/ca2227.md)|Właściwości kolekcji powinny być tylko do odczytu|
|[CA2239](../code-quality/ca2239.md)|Udostępnij metody deserializacji dla pól opcjonalnych|
