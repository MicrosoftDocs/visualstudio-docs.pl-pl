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
ms.openlocfilehash: 30acc1f38ea0d27a3a8245f586b3c41765330c50
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85283401"
---
# <a name="performance-warnings"></a>Wydajność — Ostrzeżenia
Ostrzeżenia dotyczące wydajności obsługują biblioteki i aplikacje o wysokiej wydajności.

## <a name="in-this-section"></a>W tej sekcji

| Reguła | Opis |
| - | - |
| [CA1800: Nie rzutuj niepotrzebnie](../code-quality/ca1800.md) | Zduplikowane rzutowania zmniejszają wydajność, zwłaszcza gdy rzutowania są wykonywane w niedużej iteracji. |
| [CA1801: Dokonaj przeglądu nieużywanych parametrów](../code-quality/ca1801.md) | Podpis metody zawiera parametr, który nie jest używany w jej treści. |
| [CA1802: Używaj literałów w odpowiednich miejscach](../code-quality/ca1802.md) | Pole jest zadeklarowane jako static i tylko do odczytu (Shared i ReadOnly in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ) i jest inicjowane z wartością, która jest obliczanej w czasie kompilacji. Ponieważ wartość przypisana do pola Target jest obliczanej w czasie kompilacji, należy zmienić deklarację na pole const (const w), [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] aby wartość była obliczana w czasie kompilacji, a nie w czasie wykonywania. |
| [CA1804: Usuwaj nieużywane zmienne lokalne](../code-quality/ca1804.md) | Nieużywane zmienne lokalne i niepotrzebne przydziały zwiększają rozmiar zestawu i zmniejszają wydajność. |
| [CA1806: Nie ignoruj wyników metod](../code-quality/ca1806.md) | Nowy obiekt jest tworzony, ale nigdy nie jest używany lub metoda, która tworzy i zwraca nowy ciąg, jest wywoływana, a nowy ciąg nigdy nie jest używany lub metoda Component Object Model (COM) lub P/Invoke zwraca wynik HRESULT lub kod błędu, który nigdy nie jest używany. |
| [CA1809: Unikaj zbyt wielu zmiennych lokalnych](../code-quality/ca1809.md) | Typowa optymalizacja wydajności polega na przechowywaniu wartości w rejestrze procesora zamiast w pamięci, co określa się jako „rejestrowanie wartości”.  Aby zwiększyć szansę, że wszystkie zmienne lokalne są przechowywane, Ogranicz liczbę zmiennych lokalnych do 64. |
| [CA1810: Inicjuj pola statyczne typu referencyjnego śródwierszowo](../code-quality/ca1810.md) | Podczas gdy typ deklaruje jawny, statyczny konstruktor, kompilator just in time (JIT) do każdej metody statycznej dodaje sprawdzenie i konstruktora wystąpienia, aby upewnić się, że konstruktor statyczny został wcześniej wywołany. Sprawdzenia konstruktora statycznego mogą obniżyć wydajność. |
| [CA1811: Unikaj niewywołanego kodu prywatnego](../code-quality/ca1811.md) | Prywatny lub wewnętrzny (na poziomie zestawu) nie ma elementów wywołujących w zestawie, nie jest wywoływany przez środowisko uruchomieniowe języka wspólnego i nie jest wywoływany przez delegata. |
| [CA1812: Unikaj klas wewnętrznych bez wystąpień](../code-quality/ca1812.md) | Wystąpienie typu na poziomie zestawu nie jest tworzone przez kod w zestawie. |
| [CA1813: Unikaj niezapieczętowanych atrybutów](../code-quality/ca1813.md) | .NET oferuje metody pobierania atrybutów niestandardowych. Domyślnie te metody wyszukują hierarchie dziedziczenia atrybutu. Plombowanie atrybutu eliminuje wyszukiwanie przez hierarchię dziedziczenia i może zwiększyć wydajność. |
| [CA1814: Wybieraj tablice nieregularne zamiast wielowymiarowych](../code-quality/ca1814.md) | Nieregularna tablica to ta, której elementy są tablicami. Tablice, które składają się na elementy, mogą mieć różne rozmiary, co może spowodować mniejsze ilości wolnego miejsca dla niektórych zestawów danych. |
| [CA1815: Przesłaniaj metodę equals i operator równości w typach wartości](../code-quality/ca1815.md) | Dla typów wartości dziedziczona implementacja operatora Equas wykorzystuje bibliotekę odbić i porównuje zawartość wszystkich pól. Odbicie jest obliczeniowo kosztowne, a porównanie równości każdego pola może być niepotrzebne. Jeśli można się spodziewać, że użytkownicy będą porównywać lub sortować wystąpienia lub używać wystąpień jako kluczy tabel haszowanych, typ wartości powinien implementować Equals. |
| [CA1816: Poprawnie wywołaj metodę GC.SuppressFinalize](../code-quality/ca1816.md) | Metoda, która jest implementacją Dispose, nie wywołuje GC. SuppressFinalize lub metoda, która nie jest implementacją operacji Dispose. SuppressFinalize lub metoda wywołuje metodę GC. SuppressFinalize i przekazuje coś innego niż to (ja in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ). |
| [CA1819: Właściwości nie powinny zwracać tablic](../code-quality/ca1819.md) | Tablice zwracane przez właściwości nie są chronione przed zapisem, nawet jeśli właściwość jest tylko do odczytu. Aby zachować tablicę odporną na manipulacje, właściwość musi zwracać kopię tablicy. Zwykle użytkownicy nie rozumieją, jakie niekorzystne następstwa dla wydajności ma wywołanie takiej właściwości. |
| [CA1820: Testuj obecność pustych ciągów przy użyciu długości ciągu](../code-quality/ca1820.md) | Porównywanie ciągów za pomocą właściwości String.Length lub metody String.IsNullOrEmpty jest znacznie szybsze niż użycie operatora Equals. |
| [CA1821: Usuwaj puste finalizatory](../code-quality/ca1821.md) | Jeśli to tylko możliwe, należy unikać finalizatorów ze względu na dodatkowe obciążenie, które bierze udział w śledzeniu okresu istnienia obiektu. Pusty finalizator wiąże się z dodatkowymi kosztami bez korzyści. |
| [CA1822: Oznaczaj składowe jako statyczne](../code-quality/ca1822.md) | Elementy członkowskie, które nie uzyskują dostępu do danych wystąpienia lub wywołania metody wystąpienia, mogą być oznaczone jako statyczne (udostępnione w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ). Po oznaczeniu metod jako statyczne kompilator wygeneruje niewirtualne wywołania do tych członków. To może dać wymierny zysk wydajnościowy dla kodu wrażliwego na wydajność. |
| [CA1823: Unikaj nieużywanych pól prywatnych](../code-quality/ca1823.md) | Zostały wykryte pola prywatne, które w zestawie nie są widoczne jako dostępne. |
| [CA1824: Oznaczaj zestawy za pomocą atrybutu NeutralResourcesLanguageAttribute](../code-quality/ca1824.md) | Atrybut NeutralResourcesLanguage informuje ResourceManager języka, który był używany do wyświetlania zasobów neutralnej kultury dla zestawu. To zwiększa wydajność wyszukiwania dla pierwszego zasobu, który się ładuje i może zmniejszyć zestaw roboczy. |
| [CA1825: Unikaj alokacji tablic o zerowej długości](../code-quality/ca1825.md) | Inicjowanie tablicy o zerowej długości prowadzi do niepotrzebnej alokacji pamięci. Zamiast tego należy użyć statycznie przydzielonego wystąpienia pustej tablicy przez wywołanie <xref:System.Array.Empty%2A?displayProperty=nameWithType> . Alokacja pamięci jest współdzielona przez wszystkie wywołania tej metody. |
| [CA1826: Użyj właściwości zamiast metody Linq Enumerable](../code-quality/ca1826.md) | <xref:System.Linq.Enumerable>Metoda LINQ została użyta na typie, który obsługuje równoważną, wydajniejszą właściwość. |
| [CA1827: Nie używaj funkcji Count/LongCount, gdy można użyć funkcji Any](../code-quality/ca1827.md) | <xref:System.Linq.Enumerable.Count%2A>Metoda or <xref:System.Linq.Enumerable.LongCount%2A> została użyta w przypadku, gdy <xref:System.Linq.Enumerable.Any%2A> Metoda byłaby bardziej wydajna. |
| [CA1828: Nie używaj funkcji CountAsync/LongCountAsync, gdy można użyć funkcji AnyAsync](../code-quality/ca1828.md) | <xref:Microsoft.EntityFrameworkCore.EntityFrameworkQueryableExtensions.CountAsync%2A>Metoda or <xref:Microsoft.EntityFrameworkCore.EntityFrameworkQueryableExtensions.LongCountAsync%2A> została użyta w przypadku, gdy <xref:Microsoft.EntityFrameworkCore.EntityFrameworkQueryableExtensions.AnyAsync%2A> Metoda byłaby bardziej wydajna. |
| [CA1829: Użyj właściwości Length/Count zamiast metody Enumerable.Count](../code-quality/ca1829.md) | <xref:System.Linq.Enumerable.Count%2A>Metoda LINQ została użyta w typie, który obsługuje równoważną, wydajniejszą `Length` lub `Count` Właściwość. |
| [CA1831: Użyj AsSpan zamiast indeksatorów opartych na zakresie, aby uzyskać ciąg, gdy jest to odpowiednie](../code-quality/ca1831.md) | W przypadku korzystania z indeksatora zakresu w ciągu i niejawnego przypisywania wartości do &lt; typu char ReadOnlySpan &gt; , Metoda <xref:System.String.Substring%2A?#System_String_Substring_System_Int32_System_Int32_> zostanie użyta zamiast <xref:System.Span%601.Slice%2A?#System_Span_1_Slice_System_Int32_System_Int32_> , która tworzy kopię żądanego fragmentu ciągu. |
| [CA1832: Użyj AsSpan lub AsMemory zamiast indeksatorów opartych na zakresie do pobierania ReadOnlySpan lub ReadOnlyMemory części tablicy](../code-quality/ca1832.md) | W przypadku korzystania z indeksatora zakresu w tablicy i niejawnego przypisywania wartości <xref:System.ReadOnlySpan%601> do <xref:System.ReadOnlyMemory%601> typu lub, Metoda <xref:System.Runtime.CompilerServices.RuntimeHelpers.GetSubArray%2A> zostanie użyta zamiast <xref:System.Span%601.Slice%2A?#System_Span_1_Slice_System_Int32_System_Int32_> , która tworzy kopię żądanego fragmentu tablicy. |
| [CA1833: Użyj AsSpan lub AsMemory zamiast indeksatorów opartych na zakresie w celu uzyskania fragmentu lub pamięci tablicy](../code-quality/ca1833.md) | W przypadku korzystania z indeksatora zakresu w tablicy i niejawnego przypisywania wartości <xref:System.Span%601> do <xref:System.Memory%601> typu lub, Metoda <xref:System.Runtime.CompilerServices.RuntimeHelpers.GetSubArray%2A> zostanie użyta zamiast <xref:System.Span%601.Slice%2A?#System_Span_1_Slice_System_Int32_System_Int32_> , która tworzy kopię żądanego fragmentu tablicy. |
| [CA1835: Preferuj przeciążenia oparte na Memory' dla elementu "ReadAsync" i "WriteAsync"](../code-quality/ca1835.md) | Element "Stream" ma Przeciążenie "ReadAsync", które przyjmuje &lt; &gt; jako pierwszy argument "bajt pamięci", i Przeciążenie "WriteAsync", które pobiera "ReadOnlyMemory &lt; Byte &gt; " jako pierwszy argument. Preferuj wywoływanie przeciążeń opartych na pamięci, co jest bardziej wydajne. |
