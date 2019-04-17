---
title: Dodawanie adnotacji do zachowania blokującego
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- _Releases_nonreentrant_lock_
- _Lock_kind_mutex_
- _Lock_kind_critical_section_
- _Acquires_lock_
- _Releases_lock_
- _Has_lock_kind_
- _Releases_exclusive_lock_
- _Post_same_lock_
- _Requires_exclusive_lock_held_
- _Requires_shared_lock_held_
- _Lock_kind_semaphore_
- _Requires_lock_held_
- _Acquires_exclusive_lock_
- _Create_lock_level_
- _Acquires_nonreentrant_lock_
- _Releases_shared_lock_
- _Has_lock_level_
- _Lock_kind_spin_lock_
- _Requires_lock_not_held_
- _Acquires_shared_lock_
- _Requires_no_locks_held_
- _Lock_level_order_
- _Lock_kind_event_
ms.assetid: 07769c25-9b97-4ab7-b175-d1c450308d7a
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: ace3a8b729a9d0f54817bdad2eb5b8ee5343c0a9
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59653011"
---
# <a name="annotating-locking-behavior"></a>Dodawanie adnotacji do zachowania blokującego
Aby uniknąć błędów współbieżności w programach wielowątkowych, zawsze postępuj zgodnie z odpowiednią dyscypliny blokowania i korzystanie z adnotacji SAL.

 Współbieżność usterki są bardzo trudne do odtworzenia, diagnozowanie i debugowanie, ponieważ są one deterministyczna. Uzasadnienie o wątku z przeplotem jest trudne w najlepszym i staje się niepraktyczne, projektując treści kodu, który ma więcej niż kilka wątków. Dlatego jest dobrym rozwiązaniem, postępuj zgodnie z blokowaniem dyscypliny w programach wielowątkowych. Na przykład obeying kolejności blokady podczas uzyskiwania blokady wielu pomaga uniknąć zakleszczenia i uzyskiwanie właściwego guarding blokady przed uzyskaniem dostępu do zasobu udostępnionego zapobiega wyścigu.

 Niestety, pozornie proste zasady blokowania zaskakująco trudno jest wykonać w praktyce. Podstawowe ograniczenia w obecnie języków programowania i kompilatory to, że ich nie obsługują bezpośrednio Specyfikacja i analizy wymagania współbieżności. Programiści trzeba polegać na komentarzach nieformalnego kodu, aby wyrazić swoich zamiarach dotyczące wykorzystania do blokady.

 Adnotacje SAL współbieżności są przeznaczone do pomagają w określeniu blokowania efekty uboczne w celu blokowania odpowiedzialność, opieki danych, blokowanie kolejności hierarchii i innych oczekiwanego zachowania blokującego. Wprowadzając reguł niejawnych jawne, adnotacji współbieżności SAL zapewnia spójny sposób dokumentów, jak Twój kod przy użyciu reguł blokowania. Adnotacje współbieżności również zwiększyć możliwość wyszukiwania, sytuacje wyścigu, zakleszczenia, operacje synchronizacji niedopasowanych i inne błędy współbieżnością subtelnych narzędzi analizy kodu.

## <a name="general-guidelines"></a>Ogólne wskazówki
 Za pomocą funkcji adnotacje, można podać umowy, które są też dorozumianych przez definicje funkcji między klientami (obiekty wywołujące) i implementacji (wywoływane), a express invariants i inne właściwości programu, który może dodatkowo ulepszyć analizy.

 SAL obsługuje wiele różnych elementów podstawowych blokowania — na przykład sekcji krytycznych, muteksy, pokrętła blokad i innych obiektów zasobów. Wiele adnotacji współbieżności zająć wyrażenie blokady, jako parametr. Zgodnie z Konwencją blokady jest określona przez wyrażenie ścieżki obiektu bazowego blokady.

 Niektóre reguły własność wątku na uwadze:

-   Pokrętła blokady są uncounted blokad, które mieć prawa własności do zwykłego wątku.

-   Sekcji krytycznych i Muteksy są liczone blokad, które mieć prawa własności do zwykłego wątku.

-   Semaforów i zdarzenia są zliczane blokad, które nie mają własność wyczyść wątku.

## <a name="locking-annotations"></a>Blokowanie adnotacji
 W poniższej tabeli wymieniono blokowania adnotacji.

|Adnotacja|Opis|
|----------------|-----------------|
|`_Acquires_exclusive_lock_(expr)`|Oznacza stosowanym funkcji i wskazuje, że we wpisie w stan funkcji zwiększa o jeden blokady na wyłączność liczbę blokady obiektu, który jest nazwany przez `expr`.|
|`_Acquires_lock_(expr)`|Oznacza stosowanym funkcji i wskazuje, że we wpisie w stan funkcji zwiększa o jeden liczbę blokad blokady obiektu, który jest nazwany przez `expr`.|
|`_Acquires_nonreentrant_lock_(expr)`|Lock, który jest nazwany przez `expr` nabywa się.  Błąd jest zgłaszany, gdy blokada jest już używana.|
|`_Acquires_shared_lock_(expr)`|Oznacza stosowanym funkcji i wskazuje, że we wpisie w stan funkcji zwiększa o jeden blokady współużytkowanej liczbę blokady obiektu, który jest nazwany przez `expr`.|
|`_Create_lock_level_(name)`|Instrukcja, która deklaruje symbol `name` jako poziom blokady, dzięki czemu mogą być używane w adnotacjach `_Has_Lock_level_` i `_Lock_level_order_`.|
|`_Has_lock_kind_(kind)`|Oznacza stosowanym dowolnego obiektu, aby uzyskać dokładniejsze informacje o typie obiektu zasobów. Czasami wspólny typ jest używane dla różnych rodzajów zasobów i przeciążone typ nie jest wystarczające do odróżniania wymagania semantycznego między różnymi zasobami. Poniżej przedstawiono listę wstępnie zdefiniowanych `kind` parametry:<br /><br /> `_Lock_kind_mutex_`<br /> Rodzaj Identyfikator blokady dla muteksy.<br /><br /> `_Lock_kind_event_`<br /> Rodzaj Identyfikator blokady dla zdarzeń.<br /><br /> `_Lock_kind_semaphore_`<br /> Rodzaj Identyfikator blokady dla semaforów.<br /><br /> `_Lock_kind_spin_lock_`<br /> Rodzaj Identyfikator blokady blokad pokrętła.<br /><br /> `_Lock_kind_critical_section_`<br /> Rodzaj Identyfikator blokady dla sekcji krytycznych.|
|`_Has_lock_level_(name)`|Oznacza stosowanym obiektu blokady i nadaje jej poziom blokady `name`.|
|`_Lock_level_order_(name1, name2)`|Instrukcję, która zapewnia blokady kolejność między `name1` i `name2`.|
|`_Post_same_lock_(expr1, expr2)`|Oznacza stosowanym funkcji i wskazuje we wpisie w stan blokady dwóch `expr1` i `expr2`, są traktowane tak, jakby są tego samego obiektu blokady.|
|`_Releases_exclusive_lock_(expr)`|Oznacza stosowanym funkcji i wskazuje, że we wpisie w stanie zmniejsza funkcji przez jeden licznik blokady na wyłączność zablokować obiektu, który jest nazwany przez `expr`.|
|`_Releases_lock_(expr)`|Oznacza stosowanym funkcji i wskazuje, że we wpisie w stanie zmniejsza funkcji o jeden liczbę blokad blokady obiektu, który jest nazwany przez `expr`.|
|`_Releases_nonreentrant_lock_(expr)`|Lock, który jest nazwany przez `expr` wydaniu. Błąd jest zgłaszany, jeśli blokada nie jest obecnie nałożona.|
|`_Releases_shared_lock_(expr)`|Oznacza stosowanym funkcji i wskazuje, że we wpisie w stanie zmniejsza funkcji przez jeden licznik blokady współużytkowanej zablokować obiektu, który jest nazwany przez `expr`.|
|`_Requires_lock_held_(expr)`|Oznacza stosowanym funkcji i wskazuje, w pre stan obiektu, który jest nazwany przez liczbę blokad `expr` co najmniej jeden.|
|`_Requires_lock_not_held_(expr)`|Oznacza stosowanym funkcji i wskazuje, w pre stan obiektu, który jest nazwany przez liczbę blokad `expr` wynosi zero.|
|`_Requires_no_locks_held_`|Oznacza stosowanym funkcji i wskazuje, że liczba blokady wszystkich blokad, które są znane z modułu sprawdzania zero.|
|`_Requires_shared_lock_held_(expr)`|Oznacza stosowanym funkcji i wskazuje, czy w pre stan blokady współużytkowanej liczba obiekt, który jest nazwany przez `expr` co najmniej jeden.|
|`_Requires_exclusive_lock_held_(expr)`|Oznacza stosowanym funkcji i wskazuje, czy w pre stan blokady na wyłączność liczba obiekt, który jest nazwany przez `expr` co najmniej jeden.|

## <a name="sal-intrinsics-for-unexposed-locking-objects"></a>Wewnętrzne SAL nieujawnionych blokowanie obiektów
 Niektóre obiekty blokady nie są widoczne przy wdrażaniu funkcji blokowania skojarzone.  W poniższej tabeli wymieniono SAL wewnętrzne zmienne, które umożliwią adnotacje dla funkcji, które działają na tych obiektach nieujawnionych blokady.

|Adnotacja|Opis|
|----------------|-----------------|
|`_Global_cancel_spin_lock_`|W tym artykule opisano Anuluj blokadę pokrętła.|
|`_Global_critical_region_`|W tym artykule opisano krytyczne regionu.|
|`_Global_interlock_`|W tym artykule opisano operacje blokowane.|
|`_Global_priority_region_`|W tym artykule opisano region priorytetu.|

## <a name="shared-data-access-annotations"></a>Adnotacje dostępu do udostępnionych danych
 W poniższej tabeli wymieniono adnotacji, aby uzyskać dostęp do udostępnionych danych.

|Adnotacja|Opis|
|----------------|-----------------|
|`_Guarded_by_(expr)`|Oznacza stosowanym zmienną i wskazuje, że zawsze, gdy zmienna jest dostępny, liczbę blokad blokady obiektu, który jest nazwany przez `expr` co najmniej jeden.|
|`_Interlocked_`|Oznacza stosowanym zmienną i jest odpowiednikiem `_Guarded_by_(_Global_interlock_)`.|
|`_Interlocked_operand_`|Parametr funkcji adnotacjami jest operand docelowej jednego z różnych funkcji Interlocked.  Te operandy muszą posiadać określone dodatkowe właściwości.|
|`_Write_guarded_by_(expr)`|Oznacza stosowanym zmienną i wskazuje, że zawsze, gdy zmienna jest modyfikowany, liczbę blokad blokady obiektu, który jest nazwany przez `expr` co najmniej jeden.|

## <a name="smart-lock-and-raii-annotations"></a>Blokada Smart Lock i adnotacje RAII
 Inteligentnych zamków zazwyczaj opakować natywnych blokad i zarządzanie nimi ich istnienia. W poniższej tabeli wymieniono adnotacji, które mogą być używane z inteligentnych zamków i idiomu RAII wzorców, obsługę `move` semantyki.

|Adnotacja|Opis|
|----------------|-----------------|
|`_Analysis_assume_smart_lock_acquired_`|Informuje, analizator założono pozyskany blokady inteligentnej. Ta adnotacja oczekuje, że typ blokady odwołanie jako parametr.|
|`_Analysis_assume_smart_lock_released_`|Informuje, analizator założono, że zwolniono blokady inteligentnej. Ta adnotacja oczekuje, że typ blokady odwołanie jako parametr.|
|`_Moves_lock_(target, source)`|W tym artykule opisano `move constructor` operacji, który przenosi stan blokady z `source` obiekt `target`. `target` Należy traktować jako obiekt nowo skonstruowany, dzięki czemu dowolny stan miał wcześniej utracone i zastąpione przez `source` stanu. `source` Jest również Resetuj do stanu czystego nie blokady docelowej liczby lub Tworzenie aliasów, ale aliasy wskazujących na niego pozostają niezmienione.|
|`_Replaces_lock_(target, source)`|W tym artykule opisano `move assignment operator` semantykę, gdzie blokada docelowy jest zwalniana przed przeniesieniem stanu ze źródła. To może być traktowane jako kombinacji `_Moves_lock_(target, source)` poprzedzone `_Releases_lock_(target)`.|
|`_Swaps_locks_(left, right)`|W tym artykule opisano standardowe `swap` zachowanie, które przyjęto założenie, że obiekty `left` i `right` wymiany ich stanu. Stan wymieniane obejmuje blokady aliasów i liczba obiektu docelowego, jeśli jest obecny. Aliasy, które wskazują na `left` i `right` obiekty pozostają bez zmian.|
|`_Detaches_lock_(detached, lock)`|W tym artykule opisano scenariusz, w którym typ otoki blokady umożliwia odmówiono z jego zawartego zasobu. Jest to podobne do jak `std::unique_ptr` współpracuje z jego wewnętrzny wskaźnik: umożliwia programistom wyodrębnić wskaźnik i pozostawienie jej kontenera inteligentnego wskaźnika w stanu czystego. Podobnej logiki jest obsługiwana przez `std::unique_lock` i może być implementowany w otoki niestandardowe blokady. Odłączony blokady zachowuje swój stan (blokady aliasów i liczba obiekt docelowy, jeśli istnieje), podczas gdy otoki jest resetowana do zawierać zero liczbę blokad i żadne miejsce docelowe aliasów, zachowując swoje własne aliasy. Nie istnieje żadna operacja związane z liczbami blokady (zwalniania i uzyskiwanie). Ta adnotacja zachowuje się dokładnie tak jak `_Moves_lock_` z tą różnicą, że odłączony argument powinien być `return` zamiast `this`.|

## <a name="see-also"></a>Zobacz też

- [Korzystanie z adnotacji SAL w celu zmniejszenia liczby defektów kodu C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
- [Informacje o języku SAL](../code-quality/understanding-sal.md)
- [Dodawanie adnotacji do parametrów funkcji i zwracanych wartości](../code-quality/annotating-function-parameters-and-return-values.md)
- [Zachowanie funkcji dodawania adnotacji](../code-quality/annotating-function-behavior.md)
- [Dodawanie adnotacji do struktur i klas](../code-quality/annotating-structs-and-classes.md)
- [Określanie miejsca i warunków stosowania adnotacji](../code-quality/specifying-when-and-where-an-annotation-applies.md)
- [Funkcje wewnętrzne](../code-quality/intrinsic-functions.md)
- [Najlepsze rozwiązania i przykłady](../code-quality/best-practices-and-examples-sal.md)
- [Blog zespołu ds. analizy kodu](http://go.microsoft.com/fwlink/p/?LinkId=251197)