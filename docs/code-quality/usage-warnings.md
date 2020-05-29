---
title: 'Wykorzystanie — Ostrzeżenia '
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.usagerules
helpviewer_keywords:
- warnings, usage
- managed code analysis warnings, usage warnings
- usage warnings
ms.assetid: fe7dc2a3-289d-4bf7-a1e4-0947a81287c4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 01dfa23896f006dbf904a3e097e0d6fa296e0361
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2020
ms.locfileid: "84184578"
---
# <a name="usage-warnings"></a>Wykorzystanie — Ostrzeżenia 

Ostrzeżenia dotyczące użycia obsługują poprawne użycie platformy .NET.

## <a name="in-this-section"></a>W tej sekcji

|Reguła|Opis|
|----------|-----------------|
|[CA1801: Dokonaj przeglądu nieużywanych parametrów](../code-quality/ca1801.md)|Podpis metody zawiera parametr, który nie jest używany w jej treści.|
|[CA1806: Nie ignoruj wyników metod](../code-quality/ca1806.md)|Nowy obiekt jest tworzony, ale nigdy nie jest używany; albo metoda, która tworzy i zwraca nowy ciąg, jest wywoływana, ale nowy ciąg nigdy nie jest używany; albo metody COM lub P/Invoke zwracają HRESULT lub kod błędu, który nigdy nie jest używany.|
|[CA1816: Poprawnie wywołaj metodę GC.SuppressFinalize](../code-quality/ca1816.md)|Metoda, która jest implementacją Dispose, nie wywołuje GC. SuppressFinalize lub metoda, która nie jest implementacją operacji Dispose. SuppressFinalize lub metoda wywołuje metodę GC. SuppressFinalize i przekazuje coś innego niż to (mi w Visual Basic).|
|[CA2200: Ponowie zgłoś wyjątek, aby zachować szczegóły stosu](../code-quality/ca2200.md)|Wyjątek jest zgłaszany ponownie i jest on jawnie określony w instrukcji „throw”. Jeśli wyjątek jest zgłaszany ponownie przez określenie wyjątku w instrukcji „throw”, lista wywołań metod między pierwotną metodą, która zgłosiła wyjątek, a bieżącą zostanie utracona.|
|[CA2201: Nie zgłaszaj wyjątków o zastrzeżonych typach](../code-quality/ca2201.md)|Powoduje to, że oryginalny błąd trudno wykryć i debugować.|
|[CA2202: Nie likwiduj obiektów wielokrotnie](../code-quality/ca2202.md)|Implementacja metody zawiera ścieżki kodu, które powodują wielokrotne wywołania do System.IDisposable.Dispose lub równoważnika (na przykład użycie metody Close() na niektórych typach) dla tego samego obiektu.|
|[CA2204: Pisownia literałów powinna być poprawna](../code-quality/ca2204.md)|Ciąg literału w treści metody zawiera jeden lub więcej wyrazów, które nie są rozpoznawane przez bibliotekę sprawdzania pisowni Microsoft.|
|[CA2205: Użyj zarządzanych odpowiedników funkcji API Win32](../code-quality/ca2205.md)|Zdefiniowana jest metoda Invoke platformy i dostępna jest metoda .NET z równoważną funkcjonalnością.|
|[CA2207: Pola statyczne typu wartości inicjuj bezpośrednio](../code-quality/ca2207.md)|Typ wartości deklaruje jawny, statyczny konstruktor. Aby naprawić naruszenie tej zasady, zainicjuj wszystkie dane statyczne, gdy jest on zadeklarowany, i usuń konstruktor statyczny.|
|[CA2208: Poprawnie twórz wystąpienia wyjątków argumentów](../code-quality/ca2208.md)|Wywołanie odnosi się do domyślnego (bezparametrowego) konstruktora typu wyjątku, który jest elementem ArgumentException lub od niego pochodzi, albo niepoprawny argument ciągu jest przekazywany do sparametryzowania konstruktora typu wyjątku lub pochodzi od elementu ArgumentException.|
|[CA2211: Pola niebędące stałymi nie powinny być widoczne](../code-quality/ca2211.md)|Pola statyczne, które nie są stałymi lub tylko do odczytu, nie są bezpieczne wątkowo. Dostęp do takiego pola musi być starannie kontrolowany i wymaga zaawansowanych technik programowania do synchronizowania dostępu do obiektu klasy.|
|[CA2212: Nie oznaczaj składników usługi atrybutem WebMethod](../code-quality/ca2212.md)|Metoda w typie, która dziedziczy z elementu System. EnterpriseServices. ServicedComponent, jest oznaczona za pomocą elementu System. Web. Services. WebMethodAttribute. Ze względu na to, że atrybut WebMethodAttribute i metoda ServicedComponent mają sprzeczne zachowanie i wymagania dotyczące przepływu kontekstu i transakcji, w niektórych scenariuszach zachowanie metod będzie niepoprawne.|
|[CA2213: Pola możliwe do likwidacji należy likwidować](../code-quality/ca2213.md)|Typ, który implementuje element System.IDisposable, deklaruje pola takiego typu, które implementują także IDisposable. Metoda Dispose pola nie jest wywoływana przez metodę Dispose typu deklarującego.|
|[CA2214: Nie wywołuj w konstruktorach metod, które można przesłaniać](../code-quality/ca2214.md)|Gdy Konstruktor wywołuje metodę wirtualną, istnieje możliwość, że Konstruktor wystąpienia, który wywołuje metodę, nie został wykonany.|
|[CA2215: Metody Dispose powinny wywoływać metodę Dispose klasy bazowej](../code-quality/ca2215.md)|Jeśli typ dziedziczy z typu usuwalnego, musi on wywołać metodę Dispose typu podstawowego z własną metodę Dispose.|
|[CA2216: Typy możliwe do likwidacji powinny deklarować finalizator](../code-quality/ca2216.md)|Typ, który implementuje System. IDisposable i zawiera pola, które sugerują użycie niezarządzanych zasobów, nie implementuje finalizatora zgodnie z opisem przez obiekt Object. Finalize.|
|[CA2217: Nie oznaczaj typów wyliczeniowych atrybutem Flags](../code-quality/ca2217.md)|Widoczne na zewnątrz Wyliczenie jest oznaczone atrybutem FlagsAttribute i ma co najmniej jedną wartość, która nie ma uprawnień do dwóch lub kombinacji innych zdefiniowanych wartości w wyliczeniu.|
|[CA2218: Przesłaniaj metodę GetHashCode w razie przesłaniania metody Equals](../code-quality/ca2218.md)|GetHashCode zwraca wartość opartą na bieżącym wystąpieniu, które jest odpowiednie dla algorytmów wyznaczających wartości skrótu i struktur danych, takich jak tabela skrótów. Dwa obiekty, które są równe i tego samego typu, muszą zwrócić tę samą wartość skrótu.|
|[CA2219: Nie zgłaszaj wyjątków w klauzulach wyjątków](../code-quality/ca2219.md)|Kiedy wyjątek jest zgłaszany w klauzuli „finally” lub „fault”, nowy wyjątek ukrywa aktywny wyjątek. Gdy wyjątek jest zgłaszany w klauzuli „filter”, środowisko uruchomieniowe dyskretnie przechwytuje wyjątek. Powoduje to, że oryginalny błąd trudno wykryć i debugować.|
|[CA2220: Finalizatory powinny wywoływać finalizator klasy bazowej](../code-quality/ca2220.md)|Finalizacja musi być powielana w hierarchii dziedziczenia. Aby to zagwarantować, typy muszą wywołać metody Finalize swoich klas bazowych w ich własnej metodzie Finalize.|
|[CA2221: Finalizatory powinny być chronione](../code-quality/ca2221.md)|Finalizatory muszą korzystać z modyfikatora dostępu „family”.|
|[CA2222: Nie obniżaj dziedziczonej widoczności składowych](../code-quality/ca2222.md)|Nie zmieniaj modyfikatora dostępu dla dziedziczonych elementów członkowskich. Zmiana dziedziczonej składowej na prywatną nie uniemożliwia wywołującym uzyskania dostępu do implementacji metody klasy podstawowej.|
|[CA2223: Składowe powinny różnić się nie tylko zwracanym typem](../code-quality/ca2223.md)|Chociaż środowisko uruchomieniowe języka wspólnego pozwala na używanie typów zwracanych do rozróżnienia między inaczej identycznymi członkami, funkcja ta nie jest objęta specyfikacją języka wspólnego (CLS) ani nie jest wspólną cechą języków programowania .NET.|
|[CA2224: Przesłaniaj metodę equals w przypadku przeciążania operatora równości](../code-quality/ca2224.md)|Typ publiczny implementuje operator równości, ale nie przesłania obiektu Object. Equals.|
|[CA2225: Przeciążenia operatorów mają nazwane elementy alternatywne](../code-quality/ca2225.md)|Wykryto przeciążony operator i nie znaleziono metody alternatywnej o oczekiwanej nazwie. Nazwany alternatywny element członkowski zapewnia dostęp do tych samych funkcji co operator i jest udostępniany deweloperom programu w językach, które nie obsługują przeciążonych operatorów.|
|[CA2226: Operatory powinny mieć symetryczne przeciążenia](../code-quality/ca2226.md)|Typ implementuje operator równości lub nierówności i nie implementuje operatora przeciwległego.|
|[CA2227: Właściwości kolekcji powinny być tylko do odczytu](../code-quality/ca2227.md)|Właściwość zapisywalnej kolekcji pozwala użytkownikowi zastąpić kolekcję inną kolekcją. Właściwość tylko do odczytu uniemożliwia zastępowanie kolekcji, ale nadal umożliwia ustawienie poszczególnych członków.|
|[CA2228: Nie publikuj zasobów w formatach z wersji wstępnych](../code-quality/ca2228.md)|Pliki zasobów, które zostały skompilowane przy użyciu wersji wstępnych programu .NET, mogą nie być używane przez obsługiwane wersje programu .NET.|
|[CA2229: Zaimplementuj konstruktory serializacji](../code-quality/ca2229.md)|Aby naprawić naruszenie tej zasady, należy zaimplementować konstruktora serializacji. Dla zamkniętej klasy należy ustawić konstruktor prywatny; w przeciwnym razie powinien być chroniony.|
|[CA2230: Użyj elementu params dla argumentów zmiennych](../code-quality/ca2230.md)|Typ publiczny lub chroniony zawiera metodę publiczną lub chronioną, która używa wywoływania VarArgs zamiast słowa kluczowego params.|
|[CA2231: Przeciążaj operator równości w przypadku przesłaniania metody ValueType.Equals](../code-quality/ca2231.md)|Typ wartości przesłania `Object.Equals` , ale nie implementuje operatora równości.|
|[CA2232: Oznacz punkty wejścia modelu Windows Forms atrybutem STAThread](../code-quality/ca2232.md)|STAThreadAttribute wskazuje, że model wątkowości COM dla aplikacji jest jednowątkowym apartamentem. Atrybut ten musi być obecny w punkcie wejścia każdej aplikacji korzystającej z Windows Forms; jeśli zostanie pominięty, składniki systemu Windows mogą nie działać poprawnie.|
|[CA2233: Operacje nie powinny powodować przepełnienia](../code-quality/ca2233.md)|Nie należy wykonywać operacji arytmetycznych bez uprzedniego sprawdzenia operandów, aby upewnić się, że wynik operacji nie należy do zakresu możliwych wartości dla typów danych.|
|[CA2234: Przekazuj obiekty System.Uri zamiast ciągów](../code-quality/ca2234.md)|Wykonano wywołanie do metody, która ma parametr typu ciąg, którego nazwa zawiera „uri”, „URI”, „urn”, „URN”, „url” lub „URL”.  Deklarujący typ metody zawiera odpowiadające przeciążenie metody z parametrem System.Uri.|
|[CA2235: Oznacz wszystkie pola nieprzeznaczone do serializacji](../code-quality/ca2235.md)|Pola wystąpienia typu, który nie może być serializowany, jest zadeklarowany w typie, który jest możliwy do serializacji.|
|[CA2236: Wywołuj metody klasy bazowej dla typów ISerializable](../code-quality/ca2236.md)|Aby naprawić naruszenie tej zasady, należy wywołać metodę GetObjectData typu podstawowego lub konstruktor serializacji z odpowiadającej metody typu pochodnego albo konstruktora.|
|[CA2237: Oznacz typy ISerializable atrybutem SerializableAttribute](../code-quality/ca2237.md)|Aby można było rozpoznać przez środowisko uruchomieniowe języka wspólnego jako możliwy do serializacji, typy muszą być oznaczone atrybutem SerializableAttribute, nawet jeśli typ używa niestandardowej procedury serializacji za pośrednictwem implementacji interfejsu ISerializable.|
|[CA2238: Poprawnie implementuj metody serializacji](../code-quality/ca2238.md)|Metoda, która obsługuje zdarzenie szeregowania, nie ma poprawnej sygnatury zwracanego typu lub widoczności.|
|[CA2239: Udostępnij metody deserializacji dla pól opcjonalnych](../code-quality/ca2239.md)|Typ ma pole oznaczone za pomocą atrybutu System. Runtime. Serialization. OptionalFieldAttribute, a typ nie zapewnia metod obsługi zdarzeń deserializacji.|
|[CA2240: Poprawnie zaimplementuj interfejs ISerializable](../code-quality/ca2240.md)|Aby naprawić naruszenie tej zasady, należy sprawić, aby Metoda GetObjectData była widoczna i unikatowa, i upewnić się, że wszystkie pola wystąpienia są zawarte w procesie serializacji lub jawnie oznaczone atrybutem unserializationattribute.|
|[CA2241: Podaj poprawne argumenty metod formatowania](../code-quality/ca2241.md)|Argument formatu przesłany do System. String. format nie zawiera elementu formatu odpowiadającego każdemu argumentowi obiektu lub na odwrót.|
|[CA2242: Poprawnie testuj nie-liczby (NaN)](../code-quality/ca2242.md)|To wyrażenie sprawdza, czy wartość to Single.Nan lub Double.Nan. Użyj Single.IsNan(Single) lub Double.IsNan(Double) do testowania wartości.|
|[CA2243: Analiza literałów ciągów atrybutów powinna przebiegać poprawnie](../code-quality/ca2243.md)|Parametr literału ciągu atrybutu nie jest analizowany poprawnie dla adresu URL, identyfikatora GUID lub wersji.|
|[CA2244: nie Duplikuj zainicjowanych elementów indeksowanych](../code-quality/ca2244.md)|Inicjator obiektu ma więcej niż jeden indeks elementu indeksowanego z tym samym indeksem stałym. Wszystkie oprócz ostatniego inicjatora są nadmiarowe.|
|[CA2245: Nie przypisuj właściwości do samej siebie](../code-quality/ca2245.md)|Właściwość została przypadkowo przypisana do samej siebie.|
|[CA2246: Nie przypisuj symbolu i jego składowej w tej samej instrukcji](../code-quality/ca2246.md)|Przypisanie symbolu i jego elementu członkowskiego, czyli pola lub właściwości, w tej samej instrukcji nie jest zalecane. Nie jest jasne, jeśli dostęp do elementu członkowskiego był przeznaczony do użycia starej wartości symbolu przed przypisaniem lub nową wartością z przypisania w tej instrukcji.|
