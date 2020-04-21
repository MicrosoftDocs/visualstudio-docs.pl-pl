---
title: Zestaw reguł macierzystych reguł zalecanych
ms.date: 11/04/2016
ms.topic: reference
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4a86cb62fe0ae0db971a417ef923f45eedbefe0c
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649294"
---
# <a name="native-recommended-rules-rule-set"></a>Zestaw reguł macierzystych reguł zalecanych

Reguły natywne zalecane koncentrują się na najbardziej krytycznych i typowych problemów w kodzie macierzystym, w tym potencjalnych luk w zabezpieczeniach i awarii aplikacji. Ten zestaw reguł zawiera wszystkie reguły w zestawie reguł [reguł minimalnych reguł natywnych.](native-minimum-rules-rule-set.md)

Uwzględnij ten zestaw reguł w dowolnym niestandardowym zestawie reguł utworzonym dla projektów natywnych.

|Reguła|Opis|
|----------|-----------------|
|[C6001](../code-quality/c6001.md)|Korzystanie z pamięci niezajednawizowanej|
|[C6011](../code-quality/c6011.md)|Wskaźnik null dereferencing|
|[C6029](../code-quality/c6029.md)|Korzystanie z niezaznaczonewartości|
|[C6031](../code-quality/c6031.md)|Ignorowana wartość zwracana|
|[C6053](../code-quality/c6053.md)|Zero zakończenia od połączenia|
|[C6054](../code-quality/c6054.md)|Brak zakończenia zerowego|
|[C6059](../code-quality/c6059.md)|Złe łączenie|
|[C6063](../code-quality/c6063.md)|Brak argumentu ciąg do formatowania funkcji|
|[C6064](../code-quality/c6064.md)|Brak argumentu liczby całkowitej do formatowania funkcji|
|[C6066](../code-quality/c6066.md)|Brak argumentu wskaźnika do formatowania funkcji|
|[C6067](../code-quality/c6067.md)|Brak argumentu wskaźnika ciągu do formatowania funkcji|
|[C6101](../code-quality/c6101.md)|Zwracanie niezainicjowanej pamięci|
|[C6200](../code-quality/c6200.md)|Indeks przekracza maksymalną wartość buforu|
|[C6201](../code-quality/c6201.md)|Indeks przekracza maksymalną bufor stosu|
|[C6214](../code-quality/c6214.md)|Nieprawidłowe rzutowanie HRESULT do BOOL|
|[C6215](../code-quality/c6215.md)|Nieprawidłowy rzut BOOL do HRESULT|
|[C6216](../code-quality/c6216.md)|Nieprawidłowy kompilator-wstawiony oddanych BOOL do HRESULT|
|[C6217](../code-quality/c6217.md)|Nieprawidłowy test HRESULT z not|
|[C6220](../code-quality/c6220.md)|Nieprawidłowe porównanie HRESULT do -1|
|[C6226](../code-quality/c6226.md)|Nieprawidłowe przypisanie HRESULT do -1|
|[C6230](../code-quality/c6230.md)|Nieprawidłowe użycie HRESULT jako wartości logicznej|
|[C6235](../code-quality/c6235.md)|Stała niezerowa z logiczną lub logiczną|
|[C6236](../code-quality/c6236.md)|Logiczne lub ze stałą niezerową|
|[C6237](../code-quality/c6237.md)|Zero z logicznego i traci skutki uboczne|
|[C6242](../code-quality/c6242.md)|Lokalne unwind wymuszone|
|[C6248](../code-quality/c6248.md)|Tworzenie null DACL|
|[C6250](../code-quality/c6250.md)|Niepublikowane deskryptory adresów|
|[C6255](../code-quality/c6255.md)|Niechronione stosowanie alloca|
|[C6258](../code-quality/c6258.md)|Korzystanie z wątku zakończenia|
|[C6259](../code-quality/c6259.md)|Martwy kod w przełączniku bitowym lub ograniczonym|
|[C6260](../code-quality/c6260.md)|Stosowanie arytmetyki bajtowej|
|[C6262](../code-quality/c6262.md)|Nadmierne użycie stosu|
|[C6263](../code-quality/c6263.md)|Korzystanie z alloca w pętli|
|[C6268](../code-quality/c6268.md)|Brak nawiasów w obsadzie|
|[C6269](../code-quality/c6269.md)|Wyłuskanie wskaźnika ignorowane|
|[C6270](../code-quality/c6270.md)|Brak argumentu float do formatowania funkcji|
|[C6271](../code-quality/c6271.md)|Dodatkowy argument do formatowania funkcji|
|[C6272](../code-quality/c6272.md)|Argument Non-Float do formatowania funkcji|
|[C6273](../code-quality/c6273.md)|Argument niekłacji całkowitej do formatowania funkcji|
|[C6274](../code-quality/c6274.md)|Argument bez znaku do formatowania funkcji|
|[C6276](../code-quality/c6276.md)|Nieprawidłowe rzutnie ciągiem|
|[C6277](../code-quality/c6277.md)|Nieprawidłowe wywołanie createprocess|
|[C6278](../code-quality/c6278.md)|Rozbieżność scalar-delete (nowa skalar-usuń)|
|[C6279](../code-quality/c6279.md)|Scalar-Nowa tablica-Usuń niezgodność|
|[C6280](../code-quality/c6280.md)|Niezgodność alokacji alokacji alokacji pamięci|
|[C6281](../code-quality/c6281.md)|Pierwszeństwo relacji bitowych|
|[C6282](../code-quality/c6282.md)|Przypisanie zastępuje test|
|[C6283](../code-quality/c6283.md)|Prymitywne tablicy-Nowy scalar-delete niezgodność|
|[C6284](../code-quality/c6284.md)|Nieprawidłowy argument obiektu do formatowania funkcji|
|[C6285](../code-quality/c6285.md)|Logiczne lub stałe|
|[C6286](../code-quality/c6286.md)|Non-Zero logiczne lub utraty skutków ubocznych|
|[C6287](../code-quality/c6287.md)|Test nadmiarowy|
|[C6288](../code-quality/c6288.md)|Wzajemne włączenie ponad logiczne i jest fałszywe|
|[C6289](../code-quality/c6289.md)|Wzajemne wykluczenie nad logicznym lub jest prawdziwe|
|[C6290](../code-quality/c6290.md)|Logiczne, nie bitowe i pierwszeństwo|
|[C6291](../code-quality/c6291.md)|Logiczne, nie bitowe lub pierwszeństwo|
|[C6292](../code-quality/c6292.md)|Pętla liczy się od maksimum|
|[C6293](../code-quality/c6293.md)|Pętla odlicza od minimum|
|[C6294](../code-quality/c6294.md)|Obiekt pętli nigdy nie został wykonany|
|[C6295](../code-quality/c6295.md)|Nieskończona pętla|
|[C6296](../code-quality/c6296.md)|Pętla jest wykonywana tylko raz|
|[C6297](../code-quality/c6297.md)|Wynik shift cast do większych rozmiarów|
|[C6299](../code-quality/c6299.md)|Porównanie bitfield do logicznego|
|[C6302](../code-quality/c6302.md)|Nieprawidłowy argument ciąg znaków do formatowania funkcji|
|[C6303](../code-quality/c6303.md)|Nieprawidłowy argument szeroki ciąg znaków do formatowania funkcji|
|[C6305](../code-quality/c6305.md)|Niedopasowane użycie rozmiaru i liczby|
|[C6306](../code-quality/c6306.md)|Wywołanie funkcji niepoprawnego argumentu zmiennej|
|[C6308](../code-quality/c6308.md)|Wyciek realokacji|
|[C6310](../code-quality/c6310.md)|Stała filtru nielegalnego wyjątku|
|[C6312](../code-quality/c6312.md)|Pętla kontynuacji wykonywania wyjątku|
|[C6314](../code-quality/c6314.md)|Bitowe lub pierwszeństwo|
|[C6317](../code-quality/c6317.md)|Nie uzupełniać|
|[C6318](../code-quality/c6318.md)|Wyjątek Kontynuuj wyszukiwanie|
|[C6319](../code-quality/c6319.md)|Ignorowane przez przecinek|
|[C6324](../code-quality/c6324.md)|Kopiuj ciąg zamiast porównywania ciągów|
|[C6328](../code-quality/c6328.md)|Niezgodność typu potencjalnego argumentu|
|[C6331](../code-quality/c6331.md)|Nieprawidłowe flagi VirtualFree|
|[C6332](../code-quality/c6332.md)|Nieprawidłowy parametr VirtualFree|
|[C6333](../code-quality/c6333.md)|Nieprawidłowy rozmiar VirtualFree|
|[C6335](../code-quality/c6335.md)|Nieszczelny uchwyt procesu|
|[C6381](../code-quality/c6381.md)|Brak informacji o zamknięciu systemu|
|[C6383](../code-quality/c6383.md)|Przekroczenie buforu liczby bajtów liczba elementu|
|[C6384](../code-quality/c6384.md)|Podział rozmiaru wskaźnika|
|[C6385](../code-quality/c6385.md)|Odczyt Przekroczenia|
|[C6386](../code-quality/c6386.md)|Przekroczenie zapisu|
|[C6387](../code-quality/c6387.md)|Nieprawidłowa wartość parametru|
|[C6388](../code-quality/c6388.md)|Nieprawidłowa wartość parametru|
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
|[C6995](../code-quality/c6995.md)|Nie można zapisać pliku dziennika XML|
|[C26100](../code-quality/c26100.md)|Sytuacja wyścigu|
|[C26101](../code-quality/c26101.md)|Nieprawidłowe używanie operacji zablokowanej|
|[C26110](../code-quality/c26110.md)|Nietrzymanie blokady przez rozmówcę|
|[C26111](../code-quality/c26111.md)|Nie można zwolnić blokady przez rozmówcę|
|[C26112](../code-quality/c26112.md)|Rozmówca nie może przytrzymać żadnej blokady|
|[C26115](../code-quality/c26115.md)|Nie można zwolnić blokady|
|[C26116](../code-quality/c26116.md)|Nienabycie lub wstrzymanie blokady|
|[C26117](../code-quality/c26117.md)|Zwalnianie blokady nietrzymałej|
|[C26140](../code-quality/c26140.md)|Błąd adnotacji sal współbieżności|
|[C26441](../code-quality/c26441.md)|NO_UNNAMED_GUARDS|
|[C26444](../code-quality/c26444.md)|NO_UNNAMED_RAII_OBJECTS|
|[C26498](../code-quality/c26498.md)|USE_CONSTEXPR_FOR_FUNCTIONCALL|
|[C28020](../code-quality/c28020.md)|Wyrażenie nie jest prawdziwe w tym wywołaniu|
|[C28021](../code-quality/c28021.md)|Parametr, o który się dozowane, musi być wskaźnikiem|
|[C28022](../code-quality/c28022.md)|Klasa(y) funkcji tej funkcji nie jest zgodna z klasą(y) funkcji (typedef) używaną do zdefiniowania.|
|[C28023](../code-quality/c28023.md)|Funkcja, która jest przypisywana \_lub\_\_ przekazywana, powinna mieć adnotację klasy funkcji dla co najmniej jednej z klas|
|[C28024](../code-quality/c28024.md)|Przypisany wskaźnik funkcji jest opisywany z klasą funkcji, która nie znajduje się na liście klas funkcyjnych.|
|[C28039](../code-quality/c28039.md)|Typ rzeczywistego parametru powinien dokładnie odpowiadać typowi|
|[C28112](../code-quality/c28112.md)|Zmienna, do której uzyskuje się dostęp za pośrednictwem funkcji Interlocked, musi być zawsze dostępna za pomocą funkcji Interlocked.|
|[C28113](../code-quality/c28113.md)|Uzyskiwanie dostępu do zmiennej lokalnej za pomocą funkcji Interlocked|
|[C28125](../code-quality/c28125.md)|Funkcja musi być wywoływana z poziomu bloku try/except|
|[C28137](../code-quality/c28137.md)|Argument zmiennej powinien być stałą (literalną)|
|[C28138](../code-quality/c28138.md)|Argument stały powinien być zmienny|
|[C28159](../code-quality/c28159.md)|Zamiast tego należy rozważyć użycie innej funkcji.|
|[C28160](../code-quality/c28160.md)|Adnotacja o błędzie|
|[C28163](../code-quality/c28163.md)|Funkcja nigdy nie powinna być wywoływana z poziomu bloku try/except|
|[C28164](../code-quality/c28164.md)|Argument jest przekazywany do funkcji, która oczekuje wskaźnika do obiektu (nie wskaźnik do wskaźnika)|
|[C28182](../code-quality/c28182.md)|Wskaźnik NULL dereferencing. Wskaźnik zawiera taką samą wartość NULL, jak inny wskaźnik.|
|[C28183](../code-quality/c28183.md)|Argument może być jedną wartością i jest kopią wartości znajdującej się w wskaźniku|
|[C28193](../code-quality/c28193.md)|Zmienna posiada wartość, która musi zostać zbadana|
|[C28196](../code-quality/c28196.md)|Wymóg nie jest spełniony. (Wyrażenie nie ocenia true.)|
|[C28202](../code-quality/c28202.md)|Nielegalne odniesienie do niestatycznych członków|
|[C28203](../code-quality/c28203.md)|Niejednoznaczne odwołanie do elementu członkowskiego klasy.|
|[C28205](../code-quality/c28205.md)|\_Niepowodzenie\_ \_lub\_\_ Porażka używana w kontekście niezgodnym z prawem|
|[C28206](../code-quality/c28206.md)|Lewy operand wskazuje na strukturę, użyj '->'|
|[C28207](../code-quality/c28207.md)|Lewy operand jest strukturą, użyj '.'|
|[C28209](../code-quality/c28209.md)|Deklaracja symbolu ma sprzeczną deklarację|
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
|[C28244](../code-quality/c28244.md)|Adnotacja funkcji ma nierozłączny parametr/adnotację zewnętrzną|
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
|[C28306](../code-quality/c28306.md)|Adnotacja na parametr jest przestarzała|
|[C28307](../code-quality/c28307.md)|Adnotacja na parametr jest przestarzała|
|[C28350](../code-quality/c28350.md)|Adnotacja opisuje sytuację, która nie jest warunkowo stosowana.|
|[C28351](/cpp/code-quality/c28351)|Adnotacja opisuje, gdzie wartość dynamiczna (zmienna) nie może być używana w warunku.|
