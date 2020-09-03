---
title: Zestaw reguł Mixed Recommended Rules
ms.date: 11/04/2016
ms.topic: reference
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4ce28a8c1dd5c9ec510e4bf30b6e710b2b4dbc2a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "81649311"
---
# <a name="mixed-recommended-rules-rule-set"></a>Zestaw reguł Mixed Recommended Rules

Zastosowanie mieszanych reguł firmy Microsoft koncentruje się na typowych i krytycznych problemach w projektach języka C++, które obsługują środowisko uruchomieniowe języka wspólnego, w tym potencjalne luki w zabezpieczeniach, awarie aplikacji oraz inne ważne błędy logiki i projektowania. Ten zestaw reguł zawiera wszystkie reguły w zestawie reguł dla [mieszanych reguł minimalnych](mixed-minimum-rules-rule-set.md) .

Dołącz ten zestaw reguł do dowolnego niestandardowego zestawu reguł tworzonego dla projektów języka C++, które obsługują środowisko uruchomieniowe języka wspólnego.

|Reguła|Opis|
|----------|-----------------|
|[C6001](../code-quality/c6001.md)|Używanie niezainicjowanej pamięci|
|[C6011](../code-quality/c6011.md)|Wyłuskanie wskaźnika o wartości null|
|[C6029](../code-quality/c6029.md)|Użycie niesprawdzonej wartości|
|[C6031](../code-quality/c6031.md)|Wartość zwracana została zignorowana|
|[C6053](../code-quality/c6053.md)|Zakończenie zerowe od wywołania|
|[C6054](../code-quality/c6054.md)|Brak zakończenia zerowej|
|[C6059](../code-quality/c6059.md)|Złe łączenie|
|[C6063](../code-quality/c6063.md)|Brak argumentu ciągu do funkcji formatowania|
|[C6064](../code-quality/c6064.md)|Brak argumentu typu Integer dla funkcji formatowania|
|[C6066](../code-quality/c6066.md)|Brak argumentu wskaźnika dla funkcji formatowania|
|[C6067](../code-quality/c6067.md)|Brak argumentu wskaźnika ciągu do funkcji formatowania|
|[C6101](../code-quality/c6101.md)|Zwracanie niezainicjowanej pamięci|
|[C6200](../code-quality/c6200.md)|Indeks przekracza maksymalny rozmiar buforu|
|[C6201](../code-quality/c6201.md)|Indeks przekracza maksymalną wartość buforu stosu|
|[C6214](../code-quality/c6214.md)|Nieprawidłowe rzutowanie HRESULT do wartości LOGICZNEj|
|[C6215](../code-quality/c6215.md)|Nieprawidłowa wartość logiczna rzutowania do HRESULT|
|[C6216](../code-quality/c6216.md)|Nieprawidłowa wartość logiczna rzutowania wstawionego przez kompilator do HRESULT|
|[C6217](../code-quality/c6217.md)|Nieprawidłowy test HRESULT z|
|[C6220](../code-quality/c6220.md)|Nieprawidłowe porównanie HRESULT z-1|
|[C6226](../code-quality/c6226.md)|Nieprawidłowe przypisanie HRESULT do-1|
|[C6230](../code-quality/c6230.md)|Nieprawidłowe użycie HRESULT jako wartości logicznej|
|[C6235](../code-quality/c6235.md)|Stała niezerowa z wartością logiczną lub|
|[C6236](../code-quality/c6236.md)|Logiczna — lub z niezerową stałą|
|[C6237](../code-quality/c6237.md)|Zero ze koniunkcją logiczną i powoduje utratę efektów ubocznych|
|[C6242](../code-quality/c6242.md)|Wymuszone lokalne rozwinięcie|
|[C6248](../code-quality/c6248.md)|Tworzenie listy DACL o wartości null|
|[C6250](../code-quality/c6250.md)|Niezwolnione deskryptory adresów|
|[C6255](../code-quality/c6255.md)|Niechronione użycie alloca|
|[C6258](../code-quality/c6258.md)|Korzystanie z wątku przerywania|
|[C6259](../code-quality/c6259.md)|Martwy kod w przełączniku bitowym lub ograniczonym|
|[C6260](../code-quality/c6260.md)|Użycie arytmetyki bajtowej|
|[C6262](../code-quality/c6262.md)|Nadmierne użycie stosu|
|[C6263](../code-quality/c6263.md)|Korzystanie z usługi alloca w pętli|
|[C6268](../code-quality/c6268.md)|Brak nawiasów w rzutowaniu|
|[C6269](../code-quality/c6269.md)|Zignorowano odwołanie do wskaźnika|
|[C6270](../code-quality/c6270.md)|Brak argumentu zmiennoprzecinkowego do funkcji formatowania|
|[C6271](../code-quality/c6271.md)|Dodatkowy argument funkcji formatowania|
|[C6272](../code-quality/c6272.md)|Argument inny niż zmiennoprzecinkowy do formatowania funkcji|
|[C6273](../code-quality/c6273.md)|Argument niebędący liczbą całkowitą do sformatowania funkcji|
|[C6274](../code-quality/c6274.md)|Argument niebędący znakiem do funkcji formatowania|
|[C6276](../code-quality/c6276.md)|Nieprawidłowe rzutowanie ciągu|
|[C6277](../code-quality/c6277.md)|Nieprawidłowe wywołanie metody CreateProcess|
|[C6278](../code-quality/c6278.md)|Niezgodność Array-New skalarna Delete|
|[C6279](../code-quality/c6279.md)|Skalarna — niezgodność z nową tablicą|
|[C6280](../code-quality/c6280.md)|Niezgodność alokacji pamięci|
|[C6281](../code-quality/c6281.md)|Pierwszeństwo relacji bitowej|
|[C6282](../code-quality/c6282.md)|Przypisanie zastępuje test|
|[C6283](../code-quality/c6283.md)|Niezgodność z tablicą pierwotną — Nowa funkcja skalarna usuwania|
|[C6284](../code-quality/c6284.md)|Nieprawidłowy argument obiektu dla funkcji formatowania|
|[C6285](../code-quality/c6285.md)|Logiczne-lub stałe|
|[C6286](../code-quality/c6286.md)|Niezerowe logiczne lub utrata efektów ubocznych|
|[C6287](../code-quality/c6287.md)|Test nadmiarowy|
|[C6288](../code-quality/c6288.md)|Wzajemne włączenie przy użyciu operatora logicznego i ma wartość false|
|[C6289](../code-quality/c6289.md)|Wzajemne wykluczenie z użyciem operatora logicznego OR jest prawdziwe|
|[C6290](../code-quality/c6290.md)|Niestandardowa koniunkcja logiczna|
|[C6291](../code-quality/c6291.md)|Niestandardowa koniunkcja logiczna|
|[C6292](../code-quality/c6292.md)|Pętla zlicza w górę od maksimum|
|[C6293](../code-quality/c6293.md)|Pętla liczy w dół od minimum|
|[C6294](../code-quality/c6294.md)|Treść pętli nigdy nie została wykonana|
|[C6295](../code-quality/c6295.md)|Nieskończona pętla|
|[C6296](../code-quality/c6296.md)|Pętla zostanie wykonana tylko raz|
|[C6297](../code-quality/c6297.md)|Wynik rzutowania przesunięcia na większy rozmiar|
|[C6299](../code-quality/c6299.md)|Porównanie pole bitowe z wartością logiczną|
|[C6302](../code-quality/c6302.md)|Nieprawidłowy argument ciągu znaków dla funkcji formatowania|
|[C6303](../code-quality/c6303.md)|Nieprawidłowy argument ciągu znaków dwubajtowych do funkcji formatowania|
|[C6305](../code-quality/c6305.md)|Użycie niedopasowanego rozmiaru i liczby|
|[C6306](../code-quality/c6306.md)|Nieprawidłowe wywołanie funkcji zmiennej argumentu|
|[C6308](../code-quality/c6308.md)|Przeciek realloc|
|[C6310](../code-quality/c6310.md)|Niedozwolona stała filtru wyjątków|
|[C6312](../code-quality/c6312.md)|Pętla kontynuacji wykonywania wyjątków|
|[C6314](../code-quality/c6314.md)|Pierwszeństwo bitowe|
|[C6317](../code-quality/c6317.md)|Nie uzupełniaj|
|[C6318](../code-quality/c6318.md)|Wyjątek — Kontynuuj wyszukiwanie|
|[C6319](../code-quality/c6319.md)|Zignorowane przez przecinek|
|[C6324](../code-quality/c6324.md)|Kopiowanie ciągu zamiast porównywania ciągów|
|[C6328](../code-quality/c6328.md)|Niezgodność typu argumentu potencjalnego|
|[C6331](../code-quality/c6331.md)|VirtualFree nieprawidłowe flagi|
|[C6332](../code-quality/c6332.md)|VirtualFree nieprawidłowy parametr|
|[C6333](../code-quality/c6333.md)|Nieprawidłowy rozmiar VirtualFree|
|[C6335](../code-quality/c6335.md)|Przeciek uchwytu procesu|
|[C6381](../code-quality/c6381.md)|Brak informacji o zamknięciu|
|[C6383](../code-quality/c6383.md)|Przepełnienie buforu liczby elementów-count|
|[C6384](../code-quality/c6384.md)|Dzielenie rozmiaru wskaźnika|
|[C6385](../code-quality/c6385.md)|Przepełnienie odczytu|
|[C6386](../code-quality/c6386.md)|Przepełnienie zapisu|
|[C6387](../code-quality/c6387.md)|Nieprawidłowa wartość parametru|
|[C6388](../code-quality/c6388.md)|Nieprawidłowa wartość parametru|
|[C6500](../code-quality/c6500.md)|Nieprawidłowa właściwość atrybutu|
|[C6501](../code-quality/c6501.md)|Sprzeczne wartości właściwości atrybutów|
|[C6503](../code-quality/c6503.md)|Odwołania nie mogą być puste|
|[C6504](../code-quality/c6504.md)|Wartość zerowa przy niewskaźniku|
|[C6505](../code-quality/c6505.md)|MustCheck na void|
|[C6506](../code-quality/c6506.md)|Rozmiar buforu dla elementu nie będącego wskaźnikiem lub tablicą|
|[C6508](../code-quality/c6508.md)|Dostęp do zapisu dla stałej|
|[C6509](../code-quality/c6509.md)|Return użyty w warunku wstępnym|
|[C6510](../code-quality/c6510.md)|Przerwano wartość null dla niebędącego wskaźnikiem|
|[C6511](../code-quality/c6511.md)|MustCheck musi mieć wartość yes lub No|
|[C6513](../code-quality/c6513.md)|Rozmiar elementu bez rozmiaru buforu|
|[C6514](../code-quality/c6514.md)|Rozmiar buforu przekracza rozmiar tablicy|
|[C6515](../code-quality/c6515.md)|Rozmiar buforu dla elementu nie będącego wskaźnikiem|
|[C6516](../code-quality/c6516.md)|Brak właściwości dla atrybutu|
|[C6517](../code-quality/c6517.md)|Prawidłowy rozmiar dla bufora bez możliwości odczytu|
|[C6518](../code-quality/c6518.md)|Rozmiar zapisywalny bufora bez możliwości zapisu|
|[C6522](../code-quality/c6522.md)|Nieprawidłowy typ ciągu rozmiaru|
|[C6525](../code-quality/c6525.md)|Nieprawidłowy ciąg rozmiaru nieosiągalnej lokalizacji|
|[C6527](../code-quality/c6527.md)|Nieprawidłowa Adnotacja: Właściwość "NeedsRelease" nie może być użyta dla wartości typu void|
|[C6530](../code-quality/c6530.md)|Nierozpoznany styl ciągu formatu|
|[C6540](../code-quality/c6540.md)|Użycie adnotacji atrybutów dla tej funkcji spowoduje unieważnienie wszystkich istniejących adnotacji __declspec|
|[C6551](../code-quality/c6551.md)|Nieprawidłowa specyfikacja rozmiaru: nie przeanalizować wyrażenia|
|[C6552](../code-quality/c6552.md)|Nieprawidłowe DEREF = lub Notref =: nie możliwy do przeanalizowania wyrażenia|
|[C6701](../code-quality/c6701.md)|Wartość nie jest prawidłową wartością tak/nie/może|
|[C6702](../code-quality/c6702.md)|Wartość nie jest wartością ciągu.|
|[C6703](../code-quality/c6703.md)|Wartość nie jest liczbą|
|[C6704](../code-quality/c6704.md)|Nieoczekiwany błąd wyrażenia adnotacji|
|[C6705](../code-quality/c6705.md)|Oczekiwana liczba argumentów adnotacji jest niezgodna z rzeczywistą liczbą argumentów dla adnotacji|
|[C6706](../code-quality/c6706.md)|Nieoczekiwany błąd adnotacji dla adnotacji|
|[C6995](../code-quality/c6995.md)|Nie można zapisać pliku dziennika XML|
|[C26100](../code-quality/c26100.md)|Sytuacja wyścigu|
|[C26101](../code-quality/c26101.md)|Nie można prawidłowo użyć operacji zablokowanej|
|[C26110](../code-quality/c26110.md)|Wystąpił błąd blokady wywołującej|
|[C26111](../code-quality/c26111.md)|Obiekt wywołujący nie może zwolnić blokady|
|[C26112](../code-quality/c26112.md)|Obiekt wywołujący nie może blokować żadnej blokady|
|[C26115](../code-quality/c26115.md)|Niepowodzenie zwolnienia blokady|
|[C26116](../code-quality/c26116.md)|Nie można uzyskać lub wstrzymać blokady|
|[C26117](../code-quality/c26117.md)|Zwalnianie niezautrzymywanej blokady|
|[C26140](../code-quality/c26140.md)|Błąd adnotacji dotyczącej współbieżności SAL|
|[C28020](../code-quality/c28020.md)|Wyrażenie nie jest prawdziwe w tym wywołaniu|
|[C28021](../code-quality/c28021.md)|Parametr, którego typem jest adnotacja, musi być wskaźnikiem|
|[C28022](../code-quality/c28022.md)|Klasy funkcji w tej funkcji nie są zgodne z klasami funkcji dla elementu typedef użytego do jego zdefiniowania.|
|[C28023](../code-quality/c28023.md)|Przypisana lub przenoszona funkcja powinna mieć \_ \_ \_ adnotację klasy funkcji dla co najmniej jednej z klas (ES)|
|[C28024](../code-quality/c28024.md)|Wskaźnik funkcji, do której jest przypisany, ma adnotację z klasą funkcji, która nie znajduje się na liście klas funkcji.|
|[C28039](../code-quality/c28039.md)|Typ rzeczywistego parametru powinien dokładnie pasować do typu|
|[C28112](../code-quality/c28112.md)|Do zmiennej, do której uzyskuje się dostęp za pośrednictwem funkcji zablokowaniej, zawsze należy uzyskać dostęp za pośrednictwem funkcji Zablokowani.|
|[C28113](../code-quality/c28113.md)|Uzyskiwanie dostępu do zmiennej lokalnej przez zablokowaną funkcję|
|[C28125](../code-quality/c28125.md)|Funkcja musi być wywołana z poziomu bloku try/except|
|[C28137](../code-quality/c28137.md)|Zmienna argument powinien zamiast niego być (literałem)|
|[C28138](../code-quality/c28138.md)|Argument stałej powinien zamiast tego mieć wartość zmienna|
|[C28159](../code-quality/c28159.md)|Zamiast tego Rozważ użycie innej funkcji.|
|[C28160](../code-quality/c28160.md)|Błąd adnotacji|
|[C28163](../code-quality/c28163.md)|Funkcja nigdy nie powinna być wywoływana z wewnątrz bloku try/except|
|[C28164](../code-quality/c28164.md)|Argument jest przesyłany do funkcji, która oczekuje wskaźnika do obiektu (nie wskaźnika do wskaźnika)|
|[C28182](../code-quality/c28182.md)|Wyłuskanie wskaźnika o wartości NULL. Wskaźnik zawiera taką samą wartość NULL jak inny wskaźnik.|
|[C28183](../code-quality/c28183.md)|Argument może być jedną wartością i jest kopią wartości znalezionej we wskaźniku|
|[C28193](../code-quality/c28193.md)|Zmienna przechowuje wartość, która musi być zbadana|
|[C28196](../code-quality/c28196.md)|Wymaganie nie jest spełnione. (Wyrażenie nie jest szacowane na wartość true).|
|[C28202](../code-quality/c28202.md)|Niedozwolone odwołanie do niestatycznej składowej|
|[C28203](../code-quality/c28203.md)|Niejednoznaczne odwołanie do składowej klasy.|
|[C28205](../code-quality/c28205.md)|\_Powodzenie \_ lub \_ w \_ przypadku niepowodzenia \_ używane w niedozwolonym kontekście|
|[C28206](../code-quality/c28206.md)|Lewy argument operacji wskazuje na strukturę, użyj "->"|
|[C28207](../code-quality/c28207.md)|Lewy argument operacji jest strukturą, użyj "."|
|[C28209](../code-quality/c28209.md)|Deklaracja symbolu ma sprzeczną deklarację|
|[C28210](../code-quality/c28210.md)|Adnotacje dla kontekstu __on_failure nie mogą być w jawnym kontekście wstępnym|
|[C28211](../code-quality/c28211.md)|Oczekiwano nazwy kontekstu statycznego dla SAL_context|
|[C28212](../code-quality/c28212.md)|Oczekiwano wyrażenia wskaźnika dla adnotacji|
|[C28213](../code-quality/c28213.md)|\_ \_ Adnotacja use decl adnotacji \_ \_ musi być używana do odwoływania się, bez modyfikacji, wcześniejszej deklaracji.|
|[C28214](../code-quality/c28214.md)|Nazwy parametrów atrybutu muszą być P1... P9|
|[C28215](../code-quality/c28215.md)|Nie można zastosować typefix do parametru, który ma już typefix|
|[C28216](../code-quality/c28216.md)|Adnotacja Checkreturn dotyczy ma zastosowanie tylko do warunki końcowe dla określonego parametru funkcji.|
|[C28217](../code-quality/c28217.md)|W przypadku funkcji liczba parametrów do adnotacji jest niezgodna z znalezionymi w pliku|
|[C28218](../code-quality/c28218.md)|Dla parametru funkcji parametr adnotacji nie jest zgodny z znalezionym w pliku|
|[C28219](../code-quality/c28219.md)|Oczekiwano składowej wyliczenia dla adnotacji, parametr w adnotacji|
|[C28220](../code-quality/c28220.md)|Oczekiwano wyrażenia liczby całkowitej dla adnotacji, parametr w adnotacji|
|[C28221](../code-quality/c28221.md)|Oczekiwano wyrażenia ciągu dla parametru w adnotacji|
|[C28222](../code-quality/c28222.md)|\_oczekiwano __yes, _NO lub \_ _maybe dla adnotacji|
|[C28223](../code-quality/c28223.md)|Nie znaleziono oczekiwanego tokenu/identyfikatora dla adnotacji, parametr|
|[C28224](../code-quality/c28224.md)|Adnotacja wymaga parametrów|
|[C28225](../code-quality/c28225.md)|Nie znaleziono poprawnej liczby wymaganych parametrów w adnotacji|
|[C28226](../code-quality/c28226.md)|Adnotacja nie może być PrimOp (w bieżącej deklaracji)|
|[C28227](../code-quality/c28227.md)|Adnotacja nie może być PrimOp (patrz wcześniejsza deklaracja)|
|[C28228](../code-quality/c28228.md)|Parametr adnotacji: nie można użyć typu w adnotacjach|
|[C28229](../code-quality/c28229.md)|Adnotacja nie obsługuje parametrów|
|[C28230](../code-quality/c28230.md)|Typ parametru nie ma składowej.|
|[C28231](../code-quality/c28231.md)|Adnotacja jest prawidłowa tylko na tablicy|
|[C28232](../code-quality/c28232.md)|pre, post lub DEREF nie zostały zastosowane do żadnej adnotacji|
|[C28233](../code-quality/c28233.md)|pre, post lub DEREF zastosowany do bloku|
|[C28234](../code-quality/c28234.md)|wyrażenie __at nie ma zastosowania do bieżącej funkcji|
|[C28235](../code-quality/c28235.md)|Funkcja nie może być autonomiczna jako adnotacja|
|[C28236](../code-quality/c28236.md)|Nie można użyć adnotacji w wyrażeniu|
|[C28237](../code-quality/c28237.md)|Adnotacja w parametrze nie jest już obsługiwana|
|[C28238](../code-quality/c28238.md)|Adnotacja dla parametru ma więcej niż jedną wartość, stringValue i longValue. Użyj paramn = XXX|
|[C28239](../code-quality/c28239.md)|Adnotacja dla parametru ma wartość Value, stringValue lub longValue; i paramn = xxx. Używaj tylko paramn = XXX|
|[C28240](../code-quality/c28240.md)|Adnotacja dla parametru ma Param2, ale nie param1|
|[C28241](../code-quality/c28241.md)|Nie rozpoznano adnotacji dla funkcji w parametrze|
|[C28243](../code-quality/c28243.md)|Adnotacja dla funkcji dla parametru wymaga większej liczby odniesień, niż pozwala na to rzeczywisty typ z adnotacją|
|[C28244](../code-quality/c28244.md)|Adnotacja dla funkcji ma niemożliwy do przeanalizowania parametr/zewnętrzną adnotację|
|[C28245](../code-quality/c28245.md)|Adnotacja dla funkcji zawiera adnotacje "This" dla funkcji nie będącej składową|
|[C28246](../code-quality/c28246.md)|Adnotacja parametru funkcji jest niezgodna z typem parametru|
|[C28250](../code-quality/c28250.md)|Niespójna adnotacja dla funkcji: poprzednie wystąpienie zawiera błąd.|
|[C28251](../code-quality/c28251.md)|Niespójna adnotacja dla funkcji: to wystąpienie zawiera błąd.|
|[C28252](../code-quality/c28252.md)|Niespójna adnotacja dla funkcji: parametr ma inne adnotacje w tym wystąpieniu.|
|[C28253](../code-quality/c28253.md)|Niespójna adnotacja dla funkcji: parametr ma inne adnotacje w tym wystąpieniu.|
|[C28254](../code-quality/c28254.md)|dynamic_cast<> () nie jest obsługiwane w adnotacjach|
|[C28262](../code-quality/c28262.md)|Znaleziono błąd składniowy w adnotacji w funkcji dla adnotacji|
|[C28263](../code-quality/c28263.md)|Znaleziono błąd składni w adnotacji warunkowej dla wewnętrznej adnotacji|
|[C28267](../code-quality/c28267.md)|W adnotacji znaleziono błąd składni w funkcji.|
|[C28272](../code-quality/c28272.md)|Adnotacja dla funkcji, parametr podczas badania, jest niespójna z deklaracją funkcji|
|[C28273](../code-quality/c28273.md)|W przypadku funkcji wskazówki są niespójne z deklaracją funkcji|
|[C28275](../code-quality/c28275.md)|Parametr do \_ wartości makra \_ \_ ma wartość null.|
|[C28279](../code-quality/c28279.md)|Dla symbolu znaleziono "BEGIN" bez odpowiadającego mu "End"|
|[C28280](../code-quality/c28280.md)|Dla symbolu znaleziono element "End" bez odpowiadającego mu elementu "BEGIN|
|[C28282](../code-quality/c28282.md)|Ciągi formatu muszą znajdować się w warunkach wstępnych|
|[C28285](../code-quality/c28285.md)|Dla funkcji, błąd składni w parametrze|
|[C28286](../code-quality/c28286.md)|Dla funkcji, błąd składniowy blisko końca|
|[C28287](../code-quality/c28287.md)|Dla funkcji, błąd składni w \_ elemencie \_ adnotacji at () (Nierozpoznana Nazwa parametru)|
|[C28288](../code-quality/c28288.md)|Dla funkcji, błąd składni w \_ elemencie \_ Annotation () (Nieprawidłowa nazwa parametru)|
|[C28289](../code-quality/c28289.md)|Dla funkcji: ReadableTo lub WritableTo nie ma specyfikacji limitu jako parametru|
|[C28290](../code-quality/c28290.md)|Adnotacja dla funkcji zawiera więcej elementów zewnętrznych niż rzeczywista liczba parametrów|
|[C28291](../code-quality/c28291.md)|wpis o wartości null/notnull na poziomie DEREF 0 jest bezużyteczne dla funkcji.|
|[C28300](../code-quality/c28300.md)|Operandy wyrażenia niezgodnych typów dla operatora|
|[C28301](../code-quality/c28301.md)|Brak adnotacji dla pierwszej deklaracji funkcji.|
|[C28302](../code-quality/c28302.md)|Znaleziono dodatkowy \_ \_ operator DEREF w adnotacji.|
|[C28303](../code-quality/c28303.md)|\_Znaleziono niejednoznaczny \_ operator DEREF w adnotacji.|
|[C28304](../code-quality/c28304.md)|Znaleziono niepoprawnie umieszczony \_ operator Notref \_ został zastosowany do tokenu.|
|[C28305](../code-quality/c28305.md)|Wykryto błąd podczas analizowania tokenu.|
|[C28306](../code-quality/c28306.md)|Adnotacja dla parametru jest przestarzała|
|[C28307](../code-quality/c28307.md)|Adnotacja dla parametru jest przestarzała|
|[C28350](../code-quality/c28350.md)|Adnotacja zawiera opis sytuacji, która nie jest stosowana warunkowo.|
|[C28351](/cpp/code-quality/c28351)|Adnotacja opisuje, gdzie w warunku nie można używać wartości dynamicznej (zmiennej).|
|[CA1001](../code-quality/ca1001.md)|Typy, do których należą pola możliwe do likwidacji, powinny być możliwe do likwidacji|
|[CA1009](../code-quality/ca1009.md)|Poprawnie deklaruj procedury obsługi zdarzeń|
|[CA1016](../code-quality/ca1016.md)|Oznacz zestawy atrybutem AssemblyVersion|
|[CA1033](../code-quality/ca1033.md)|Metody interfejsu powinny móc zostać wywołane przez typy podrzędne|
|[CA1049](../code-quality/ca1049.md)|Typy, do których należą natywne zasoby, powinny być możliwe do likwidacji|
|[CA1060](../code-quality/ca1060.md)|Przenieś metody P/Invoke do klasy NativeMethods|
|[CA1061](../code-quality/ca1061.md)|Nie ukrywaj metod klasy bazowej|
|[CA1063](../code-quality/ca1063.md)|Poprawnie zaimplementuj interfejs IDisposable|
|[CA1065](../code-quality/ca1065.md)|Nie wywołuj wyjątków w nieoczekiwanych lokalizacjach|
|[CA1301](../code-quality/ca1301.md)|Unikaj duplikowania akceleratorów|
|[CA1400](../code-quality/ca1400.md)|Punkty wejścia P/Invoke powinny istnieć|
|[CA1401](../code-quality/ca1401.md)|Elementy P/Invoke nie powinny być widoczne|
|[CA1403](../code-quality/ca1403.md)|Typy z automatycznym układem nie powinny być widoczne dla modelu COM|
|[CA1404](../code-quality/ca1404.md)|Wywołaj metodę GetLastError bezpośrednio po elemencie P/Invoke|
|[CA1405](../code-quality/ca1405.md)|Typy podstawowe typów widocznych dla modelu COM powinny być widoczne dla modelu COM|
|[CA1410](../code-quality/ca1410.md)|Metody rejestracji modelu COM powinny mieć swoje odpowiedniki|
|[CA1415](../code-quality/ca1415.md)|Poprawnie zadeklaruj elementy P/Invoke|
|[CA1821](../code-quality/ca1821.md)|Usuwaj puste finalizatory|
|[CA1900](../code-quality/ca1900.md)|Pola typu wartości powinny być przenośne|
|[CA1901](../code-quality/ca1901.md)|Deklaracje metody P/Invoke powinny być przenośne|
|[CA2002](../code-quality/ca2002.md)|Nie blokuj obiektów o słabej tożsamości|
|[CA2100](../code-quality/ca2100.md)|Sprawdź zapytania SQL pod kątem luk w zabezpieczeniach|
|[CA2101](../code-quality/ca2101.md)|Określ kierowanie dla argumentów ciągu P/Invoke|
|[CA2108](../code-quality/ca2108.md)|Przejrzyj zabezpieczenia deklaratywne dla typów wartości|
|[CA2111](../code-quality/ca2111.md)|Wskaźniki nie powinny być widoczne|
|[CA2112](../code-quality/ca2112.md)|Zabezpieczone typy nie powinny ujawniać pól|
|[CA2114](../code-quality/ca2114.md)|Zabezpieczenie metody powinno być nadzbiorem typu|
|[CA2116](../code-quality/ca2116.md)|Metody z atrybutem APTCA powinny wywoływać tylko metody z atrybutem APTCA|
|[CA2117](../code-quality/ca2117.md)|Typy z atrybutem APTCA powinny rozszerzać tylko typy podstawowe z atrybutem APTCA|
|[CA2122](../code-quality/ca2122.md)|Nie ujawniaj pośrednio metod żądaniami LinkDemand|
|[CA2123](../code-quality/ca2123.md)|Przesłonięcia żądań konsolidacji powinny być identyczne z podstawowymi|
|[CA2124](../code-quality/ca2124.md)|Opakuj podatne na przejęcie klauzule finally w zewnętrzny blok try|
|[CA2126](../code-quality/ca2126.md)|Żądania LinkDemand dla typu wymagają żądań dziedziczenia|
|[CA2131](../code-quality/ca2131.md)|Typy krytyczne pod względem zabezpieczeń nie mogą brać udziału w określaniu równoważności typów|
|[CA2132](../code-quality/ca2132.md)|Konstruktory domyślne muszą być co najmniej tak krytyczne jak konstruktory domyślne typu podstawowego|
|[CA2133](../code-quality/ca2133.md)|Delegaci muszą być powiązani z metodami ze spójną przezroczystością|
|[CA2134](../code-quality/ca2134.md)|Metody muszą zachowywać spójną przezroczystość podczas nadpisywania metod bazowych|
|[CA2137](../code-quality/ca2137.md)|Metody przezroczyste muszą zawierać tylko weryfikowalny język pośredni|
|[CA2138](../code-quality/ca2138.md)|Metody przezroczyste nie mogą wywoływać metod z atrybutem SuppressUnmanagedCodeSecurity|
|[CA2140](../code-quality/ca2140.md)|Kod przezroczysty nie może przywoływać elementów krytycznych pod względem zabezpieczeń|
|[CA2141](../code-quality/ca2141.md)|Metody przezroczyste nie mogą spełniać LinkDemands|
|[CA2146](../code-quality/ca2146.md)|Typy muszą być co najmniej tak krytyczne jak ich typy i interfejsy podstawowe|
|[CA2147](../code-quality/ca2147.md)|Metody przezroczyste nie mogą używać asercji zabezpieczeń|
|[CA2149](../code-quality/ca2149.md)|Metody przezroczyste nie mogą wywoływać kodu natywnego|
|[CA2200](../code-quality/ca2200.md)|Ponowie zgłoś wyjątek, aby zachować szczegóły stosu|
|[CA2202](../code-quality/ca2202.md)|Nie likwiduj obiektów wielokrotnie|
|[CA2207](../code-quality/ca2207.md)|Pola statyczne typu wartości inicjuj bezpośrednio|
|[CA2212](../code-quality/ca2212.md)|Nie oznaczaj składników usługi atrybutem WebMethod|
|[CA2213](../code-quality/ca2213.md)|Pola możliwe do likwidacji należy likwidować|
|[CA2214](../code-quality/ca2214.md)|Nie wywołuj w konstruktorach metod, które można przesłaniać|
|[CA2216](../code-quality/ca2216.md)|Typy możliwe do likwidacji powinny deklarować finalizator|
|[CA2220](../code-quality/ca2220.md)|Finalizatory powinny wywoływać finalizator klasy bazowej|
|[CA2229](../code-quality/ca2229.md)|Zaimplementuj konstruktory serializacji|
|[CA2231](../code-quality/ca2231.md)|Przeciążaj operator równości w przypadku przesłaniania metody ValueType.Equals|
|[CA2232](../code-quality/ca2232.md)|Oznacz punkty wejścia modelu Windows Forms atrybutem STAThread|
|[CA2235](../code-quality/ca2235.md)|Oznacz wszystkie pola nieprzeznaczone do serializacji|
|[CA2236](../code-quality/ca2236.md)|Wywołuj metody klasy bazowej dla typów ISerializable|
|[CA2237](../code-quality/ca2237.md)|Oznacz typy ISerializable atrybutem SerializableAttribute|
|[CA2238](../code-quality/ca2238.md)|Poprawnie implementuj metody serializacji|
|[CA2240](../code-quality/ca2240.md)|Poprawnie zaimplementuj interfejs ISerializable|
|[CA2241](../code-quality/ca2241.md)|Podaj poprawne argumenty metod formatowania|
|[CA2242](../code-quality/ca2242.md)|Poprawnie testuj nie-liczby (NaN)|
