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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f6d1e40b809f27292f2a808458584837913d881f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75587306"
---
# <a name="naming-warnings"></a>Nazewnictwo — Ostrzeżenia

Obsługa ostrzeżeń dotyczących nazewnictwa spełnia konwencje nazewnictwa wytycznych dotyczących projektowania platformy .NET.

## <a name="in-this-section"></a>W tej sekcji

|Reguła|Opis|
|----------|-----------------|
|[CA1700: Nie nadawaj wartościom wyliczeniowym nazwy „Reserved”](../code-quality/ca1700.md)|Ta reguła zakłada, że element członkowski wyliczenia o nazwie, która zawiera „reserved”, nie jest obecnie używany, ale jest symbolem zastępczym do zmiany nazwy lub usunięcia w przyszłej wersji. Zmiana nazwy lub usuwanie członka jest zmianą przerywającą.|
|[CA1713: Zdarzenia nie powinny mieć prefiksu „before” ani „after”](../code-quality/ca1713.md)|Nazwa zdarzenia rozpoczyna się od „Before” lub „After”. Nazwa powiązanych zdarzeń, które są wywoływane w określonej kolejności, używa czasu teraźniejszego lub przeszłego, aby wskazać względne położenie akcji w sekwencji.|
|[CA1714: Wyliczenia z atrybutem Flags powinny mieć nazwy w liczbie mnogiej](../code-quality/ca1714.md)|Publiczne Wyliczenie ma atrybut System. FlagsAttribute, a jego nazwa nie kończy się znakiem "s". Typy oznaczone za pomocą FlagsAttribute mają nazwy, które są w liczbie mnogiej, ponieważ atrybut wskazuje, że można określić więcej niż jedną wartość.|
|[CA1704: Pisownia identyfikatorów powinna być poprawna](../code-quality/ca1704.md)|Nazwa widocznego na zewnątrz identyfikatora zawiera jeden lub więcej wyrazów, które nie są rozpoznane przez bibliotekę sprawdzania pisowni Microsoft.|
|[CA1708: Identyfikatory powinny różnić się nie tylko wielkością liter](../code-quality/ca1708.md)|Identyfikatory przestrzeni nazw, typów, elementów członkowskich i parametry nie mogą się różnić jedynie wielkością liter, ponieważ języki dla środowiska uruchomieniowego języka wspólnego nie muszą rozróżniać wielkości liter.|
|[CA1715: Identyfikatory powinny mieć poprawny prefiks](../code-quality/ca1715.md)|Nazwa widocznego na zewnątrz interfejsu nie zaczyna się od wielkiej litery "I".  Nazwa parametru typu ogólnego na widocznym zewnętrznie typie lub metodzie nie zaczyna się od wielkiej litery "T".|
|[CA1720: Identyfikatory nie powinny zawierać nazw typów](../code-quality/ca1720.md)|Nazwa parametru w widocznym na zewnątrz elemencie członkowskim zawiera nazwę typu danych lub nazwa widocznego na zewnątrz elementu członkowskiego zawiera specyficzną dla języka nazwę typu danych.|
|[CA1722: Identyfikatory nie powinny mieć nieprawidłowych prefiksów](../code-quality/ca1722.md)|Zgodnie z konwencją, tylko niektóre elementy programowania mają nazwy rozpoczynające się od określonego prefiksu.|
|[CA1711: Identyfikatory nie powinny mieć nieprawidłowych sufiksów](../code-quality/ca1711.md)|Według konwencji nazwy typów, które rozszerzają pewne typy podstawowe lub implementują dane interfejsy lub typy pochodzące z tych typów, powinny kończyć się określonym zarezerwowanym sufiksem. Inne nazwy typów nie powinny używać tych zarezerwowanych sufiksów.|
|[CA1717: Tylko wyliczenia z atrybutem Flags powinny mieć nazwy w liczbie mnogiej](../code-quality/ca1717.md)|Zgodnie z konwencjami nazewnictwa, nazwa w liczbie mnogiej dla wyliczenia wskazuje, że w tym samym czasie można określić więcej niż jedną wartość wyliczenia.|
|[CA1725: Nazwy parametrów powinny być zgodne z deklaracją podstawową](../code-quality/ca1725.md)|Spójne nazywanie parametrów w zastąpieniu hierarchii zwiększa użyteczność zastąpienia metody. Jeśli nazwa parametru w metodzie pochodnej różni się od nazwy podstawowej deklaracji, może nie być jasne, czy metoda jest zastąpieniem metody podstawowej, czy też nowym przeciążeniem metody.|
|[CA1719: Nazwy parametrów nie powinny być zgodne z nazwami składowych](../code-quality/ca1719.md)|Nazwa parametru powinna komunikować znaczenie parametru, a nazwa elementu członkowskiego powinna komunikować znaczenie elementu członkowskiego. W projekcie rzadko są one takie same. Nazywanie parametru tak samo jak nazwa jego elementu członkowskiego jest nieintuicyjne i utrudnia korzystanie z biblioteki.|
|[CA1701: Wyrazy złożone ciągu zasobu powinny mieć prawidłową wielkość liter](../code-quality/ca1701.md)|Każdy wyraz w ciągu zasobu jest podzielony na tokeny, które są oparte na wielkości liter. Każda ciągła kombinacja dwóch tokenów jest sprawdzana przez bibliotekę sprawdzania pisowni firmy Microsoft. Jeżeli zostanie rozpoznana, dane słowo powoduje naruszenie reguły.|
|[CA1703: Pisownia ciągów zasobów powinna być poprawna](../code-quality/ca1703.md)|Ciąg zasobu zawiera jeden lub więcej wyrazów, które nie są rozpoznane przez bibliotekę sprawdzania pisowni Microsoft.|
|[CA1724: Nazwy typów nie powinny być takie same jak nazwy przestrzeni nazw](../code-quality/ca1724.md)|Nazwy typów nie powinny być zgodne z nazwami przestrzeni nazw platformy .NET. Naruszenie tej reguły może zmniejszyć użyteczność biblioteki.|
|[CA1707: Identyfikatory nie powinny zawierać znaków podkreślenia](../code-quality/ca1707.md)|Przez konwencję identyfikatory nazw nie zawierają znaku podkreślenia (_). Ta reguła sprawdza przestrzenie nazw, typy, elementy członkowskie i parametry.|
|[CA1721: Nazwy właściwości nie powinny być takie same jak nazwy metod Get](../code-quality/ca1721.md)|Nazwa publicznego lub chronionego elementu członkowskiego zaczyna się od „Get” i odpowiada nazwie właściwości publicznej lub chronionej. Metody „Get” i właściwości powinny mieć nazwy, które wyraźnie odróżniają ich funkcje.|
|[CA1716: Identyfikatory nie powinny być zgodne ze słowami kluczowymi](../code-quality/ca1716.md)|Przestrzeń nazw lub nazwa typu odpowiada zastrzeżonym słowom kluczowym w języku programowania. Identyfikatory przestrzeni nazw i typów nie powinny być zgodne ze słowami kluczowymi, które są definiowane przez języki dla środowiska uruchomieniowego języka wspólnego.|
|[CA1726: Używaj preferowanych terminów](../code-quality/ca1726.md)|Nazwa widocznego na zewnątrz identyfikatora zawiera termin, dla którego istnieje alternatywny, preferowany zamiennik. Alternatywnie nazwa zawiera określenie „Flag” lub „Flags”.|
|[CA1709: Identyfikatory powinny mieć prawidłową wielkość liter](../code-quality/ca1709.md)|Według Konwencji nazwy parametrów używają notacji CamelCase wielkości liter, a przestrzeń nazw, typ i nazwy elementów członkowskich używają wielkości liter w Pascalu.|
|[CA1702: W wyrazach złożonych należy poprawnie używać wielkości liter](../code-quality/ca1702.md)|Nazwa identyfikatora zawiera wiele wyrazów i co najmniej jeden z nich wydaje się wyrazem złożonym, w którym wielkość liter nie jest poprawna.|
|[CA1712: Nie dodawaj prefiksu z nazwą typu do wartości wyliczeniowych](../code-quality/ca1712.md)|Nazwy elementów członkowskich wyliczenia nie są poprzedzone nazwą typu, ponieważ oczekuje się, że informacje o typie są udostępniane przez narzędzia deweloperskie.|
|[CA1710: Identyfikatory powinny mieć poprawny sufiks](../code-quality/ca1710.md)|Według Konwencji nazwy typów, które poszerzają pewne typy podstawowe lub implementują określone interfejsy lub typy pochodzące z tych typów, mają sufiks skojarzony z typem podstawowym lub interfejsem.|
