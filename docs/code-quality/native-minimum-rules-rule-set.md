---
title: Zestaw reguł Native Minimum Rules
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 2d898bc4-fba5-472e-8f09-b0c6b511c5a3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e8abf4d4c5d2158ab4a3c9deeb11ab93e31b4cc3
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649336"
---
# <a name="native-minimum-rules-rule-set"></a>Zestaw reguł Native Minimum Rules

Minimalne reguły natywne firmy Microsoft koncentrują się na najbardziej krytycznych problemach w kodzie macierzystym, w tym potencjalnych lukach w zabezpieczeniach i awariach aplikacji.

Uwzględnij ten zestaw reguł w dowolnym niestandardowym zestawie reguł utworzonym dla projektów natywnych.

|Reguła|Opis|
|----------|-----------------|
|[C6001](../code-quality/c6001.md)|Korzystanie z pamięci niezajednawizowanej|
|[C6011](../code-quality/c6011.md)|Wskaźnik null dereferencing|
|[C6029](../code-quality/c6029.md)|Korzystanie z niezaznaczonewartości|
|[C6053](../code-quality/c6053.md)|Zero zakończenia od połączenia|
|[C6059](../code-quality/c6059.md)|Złe łączenie|
|[C6063](../code-quality/c6063.md)|Brak argumentu ciąg do formatowania funkcji|
|[C6064](../code-quality/c6064.md)|Brak argumentu liczby całkowitej do formatowania funkcji|
|[C6066](../code-quality/c6066.md)|Brak argumentu wskaźnika do formatowania funkcji|
|[C6067](../code-quality/c6067.md)|Brak argumentu wskaźnika ciągu do formatowania funkcji|
|[C6101](../code-quality/c6101.md)|Zwracanie niezainicjowanej pamięci|
|[C6200](../code-quality/c6200.md)|Indeks przekracza maksymalną wartość buforu|
|[C6201](../code-quality/c6201.md)|Indeks przekracza maksymalną bufor stosu|
|[C6270](../code-quality/c6270.md)|Brak argumentu float do formatowania funkcji|
|[C6271](../code-quality/c6271.md)|Dodatkowy argument do formatowania funkcji|
|[C6272](../code-quality/c6272.md)|Argument Non-Float do formatowania funkcji|
|[C6273](../code-quality/c6273.md)|Argument niekłacji całkowitej do formatowania funkcji|
|[C6274](../code-quality/c6274.md)|Argument bez znaku do formatowania funkcji|
|[C6276](../code-quality/c6276.md)|Nieprawidłowe rzutnie ciągiem|
|[C6277](../code-quality/c6277.md)|Nieprawidłowe wywołanie createprocess|
|[C6284](../code-quality/c6284.md)|Nieprawidłowy argument obiektu do formatowania funkcji|
|[C6290](../code-quality/c6290.md)|Logiczne, nie bitowe i pierwszeństwo|
|[C6291](../code-quality/c6291.md)|Logiczne, nie bitowe lub pierwszeństwo|
|[C6302](../code-quality/c6302.md)|Nieprawidłowy argument ciąg znaków do formatowania funkcji|
|[C6303](../code-quality/c6303.md)|Nieprawidłowy argument szeroki ciąg znaków do formatowania funkcji|
|[C6305](../code-quality/c6305.md)|Niedopasowane użycie rozmiaru i liczby|
|[C6306](../code-quality/c6306.md)|Wywołanie funkcji niepoprawnego argumentu zmiennej|
|[C6328](../code-quality/c6328.md)|Niezgodność typu potencjalnego argumentu|
|[C6385](../code-quality/c6385.md)|Odczyt Przekroczenia|
|[C6386](../code-quality/c6386.md)|Przekroczenie zapisu|
|[C6387](../code-quality/c6387.md)|Nieprawidłowa wartość parametru|
|[C6500](../code-quality/c6500.md)|Nieprawidłowa właściwość atrybutu|
|[C6501](../code-quality/c6501.md)|Sprzeczne wartości właściwości atrybutu|
|[C6503](../code-quality/c6503.md)|Odwołania nie mogą być null|
|[C6504](../code-quality/c6504.md)|Null na wskaźnik bez wskaźnika|
|[C6505](../code-quality/c6505.md)|MustCheck On Void|
|[C6506](../code-quality/c6506.md)|Rozmiar buforu w przypadku braku wskaźnika lub tablicy|
|[C6508](../code-quality/c6508.md)|Dostęp do zapisu na stałej|
|[C6509](../code-quality/c6509.md)|Zwrot używany w warunku wstępnym|
|[C6510](../code-quality/c6510.md)|Wartość null zakończona w przypadku braku wskaźnika|
|[C6511](../code-quality/c6511.md)|MustCheck musi być tak lub nie|
|[C6513](../code-quality/c6513.md)|Rozmiar elementu bez rozmiaru buforu|
|[C6514](../code-quality/c6514.md)|Rozmiar buforu przekracza rozmiar tablicy|
|[C6515](../code-quality/c6515.md)|Rozmiar buforu na wskaźniku nie wskaźnik|
|[C6516](../code-quality/c6516.md)|Brak właściwości na atrybut|
|[C6517](../code-quality/c6517.md)|Prawidłowy rozmiar w buforze nieczytalnym|
|[C6518](../code-quality/c6518.md)|Zapisywalny rozmiar w buforze nieobjętym do skrytego|
|[C6522](../code-quality/c6522.md)|Nieprawidłowy typ ciągu rozmiaru|
|[C6525](../code-quality/c6525.md)|Nieprawidłowy rozmiar ciąg nieosiągalny lokalizacja|
|[C6527](../code-quality/c6527.md)|Nieprawidłowa adnotacja: właściwość "NeedsRelease" nie może być używana w wartościach typu void|
|[C6530](../code-quality/c6530.md)|Nierozpoznany styl ciągu formatu|
|[C6540](../code-quality/c6540.md)|Użycie adnotacji atrybutów w tej funkcji spowoduje unieważnienie wszystkich istniejących adnotacji __declspec|
|[C6551](../code-quality/c6551.md)|Nieprawidłowa specyfikacja rozmiaru: wyrażenie nie jest parsable|
|[C6552](../code-quality/c6552.md)|Nieprawidłowy Deref= lub Notref=: wyrażenie nie do przysparwalenia|
|[C6701](../code-quality/c6701.md)|Wartość nie jest prawidłową wartością Tak/Nie/Może|
|[C6702](../code-quality/c6702.md)|Wartość nie jest wartością ciągu|
|[C6703](../code-quality/c6703.md)|Wartość nie jest liczbą|
|[C6704](../code-quality/c6704.md)|Nieoczekiwany błąd wyrażenia adnotacji|
|[C6705](../code-quality/c6705.md)|Oczekiwana liczba argumentów adnotacji nie odpowiada rzeczywistej liczbie argumentów adnotacji|
|[C6706](../code-quality/c6706.md)|Nieoczekiwany błąd adnotacji adnotacji|
|[C26450](../code-quality/c26450.md)|RESULT_OF_ARITHMETIC_OPERATION_PROVABLY_LOSSY|
|[C26451](../code-quality/c26451.md)|RESULT_OF_ARITHMETIC_OPERATION_CAST_TO_LARGER_SIZE|
|[C26452](../code-quality/c26452.md)|SHIFT_COUNT_NEGATIVE_OR_TOO_BIG|
|[C26453](../code-quality/c26453.md)|LEFTSHIFT_NEGATIVE_SIGNED_NUMBER|
|[C26454](../code-quality/c26454.md)|RESULT_OF_ARITHMETIC_OPERATION_NEGATIVE_UNSIGNED|
|[C26495](../code-quality/c26495.md)|MEMBER_UNINIT|
|[C28021](../code-quality/c28021.md)|Parametr, o który się dozowane, musi być wskaźnikiem|
|[C28182](../code-quality/c28182.md)|Wskaźnik NULL dereferencing. Wskaźnik zawiera taką samą wartość NULL, jak inny wskaźnik.|
|[C28202](../code-quality/c28202.md)|Nielegalne odniesienie do niestatycznych członków|
|[C28203](../code-quality/c28203.md)|Niejednoznaczne odwołanie do elementu członkowskiego klasy.|
|[C28205](../code-quality/c28205.md)|\_Niepowodzenie\_ \_lub\_\_ Porażka używana w kontekście niezgodnym z prawem|
|[C28206](../code-quality/c28206.md)|Lewy operand wskazuje na strukturę, użyj '->'|
|[C28207](../code-quality/c28207.md)|Lewy operand jest strukturą, użyj '.'|
|[C28210](../code-quality/c28210.md)|Adnotacje dla kontekstu __on_failure nie mogą znajdować się w jawnym kontekście wstępnym|
|[C28211](../code-quality/c28211.md)|Nazwa kontekstu statycznego oczekiwana dla SAL_context|
|[C28212](../code-quality/c28212.md)|Oczekiwane wyrażenie wskaźnika dla adnotacji|
|[C28213](../code-quality/c28213.md)|Adnotacje \_\_\_odznaczaniami\_ należy używać do odwoływania się, bez modyfikacji, do wcześniejszej deklaracji.|
|[C28214](../code-quality/c28214.md)|Nazwy parametrów atrybutu muszą być p1... p9|
|[C28215](../code-quality/c28215.md)|Poprawki typu nie można zastosować do parametru, który ma już poprawkę typu|
|[C28216](../code-quality/c28216.md)|Adnotacje checkReturn dotyczą tylko warunków postconditions dla określonego parametru funkcji.|
|[C28217](../code-quality/c28217.md)|W przypadku funkcji liczba parametrów do adnotacji nie jest zgodna z parametrami znalezionymi w pliku|
|[C28218](../code-quality/c28218.md)|W przypadku parametru funkcji parametr adnotacji nie jest zgodny z parametrem znalezionym w pliku|
|[C28219](../code-quality/c28219.md)|Element członkowski wyliczenia oczekiwany dla adnotacji parametr w adnotacji|
|[C28220](../code-quality/c28220.md)|Oczekiwane wyrażenie liczby całkowitej dla adnotacji parametru w adnotacji|
|[C28221](../code-quality/c28221.md)|Oczekiwano wyrażenia ciągu dla parametru w adnotacji|
|[C28222](../code-quality/c28222.md)|__yes, \__no lub \__maybe oczekiwane do adnotacji|
|[C28223](../code-quality/c28223.md)|Nie odnalazł oczekiwanego tokenu/identyfikatora adnotacji, parametru|
|[C28224](../code-quality/c28224.md)|Adnotacja wymaga parametrów|
|[C28225](../code-quality/c28225.md)|Nie znaleźliśmy prawidłowej liczby wymaganych parametrów w adnotacji|
|[C28226](../code-quality/c28226.md)|Adnotacja nie może być również PrimOp (w bieżącej deklaracji)|
|[C28227](../code-quality/c28227.md)|Adnotacja nie może być również PrimOp (patrz uprzednia deklaracja)|
|[C28228](../code-quality/c28228.md)|Parametr Adnotacji: nie można używać typu w adnotacjach|
|[C28229](../code-quality/c28229.md)|Adnotacja nie obsługuje parametrów|
|[C28230](../code-quality/c28230.md)|Typ parametru nie ma elementu członkowskiego.|
|[C28231](../code-quality/c28231.md)|Adnotacja jest prawidłowa tylko w tablicy|
|[C28232](../code-quality/c28232.md)|pre, post lub deref nie stosowane do żadnej adnotacji|
|[C28233](../code-quality/c28233.md)|pre, post lub deref zastosowane do bloku|
|[C28234](../code-quality/c28234.md)|wyrażenie __at nie ma zastosowania do bieżącej funkcji|
|[C28235](../code-quality/c28235.md)|Funkcja nie może być autonomiczna jako adnotacja|
|[C28236](../code-quality/c28236.md)|Adnotacji nie można używać w wyrażeniu|
|[C28237](../code-quality/c28237.md)|Adnotacja na parametr nie jest już obsługiwana|
|[C28238](../code-quality/c28238.md)|Adnotacja na parametr ma więcej niż jedną wartość, stringValue i longValue. Użyj paramn=xxx|
|[C28239](../code-quality/c28239.md)|Adnotacja na parametr ma zarówno wartość, stringValue lub longValue; i paramn=xxx. Używaj tylko paramn=xxx|
|[C28240](../code-quality/c28240.md)|Adnotacja na parametr ma param2, ale nie param1|
|[C28241](../code-quality/c28241.md)|Adnotacja dla parametru funkcji na nie jest rozpoznawana|
|[C28243](../code-quality/c28243.md)|Adnotacja dla funkcji na parametrze wymaga więcej wyłudów niż rzeczywisty typ z adnotacją pozwala|
|[C28245](../code-quality/c28245.md)|Adnotacja funkcji oznacza "to" w funkcji niebędącej członkiem|
|[C28246](../code-quality/c28246.md)|Adnotacja parametru funkcji nie jest zgodna z typem parametru|
|[C28250](../code-quality/c28250.md)|Niespójna adnotacja dla funkcji: poprzednie wystąpienie ma błąd.|
|[C28251](../code-quality/c28251.md)|Niespójna adnotacja dla funkcji: to wystąpienie ma błąd.|
|[C28252](../code-quality/c28252.md)|Niespójna adnotacja dla funkcji: parametr ma inne adnotacje w tym wystąpieniu.|
|[C28253](../code-quality/c28253.md)|Niespójna adnotacja dla funkcji: parametr ma inne adnotacje w tym wystąpieniu.|
|[C28254](../code-quality/c28254.md)|dynamic_cast<>() nie jest obsługiwana w adnotacjach|
|[C28262](../code-quality/c28262.md)|W funkcji znaleziono błąd składniowy w adnotacji, dla adnotacji|
|[C28263](../code-quality/c28263.md)|Znaleziono błąd składni w adnotacji warunkowej dla adnotacji wewnętrznej|
|[C28267](../code-quality/c28267.md)|W funkcji znaleziono błąd składniowy w adnotacjach.|
|[C28272](../code-quality/c28272.md)|Adnotacja funkcji, parametr podczas badania jest niezgodny z deklaracją funkcji|
|[C28273](../code-quality/c28273.md)|W przypadku funkcji wskazówki są niezgodne z deklaracją funkcji|
|[C28275](../code-quality/c28275.md)|Parametr do \_\_wartości\_ makro ma wartość null|
|[C28279](../code-quality/c28279.md)|W przypadku symbolu znaleziono "begin" bez pasującego "końca"|
|[C28280](../code-quality/c28280.md)|W przypadku symbolu znaleziono "koniec" bez pasującego "begin"|
|[C28282](../code-quality/c28282.md)|Formatowanie ciągów musi być w warunkach wstępnych|
|[C28285](../code-quality/c28285.md)|W przypadku funkcji błąd składni w parametrze|
|[C28286](../code-quality/c28286.md)|W przypadku funkcji błąd składniowy na końcu|
|[C28287](../code-quality/c28287.md)|Dla funkcji, błąd składni w \_adnotacji At\_() (nazwa parametru nierozpoznanego)|
|[C28288](../code-quality/c28288.md)|Dla funkcji, błąd składni w \_adnotacji At\_() (nieprawidłowa nazwa parametru)|
|[C28289](../code-quality/c28289.md)|Dla funkcji: ReadableTo lub WritableTo nie miał specyfikacji limitu jako parametru|
|[C28290](../code-quality/c28290.md)|adnotacja funkcji zawiera więcej zewnętrznych niż rzeczywista liczba parametrów|
|[C28291](../code-quality/c28291.md)|post null/notnull na poziomie deref 0 jest bez znaczenia dla funkcji.|
|[C28300](../code-quality/c28300.md)|Wyrażeń argumenty niezgodnych typów dla operatora|
|[C28301](../code-quality/c28301.md)|Brak adnotacji dla pierwszej deklaracji funkcji.|
|[C28302](../code-quality/c28302.md)|Dodatkowy \_operator\_ Deref został znaleziony na adnotacji.|
|[C28303](../code-quality/c28303.md)|Niejednoznaczny \_operator Deref\_ został znaleziony na adnotacji.|
|[C28304](../code-quality/c28304.md)|Nieprawidłowo umieszczony \_operator\_ Notref został znaleziony zastosowany do tokenu.|
|[C28305](../code-quality/c28305.md)|Wykryto błąd podczas analizowania tokenu.|
|[C28350](../code-quality/c28350.md)|Adnotacja opisuje sytuację, która nie jest warunkowo stosowana.|
|[C28351](/cpp/code-quality/c28351)|Adnotacja opisuje, gdzie wartość dynamiczna (zmienna) nie może być używana w warunku.|
