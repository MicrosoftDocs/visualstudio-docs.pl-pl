---
title: Globalizacja — Ostrzeżenia
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.globalizationrules
helpviewer_keywords:
- warnings, globalization
- globalization warnings
- globalization [Visual Studio], warnings
- managed code analysis warnings, globalization warnings
ms.assetid: a8d12d41-14bf-4b43-af24-168312d7c390
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fecc46ac6e1221cb547e98711d95b743010d4c6c
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75587579"
---
# <a name="globalization-warnings"></a>Globalizacja — Ostrzeżenia
Ostrzeżenia globalizacji obsługują biblioteki i aplikacje gotowe do zastosowania na całym świecie.

## <a name="in-this-section"></a>W tej sekcji

|Reguła|Opis|
|----------|-----------------|
|[CA1300: Określ wyliczenie MessageBoxOptions](../code-quality/ca1300.md)|Aby poprawnie wyświetlić okno komunikatu dla kultur stosujących pismo od prawej do lewej, członkowie RightAlign i RtlReading wyliczenia MessageBoxOptions muszą być przekazani do metody Show.|
|[CA1301: Unikaj duplikowania akceleratorów](../code-quality/ca1301.md)|Klucz dostępu, znany również jako akcelerator, umożliwia dostęp z klawiatury do formantu za pomocą klawisza ALT. Gdy wiele kontrolek ma zduplikowane klucze dostępu, zachowanie klucza dostępu nie jest dobrze zdefiniowane.|
|[CA1302: Nie umieszczaj w kodzie na stałe ciągów specyficznych dla ustawień regionalnych](../code-quality/ca1302.md)|Wyliczenie System.Environment.SpecialFolder zawiera elementy, które odwołują się do folderów specjalnych systemu. Lokalizacje tych folderów mogą mieć różne wartości w poszczególnych systemach operacyjnych; użytkownik może zmienić niektóre z tych lokalizacji; lokalizacje są zlokalizowane. Metoda Environment. GetFolderPath zwraca lokalizacje skojarzone ze środowiskiem. Wyliczenie SpecialFolder, zlokalizowane i odpowiednie dla aktualnie uruchomionego komputera.|
|[CA1303: Nie przekazuj literałów jako parametrów zlokalizowanych](../code-quality/ca1303.md)|Metoda widoczna na zewnątrz przekazuje literał ciągu jako parametr do konstruktora lub metody .NET, a ten ciąg powinien być Lokalizowalny.|
|[CA1304: Określ klasę CultureInfo](../code-quality/ca1304.md)|Metoda lub konstruktor wywołuje członka mającego przeciążenie, które akceptuje parametr System.Globalization.CultureInfo i metodę lub konstruktor niewywołujący przeciążenia, które wymaga parametru CultureInfo. Kiedy obiekt CultureInfo lub System.IFormatProvider nie jest podany, domyślna wartość, która jest dostarczana przez członka przeciążonego, może nie wywoływać oczekiwanego efektu we wszystkich ustawieniach regionalnych.|
|[CA1305: Określ interfejs IFormatProvider](../code-quality/ca1305.md)|Metoda lub konstruktor wywołują jednego lub kilku członków, którzy mają przeciążenia akceptujące parametr System.IFormatProvider, i metody lub konstruktora, który nie wywołuje przeciążenia przyjmującego parametr IFormatProvider. Kiedy obiekt System.Globalization.CultureInfo lub IFormatProvider nie jest podany, domyślna wartość przekazywana przez członka przeciążonego może nie wywoływać oczekiwanego efektu we wszystkich ustawieniach regionalnych.|
|[CA1306: Określ ustawienia regionalne dla typów danych](../code-quality/ca1306.md)|Ustawienia regionalne określą specyficzne dla kultur elementy prezentacji danych, takie jak formatowanie, które jest używane dla wartości liczbowych, symbole walut i porządek sortowania. Podczas tworzenia elementu DataTable lub DataSet należy jawnie ustawić ustawienia regionalne.|
|[CA1307: Określ wyliczenie StringComparison](../code-quality/ca1307.md)|Operacja porównania ciągu używa przeciążenia metody, które nie ustawia parametru StringComparison.|
|[CA1308: Normalizuj ciągi do postaci zapisanej wielkimi literami](../code-quality/ca1308.md)|Ciągi powinny być znormalizowane do użycia wielkich liter. Małe grupy znaków nie mogą wykonywać rund, gdy są one konwertowane na małe litery.|
|[CA1309: Używaj wyliczenia StringComparison stosującego reguły sortowania oparte na wartości](../code-quality/ca1309.md)|Operacja porównania ciągu, która jest nielingwistyczna, nie ustawia parametru StringComparison na Ordinal lub OrdinalIgnoreCase. Poprzez jawne ustawienie parametru na StringComparison.Ordinal lub StringComparison.OrdinalIgnoreCase kod często zaczyna działać szybciej, staje się bardziej poprawny i niezawodny.|
|[CA2101: Określ marshaling dla argumentów ciągu wywołania P/Invoke](../code-quality/ca2101.md)|Element członkowski wywołania platformy zezwala na częściowo zaufane obiekty wywołujące, ma parametr String i nie jest jawnie zorganizowany przez ciąg. Może to spowodować potencjalne luki w zabezpieczeniach.|
