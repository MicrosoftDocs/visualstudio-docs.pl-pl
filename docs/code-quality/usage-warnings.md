---
title: Wykorzystanie — Ostrzeżenia
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.usagerules
helpviewer_keywords:
- warnings, usage
- managed code analysis warnings, usage warnings
- usage warnings
ms.assetid: fe7dc2a3-289d-4bf7-a1e4-0947a81287c4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e607da01d160212eea03b1fe81dfb2fbf4ede3f6
ms.sourcegitcommit: 034c503ae04e22cf840ccb9770bffd012e40fb2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/14/2019
ms.locfileid: "72305686"
---
# <a name="usage-warnings"></a>Wykorzystanie — Ostrzeżenia

Ostrzeżenia dotyczące użycia obsługują poprawne użycie platformy .NET.

## <a name="in-this-section"></a>W tej sekcji

|Reguła|Opis|
|----------|-----------------|
|[CA1801: Przejrzyj nieużywane parametry @ no__t-0|Podpis metody zawiera parametr, który nie jest używany w jej treści.|
|[CA1806: Nie Ignoruj wyników metody @ no__t-0|Nowy obiekt jest tworzony, ale nigdy nie jest używany; albo metoda, która tworzy i zwraca nowy ciąg, jest wywoływana, ale nowy ciąg nigdy nie jest używany; albo metody COM lub P/Invoke zwracają HRESULT lub kod błędu, który nigdy nie jest używany.|
|[CA1816: Wywołaj metodę GC. SuppressFinalize prawidłowo @ no__t-0|Metoda, która jest implementacją Dispose, nie wywołuje GC. SuppressFinalize; lub metody, która nie jest implementacją Dispose, wywołuje GC. SuppressFinalize; lub metoda wywołuje metodę GC. SuppressFinalize i przekazuje na coś innego niż to (Me w języku Visual Basic).|
|[CA2200: Zgłoś ponownie, aby zachować szczegóły stosu @ no__t-0|Wyjątek jest zgłaszany ponownie i jest on jawnie określony w instrukcji „throw”. Jeśli wyjątek jest zgłaszany ponownie przez określenie wyjątku w instrukcji „throw”, lista wywołań metod między pierwotną metodą, która zgłosiła wyjątek, a bieżącą zostanie utracona.|
|[CA2201: Nie zgłaszaj typów wyjątków zarezerwowanych @ no__t-0|Powoduje to, że oryginalny błąd trudno wykryć i debugować.|
|[CA2202: Nie usuwaj obiektów wiele razy, @ no__t-0|Implementacja metody zawiera ścieżki kodu, które powodują wielokrotne wywołania do System.IDisposable.Dispose lub równoważnika (na przykład użycie metody Close() na niektórych typach) dla tego samego obiektu.|
|[CA2204: Literały powinny być napisane poprawnie @ no__t-0|Ciąg literału w treści metody zawiera jeden lub więcej wyrazów, które nie są rozpoznawane przez bibliotekę sprawdzania pisowni Microsoft.|
|[CA2205: Użyj zarządzanych odpowiedników Win32 API @ no__t-0|Zdefiniowana jest metoda Invoke platformy i dostępna jest metoda .NET z równoważną funkcjonalnością.|
|[CA2207: Pola statyczne typu wartości Inicjalizacja w tekście @ no__t-0|Typ wartości deklaruje jawny, statyczny konstruktor. Aby naprawić naruszenie tej zasady, zainicjuj wszystkie dane statyczne, gdy jest on zadeklarowany, i usuń konstruktor statyczny.|
|[CA2208: Poprawne wystąpienie wyjątków argumentów @ no__t-0|Wywołanie odnosi się do domyślnego (bezparametrowego) konstruktora typu wyjątku, który jest elementem ArgumentException lub od niego pochodzi, albo niepoprawny argument ciągu jest przekazywany do sparametryzowania konstruktora typu wyjątku lub pochodzi od elementu ArgumentException.|
|[CA2211: Pola niebędące stałymi nie powinny być widoczne @ no__t-0|Pola statyczne, które nie są stałymi lub tylko do odczytu, nie są bezpieczne wątkowo. Dostęp do takiego pola musi być starannie kontrolowany i wymaga zaawansowanych technik programowania do synchronizowania dostępu do obiektu klasy.|
|[CA2212: Nie należy oznaczać serwisowanych składników za pomocą metody WEBMETHOD @ no__t-0|Metoda w typie, która dziedziczy z elementu System. EnterpriseServices. ServicedComponent, jest oznaczona za pomocą elementu System. Web. Services. WebMethodAttribute. Ze względu na to, że atrybut WebMethodAttribute i metoda ServicedComponent mają sprzeczne zachowanie i wymagania dotyczące przepływu kontekstu i transakcji, w niektórych scenariuszach zachowanie metod będzie niepoprawne.|
|[CA2213: Pola jednorazowe powinny zostać usunięte @ no__t-0|Typ, który implementuje element System.IDisposable, deklaruje pola takiego typu, które implementują także IDisposable. Metoda Dispose pola nie jest wywoływana przez metodę Dispose typu deklarującego.|
|[CA2214: Nie wywołuj metod założenia w konstruktorach @ no__t-0|Gdy Konstruktor wywołuje metodę wirtualną, istnieje możliwość, że Konstruktor wystąpienia, który wywołuje metodę, nie został wykonany.|
|[CA2215: Metody Dispose powinny wywoływać klasę bazową Dispose @ no__t-0|Jeśli typ dziedziczy z typu usuwalnego, musi on wywołać metodę Dispose typu podstawowego z własną metodę Dispose.|
|[CA2216: Typy jednorazowe powinny deklarować finalizator @ no__t-0|Typ, który implementuje System. IDisposable i zawiera pola, które sugerują użycie niezarządzanych zasobów, nie implementuje finalizatora zgodnie z opisem przez obiekt Object. Finalize.|
|[CA2217: Nie oznaczaj typów wyliczeniowych atrybutem FlagsAttribute @ no__t-0|Widoczne na zewnątrz Wyliczenie jest oznaczone atrybutem FlagsAttribute i ma co najmniej jedną wartość, która nie ma uprawnień do dwóch lub kombinacji innych zdefiniowanych wartości w wyliczeniu.|
|[CA2218: Zastąp GetHashCode przy zastępowaniu Equals równą @ no__t-0|GetHashCode zwraca wartość opartą na bieżącym wystąpieniu, które jest odpowiednie dla algorytmów wyznaczających wartości skrótu i struktur danych, takich jak tabela skrótów. Dwa obiekty, które są równe i tego samego typu, muszą zwrócić tę samą wartość skrótu.|
|[CA2219: Nie zgłaszaj wyjątków w klauzulach wyjątków @ no__t-0|Kiedy wyjątek jest zgłaszany w klauzuli „finally” lub „fault”, nowy wyjątek ukrywa aktywny wyjątek. Gdy wyjątek jest zgłaszany w klauzuli „filter”, środowisko uruchomieniowe dyskretnie przechwytuje wyjątek. Powoduje to, że oryginalny błąd trudno wykryć i debugować.|
|[CA2220: Finalizatory powinny wywoływać finalizator klasy bazowej @ no__t-0|Finalizacja musi być powielana w hierarchii dziedziczenia. Aby to zagwarantować, typy muszą wywołać metody Finalize swoich klas bazowych w ich własnej metodzie Finalize.|
|[CA2221: Finalizatory powinny być chronione @ no__t-0|Finalizatory muszą korzystać z modyfikatora dostępu „family”.|
|[CA2222: Nie zmniejszaj dziedziczonej widoczności składowej @ no__t-0|Nie zmieniaj modyfikatora dostępu dla dziedziczonych elementów członkowskich. Zmiana dziedziczonej składowej na prywatną nie uniemożliwia wywołującym uzyskania dostępu do implementacji metody klasy podstawowej.|
|[CA2223: Elementy członkowskie powinny różnić się nie tylko zwracanym typem @ no__t-0|Chociaż środowisko uruchomieniowe języka wspólnego pozwala na używanie typów zwracanych do rozróżnienia między inaczej identycznymi członkami, funkcja ta nie jest objęta specyfikacją języka wspólnego (CLS) ani nie jest wspólną cechą języków programowania .NET.|
|[CA2224: Zastąp wartość Equals w przypadku przeciążania operatora równą @ no__t-0|Typ publiczny implementuje operator równości, ale nie przesłania obiektu Object. Equals.|
|[CA2225: Przeciążenia operatorów mają nazwane alternatywy @ no__t-0|Wykryto przeciążony operator i nie znaleziono metody alternatywnej o oczekiwanej nazwie. Nazwany alternatywny element członkowski zapewnia dostęp do tych samych funkcji co operator i jest udostępniany deweloperom programu w językach, które nie obsługują przeciążonych operatorów.|
|[CA2226: Operatory powinny mieć symetryczne przeciążenia @ no__t-0|Typ implementuje operator równości lub nierówności i nie implementuje operatora przeciwległego.|
|[CA2227: Właściwości kolekcji powinny być tylko do odczytu @ no__t-0|Właściwość zapisywalnej kolekcji pozwala użytkownikowi zastąpić kolekcję inną kolekcją. Właściwość tylko do odczytu uniemożliwia zastępowanie kolekcji, ale nadal umożliwia ustawienie poszczególnych członków.|
|[CA2228: Nie dostarczaj niezwolnionych formatów zasobów @ no__t-0|Pliki zasobów, które zostały skompilowane przy użyciu wersji wstępnych programu .NET, mogą nie być używane przez obsługiwane wersje programu .NET.|
|[CA2229: Implementuj konstruktory serializacji @ no__t-0|Aby naprawić naruszenie tej zasady, należy zaimplementować konstruktora serializacji. Dla zamkniętej klasy należy ustawić konstruktor prywatny; w przeciwnym razie powinien być chroniony.|
|[CA2230: Użyj parametrów dla argumentów zmiennych @ no__t-0|Typ publiczny lub chroniony zawiera metodę publiczną lub chronioną, która używa wywoływania VarArgs zamiast słowa kluczowego params.|
|[CA2231: Operator przeciążenia jest równy na przesłanianiu ValueType. Equals @ no__t-0|Typ wartości przesłania `Object.Equals`, ale nie implementuje operatora równości.|
|[CA2232: Oznacz punkty wejścia Windows Forms za pomocą STAThread @ no__t-0|STAThreadAttribute wskazuje, że model wątkowości COM dla aplikacji jest jednowątkowym apartamentem. Atrybut ten musi być obecny w punkcie wejścia każdej aplikacji korzystającej z Windows Forms; jeśli zostanie pominięty, składniki systemu Windows mogą nie działać poprawnie.|
|[CA2233: Operacje nie powinny przepełniać wartości @ no__t-0|Nie należy wykonywać operacji arytmetycznych bez uprzedniego sprawdzenia operandów, aby upewnić się, że wynik operacji nie należy do zakresu możliwych wartości dla typów danych.|
|[CA2234: Przekaż obiekty System. URI zamiast ciągów @ no__t-0|Wykonano wywołanie do metody, która ma parametr typu ciąg, którego nazwa zawiera „uri”, „URI”, „urn”, „URN”, „url” lub „URL”.  Deklarujący typ metody zawiera odpowiadające przeciążenie metody z parametrem System.Uri.|
|[CA2235: Oznacz wszystkie pola, które nie są możliwe do serializacji @ no__t-0|Pola wystąpienia typu, który nie może być serializowany, jest zadeklarowany w typie, który jest możliwy do serializacji.|
|[CA2236: Wywoływanie metod klasy bazowej dla typów ISerializable @ no__t-0|Aby naprawić naruszenie tej zasady, należy wywołać metodę GetObjectData typu podstawowego lub konstruktor serializacji z odpowiadającej metody typu pochodnego albo konstruktora.|
|[CA2237: Oznacz typy ISerializable atrybutem SerializableAttribute @ no__t-0|Aby można było rozpoznać przez środowisko uruchomieniowe języka wspólnego jako możliwy do serializacji, typy muszą być oznaczone atrybutem SerializableAttribute, nawet jeśli typ używa niestandardowej procedury serializacji za pośrednictwem implementacji interfejsu ISerializable.|
|[CA2238: Poprawnie Implementuj metody serializacji @ no__t-0|Metoda, która obsługuje zdarzenie szeregowania, nie ma poprawnej sygnatury zwracanego typu lub widoczności.|
|[CA2239: Zapewnianie metod deserializacji dla pól opcjonalnych @ no__t-0|Typ ma pole oznaczone za pomocą atrybutu System. Runtime. Serialization. OptionalFieldAttribute, a typ nie zapewnia metod obsługi zdarzeń deserializacji.|
|[CA2240: Zaimplementuj poprawnie interfejs ISerializable @ no__t-0|Aby naprawić naruszenie tej zasady, należy sprawić, aby Metoda GetObjectData była widoczna i unikatowa, i upewnić się, że wszystkie pola wystąpienia są zawarte w procesie serializacji lub jawnie oznaczone atrybutem unserializationattribute.|
|[CA2241: Podaj poprawne argumenty do formatowania metod @ no__t-0|Argument formatu przesłany do System. String. format nie zawiera elementu formatu odpowiadającego każdemu argumentowi obiektu lub na odwrót.|
|[CA2242: Testuj poprawnie wartość NaN @ no__t-0|To wyrażenie sprawdza, czy wartość to Single.Nan lub Double.Nan. Użyj Single.IsNan(Single) lub Double.IsNan(Double) do testowania wartości.|
|[CA2243: Literały ciągu atrybutów powinny analizować się poprawnie @ no__t-0|Parametr literału ciągu atrybutu nie jest analizowany poprawnie dla adresu URL, identyfikatora GUID lub wersji.|