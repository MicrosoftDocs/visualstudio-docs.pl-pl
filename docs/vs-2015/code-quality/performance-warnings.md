---
title: Ostrzeżenia dotyczące wydajności | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.performancerules
helpviewer_keywords:
- warnings, performance
- performance warnings
- performance, warnings
- managed code analysis warnings, performance warnings
ms.assetid: e014ac3a-02e6-46d9-942c-3491dd63782f
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 9f1b8ae5f4133605bd6488baa715a451467237f9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72608719"
---
# <a name="performance-warnings"></a>Wydajność — Ostrzeżenia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ostrzeżenia dotyczące wydajności obsługują biblioteki i aplikacje o wysokiej wydajności.

## <a name="in-this-section"></a>W tej sekcji

|Reguła|Opis|
|----------|-----------------|
|[CA1800: Nie rzutuj niepotrzebnie](../code-quality/ca1800-do-not-cast-unnecessarily.md)|Zduplikowane rzutowania zmniejszają wydajność, zwłaszcza gdy rzutowania są wykonywane w niedużej iteracji.|
|[CA1801: Dokonaj przeglądu nieużywanych parametrów](../code-quality/ca1801-review-unused-parameters.md)|Podpis metody zawiera parametr, który nie jest używany w jej treści.|
|[CA1802: Używaj literałów w odpowiednich miejscach](../code-quality/ca1802-use-literals-where-appropriate.md)|Pole jest zadeklarowane jako static i tylko do odczytu (Shared i ReadOnly in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ) i jest inicjowane z wartością, która jest obliczanej w czasie kompilacji. Ponieważ wartość przypisana do pola Target jest obliczanej w czasie kompilacji, należy zmienić deklarację na pole const (const w), [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] aby wartość była obliczana w czasie kompilacji, a nie w czasie wykonywania.|
|[CA1804: Usuwaj nieużywane zmienne lokalne](../code-quality/ca1804-remove-unused-locals.md)|Nieużywane zmienne lokalne i niepotrzebne przydziały zwiększają rozmiar zestawu i zmniejszają wydajność.|
|[CA1806: Nie ignoruj wyników metod](../code-quality/ca1806-do-not-ignore-method-results.md)|Nowy obiekt jest tworzony, ale nigdy nie jest używany lub metoda, która tworzy i zwraca nowy ciąg, jest wywoływana, a nowy ciąg nigdy nie jest używany lub metoda Component Object Model (COM) lub P/Invoke zwraca wynik HRESULT lub kod błędu, który nigdy nie jest używany.|
|[CA1809: Unikaj zbyt wielu zmiennych lokalnych](../code-quality/ca1809-avoid-excessive-locals.md)|Typowa optymalizacja wydajności polega na przechowywaniu wartości w rejestrze procesora zamiast w pamięci, co określa się jako „rejestrowanie wartości”.  Aby zwiększyć szansę, że wszystkie zmienne lokalne są przechowywane, Ogranicz liczbę zmiennych lokalnych do 64.|
|[CA1810: Inicjuj pola statyczne typu referencyjnego śródwierszowo](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)|Podczas gdy typ deklaruje jawny, statyczny konstruktor, kompilator just in time (JIT) do każdej metody statycznej dodaje sprawdzenie i konstruktora wystąpienia, aby upewnić się, że konstruktor statyczny został wcześniej wywołany. Sprawdzenia konstruktora statycznego mogą obniżyć wydajność.|
|[CA1811: Unikaj niewywołanego kodu prywatnego](../code-quality/ca1811-avoid-uncalled-private-code.md)|Prywatny lub wewnętrzny (na poziomie zestawu) nie ma elementów wywołujących w zestawie, nie jest wywoływany przez środowisko uruchomieniowe języka wspólnego i nie jest wywoływany przez delegata.|
|[CA1812: Unikaj klas wewnętrznych bez wystąpień](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)|Wystąpienie typu na poziomie zestawu nie jest tworzone przez kod w zestawie.|
|[CA1813: Unikaj niezapieczętowanych atrybutów](../code-quality/ca1813-avoid-unsealed-attributes.md)|[!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]Biblioteka klas zawiera metody pobierania atrybutów niestandardowych. Domyślnie te metody wyszukują hierarchie dziedziczenia atrybutu. Plombowanie atrybutu eliminuje wyszukiwanie przez hierarchię dziedziczenia i może zwiększyć wydajność.|
|[CA1814: Wybieraj tablice nieregularne zamiast wielowymiarowych](../code-quality/ca1814-prefer-jagged-arrays-over-multidimensional.md)|Nieregularna tablica to ta, której elementy są tablicami. Tablice, które składają się na elementy, mogą mieć różne rozmiary, co może spowodować mniejsze ilości wolnego miejsca dla niektórych zestawów danych.|
|[CA1815: Przesłaniaj metodę equals i operator równości w typach wartości](../code-quality/ca1815-override-equals-and-operator-equals-on-value-types.md)|Dla typów wartości dziedziczona implementacja operatora Equas wykorzystuje bibliotekę odbić i porównuje zawartość wszystkich pól. Odbicie jest obliczeniowo kosztowne, a porównanie równości każdego pola może być niepotrzebne. Jeśli można się spodziewać, że użytkownicy będą porównywać lub sortować wystąpienia lub używać wystąpień jako kluczy tabel haszowanych, typ wartości powinien implementować Equals.|
|[CA1816: Poprawnie wywołaj metodę GC.SuppressFinalize](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)|Metoda, która jest implementacją Dispose, nie wywołuje GC. SuppressFinalize lub metoda, która nie jest implementacją operacji Dispose. SuppressFinalize lub metoda wywołuje metodę GC. SuppressFinalize i przekazuje coś innego niż to (ja in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ).|
|[CA1819: Właściwości nie powinny zwracać tablic](../code-quality/ca1819-properties-should-not-return-arrays.md)|Tablice zwracane przez właściwości nie są chronione przed zapisem, nawet jeśli właściwość jest tylko do odczytu. Aby zachować tablicę odporną na manipulacje, właściwość musi zwracać kopię tablicy. Zwykle użytkownicy nie rozumieją, jakie niekorzystne następstwa dla wydajności ma wywołanie takiej właściwości.|
|[CA1820: Testuj obecność pustych ciągów przy użyciu długości ciągu](../code-quality/ca1820-test-for-empty-strings-using-string-length.md)|Porównywanie ciągów za pomocą właściwości String.Length lub metody String.IsNullOrEmpty jest znacznie szybsze niż użycie operatora Equals.|
|[CA1821: Usuwaj puste finalizatory](../code-quality/ca1821-remove-empty-finalizers.md)|Jeśli to tylko możliwe, należy unikać finalizatorów ze względu na dodatkowe obciążenie, które bierze udział w śledzeniu okresu istnienia obiektu. Pusty finalizator wiąże się z dodatkowymi kosztami bez korzyści.|
|[CA1822: Oznaczaj składowe jako statyczne](../code-quality/ca1822-mark-members-as-static.md)|Elementy członkowskie, które nie uzyskują dostępu do danych wystąpienia lub wywołania metody wystąpienia, mogą być oznaczone jako statyczne (udostępnione w [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ). Po oznaczeniu metod jako statyczne kompilator wygeneruje niewirtualne wywołania do tych członków. To może dać wymierny zysk wydajnościowy dla kodu wrażliwego na wydajność.|
|[CA1823: Unikaj nieużywanych pól prywatnych](../code-quality/ca1823-avoid-unused-private-fields.md)|Zostały wykryte pola prywatne, które w zestawie nie są widoczne jako dostępne.|
|[CA1824: Oznaczaj zestawy za pomocą atrybutu NeutralResourcesLanguageAttribute](../code-quality/ca1824-mark-assemblies-with-neutralresourceslanguageattribute.md)|Atrybut NeutralResourcesLanguage informuje ResourceManager języka, który był używany do wyświetlania zasobów neutralnej kultury dla zestawu. To zwiększa wydajność wyszukiwania dla pierwszego zasobu, który się ładuje i może zmniejszyć zestaw roboczy.|
