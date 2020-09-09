---
title: Zestaw reguł macierzystych reguł zalecanych
ms.date: 11/04/2016
ms.topic: reference
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 94fd7ba7b742c2615dc8f161c5ea156b4fd0a7f4
ms.sourcegitcommit: ed4372bb6f4ae64f1fd712b2b253bf91d9ff96bf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/09/2020
ms.locfileid: "89600023"
---
# <a name="native-recommended-rules-rule-set"></a>Zestaw reguł macierzystych reguł zalecanych

Natywne zalecane reguły koncentrują się na najważniejszych i typowych problemach w kodzie natywnym, w tym potencjalnych luk w zabezpieczeniach i awarii aplikacji. Ten zestaw reguł zawiera wszystkie reguły z [natywnego zestawu reguł minimalnych reguł](native-minimum-rules-rule-set.md) .

Dołącz ten zestaw reguł do dowolnego niestandardowego zestawu reguł tworzonego dla projektów natywnych.

|Reguła|Opis|
|----------|-----------------|
|[C6001](/cpp/code-quality/c6001)|Używanie niezainicjowanej pamięci|
|[C6011](/cpp/code-quality/c6011)|Wyłuskanie wskaźnika o wartości null|
|[C6029](/cpp/code-quality/c6029)|Użycie niesprawdzonej wartości|
|[C6031](/cpp/code-quality/c6031)|Wartość zwracana została zignorowana|
|[C6053](/cpp/code-quality/c6053)|Zakończenie zerowe od wywołania|
|[C6054](/cpp/code-quality/c6054)|Brak zakończenia zerowej|
|[C6059](/cpp/code-quality/c6059)|Złe łączenie|
|[C6063](/cpp/code-quality/c6063)|Brak argumentu ciągu do funkcji formatowania|
|[C6064](/cpp/code-quality/c6064)|Brak argumentu typu Integer dla funkcji formatowania|
|[C6066](/cpp/code-quality/c6066)|Brak argumentu wskaźnika dla funkcji formatowania|
|[C6067](/cpp/code-quality/c6067)|Brak argumentu wskaźnika ciągu do funkcji formatowania|
|[C6101](/cpp/code-quality/c6101)|Zwracanie niezainicjowanej pamięci|
|[C6200](/cpp/code-quality/c6200)|Indeks przekracza maksymalny rozmiar buforu|
|[C6201](/cpp/code-quality/c6201)|Indeks przekracza maksymalną wartość buforu stosu|
|[C6214](/cpp/code-quality/c6214)|Nieprawidłowe rzutowanie HRESULT do wartości LOGICZNEj|
|[C6215](/cpp/code-quality/c6215)|Nieprawidłowa wartość logiczna rzutowania do HRESULT|
|[C6216](/cpp/code-quality/c6216)|Nieprawidłowa wartość logiczna rzutowania wstawionego przez kompilator do HRESULT|
|[C6217](/cpp/code-quality/c6217)|Nieprawidłowy test HRESULT z|
|[C6220](/cpp/code-quality/c6220)|Nieprawidłowe porównanie HRESULT z-1|
|[C6226](/cpp/code-quality/c6226)|Nieprawidłowe przypisanie HRESULT do-1|
|[C6230](/cpp/code-quality/c6230)|Nieprawidłowe użycie HRESULT jako wartości logicznej|
|[C6235](/cpp/code-quality/c6235)|Stała niezerowa z wartością logiczną lub|
|[C6236](/cpp/code-quality/c6236)|Logiczna — lub z niezerową stałą|
|[C6237](/cpp/code-quality/c6237)|Zero ze koniunkcją logiczną i powoduje utratę efektów ubocznych|
|[C6242](/cpp/code-quality/c6242)|Wymuszone lokalne rozwinięcie|
|[C6248](/cpp/code-quality/c6248)|Tworzenie listy DACL o wartości null|
|[C6250](/cpp/code-quality/c6250)|Niezwolnione deskryptory adresów|
|[C6255](/cpp/code-quality/c6255)|Niechronione użycie alloca|
|[C6258](/cpp/code-quality/c6258)|Korzystanie z wątku przerywania|
|[C6259](/cpp/code-quality/c6259)|Martwy kod w przełączniku bitowym lub ograniczonym|
|[C6260](/cpp/code-quality/c6260)|Użycie arytmetyki bajtowej|
|[C6262](/cpp/code-quality/c6262)|Nadmierne użycie stosu|
|[C6263](/cpp/code-quality/c6263)|Korzystanie z usługi alloca w pętli|
|[C6268](/cpp/code-quality/c6268)|Brak nawiasów w rzutowaniu|
|[C6269](/cpp/code-quality/c6269)|Zignorowano odwołanie do wskaźnika|
|[C6270](/cpp/code-quality/c6270)|Brak argumentu zmiennoprzecinkowego do funkcji formatowania|
|[C6271](/cpp/code-quality/c6271)|Dodatkowy argument funkcji formatowania|
|[C6272](/cpp/code-quality/c6272)|Argument inny niż zmiennoprzecinkowy do formatowania funkcji|
|[C6273](/cpp/code-quality/c6273)|Argument niebędący liczbą całkowitą do sformatowania funkcji|
|[C6274](/cpp/code-quality/c6274)|Argument niebędący znakiem do funkcji formatowania|
|[C6276](/cpp/code-quality/c6276)|Nieprawidłowe rzutowanie ciągu|
|[C6277](/cpp/code-quality/c6277)|Nieprawidłowe wywołanie metody CreateProcess|
|[C6278](/cpp/code-quality/c6278)|Niezgodność Array-New skalarna Delete|
|[C6279](/cpp/code-quality/c6279)|Skalarna — niezgodność z nową tablicą|
|[C6280](/cpp/code-quality/c6280)|Niezgodność alokacji pamięci|
|[C6281](/cpp/code-quality/c6281)|Pierwszeństwo relacji bitowej|
|[C6282](/cpp/code-quality/c6282)|Przypisanie zastępuje test|
|[C6283](/cpp/code-quality/c6283)|Niezgodność z tablicą pierwotną — Nowa funkcja skalarna usuwania|
|[C6284](/cpp/code-quality/c6284)|Nieprawidłowy argument obiektu dla funkcji formatowania|
|[C6285](/cpp/code-quality/c6285)|Logiczne-lub stałe|
|[C6286](/cpp/code-quality/c6286)|Niezerowe logiczne lub utrata efektów ubocznych|
|[C6287](/cpp/code-quality/c6287)|Test nadmiarowy|
|[C6288](/cpp/code-quality/c6288)|Wzajemne włączenie przy użyciu operatora logicznego i ma wartość false|
|[C6289](/cpp/code-quality/c6289)|Wzajemne wykluczenie z użyciem operatora logicznego OR jest prawdziwe|
|[C6290](/cpp/code-quality/c6290)|Niestandardowa koniunkcja logiczna|
|[C6291](/cpp/code-quality/c6291)|Niestandardowa koniunkcja logiczna|
|[C6292](/cpp/code-quality/c6292)|Pętla zlicza w górę od maksimum|
|[C6293](/cpp/code-quality/c6293)|Pętla liczy w dół od minimum|
|[C6294](/cpp/code-quality/c6294)|Treść pętli nigdy nie została wykonana|
|[C6295](/cpp/code-quality/c6295)|Nieskończona pętla|
|[C6296](/cpp/code-quality/c6296)|Pętla zostanie wykonana tylko raz|
|[C6297](/cpp/code-quality/c6297)|Wynik rzutowania przesunięcia na większy rozmiar|
|[C6299](/cpp/code-quality/c6299)|Porównanie pole bitowe z wartością logiczną|
|[C6302](/cpp/code-quality/c6302)|Nieprawidłowy argument ciągu znaków dla funkcji formatowania|
|[C6303](/cpp/code-quality/c6303)|Nieprawidłowy argument ciągu znaków dwubajtowych do funkcji formatowania|
|[C6305](/cpp/code-quality/c6305)|Użycie niedopasowanego rozmiaru i liczby|
|[C6306](/cpp/code-quality/c6306)|Nieprawidłowe wywołanie funkcji zmiennej argumentu|
|[C6308](/cpp/code-quality/c6308)|Przeciek realloc|
|[C6310](/cpp/code-quality/c6310)|Niedozwolona stała filtru wyjątków|
|[C6312](/cpp/code-quality/c6312)|Pętla kontynuacji wykonywania wyjątków|
|[C6314](/cpp/code-quality/c6314)|Pierwszeństwo bitowe|
|[C6317](/cpp/code-quality/c6317)|Nie uzupełniaj|
|[C6318](/cpp/code-quality/c6318)|Wyjątek — Kontynuuj wyszukiwanie|
|[C6319](/cpp/code-quality/c6319)|Zignorowane przez przecinek|
|[C6324](/cpp/code-quality/c6324)|Kopiowanie ciągu zamiast porównywania ciągów|
|[C6328](/cpp/code-quality/c6328)|Niezgodność typu argumentu potencjalnego|
|[C6331](/cpp/code-quality/c6331)|VirtualFree nieprawidłowe flagi|
|[C6332](/cpp/code-quality/c6332)|VirtualFree nieprawidłowy parametr|
|[C6333](/cpp/code-quality/c6333)|Nieprawidłowy rozmiar VirtualFree|
|[C6335](/cpp/code-quality/c6335)|Przeciek uchwytu procesu|
|[C6381](/cpp/code-quality/c6381)|Brak informacji o zamknięciu|
|[C6383](/cpp/code-quality/c6383)|Przepełnienie buforu liczby elementów-count|
|[C6384](/cpp/code-quality/c6384)|Dzielenie rozmiaru wskaźnika|
|[C6385](/cpp/code-quality/c6385)|Przepełnienie odczytu|
|[C6386](/cpp/code-quality/c6386)|Przepełnienie zapisu|
|[C6387](/cpp/code-quality/c6387)|Nieprawidłowa wartość parametru|
|[C6388](/cpp/code-quality/c6388)|Nieprawidłowa wartość parametru|
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
|[C6995](/cpp/code-quality/c6995)|Nie można zapisać pliku dziennika XML|
|[C26100](/cpp/code-quality/c26100)|Sytuacja wyścigu|
|[C26101](/cpp/code-quality/c26101)|Nie można prawidłowo użyć operacji zablokowanej|
|[C26110](/cpp/code-quality/c26110)|Wystąpił błąd blokady wywołującej|
|[C26111](/cpp/code-quality/c26111)|Obiekt wywołujący nie może zwolnić blokady|
|[C26112](/cpp/code-quality/c26112)|Obiekt wywołujący nie może blokować żadnej blokady|
|[C26115](/cpp/code-quality/c26115)|Niepowodzenie zwolnienia blokady|
|[C26116](/cpp/code-quality/c26116)|Nie można uzyskać lub wstrzymać blokady|
|[C26117](/cpp/code-quality/c26117)|Zwalnianie niezautrzymywanej blokady|
|[C26140](/cpp/code-quality/c26140)|Błąd adnotacji dotyczącej współbieżności SAL|
|[C26441](/cpp/code-quality/C26441)|NO_UNNAMED_GUARDS|
|[C26444](/cpp/code-quality/c26444)|NO_UNNAMED_RAII_OBJECTS|
|[C26498](/cpp/code-quality/C26498)|USE_CONSTEXPR_FOR_FUNCTIONCALL|
|[C28020](/cpp/code-quality/c28020)|Wyrażenie nie jest prawdziwe w tym wywołaniu|
|[C28021](/cpp/code-quality/c28021)|Parametr, którego typem jest adnotacja, musi być wskaźnikiem|
|[C28022](/cpp/code-quality/c28022)|Klasy funkcji w tej funkcji nie są zgodne z klasami funkcji dla elementu typedef użytego do jego zdefiniowania.|
|[C28023](/cpp/code-quality/c28023)|Przypisana lub przenoszona funkcja powinna mieć \_ \_ \_ adnotację klasy funkcji dla co najmniej jednej z klas (ES)|
|[C28024](/cpp/code-quality/c28024)|Wskaźnik funkcji, do której jest przypisany, ma adnotację z klasą funkcji, która nie znajduje się na liście klas funkcji.|
|[C28039](/cpp/code-quality/c28039)|Typ rzeczywistego parametru powinien dokładnie pasować do typu|
|[C28112](/cpp/code-quality/c28112)|Do zmiennej, do której uzyskuje się dostęp za pośrednictwem funkcji zablokowaniej, zawsze należy uzyskać dostęp za pośrednictwem funkcji Zablokowani.|
|[C28113](/cpp/code-quality/c28113)|Uzyskiwanie dostępu do zmiennej lokalnej przez zablokowaną funkcję|
|[C28125](/cpp/code-quality/c28125)|Funkcja musi być wywołana z poziomu bloku try/except|
|[C28137](/cpp/code-quality/c28137)|Zmienna argument powinien zamiast niego być (literałem)|
|[C28138](/cpp/code-quality/c28138)|Argument stałej powinien zamiast tego mieć wartość zmienna|
|[C28159](/cpp/code-quality/c28159)|Zamiast tego Rozważ użycie innej funkcji.|
|[C28160](/cpp/code-quality/c28160)|Błąd adnotacji|
|[C28163](/cpp/code-quality/c28163)|Funkcja nigdy nie powinna być wywoływana z wewnątrz bloku try/except|
|[C28164](/cpp/code-quality/c28164)|Argument jest przesyłany do funkcji, która oczekuje wskaźnika do obiektu (nie wskaźnika do wskaźnika)|
|[C28182](/cpp/code-quality/c28182)|Wyłuskanie wskaźnika o wartości NULL. Wskaźnik zawiera taką samą wartość NULL jak inny wskaźnik.|
|[C28183](/cpp/code-quality/c28183)|Argument może być jedną wartością i jest kopią wartości znalezionej we wskaźniku|
|[C28193](/cpp/code-quality/c28193)|Zmienna przechowuje wartość, która musi być zbadana|
|[C28196](/cpp/code-quality/c28196)|Wymaganie nie jest spełnione. (Wyrażenie nie jest szacowane na wartość true).|
|[C28202](/cpp/code-quality/c28202)|Niedozwolone odwołanie do niestatycznej składowej|
|[C28203](/cpp/code-quality/c28203)|Niejednoznaczne odwołanie do składowej klasy.|
|[C28205](/cpp/code-quality/c28205)|\_Powodzenie \_ lub \_ w \_ przypadku niepowodzenia \_ używane w niedozwolonym kontekście|
|[C28206](/cpp/code-quality/c28206)|Lewy argument operacji wskazuje na strukturę, użyj "->"|
|[C28207](/cpp/code-quality/c28207)|Lewy argument operacji jest strukturą, użyj "."|
|[C28209](/cpp/code-quality/c28209)|Deklaracja symbolu ma sprzeczną deklarację|
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
|[C28244](/cpp/code-quality/c28244)|Adnotacja dla funkcji ma niemożliwy do przeanalizowania parametr/zewnętrzną adnotację|
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
|[C28306](/cpp/code-quality/c28306)|Adnotacja dla parametru jest przestarzała|
|[C28307](/cpp/code-quality/c28307)|Adnotacja dla parametru jest przestarzała|
|[C28350](/cpp/code-quality/c28350)|Adnotacja zawiera opis sytuacji, która nie jest stosowana warunkowo.|
|[C28351](/cpp/code-quality/c28351)|Adnotacja opisuje, gdzie w warunku nie można używać wartości dynamicznej (zmiennej).|