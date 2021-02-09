---
title: Zestaw reguł Native Minimum Rules
ms.date: 11/04/2016
description: Dowiedz się więcej na temat natywnego zestawu reguł minimalnych reguł w programie Visual Studio. Zobacz opisy reguł zabezpieczeń, niezawodności i innych krytycznych problemów w kodzie natywnym.
ms.custom: SEO-VS-2020
ms.topic: reference
ms.assetid: 2d898bc4-fba5-472e-8f09-b0c6b511c5a3
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1e029e0127a361bc133c008cef36d4426617c83b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99867831"
---
# <a name="native-minimum-rules-rule-set"></a>Zestaw reguł Native Minimum Rules

Reguły minimalnej natywnej firmy Microsoft koncentrują się na najważniejszych problemach w kodzie natywnym, w tym potencjalnych luk w zabezpieczeniach i awarii aplikacji.

Dołącz ten zestaw reguł do dowolnego niestandardowego zestawu reguł tworzonego dla projektów natywnych.

|Reguła|Opis|
|----------|-----------------|
|[C6001](/cpp/code-quality/c6001)|Używanie niezainicjowanej pamięci|
|[C6011](/cpp/code-quality/c6011)|Wyłuskanie wskaźnika o wartości null|
|[C6029](/cpp/code-quality/c6029)|Użycie niesprawdzonej wartości|
|[C6053](/cpp/code-quality/c6053)|Zakończenie zerowe od wywołania|
|[C6059](/cpp/code-quality/c6059)|Złe łączenie|
|[C6063](/cpp/code-quality/c6063)|Brak argumentu ciągu do funkcji formatowania|
|[C6064](/cpp/code-quality/c6064)|Brak argumentu typu Integer dla funkcji formatowania|
|[C6066](/cpp/code-quality/c6066)|Brak argumentu wskaźnika dla funkcji formatowania|
|[C6067](/cpp/code-quality/c6067)|Brak argumentu wskaźnika ciągu do funkcji formatowania|
|[C6101](/cpp/code-quality/c6101)|Zwracanie niezainicjowanej pamięci|
|[C6200](/cpp/code-quality/c6200)|Indeks przekracza maksymalny rozmiar buforu|
|[C6201](/cpp/code-quality/c6201)|Indeks przekracza maksymalną wartość buforu stosu|
|[C6270](/cpp/code-quality/c6270)|Brak argumentu zmiennoprzecinkowego do funkcji formatowania|
|[C6271](/cpp/code-quality/c6271)|Dodatkowy argument funkcji formatowania|
|[C6272](/cpp/code-quality/c6272)|Argument inny niż zmiennoprzecinkowy do formatowania funkcji|
|[C6273](/cpp/code-quality/c6273)|Argument niebędący liczbą całkowitą do sformatowania funkcji|
|[C6274](/cpp/code-quality/c6274)|Argument niebędący znakiem do funkcji formatowania|
|[C6276](/cpp/code-quality/c6276)|Nieprawidłowe rzutowanie ciągu|
|[C6277](/cpp/code-quality/c6277)|Nieprawidłowe wywołanie metody CreateProcess|
|[C6284](/cpp/code-quality/c6284)|Nieprawidłowy argument obiektu dla funkcji formatowania|
|[C6290](/cpp/code-quality/c6290)|Logical-Not Bitwise-And pierwszeństwo|
|[C6291](/cpp/code-quality/c6291)|Logical-Not Bitwise-Or pierwszeństwo|
|[C6302](/cpp/code-quality/c6302)|Nieprawidłowy argument ciągu znaków dla funkcji formatowania|
|[C6303](/cpp/code-quality/c6303)|Nieprawidłowy argument ciągu znaków dwubajtowych do funkcji formatowania|
|[C6305](/cpp/code-quality/c6305)|Użycie niedopasowanego rozmiaru i liczby|
|[C6306](/cpp/code-quality/c6306)|Nieprawidłowe wywołanie funkcji zmiennej argumentu|
|[C6328](/cpp/code-quality/c6328)|Niezgodność typu argumentu potencjalnego|
|[C6385](/cpp/code-quality/c6385)|Przepełnienie odczytu|
|[C6386](/cpp/code-quality/c6386)|Przepełnienie zapisu|
|[C6387](/cpp/code-quality/c6387)|Nieprawidłowa wartość parametru|
|[C6500](/cpp/code-quality/c6500)|Nieprawidłowa właściwość atrybutu|
|[C6501](/cpp/code-quality/c6501)|Sprzeczne wartości właściwości atrybutów|
|[C6503](/cpp/code-quality/c6503)|Odwołania nie mogą być puste|
|[C6504](/cpp/code-quality/c6504)|Wartość zerowa przy niewskaźniku|
|[C6505](/cpp/code-quality/c6505)|MustCheck na void|
|[C6506](/cpp/code-quality/c6506)|Rozmiar buforu dla elementu nie będącego wskaźnikiem lub tablicą|
|[C6508](/cpp/code-quality/c6508)|Dostęp do zapisu dla stałej|
|[C6509](/cpp/code-quality/c6509)|Return użyty w warunku wstępnym|
|[C6510](/cpp/code-quality/c6510)|Przerwano wartość null dla niebędącego wskaźnikiem|
|[C6511](/cpp/code-quality/c6511)|MustCheck musi mieć wartość yes lub No|
|[C6513](/cpp/code-quality/c6513)|Rozmiar elementu bez rozmiaru buforu|
|[C6514](/cpp/code-quality/c6514)|Rozmiar buforu przekracza rozmiar tablicy|
|[C6515](/cpp/code-quality/c6515)|Rozmiar buforu dla elementu nie będącego wskaźnikiem|
|[C6516](/cpp/code-quality/c6516)|Brak właściwości dla atrybutu|
|[C6517](/cpp/code-quality/c6517)|Prawidłowy rozmiar dla bufora bez możliwości odczytu|
|[C6518](/cpp/code-quality/c6518)|Rozmiar zapisywalny bufora bez możliwości zapisu|
|[C6522](/cpp/code-quality/c6522)|Nieprawidłowy typ ciągu rozmiaru|
|[C6525](/cpp/code-quality/c6525)|Nieprawidłowy ciąg rozmiaru nieosiągalnej lokalizacji|
|[C6527](/cpp/code-quality/c6527)|Nieprawidłowa Adnotacja: Właściwość "NeedsRelease" nie może być użyta dla wartości typu void|
|[C6530](/cpp/code-quality/c6530)|Nierozpoznany styl ciągu formatu|
|[C6540](/cpp/code-quality/c6540)|Użycie adnotacji atrybutów dla tej funkcji spowoduje unieważnienie wszystkich istniejących adnotacji __declspec|
|[C6551](/cpp/code-quality/c6551)|Nieprawidłowa specyfikacja rozmiaru: nie przeanalizować wyrażenia|
|[C6552](/cpp/code-quality/c6552)|Nieprawidłowe DEREF = lub Notref =: nie możliwy do przeanalizowania wyrażenia|
|[C6701](/cpp/code-quality/c6701)|Wartość nie jest prawidłową wartością tak/nie/może|
|[C6702](/cpp/code-quality/c6702)|Wartość nie jest wartością ciągu.|
|[C6703](/cpp/code-quality/c6703)|Wartość nie jest liczbą|
|[C6704](/cpp/code-quality/c6704)|Nieoczekiwany błąd wyrażenia adnotacji|
|[C6705](/cpp/code-quality/c6705)|Oczekiwana liczba argumentów adnotacji jest niezgodna z rzeczywistą liczbą argumentów dla adnotacji|
|[C6706](/cpp/code-quality/c6706)|Nieoczekiwany błąd adnotacji dla adnotacji|
|[C26450](/cpp/code-quality/C26450)|RESULT_OF_ARITHMETIC_OPERATION_PROVABLY_LOSSY|
|[C26451](/cpp/code-quality/C26451)|RESULT_OF_ARITHMETIC_OPERATION_CAST_TO_LARGER_SIZE|
|[C26452](/cpp/code-quality/C26452)|SHIFT_COUNT_NEGATIVE_OR_TOO_BIG|
|[C26453](/cpp/code-quality/C26453)|LEFTSHIFT_NEGATIVE_SIGNED_NUMBER|
|[C26454](/cpp/code-quality/C26454)|RESULT_OF_ARITHMETIC_OPERATION_NEGATIVE_UNSIGNED|
|[C26495](/cpp/code-quality/C26495)|MEMBER_UNINIT|
|[C28021](/cpp/code-quality/c28021)|Parametr, którego typem jest adnotacja, musi być wskaźnikiem|
|[C28182](/cpp/code-quality/c28182)|Wyłuskanie wskaźnika o wartości NULL. Wskaźnik zawiera taką samą wartość NULL jak inny wskaźnik.|
|[C28202](/cpp/code-quality/c28202)|Niedozwolone odwołanie do niestatycznej składowej|
|[C28203](/cpp/code-quality/c28203)|Niejednoznaczne odwołanie do składowej klasy.|
|[C28205](/cpp/code-quality/c28205)|\_Powodzenie \_ lub \_ w \_ przypadku niepowodzenia \_ używane w niedozwolonym kontekście|
|[C28206](/cpp/code-quality/c28206)|Lewy argument operacji wskazuje na strukturę, użyj "->"|
|[C28207](/cpp/code-quality/c28207)|Lewy argument operacji jest strukturą, użyj "."|
|[C28210](/cpp/code-quality/c28210)|Adnotacje dla kontekstu __on_failure nie mogą być w jawnym kontekście wstępnym|
|[C28211](/cpp/code-quality/c28211)|Oczekiwano nazwy kontekstu statycznego dla SAL_context|
|[C28212](/cpp/code-quality/c28212)|Oczekiwano wyrażenia wskaźnika dla adnotacji|
|[C28213](/cpp/code-quality/c28213)|\_ \_ Adnotacja use decl adnotacji \_ \_ musi być używana do odwoływania się, bez modyfikacji, wcześniejszej deklaracji.|
|[C28214](/cpp/code-quality/c28214)|Nazwy parametrów atrybutu muszą być P1... P9|
|[C28215](/cpp/code-quality/c28215)|Nie można zastosować typefix do parametru, który ma już typefix|
|[C28216](/cpp/code-quality/c28216)|Adnotacja Checkreturn dotyczy ma zastosowanie tylko do warunki końcowe dla określonego parametru funkcji.|
|[C28217](/cpp/code-quality/c28217)|W przypadku funkcji liczba parametrów do adnotacji jest niezgodna z znalezionymi w pliku|
|[C28218](/cpp/code-quality/c28218)|Dla parametru funkcji parametr adnotacji nie jest zgodny z znalezionym w pliku|
|[C28219](/cpp/code-quality/c28219)|Oczekiwano składowej wyliczenia dla adnotacji, parametr w adnotacji|
|[C28220](/cpp/code-quality/c28220)|Oczekiwano wyrażenia liczby całkowitej dla adnotacji, parametr w adnotacji|
|[C28221](/cpp/code-quality/c28221)|Oczekiwano wyrażenia ciągu dla parametru w adnotacji|
|[C28222](/cpp/code-quality/c28222)|\_oczekiwano __yes, _NO lub \_ _maybe dla adnotacji|
|[C28223](/cpp/code-quality/c28223)|Nie znaleziono oczekiwanego tokenu/identyfikatora dla adnotacji, parametr|
|[C28224](/cpp/code-quality/c28224)|Adnotacja wymaga parametrów|
|[C28225](/cpp/code-quality/c28225)|Nie znaleziono poprawnej liczby wymaganych parametrów w adnotacji|
|[C28226](/cpp/code-quality/c28226)|Adnotacja nie może być PrimOp (w bieżącej deklaracji)|
|[C28227](/cpp/code-quality/c28227)|Adnotacja nie może być PrimOp (patrz wcześniejsza deklaracja)|
|[C28228](/cpp/code-quality/c28228)|Parametr adnotacji: nie można użyć typu w adnotacjach|
|[C28229](/cpp/code-quality/c28229)|Adnotacja nie obsługuje parametrów|
|[C28230](/cpp/code-quality/c28230)|Typ parametru nie ma składowej.|
|[C28231](/cpp/code-quality/c28231)|Adnotacja jest prawidłowa tylko na tablicy|
|[C28232](/cpp/code-quality/c28232)|pre, post lub DEREF nie zostały zastosowane do żadnej adnotacji|
|[C28233](/cpp/code-quality/c28233)|pre, post lub DEREF zastosowany do bloku|
|[C28234](/cpp/code-quality/c28234)|wyrażenie __at nie ma zastosowania do bieżącej funkcji|
|[C28235](/cpp/code-quality/c28235)|Funkcja nie może być autonomiczna jako adnotacja|
|[C28236](/cpp/code-quality/c28236)|Nie można użyć adnotacji w wyrażeniu|
|[C28237](/cpp/code-quality/c28237)|Adnotacja w parametrze nie jest już obsługiwana|
|[C28238](/cpp/code-quality/c28238)|Adnotacja dla parametru ma więcej niż jedną wartość, stringValue i longValue. Użyj paramn = XXX|
|[C28239](/cpp/code-quality/c28239)|Adnotacja dla parametru ma wartość Value, stringValue lub longValue; i paramn = xxx. Używaj tylko paramn = XXX|
|[C28240](/cpp/code-quality/c28240)|Adnotacja dla parametru ma Param2, ale nie param1|
|[C28241](/cpp/code-quality/c28241)|Nie rozpoznano adnotacji dla funkcji w parametrze|
|[C28243](/cpp/code-quality/c28243)|Adnotacja dla funkcji dla parametru wymaga większej liczby odniesień, niż pozwala na to rzeczywisty typ z adnotacją|
|[C28245](/cpp/code-quality/c28245)|Adnotacja dla funkcji zawiera adnotacje "This" dla funkcji nie będącej składową|
|[C28246](/cpp/code-quality/c28246)|Adnotacja parametru funkcji jest niezgodna z typem parametru|
|[C28250](/cpp/code-quality/c28250)|Niespójna adnotacja dla funkcji: poprzednie wystąpienie zawiera błąd.|
|[C28251](/cpp/code-quality/c28251)|Niespójna adnotacja dla funkcji: to wystąpienie zawiera błąd.|
|[C28252](/cpp/code-quality/c28252)|Niespójna adnotacja dla funkcji: parametr ma inne adnotacje w tym wystąpieniu.|
|[C28253](/cpp/code-quality/c28253)|Niespójna adnotacja dla funkcji: parametr ma inne adnotacje w tym wystąpieniu.|
|[C28254](/cpp/code-quality/c28254)|dynamic_cast<> () nie jest obsługiwane w adnotacjach|
|[C28262](/cpp/code-quality/c28262)|Znaleziono błąd składniowy w adnotacji w funkcji dla adnotacji|
|[C28263](/cpp/code-quality/c28263)|Znaleziono błąd składni w adnotacji warunkowej dla wewnętrznej adnotacji|
|[C28267](/cpp/code-quality/c28267)|W adnotacji znaleziono błąd składni w funkcji.|
|[C28272](/cpp/code-quality/c28272)|Adnotacja dla funkcji, parametr podczas badania, jest niespójna z deklaracją funkcji|
|[C28273](/cpp/code-quality/c28273)|W przypadku funkcji wskazówki są niespójne z deklaracją funkcji|
|[C28275](/cpp/code-quality/c28275)|Parametr do \_ wartości makra \_ \_ ma wartość null.|
|[C28279](/cpp/code-quality/c28279)|Dla symbolu znaleziono "BEGIN" bez odpowiadającego mu "End"|
|[C28280](/cpp/code-quality/c28280)|Dla symbolu znaleziono element "End" bez odpowiadającego mu elementu "BEGIN|
|[C28282](/cpp/code-quality/c28282)|Ciągi formatu muszą znajdować się w warunkach wstępnych|
|[C28285](/cpp/code-quality/c28285)|Dla funkcji, błąd składni w parametrze|
|[C28286](/cpp/code-quality/c28286)|Dla funkcji, błąd składniowy blisko końca|
|[C28287](/cpp/code-quality/c28287)|Dla funkcji, błąd składni w \_ elemencie \_ adnotacji at () (Nierozpoznana Nazwa parametru)|
|[C28288](/cpp/code-quality/c28288)|Dla funkcji, błąd składni w \_ elemencie \_ Annotation () (Nieprawidłowa nazwa parametru)|
|[C28289](/cpp/code-quality/c28289)|Dla funkcji: ReadableTo lub WritableTo nie ma specyfikacji limitu jako parametru|
|[C28290](/cpp/code-quality/c28290)|Adnotacja dla funkcji zawiera więcej elementów zewnętrznych niż rzeczywista liczba parametrów|
|[C28291](/cpp/code-quality/c28291)|wpis o wartości null/notnull na poziomie DEREF 0 jest bezużyteczne dla funkcji.|
|[C28300](/cpp/code-quality/c28300)|Operandy wyrażenia niezgodnych typów dla operatora|
|[C28301](/cpp/code-quality/c28301)|Brak adnotacji dla pierwszej deklaracji funkcji.|
|[C28302](/cpp/code-quality/c28302)|Znaleziono dodatkowy \_ \_ operator DEREF w adnotacji.|
|[C28303](/cpp/code-quality/c28303)|\_Znaleziono niejednoznaczny \_ operator DEREF w adnotacji.|
|[C28304](/cpp/code-quality/c28304)|Znaleziono niepoprawnie umieszczony \_ operator Notref \_ został zastosowany do tokenu.|
|[C28305](/cpp/code-quality/c28305)|Wykryto błąd podczas analizowania tokenu.|
|[C28350](/cpp/code-quality/c28350)|Adnotacja zawiera opis sytuacji, która nie jest stosowana warunkowo.|
|[C28351](/cpp/code-quality/c28351)|Adnotacja opisuje, gdzie w warunku nie można używać wartości dynamicznej (zmiennej).|