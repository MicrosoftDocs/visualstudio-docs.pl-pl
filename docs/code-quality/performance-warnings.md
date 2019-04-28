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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d44c9a4a5c59907c527c47523c6c758adaf7ee51
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62825497"
---
# <a name="performance-warnings"></a>Wydajność — Ostrzeżenia
Ostrzeżeń dotyczących wydajności obsługi bibliotek o wysokiej wydajności i aplikacji.

## <a name="in-this-section"></a>W tej sekcji

| Reguła | Opis |
| - | - |
| [CA1800: Nie Rzutuj niepotrzebnie](../code-quality/ca1800-do-not-cast-unnecessarily.md) | Zduplikowane rzutowania zmniejszają wydajność, zwłaszcza gdy rzutowania są wykonywane w niedużej iteracji. |
| [CA1801: Przejrzyj nieużywane parametry](../code-quality/ca1801-review-unused-parameters.md) | Podpis metody zawiera parametr, który nie jest używany w jej treści. |
| [CA1802: Używaj literałów wszędzie, gdzie jest to odpowiednie](../code-quality/ca1802-use-literals-where-appropriate.md) | Pole jest zadeklarowane jako statyczne i tylko do odczytu (Shared i ReadOnly w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) i jest inicjowany z wartością, która jest obliczana w czasie kompilacji. Ponieważ wartość, która jest przypisana do pola docelowego jest obliczana w czasie kompilacji, zmień deklarację na stałą (Const w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) tak, aby wartość jest obliczana w czasie kompilacji, a nie w czasie wykonywania. |
| [CA1804: Usuń nieużywane zmienne lokalne](../code-quality/ca1804-remove-unused-locals.md) | Nieużywane zmienne lokalne i niepotrzebne przydziały zwiększają rozmiar zestawu i zmniejszają wydajność. |
| [CA1806: Nie Ignoruj wyników metod](../code-quality/ca1806-do-not-ignore-method-results.md) | Nowy obiekt zostanie utworzony, ale nigdy nie jest używany, wywoływana jest metoda, która tworzy i zwraca nowy ciąg i nowy ciąg nigdy nie jest używany lub Component Object Model (COM) lub P/Invoke, metoda zwraca wartość HRESULT lub kod błędu, który nie jest nigdy używane. |
| [CA1809: Unikaj zbyt wielu zmiennych lokalnych](../code-quality/ca1809-avoid-excessive-locals.md) | Typowa optymalizacja wydajności polega na przechowywaniu wartości w rejestrze procesora zamiast w pamięci, co określa się jako „rejestrowanie wartości”.  Aby zwiększyć prawdopodobieństwo, że wszystkie zmienne lokalne są przechowywane w rejestrze procesora, należy ograniczyć liczbę zmiennych lokalnych do 64. |
| [CA1810: Inicjowanie pola statyczne typu referencyjnego śródwierszowo](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md) | Podczas gdy typ deklaruje jawny, statyczny konstruktor, kompilator just in time (JIT) do każdej metody statycznej dodaje sprawdzenie i konstruktora wystąpienia, aby upewnić się, że konstruktor statyczny został wcześniej wywołany. Sprawdzenia konstruktora statycznego mogą obniżyć wydajność. |
| [CA1811: Unikaj niewywołanego kodu prywatnego](../code-quality/ca1811-avoid-uncalled-private-code.md) | Prywatne lub wewnętrzne członek (w poziomie zestawu) nie ma obiektów wywołujących w zestawie, nie jest wywoływany przez środowisko uruchomieniowe języka wspólnego i nie jest wywoływany przez delegata. |
| [CA1812: Unikaj klas wewnętrznych bez wystąpień](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md) | Wystąpienie typu na poziomie zestawu nie jest tworzone przez kod w zestawie. |
| [CA1813: Unikaj niezapieczętowanych atrybutów](../code-quality/ca1813-avoid-unsealed-attributes.md) | Biblioteka klas .NET Framework dostarcza metody do pobierania atrybutów niestandardowych. Domyślnie te metody wyszukują hierarchie dziedziczenia atrybutu. Plombowanie atrybutu eliminuje wyszukiwanie przez hierarchię dziedziczenia i może zwiększyć wydajność. |
| [CA1814: Preferuj Tablice nieregularne wielowymiarowych](../code-quality/ca1814-prefer-jagged-arrays-over-multidimensional.md) | Nieregularna tablica to ta, której elementy są tablicami. Tablice, które tworzą elementy mogą być różne rozmiary, które mogą skutkować zapewnia większą oszczędność miejsca dla niektórych zestawów danych. |
| [CA1815: Przesłoń metodę equals i operator równości dla typów wartości](../code-quality/ca1815-override-equals-and-operator-equals-on-value-types.md) | Dla typów wartości dziedziczona implementacja operatora Equas wykorzystuje bibliotekę odbić i porównuje zawartość wszystkich pól. Odbicie jest obliczeniowo kosztowne, a porównanie równości każdego pola może być niepotrzebne. Jeśli można się spodziewać, że użytkownicy będą porównywać lub sortować wystąpienia lub używać wystąpień jako kluczy tabel haszowanych, typ wartości powinien implementować Equals. |
| [CA1816: Wywołaj GC. SuppressFinalize poprawnie](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md) | Metoda, która jest implementacją Dispose, nie wywołuje GC. SuppressFinalize lub metody, która nie jest implementacją Dispose, wywołuje GC. SuppressFinalize lub metoda wywołuje GC. SuppressFinalize i przekazuje na coś innego niż to (Me w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). |
| [CA1819: Właściwości nie powinny zwracać tablic](../code-quality/ca1819-properties-should-not-return-arrays.md) | Tablice, które są zwracane przez właściwości nie są zabezpieczony przed zapisem, nawet jeśli właściwość jest tylko do odczytu. Aby zachować tablicę odporną na manipulacje, właściwość musi zwracać kopię tablicy. Zwykle użytkownicy nie rozumieją, jakie niekorzystne następstwa dla wydajności ma wywołanie takiej właściwości. |
| [CA1820: Testuj obecność pustych ciągów przy użyciu długości ciągu](../code-quality/ca1820-test-for-empty-strings-using-string-length.md) | Porównywanie ciągów za pomocą właściwości String.Length lub metody String.IsNullOrEmpty jest znacznie szybsze niż użycie operatora Equals. |
| [CA1821: Usuwaj puste finalizatory](../code-quality/ca1821-remove-empty-finalizers.md) | Jeśli to tylko możliwe, należy unikać finalizatorów ze względu na dodatkowe obciążenie, które bierze udział w śledzeniu okresu istnienia obiektu. Pusty finalizator powoduje dodano obciążenie bez żadnych korzyści. |
| [CA1822: Oznaczaj składowe jako statyczne](../code-quality/ca1822-mark-members-as-static.md) | Elementy członkowskie, które nie uzyskuje dostępu do wystąpienia danych lub wywołanie metody wystąpienia mogą zostać oznaczone jako statyczne (współużytkowane w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). Po oznaczeniu metod jako statyczne kompilator wygeneruje niewirtualne wywołania do tych członków. To może dać wymierny zysk wydajnościowy dla kodu wrażliwego na wydajność. |
| [CA1823: Unikaj nieużywanych pól prywatnych](../code-quality/ca1823-avoid-unused-private-fields.md) | Zostały wykryte pola prywatne, które w zestawie nie są widoczne jako dostępne. |
| [CA1824: Oznacz zestawy za pomocą atrybutu NeutralResourcesLanguageAttribute](../code-quality/ca1824-mark-assemblies-with-neutralresourceslanguageattribute.md) | Atrybut NeutralResourcesLanguage informuje ResourceManager języka, który był używany do wyświetlania zasobów neutralnej kultury dla zestawu. To zwiększa wydajność wyszukiwania dla pierwszego zasobu, który się ładuje i może zmniejszyć zestaw roboczy. |
