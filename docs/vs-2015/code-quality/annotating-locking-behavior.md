---
title: Dodawanie adnotacji do zachowania blokującego | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f09b38ceb4a6824ec38f0d9206cf37e0f056ce28
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51790763"
---
# <a name="annotating-locking-behavior"></a>Dodawanie adnotacji do zachowania blokującego
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z adnotacji SAL w celu zmniejszenia liczby błędów kodu C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Informacje o języku SAL](../code-quality/understanding-sal.md)   
 [Dodawanie adnotacji do parametrów funkcji i zwracanych wartości](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Zachowanie funkcji dodawania adnotacji](../code-quality/annotating-function-behavior.md)   
 [Dodawanie adnotacji do struktur i klas](../code-quality/annotating-structs-and-classes.md)   
 [Określanie miejsca i warunków stosowania adnotacji](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Funkcje wewnętrzne](../code-quality/intrinsic-functions.md)   
 [Najlepsze praktyki i przykłady](../code-quality/best-practices-and-examples-sal.md)   
 [Blog zespołu ds. analizy kodu](http://go.microsoft.com/fwlink/p/?LinkId=251197)



