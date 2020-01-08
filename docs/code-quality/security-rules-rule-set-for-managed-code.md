---
title: Zestaw reguł zabezpieczeń dla zarządzanego kodu
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 564aeac6-03fa-41b0-b655-88179f0ab01b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: babfc00dfadc6b26f8338faf37b5b4a1f7c1d8e5
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75587228"
---
# <a name="security-rules-rule-set-for-managed-code"></a>Zestaw reguł zabezpieczeń dla zarządzanego kodu

Użyj zestawu reguł zabezpieczeń firmy Microsoft dla starszej wersji analizy kodu, aby zmaksymalizować liczbę raportowanych potencjalnych problemów z zabezpieczeniami.

|Reguła|Opis|
|----------|-----------------|
|[CA2100](../code-quality/ca2100.md)|Sprawdź zapytania SQL pod kątem luk w zabezpieczeniach|
|[CA2102](../code-quality/ca2102.md)|Przechwytuj wyjątki bez atrybutu CLSCompliant w ogólnych procedurach obsługi|
|[CA2103](../code-quality/ca2103.md)|Przejrzyj zabezpieczenia imperatywne|
|[CA2104](../code-quality/ca2104.md)|Nie deklaruj modyfikowalnych typów referencyjnych tylko do odczytu|
|[CA2105](../code-quality/ca2105.md)|Pola tablicy nie powinny być tylko do odczytu|
|[CA2106](../code-quality/ca2106.md)|Zabezpiecz asercje|
|[CA2107](../code-quality/ca2107.md)|Przejrzyj przypadki użycia metod Deny i PermitOnly|
|[CA2108](../code-quality/ca2108.md)|Przejrzyj zabezpieczenia deklaratywne dla typów wartości|
|[CA2109](../code-quality/ca2109.md)|Przejrzyj widoczne procedury obsługi zdarzeń|
|[CA2111](../code-quality/ca2111.md)|Wskaźniki nie powinny być widoczne|
|[CA2112](../code-quality/ca2112.md)|Zabezpieczone typy nie powinny ujawniać pól|
|[CA2114](../code-quality/ca2114.md)|Zabezpieczenie metody powinno być nadzbiorem typu|
|[CA2115](../code-quality/ca2115.md)|Wywołaj funkcję GC.KeepAlive w przypadku korzystania z zasobów natywnych|
|[CA2116](../code-quality/ca2116.md)|Metody z atrybutem APTCA powinny wywoływać tylko metody z atrybutem APTCA|
|[CA2117](../code-quality/ca2117.md)|Typy z atrybutem APTCA powinny rozszerzać tylko typy podstawowe z atrybutem APTCA|
|[CA2118](../code-quality/ca2118.md)|Przejrzyj przypadki użycia atrybutu SuppressUnmanagedCodeSecurityAttribute|
|[CA2119](../code-quality/ca2119.md)|Pieczętuj metody, które spełniają wymagania interfejsów prywatnych|
|[CA2120](../code-quality/ca2120.md)|Zabezpiecz konstruktory serializacji|
|[CA2121](../code-quality/ca2121.md)|Konstruktory statyczne powinny być prywatne|
|[CA2122](../code-quality/ca2122.md)|Nie ujawniaj pośrednio metod żądaniami LinkDemand|
|[CA2123](../code-quality/ca2123.md)|Przesłonięcia żądań konsolidacji powinny być identyczne z podstawowymi|
|[CA2124](../code-quality/ca2124.md)|Opakuj podatne na przejęcie klauzule finally w zewnętrzny blok try|
|[CA2126](../code-quality/ca2126.md)|Żądania LinkDemand dla typu wymagają żądań dziedziczenia|
|[CA2130](../code-quality/ca2130.md)|Stałe krytyczne pod względem zabezpieczeń powinny być przezroczyste|
|[CA2131](../code-quality/ca2131.md)|Typy krytyczne pod względem zabezpieczeń nie mogą brać udziału w określaniu równoważności typów|
|[CA2132](../code-quality/ca2132.md)|Konstruktory domyślne muszą być co najmniej tak krytyczne jak konstruktory domyślne typu podstawowego|
|[CA2133](../code-quality/ca2133.md)|Delegaci muszą być powiązani z metodami ze spójną przezroczystością|
|[CA2134](../code-quality/ca2134.md)|Metody muszą zachowywać spójną przezroczystość podczas nadpisywania metod bazowych|
|[CA2135](../code-quality/ca2135.md)|Zestawy poziomu 2 nie powinny zawierać żądań LinkDemand|
|[CA2136](../code-quality/ca2136.md)|Adnotacje przezroczystości składowych nie powinny powodować konfliktu|
|[CA2137](../code-quality/ca2137.md)|Metody przezroczyste muszą zawierać tylko weryfikowalny język pośredni|
|[CA2138](../code-quality/ca2138.md)|Metody przezroczyste nie mogą wywoływać metod z atrybutem SuppressUnmanagedCodeSecurity|
|[CA2139](../code-quality/ca2139.md)|Metody przezroczyste nie mogą używać atrybutu HandleProcessCorruptingExceptions|
|[CA2140](../code-quality/ca2140.md)|Kod przezroczysty nie może przywoływać elementów krytycznych pod względem zabezpieczeń|
|[CA2141](../code-quality/ca2141.md)|Metody przezroczyste nie mogą spełniać LinkDemands|
|[CA2142](../code-quality/ca2142.md)|Kod przezroczysty nie powinien być chroniony za pomocą żądań LinkDemand|
|[CA2143](../code-quality/ca2143.md)|Metody przezroczyste nie powinny używać żądań zabezpieczeń|
|[CA2144](../code-quality/ca2144.md)|Kod przezroczysty nie powinien ładować zestawów z tablic bajtowych|
|[CA2145](../code-quality/ca2145.md)|Metody przezroczyste nie powinny być dekorowane za pomocą atrybutu SuppressUnmanagedCodeSecurityAttribute|
|[CA2146](../code-quality/ca2146.md)|Typy muszą być co najmniej tak krytyczne jak ich typy i interfejsy podstawowe|
|[CA2147](../code-quality/ca2147.md)|Metody przezroczyste nie mogą używać asercji zabezpieczeń|
|[CA2149](../code-quality/ca2149.md)|Metody przezroczyste nie mogą wywoływać kodu natywnego|
|[CA2210](../code-quality/ca2210.md)|Zestawy powinny mieć prawidłowe silne nazwy|
|[CA2300](ca2300.md)|Nie używaj niezabezpieczonego deserializatora BinaryFormatter|
|[CA2301](ca2301.md)|Nie wywołuj metody BinaryFormatter.Deserialize bez uprzedniego ustawienia właściwości BinaryFormatter.Binder|
|[CA2302](ca2302.md)|Upewnij się, że właściwość BinaryFormatter.Binder jest ustawiona przed wywołaniem metody BinaryFormatter.Deserialize|
|[CA2305](ca2305.md)|Nie używaj niezabezpieczonego deserializatora LosFormatter|
|[CA2310](ca2310.md)|Nie używaj niezabezpieczonego deserializatora NetDataContractSerializer|
|[CA2311](ca2311.md)|Nie wykonuj deserializacji bez uprzedniego ustawienia właściwości NetDataContractSerializer.Binder|
|[CA2312](ca2312.md)|Upewnij się, że właściwość NetDataContractSerializer.Binder jest ustawiona przed deserializacją|
|[CA2315](ca2315.md)|Nie używaj niezabezpieczonego deserializatora ObjectStateFormatter|
|[CA2321](ca2321.md)|Nie wykonuj deserializacji za pomocą obiektu JavaScriptSerializer zainicjowanego przy użyciu parametru SimpleTypeResolver|
|[CA2322](ca2322.md)|Upewnij się, że obiekt JavaScriptSerializer nie został zainicjowany przy użyciu parametru SimpleTypeResolver przed deserializacją|
|[CA3001](../code-quality/ca3001.md)|Przegląd kodu pod kątem luk umożliwiających wstrzyknięcie kodu SQL|
|[CA3002](../code-quality/ca3002.md)|Przegląd kodu pod kątem luk umożliwiających działanie skryptów między witrynami|
|[CA3003](../code-quality/ca3003.md)|Przegląd kodu pod kątem luk umożliwiających wstrzyknięcie ścieżki pliku|
|[CA3004](../code-quality/ca3004.md)|Przegląd kodu pod kątem luk umożliwiających ujawnienie informacji|
|[CA3005](../code-quality/ca3005.md)|Przegląd kodu pod kątem luk umożliwiających wstrzyknięcie protokołu LDAP|
|[CA3006](../code-quality/ca3006.md)|Przegląd kodu pod kątem luk umożliwiających wstrzyknięcie polecenia procesu|
|[CA3007](../code-quality/ca3007.md)|Przegląd kodu pod kątem luk umożliwiających otwarcie przekierowania|
|[CA3008](../code-quality/ca3008.md)|Przegląd kodu pod kątem luk umożliwiających wstrzyknięcie wyrażenia XPath|
|[CA3009](../code-quality/ca3009.md)|Przegląd kodu pod kątem luk umożliwiających wstrzyknięcie kodu XML|
|[CA3010](../code-quality/ca3010.md)|Przegląd kodu pod kątem luk umożliwiających wstrzyknięcie kodu XAML|
|[CA3011](../code-quality/ca3011.md)|Przegląd kodu pod kątem luk umożliwiających wstrzyknięcie biblioteki DLL|
|[CA3012](../code-quality/ca3012.md)|Przegląd kodu pod kątem luk umożliwiających wstrzyknięcie wyrażenia regularnego|
|[CA5403](../code-quality/ca5403.md)|Nie zapisuj certyfikatu na stałe w kodzie|
