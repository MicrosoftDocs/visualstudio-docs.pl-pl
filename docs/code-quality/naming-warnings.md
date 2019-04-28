---
title: Nazewnictwo — Ostrzeżenia
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.namingrules
helpviewer_keywords:
- managed code analysis warnings, naming warnings
- naming warnings
- warnings, naming
ms.assetid: f97223ce-1d39-4134-81c9-fff2c75d979b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d3fc446207d2f8c2800135154ca435b821a0afd1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62825445"
---
# <a name="naming-warnings"></a>Nazewnictwo — Ostrzeżenia
Ostrzeżenia nazewnictwa obsługuje gotowość do konwencji nazewnictwa wytycznych projektowych programu .NET Framework.

## <a name="in-this-section"></a>W tej sekcji

|Reguła|Opis|
|----------|-----------------|
|[CA1700: Nie nadawaj wartościom wyliczenia nazwy "Reserved"](../code-quality/ca1700-do-not-name-enum-values-reserved.md)|Ta reguła zakłada, że element członkowski wyliczenia o nazwie, która zawiera „reserved”, nie jest obecnie używany, ale jest symbolem zastępczym do zmiany nazwy lub usunięcia w przyszłej wersji. Zmiana nazwy lub usuwanie członka jest zmianą przerywającą.|
|[CA1713: Zdarzenia nie powinny mieć prefiksu before ani after](../code-quality/ca1713-events-should-not-have-before-or-after-prefix.md)|Nazwa zdarzenia rozpoczyna się od „Before” lub „After”. Nazwa powiązanych zdarzeń, które są wywoływane w określonej kolejności, używa czasu teraźniejszego lub przeszłego, aby wskazać względne położenie akcji w sekwencji.|
|[CA1714: Typy wyliczeniowe flag powinny mieć nazwy w liczbie mnogiej](../code-quality/ca1714-flags-enums-should-have-plural-names.md)|Publiczne wyliczenie ma atrybut System.FlagsAttribute, a jego nazwa nie kończy się na "s". Typy, które są oznaczone atrybutem Flags mają nazwy, które mają liczbę mnogą, ponieważ ten atrybut wskazuje, że można określić więcej niż jedną wartość.|
|[CA1704: Identyfikatory powinny być zapisane poprawnie](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)|Nazwa widocznego na zewnątrz identyfikatora zawiera jeden lub więcej wyrazów, które nie są rozpoznane przez bibliotekę sprawdzania pisowni Microsoft.|
|[CA1708: Identyfikatory powinny różnić się przez więcej niż wielkością liter](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)|Identyfikatory przestrzeni nazw, typów, elementów członkowskich i parametry nie mogą się różnić jedynie wielkością liter, ponieważ języki dla środowiska uruchomieniowego języka wspólnego nie muszą rozróżniać wielkości liter.|
|[CA1715: Identyfikatory powinny mieć poprawny prefiks](../code-quality/ca1715-identifiers-should-have-correct-prefix.md)|Nazwa widocznego na zewnątrz interfejsu nie rozpoczyna się od kapitałowych "I".  Nazwa parametru typu ogólnego na widocznych zewnętrznie typie lub metodzie nie zaczyna się od wielkiej litery "T".|
|[CA1720: Identyfikatory nie powinny zawierać nazw typów](../code-quality/ca1720-identifiers-should-not-contain-type-names.md)|Nazwa parametru w widocznym na zewnątrz elemencie członkowskim zawiera nazwę typu danych lub nazwa widocznego na zewnątrz elementu członkowskiego zawiera specyficzną dla języka nazwę typu danych.|
|[CA1722: Identyfikatory nie powinny mieć niepoprawnego prefiksu](../code-quality/ca1722-identifiers-should-not-have-incorrect-prefix.md)|Zgodnie z konwencją, tylko niektóre elementy programowania mają nazwy rozpoczynające się od określonego prefiksu.|
|[CA1711: Identyfikatory nie powinny mieć niepoprawnego sufiksu](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)|Według konwencji nazwy typów, które rozszerzają pewne typy podstawowe lub implementują dane interfejsy lub typy pochodzące z tych typów, powinny kończyć się określonym zarezerwowanym sufiksem. Inne nazwy typów nie powinny używać tych zarezerwowanych sufiksów.|
|[CA1717: Tylko wyliczenia FlagsAttribute powinny mieć nazwy w liczbie mnogiej](../code-quality/ca1717-only-flagsattribute-enums-should-have-plural-names.md)|Zgodnie z konwencjami nazewnictwa, nazwa w liczbie mnogiej dla wyliczenia wskazuje, że w tym samym czasie można określić więcej niż jedną wartość wyliczenia.|
|[CA1725: Nazwy parametrów powinny pasować do deklaracji podstawowej](../code-quality/ca1725-parameter-names-should-match-base-declaration.md)|Spójne nazywanie parametrów w zastąpieniu hierarchii zwiększa użyteczność zastąpienia metody. Jeśli nazwa parametru w metodzie pochodnej różni się od nazwy podstawowej deklaracji, może nie być jasne, czy metoda jest zastąpieniem metody podstawowej, czy też nowym przeciążeniem metody.|
|[CA1719: Nazwy parametrów nie powinny odpowiadać nazwom elementu członkowskiego](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)|Nazwa parametru powinna przekazywać znaczenie parametru, a nazwa elementu członkowskiego powinna przekazywać znaczenie elementu członkowskiego. W projekcie rzadko są one takie same. Nazywanie parametru tak samo jak nazwa jego elementu członkowskiego jest nieintuicyjne i utrudnia korzystanie z biblioteki.|
|[CA1701: Wyrazy złożone ciągu zasobu powinny mieć prawidłową wielkość liter](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)|Każdego wyrazu w ciągu zasobu jest podzielony na tokeny, które są oparte na wielkość liter w wyrazie. Każda ciągła kombinacja dwóch tokenów jest sprawdzana przez bibliotekę sprawdzania pisowni firmy Microsoft. Jeżeli zostanie rozpoznana, dane słowo powoduje naruszenie reguły.|
|[CA1703: Ciągi zasobów, które powinny być zapisane poprawnie](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)|Ciąg zasobu zawiera jeden lub więcej wyrazów, które nie są rozpoznane przez bibliotekę sprawdzania pisowni Microsoft.|
|[CA1724: Nazwy typów nie powinny odpowiadać nazwom](../code-quality/ca1724-type-names-should-not-match-namespaces.md)|Nazwy typów nie powinny odpowiadać nazwy przestrzeni nazw, które są zdefiniowane w bibliotece klas programu .NET Framework. Naruszenie tej zasady może zmniejszyć użyteczność biblioteki.|
|[CA1707: Identyfikatory nie powinny zawierać podkreśleń](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)|Przez konwencję identyfikatory nazw nie zawierają znaku podkreślenia (_). Ta reguła sprawdza przestrzenie nazw, typy, elementy członkowskie i parametry.|
|[CA1721: Nazwy właściwości nie powinny odpowiadać metody get](../code-quality/ca1721-property-names-should-not-match-get-methods.md)|Nazwa publicznego lub chronionego elementu członkowskiego zaczyna się od „Get” i odpowiada nazwie właściwości publicznej lub chronionej. Metody „Get” i właściwości powinny mieć nazwy, które wyraźnie odróżniają ich funkcje.|
|[CA1716: Identyfikatory nie powinny odpowiadać słowom](../code-quality/ca1716-identifiers-should-not-match-keywords.md)|Przestrzeń nazw lub nazwa typu odpowiada zastrzeżonym słowom kluczowym w języku programowania. Identyfikatory przestrzeni nazw i typów nie powinny być zgodne ze słowami kluczowymi, które są definiowane przez języki dla środowiska uruchomieniowego języka wspólnego.|
|[CA1726: Używaj preferowanych terminów](../code-quality/ca1726-use-preferred-terms.md)|Nazwa widocznego na zewnątrz identyfikatora zawiera termin, dla którego istnieje alternatywny, preferowany zamiennik. Alternatywnie nazwa zawiera określenie „Flag” lub „Flags”.|
|[CA1709: Identyfikatory powinny mieć prawidłową wielkość liter](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)|Według Konwencji nazwy parametrów używają notacji pisane wielkości liter i przestrzeni nazw, typu i nazwy elementów członkowskich Użyj Pascal wielkość liter w wyrazie.|
|[CA1702: Wyrazy złożone powinny mieć prawidłową wielkość liter](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)|Nazwa identyfikatora zawiera wiele wyrazów i co najmniej jeden z nich wydaje się wyrazem złożonym, w którym wielkość liter nie jest poprawna.|
|[CA1712: Nie poprzedzaj wartości wyliczenia nazwą typu](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)|Nazwy elementów członkowskich wyliczenia nie mają prefiksu z nazwą typu, ponieważ informacje o typie powinien być dostarczona przez narzędzia programistyczne.|
|[CA1710: Identyfikatory powinny mieć poprawny sufiks](../code-quality/ca1710-identifiers-should-have-correct-suffix.md)|Według Konwencji nazwy typów, które rozszerzają pewne typy podstawowe lub implementują określone interfejsy lub typy pochodzące z tych typów, mają sufiks, który jest skojarzony z typem bazowym lub interfejsem.|