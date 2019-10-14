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
ms.openlocfilehash: 29ace36d35b31eeb3635d06d6244ac6fe0897ec2
ms.sourcegitcommit: 034c503ae04e22cf840ccb9770bffd012e40fb2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/14/2019
ms.locfileid: "72305661"
---
# <a name="performance-warnings"></a>Wydajność — Ostrzeżenia
Ostrzeżenia dotyczące wydajności obsługują biblioteki i aplikacje o wysokiej wydajności.

## <a name="in-this-section"></a>W tej sekcji

| Reguła | Opis |
| - | - |
| [CA1800: Nie należy rzutować niepotrzebnie @ no__t-0 | Zduplikowane rzutowania zmniejszają wydajność, zwłaszcza gdy rzutowania są wykonywane w niedużej iteracji. |
| [CA1801: Przejrzyj nieużywane parametry @ no__t-0 | Podpis metody zawiera parametr, który nie jest używany w jej treści. |
| [CA1802: Użyj literałów, gdzie odpowiednie wartości @ no__t-0 | Pole jest zadeklarowane jako static i tylko do odczytu (Shared i ReadOnly w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) i jest inicjowane z wartością, która jest obliczanej w czasie kompilacji. Ponieważ wartość, która jest przypisana do pola docelowego jest obliczana w czasie kompilacji, zmień deklarację na stałą (Const w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) tak, aby wartość jest obliczana w czasie kompilacji, a nie w czasie wykonywania. |
| [CA1804: Usuń nieużywane elementy lokalne @ no__t-0 | Nieużywane zmienne lokalne i niepotrzebne przydziały zwiększają rozmiar zestawu i zmniejszają wydajność. |
| [CA1806: Nie Ignoruj wyników metody @ no__t-0 | Nowy obiekt jest tworzony, ale nigdy nie jest używany lub metoda, która tworzy i zwraca nowy ciąg, jest wywoływana, a nowy ciąg nigdy nie jest używany lub metoda Component Object Model (COM) lub P/Invoke zwraca wynik HRESULT lub kod błędu, który nigdy nie jest używany. |
| [CA1809: Unikaj nadmiernych wartości lokalnych @ no__t-0 | Typowa optymalizacja wydajności polega na przechowywaniu wartości w rejestrze procesora zamiast w pamięci, co określa się jako „rejestrowanie wartości”.  Aby zwiększyć prawdopodobieństwo, że wszystkie zmienne lokalne są przechowywane w rejestrze procesora, należy ograniczyć liczbę zmiennych lokalnych do 64. |
| [CA1810: Inicjuj wbudowane pola typu odwołania @ no__t-0 | Podczas gdy typ deklaruje jawny, statyczny konstruktor, kompilator just in time (JIT) do każdej metody statycznej dodaje sprawdzenie i konstruktora wystąpienia, aby upewnić się, że konstruktor statyczny został wcześniej wywołany. Sprawdzenia konstruktora statycznego mogą obniżyć wydajność. |
| [CA1811: Unikaj niewywołanego kodu prywatnego @ no__t-0 | Prywatny lub wewnętrzny (na poziomie zestawu) nie ma elementów wywołujących w zestawie, nie jest wywoływany przez środowisko uruchomieniowe języka wspólnego i nie jest wywoływany przez delegata. |
| [CA1812: Unikaj klas wewnętrznych bez wystąpień @ no__t-0 | Wystąpienie typu na poziomie zestawu nie jest tworzone przez kod w zestawie. |
| [CA1813: Unikaj niezapieczętowanych atrybutów @ no__t-0 | .NET oferuje metody pobierania atrybutów niestandardowych. Domyślnie te metody wyszukują hierarchie dziedziczenia atrybutu. Plombowanie atrybutu eliminuje wyszukiwanie przez hierarchię dziedziczenia i może zwiększyć wydajność. |
| [CA1814: Preferuj tablice nieregularne dla wielowymiarowego @ no__t-0 | Nieregularna tablica to ta, której elementy są tablicami. Tablice, które składają się na elementy, mogą mieć różne rozmiary, co może spowodować mniejsze ilości wolnego miejsca dla niektórych zestawów danych. |
| [CA1815: Przesłoń metodę Equals i operator Equals w typach wartości @ no__t-0 | Dla typów wartości dziedziczona implementacja operatora Equas wykorzystuje bibliotekę odbić i porównuje zawartość wszystkich pól. Odbicie jest obliczeniowo kosztowne, a porównanie równości każdego pola może być niepotrzebne. Jeśli można się spodziewać, że użytkownicy będą porównywać lub sortować wystąpienia lub używać wystąpień jako kluczy tabel haszowanych, typ wartości powinien implementować Equals. |
| [CA1816: Wywołaj metodę GC. SuppressFinalize prawidłowo @ no__t-0 | Metoda, która jest implementacją Dispose, nie wywołuje GC. SuppressFinalize lub metoda, która nie jest implementacją operacji Dispose. SuppressFinalize lub metoda wywołuje metodę GC. SuppressFinalize i przekazuje coś innego niż to (mi w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). |
| [CA1819: Właściwości nie powinny zwracać tablic @ no__t-0 | Tablice zwracane przez właściwości nie są chronione przed zapisem, nawet jeśli właściwość jest tylko do odczytu. Aby zachować tablicę odporną na manipulacje, właściwość musi zwracać kopię tablicy. Zwykle użytkownicy nie rozumieją, jakie niekorzystne następstwa dla wydajności ma wywołanie takiej właściwości. |
| [CA1820: Testuj dla pustych ciągów przy użyciu długości ciągu @ no__t-0 | Porównywanie ciągów za pomocą właściwości String.Length lub metody String.IsNullOrEmpty jest znacznie szybsze niż użycie operatora Equals. |
| [CA1821: Usuń puste finalizatory @ no__t-0 | Jeśli to tylko możliwe, należy unikać finalizatorów ze względu na dodatkowe obciążenie, które bierze udział w śledzeniu okresu istnienia obiektu. Pusty finalizator wiąże się z dodatkowymi kosztami bez korzyści. |
| [CA1822: Oznacz składowe jako static @ no__t-0 | Elementy członkowskie, które nie uzyskuje dostępu do wystąpienia danych lub wywołanie metody wystąpienia mogą zostać oznaczone jako statyczne (współużytkowane w [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]). Po oznaczeniu metod jako statyczne kompilator wygeneruje niewirtualne wywołania do tych członków. To może dać wymierny zysk wydajnościowy dla kodu wrażliwego na wydajność. |
| [CA1823: Unikaj nieużywanych pól prywatnych @ no__t-0 | Zostały wykryte pola prywatne, które w zestawie nie są widoczne jako dostępne. |
| [CA1824: Oznacz zestawy atrybutem NeutralResourcesLanguageAttribute @ no__t-0 | Atrybut NeutralResourcesLanguage informuje ResourceManager języka, który był używany do wyświetlania zasobów neutralnej kultury dla zestawu. To zwiększa wydajność wyszukiwania dla pierwszego zasobu, który się ładuje i może zmniejszyć zestaw roboczy. |
| [CA1825: Unikaj alokacji tablic o zerowej długości @ no__t-0 | Inicjowanie tablicy o zerowej długości prowadzi do niepotrzebnej alokacji pamięci. Zamiast tego należy użyć statycznie przydzielonego wystąpienia pustej tablicy, wywołując <xref:System.Array.Empty%2A?displayProperty=nameWithType>. Alokacja pamięci jest współdzielona przez wszystkie wywołania tej metody. |
