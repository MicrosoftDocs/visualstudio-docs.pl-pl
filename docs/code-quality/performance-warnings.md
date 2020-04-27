---
title: Wydajność — Ostrzeżenia
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.performancerules
helpviewer_keywords:
- warnings, performance
- performance warnings
- performance, warnings
- managed code analysis warnings, performance warnings
ms.assetid: e014ac3a-02e6-46d9-942c-3491dd63782f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e578bedf3e6b784321ffb14628ebbe10bc45dc20
ms.sourcegitcommit: 93859158465eab3423a0c0435f06490f0a456a57
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2020
ms.locfileid: "82167349"
---
# <a name="performance-warnings"></a>Wydajność — Ostrzeżenia
Ostrzeżenia dotyczące wydajności obsługują biblioteki i aplikacje o wysokiej wydajności.

## <a name="in-this-section"></a>W tej sekcji

| Reguła | Opis |
| - | - |
| [CA1800: Nie przeprowadzaj niepotrzebnych operacji rzutowania](../code-quality/ca1800.md) | Zduplikowane rzutowania zmniejszają wydajność, zwłaszcza gdy rzutowania są wykonywane w niedużej iteracji. |
| [CA1801: Przejrzyj nieużywane parametry](../code-quality/ca1801.md) | Podpis metody zawiera parametr, który nie jest używany w jej treści. |
| [CA1802: Używaj literałów wszędzie, gdzie jest to odpowiednie](../code-quality/ca1802.md) | Pole jest zadeklarowane jako static i tylko do odczytu (Shared i ReadOnly [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]in) i jest inicjowane z wartością, która jest obliczanej w czasie kompilacji. Ponieważ wartość przypisana do pola Target jest obliczanej w czasie kompilacji, należy zmienić deklarację na pole const (const w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]), aby wartość była obliczana w czasie kompilacji, a nie w czasie wykonywania. |
| [CA1804: Usuń nieużywane zmienne lokalne](../code-quality/ca1804.md) | Nieużywane zmienne lokalne i niepotrzebne przydziały zwiększają rozmiar zestawu i zmniejszają wydajność. |
| [CA1806: Nie ignoruj wyników metod](../code-quality/ca1806.md) | Nowy obiekt jest tworzony, ale nigdy nie jest używany lub metoda, która tworzy i zwraca nowy ciąg, jest wywoływana, a nowy ciąg nigdy nie jest używany lub metoda Component Object Model (COM) lub P/Invoke zwraca wynik HRESULT lub kod błędu, który nigdy nie jest używany. |
| [CA1809: Unikaj zbyt wielu zmiennych lokalnych](../code-quality/ca1809.md) | Typowa optymalizacja wydajności polega na przechowywaniu wartości w rejestrze procesora zamiast w pamięci, co określa się jako „rejestrowanie wartości”.  Aby zwiększyć szansę, że wszystkie zmienne lokalne są przechowywane, Ogranicz liczbę zmiennych lokalnych do 64. |
| [CA1810: Zainicjuj wbudowane pola statyczne typu referencyjnego](../code-quality/ca1810.md) | Podczas gdy typ deklaruje jawny, statyczny konstruktor, kompilator just in time (JIT) do każdej metody statycznej dodaje sprawdzenie i konstruktora wystąpienia, aby upewnić się, że konstruktor statyczny został wcześniej wywołany. Sprawdzenia konstruktora statycznego mogą obniżyć wydajność. |
| [CA1811: Unikaj niewywołanego kodu prywatnego](../code-quality/ca1811.md) | Prywatny lub wewnętrzny (na poziomie zestawu) nie ma elementów wywołujących w zestawie, nie jest wywoływany przez środowisko uruchomieniowe języka wspólnego i nie jest wywoływany przez delegata. |
| [CA1812: Unikaj klas wewnętrznych bez wystąpień](../code-quality/ca1812.md) | Wystąpienie typu na poziomie zestawu nie jest tworzone przez kod w zestawie. |
| [CA1813: Unikaj niezapieczętowanych atrybutów](../code-quality/ca1813.md) | .NET oferuje metody pobierania atrybutów niestandardowych. Domyślnie te metody wyszukują hierarchie dziedziczenia atrybutu. Plombowanie atrybutu eliminuje wyszukiwanie przez hierarchię dziedziczenia i może zwiększyć wydajność. |
| [CA1814: Wybieraj tablice nieregularne zamiast wielowymiarowych](../code-quality/ca1814.md) | Nieregularna tablica to ta, której elementy są tablicami. Tablice, które składają się na elementy, mogą mieć różne rozmiary, co może spowodować mniejsze ilości wolnego miejsca dla niektórych zestawów danych. |
| [CA1815: Przesłoń metodę equals i operator równości dla typów wartości](../code-quality/ca1815.md) | Dla typów wartości dziedziczona implementacja operatora Equas wykorzystuje bibliotekę odbić i porównuje zawartość wszystkich pól. Odbicie jest obliczeniowo kosztowne, a porównanie równości każdego pola może być niepotrzebne. Jeśli można się spodziewać, że użytkownicy będą porównywać lub sortować wystąpienia lub używać wystąpień jako kluczy tabel haszowanych, typ wartości powinien implementować Equals. |
| [CA1816: Wywołaj poprawnie GC.SuppressFinalize](../code-quality/ca1816.md) | Metoda, która jest implementacją Dispose, nie wywołuje GC. SuppressFinalize lub metoda, która nie jest implementacją operacji Dispose. SuppressFinalize lub metoda wywołuje metodę GC. SuppressFinalize i przekazuje coś innego niż to (ja in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). |
| [CA1819: Właściwości nie powinny zwracać tablic](../code-quality/ca1819.md) | Tablice zwracane przez właściwości nie są chronione przed zapisem, nawet jeśli właściwość jest tylko do odczytu. Aby zachować tablicę odporną na manipulacje, właściwość musi zwracać kopię tablicy. Zwykle użytkownicy nie rozumieją, jakie niekorzystne następstwa dla wydajności ma wywołanie takiej właściwości. |
| [CA1820: Testuj obecność pustych ciągów przy użyciu długości ciągu](../code-quality/ca1820.md) | Porównywanie ciągów za pomocą właściwości String.Length lub metody String.IsNullOrEmpty jest znacznie szybsze niż użycie operatora Equals. |
| [CA1821: Usuwaj puste finalizatory](../code-quality/ca1821.md) | Jeśli to tylko możliwe, należy unikać finalizatorów ze względu na dodatkowe obciążenie, które bierze udział w śledzeniu okresu istnienia obiektu. Pusty finalizator wiąże się z dodatkowymi kosztami bez korzyści. |
| [CA1822: Oznaczaj składowe jako statyczne](../code-quality/ca1822.md) | Elementy członkowskie, które nie uzyskują dostępu do danych wystąpienia lub wywołania metody wystąpienia, mogą być oznaczone [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]jako statyczne (udostępnione w). Po oznaczeniu metod jako statyczne kompilator wygeneruje niewirtualne wywołania do tych członków. To może dać wymierny zysk wydajnościowy dla kodu wrażliwego na wydajność. |
| [CA1823: Unikaj nieużywanych pól prywatnych](../code-quality/ca1823.md) | Zostały wykryte pola prywatne, które w zestawie nie są widoczne jako dostępne. |
| [CA1824: Oznacz zestawy za pomocą NeutralResourcesLanguageAttribute](../code-quality/ca1824.md) | Atrybut NeutralResourcesLanguage informuje ResourceManager języka, który był używany do wyświetlania zasobów neutralnej kultury dla zestawu. To zwiększa wydajność wyszukiwania dla pierwszego zasobu, który się ładuje i może zmniejszyć zestaw roboczy. |
| [CA1825: Unikaj alokacji tablic o zerowej długości](../code-quality/ca1825.md) | Inicjowanie tablicy o zerowej długości prowadzi do niepotrzebnej alokacji pamięci. Zamiast tego należy użyć statycznie przydzielonego wystąpienia pustej <xref:System.Array.Empty%2A?displayProperty=nameWithType>tablicy przez wywołanie. Alokacja pamięci jest współdzielona przez wszystkie wywołania tej metody. |
| [CA1826: Użyj właściwości zamiast metody wyliczalnej LINQ](../code-quality/ca1826.md) | <xref:System.Linq.Enumerable>Metoda LINQ została użyta na typie, który obsługuje równoważną, wydajniejszą właściwość. |
| [CA1827: nie używaj Count/LongCount, jeśli można używać dowolnego](../code-quality/ca1827.md) | <xref:System.Linq.Enumerable.Count%2A>Metoda <xref:System.Linq.Enumerable.LongCount%2A> or została użyta <xref:System.Linq.Enumerable.Any%2A> w przypadku, gdy metoda byłaby bardziej wydajna. |
| [CA1828: nie używaj CountAsync/LongCountAsync, jeśli AnyAsync może być użyty](../code-quality/ca1828.md) | <xref:Microsoft.EntityFrameworkCore.EntityFrameworkQueryableExtensions.CountAsync%2A>Metoda <xref:Microsoft.EntityFrameworkCore.EntityFrameworkQueryableExtensions.LongCountAsync%2A> or została użyta <xref:Microsoft.EntityFrameworkCore.EntityFrameworkQueryableExtensions.AnyAsync%2A> w przypadku, gdy metoda byłaby bardziej wydajna. |
| [CA1829: Użyj właściwości length/Count zamiast metody wyliczalnej. Count](../code-quality/ca1829.md) | <xref:System.Linq.Enumerable.Count%2A>Metoda LINQ została użyta w typie, który obsługuje równoważną, `Length` wydajniejszą `Count` lub właściwość. |
