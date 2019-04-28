---
title: Potwierdzenia C/C++ | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [MFC], assertions
- results, checking
- result checking
- Call Stack window, assertion failures
- debugging [C++], assertions
- VERIFY macro
- assertions, side effects
- assertions
- ASSERT macro
- errors [C++], catching with assertions
- testing, error conditions with assertion statements
- _DEBUG macro
- Assertion Failed dialog box
- failures, finding locations
ms.assetid: 2d7b0121-71aa-414b-bbb6-ede1093d0bfc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 8e2d416bd932f1334468bfb3d43e050b3e71d2ec
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62564115"
---
# <a name="cc-assertions"></a>Potwierdzenia C/C++
Instrukcji asercji określa warunek, który chcą mieć wartość true w punkcie, w programie. Jeśli ten warunek nie zostanie spełniony, potwierdzenie nie powiedzie się, wykonania programu zostanie przerwany, a [błędy potwierdzenia — okno dialogowe](../debugger/assertion-failed-dialog-box.md) pojawia się.

Visual C++ obsługuje instrukcji potwierdzania, które są oparte na następujące elementy:

- Potwierdzenia MFC dla programów MFC.

- [ATLASSERT](/cpp/atl/reference/debugging-and-error-reporting-macros#atlassert) dla programów, które używają ATL.

- Potwierdzenia CRT dla programów, które używają biblioteki wykonawczej C.

- ANSI [assert — funkcja](/cpp/c-runtime-library/reference/assert-macro-assert-wassert) innych programów C/C++.

  Potwierdzenia umożliwia przechwytywania błędów logiki, sprawdź wyniki operacji i testowanie warunki błędów, które powinno zostać obsłużone.

## <a name="BKMK_In_this_topic"></a> W tym temacie
[Jak działają potwierdzenia](#BKMK_How_assertions_work)

[Potwierdzenia w kompilacjach debugowania, jak i wydania](#BKMK_Assertions_in_Debug_and_Release_builds)

[Efekty uboczne za pomocą potwierdzenia](#BKMK_Side_effects_of_using_assertions)

[Potwierdzenia CRT](#BKMK_CRT_assertions)

[Potwierdzenia MFC](#BKMK_MFC_assertions)

- [MFC ASSERT_VALID i CObject::AssertValid](#BKMK_MFC_ASSERT_VALID_and_CObject__AssertValid)

- [Ograniczenia AssertValid](#BKMK_Limitations_of_AssertValid)

  [Za pomocą potwierdzenia](#BKMK_Using_assertions)

- [Wychwytywanie błędów logicznych](#BKMK_Catching_logic_errors)

- [Sprawdzanie wyników](#BKMK_Checking_results_)

- [Błędy braku obsługi wyszukiwania](#BKMK_Testing_error_conditions_)

## <a name="BKMK_How_assertions_work"></a> Jak działają potwierdzenia
Gdy debuger zatrzymuje ze względu na potwierdzenie bibliotekę uruchomieniową C i MFC, następnie Jeśli źródło jest niedostępne, debuger przechodzi do punktu w pliku źródłowym, w którym wystąpiło potwierdzenia. Zostanie wyświetlony komunikat potwierdzenia w obu [okno danych wyjściowych](../ide/reference/output-window.md) i **potwierdzenie nie powiodło się** okno dialogowe. Możesz skopiować komunikat potwierdzenia z **dane wyjściowe** okna okna tekstowego, jeśli chcesz go zapisać do użytku w przyszłości. **Dane wyjściowe** okna może zawierać inne komunikaty o błędach także. Sprawdź te komunikaty ostrożnie, ponieważ zapewniają wskazówki do przyczynę błędu asercji.

Użyj potwierdzenia do wykrywania błędów w czasie projektowania. Zgodnie z zasadą należy użyć jednego potwierdzenia dla każdego założeń. Na przykład jeśli zakładać, że argument nie jest NULL, należy użyć potwierdzenie do przetestowania tego założeń.

[W tym temacie](#BKMK_In_this_topic)

## <a name="BKMK_Assertions_in_Debug_and_Release_builds"></a> Potwierdzenia w kompilacjach debugowania, jak i wydania
Instrukcje asercji skompilować tylko wtedy, gdy `_DEBUG` jest zdefiniowana. W przeciwnym razie kompilator traktuje potwierdzenia jako instrukcji o wartości null. W związku z tym, instrukcji potwierdzania nałożyć bez lub wydajność koszt w programach ostatecznego wydania i pozwalają unikać `#ifdef` dyrektywy.

## <a name="BKMK_Side_effects_of_using_assertions"></a> Efekty uboczne za pomocą potwierdzenia
Po dodaniu potwierdzenia w kodzie, upewnij się, że potwierdzenia nie mieć skutki uboczne. Na przykład, należy wziąć pod uwagę następujące asercja, która modyfikuje `nM` wartość:

```cpp
ASSERT(nM++ > 0); // Don't do this!
```

Ponieważ `ASSERT` w wydanej wersji programu, nie jest obliczane wyrażenie `nM` mają różne wartości w wersjach Debug i Release. Aby uniknąć tego problemu w MFC, można użyć [Sprawdź](/cpp/mfc/reference/diagnostic-services#verify) makr zamiast `ASSERT`. `VERIFY` oblicza wyrażenie we wszystkich wersjach, ale nie sprawdza wynik w pełnej wersji.

Należy zachować ostrożność szczególnie przy użyciu wywołania funkcji w instrukcji potwierdzania, ponieważ obliczania funkcji może mieć nieoczekiwane działania niepożądane.

```cpp
ASSERT ( myFnctn(0)==1 ) // unsafe if myFnctn has side effects
VERIFY ( myFnctn(0)==1 ) // safe
```

`VERIFY` wywołania `myFnctn` w wersjach zarówno debugowania, jak i wersji, więc jest można użyć. Jednak przy użyciu `VERIFY` nakłada obciążenie wywołanie zbędnych funkcji w wersji.

[W tym temacie](#BKMK_In_this_topic)

## <a name="BKMK_CRT_assertions"></a> Potwierdzenia CRT
CRTDBG. Określa plik nagłówkowy H [_ASSERT i _asserte — makra](/cpp/c-runtime-library/reference/assert-asserte-assert-expr-macros) sprawdzania potwierdzenia.

| Macro | Wynik |
|------------| - |
| `_ASSERT` | Jeśli określone wyrażenie zwróci wartość FALSE, pliku nazwa i numer wiersza `_ASSERT`. |
| `_ASSERTE` | Taki sam jak `_ASSERT`, oraz ciąg reprezentujący wyrażenie, które zostało potwierdzone. |

`_ASSERTE` jest bardziej wydajne, ponieważ raportuje potwierdzone wyrażenie, które są wartość FALSE. Może to być wystarczająco dużo, aby zidentyfikować problem bez odwołujące się do kodu źródłowego. Jednak wersji debugowania aplikacji będzie zawierać stałą typu string dla każdego wyrażenia potwierdzone przy użyciu `_ASSERTE`. Jeśli używasz wielu `_ASSERTE` makra, te wyrażenia ciągu potrwać znacznej ilości pamięci. Jeśli okaże się to być problem, użyj `_ASSERT` zapisanie w pamięci.

Gdy `_DEBUG` jest zdefiniowany, `_ASSERTE` — makro jest zdefiniowany następująco:

```cpp
#define _ASSERTE(expr) \
    do { \
        if (!(expr) && (1 == _CrtDbgReport( \
            _CRT_ASSERT, __FILE__, __LINE__, #expr))) \
            _CrtDbgBreak(); \
    } while (0)
```

Jeśli potwierdzona wyrażenie ma wartość FALSE, [_CrtDbgReport](/cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw) jest wywoływana, aby zgłosić błąd potwierdzenia (przy użyciu okno dialogowe komunikatu, domyślnie). Jeśli wybierzesz **ponów** w oknie dialogowym komunikatu `_CrtDbgReport` zwraca 1 i `_CrtDbgBreak` wywołuje debugera za pomocą `DebugBreak`.

### <a name="checking-for-heap-corruption"></a>Sprawdzanie, czy uszkodzenie sterty
W poniższym przykładzie użyto [_CrtCheckMemory](/cpp/c-runtime-library/reference/crtcheckmemory) aby wykryć ewentualne uszkodzenia sterty:

```cpp
_ASSERTE(_CrtCheckMemory());
```

### <a name="checking-pointer-validity"></a>Sprawdzanie poprawności wskaźnika
W poniższym przykładzie użyto [_crtisvalidpointer —](/cpp/c-runtime-library/reference/crtisvalidpointer) Aby sprawdzić, czy zakres pamięci danego nadaje się do odczytu lub zapisu.

```cpp
_ASSERTE(_CrtIsValidPointer( address, size, TRUE );
```

W poniższym przykładzie użyto [_crtisvalidheappointer —](/cpp/c-runtime-library/reference/crtisvalidheappointer) Aby sprawdzić, wskaźnik wskazuje pamięci lokalnej sterty (sterty tworzony i zarządzany przez to wystąpienie biblioteki wykonawczej C — Biblioteka DLL może mieć własne wystąpienie biblioteki, i w związku z tym swój własny sterty, poza stosu aplikacji). Ta asercja nie przechwytuje tylko wartość null lub liczbach adresy, ale także wskaźniki do zmiennych statycznych, zmiennych stosu i inne nielokalnych pamięci.

```cpp
_ASSERTE(_CrtIsValidPointer( myData );
```

### <a name="checking-a-memory-block"></a>Sprawdzanie bloku pamięci
W poniższym przykładzie użyto [_crtismemoryblock —](/cpp/c-runtime-library/reference/crtismemoryblock) Aby sprawdzić, czy blok pamięci znajduje się w lokalnej sterty i ma typ bloku prawidłowe.

```cpp
_ASSERTE(_CrtIsMemoryBlock (myData, size, &requestNumber, &filename, &linenumber));
```

[W tym temacie](#BKMK_In_this_topic)

## <a name="BKMK_MFC_assertions"></a> Potwierdzenia MFC
Definiuje MFC [ASERCJA](https://msdn.microsoft.com/Library/1e70902d-d58c-4e7b-9f69-2aeb6cbe476c) — makro sprawdzania potwierdzenia. Umożliwia on również definiowanie `MFC ASSERT_VALID` i `CObject::AssertValid` metody do sprawdzania stanu wewnętrznego `CObject`-pochodnych obiektu.

Jeśli argument MFC `ASSERT` — makro osiągnie wartość zero lub wartość FAŁSZ, makro zatrzymuje wykonywanie programów, a ostrzega o tym użytkownika; w przeciwnym razie wykonywanie jest kontynuowane.

Jeśli potwierdzenie nie powiedzie się, okno dialogowe komunikatu zawiera nazwę pliku źródłowego i numer wiersza asercji. Jeśli w oknie dialogowym wybierz pozycję Ponów próbę polu wywołanie [afxdebugbreak —](/cpp/mfc/reference/diagnostic-services#afxdebugbreak) powoduje wykonanie na przerwanie i przejście do debugera. W tym momencie możesz analizować stos wywołań i użyj innych obiektów debugera, aby określić, dlaczego potwierdzenie nie powiodło się. Po włączeniu [Just-in-time debugging](../debugger/just-in-time-debugging-in-visual-studio.md)i debuger nie została jeszcze uruchomiona, okno dialogowe można uruchomić debugera.

Poniższy przykład pokazuje, jak używać `ASSERT` Aby sprawdzić wartość zwracaną przez funkcję:

```cpp
int x = SomeFunc(y);
ASSERT(x >= 0);   //  Assertion fails if x is negative
```

Możesz użyć ASSERT, za pomocą [IsKindOf](https://docs.microsoft.com/cpp/mfc/reference/cobject-class#iskindof) funkcję, aby zapewnić typ sprawdzania argumentów funkcji:

```cpp
ASSERT( pObject1->IsKindOf( RUNTIME_CLASS( CPerson ) ) );
```

`ASSERT` — Makro nie tworzy kodu w pełnej wersji. Jeśli potrzebujesz można obliczyć wartości wyrażenia w pełnej wersji, użyj [Sprawdź](https://msdn.microsoft.com/library/s8c29sw2.aspx#verify) makr zamiast ASSERT.

### <a name="BKMK_MFC_ASSERT_VALID_and_CObject__AssertValid"></a> MFC ASSERT_VALID i CObject::AssertValid
[CObject::AssertValid](https://docs.microsoft.com/cpp/mfc/reference/cobject-class#assertvalid) metoda zapewnia sprawdzania w trakcie wykonywania wewnętrznego stanu obiektu. Mimo że nie musisz przesłonić `AssertValid` po utworzeniu klasy pochodnej klasy z `CObject`, aby włączyć klasy bardziej niezawodna w ten sposób. `AssertValid` należy wykonać potwierdzenia na wszystkich zmiennych Członkowskich obiektu, aby sprawdzić, czy zawierają one prawidłowe wartości. Na przykład należy sprawdzić, wskaźnik zmienne składowe nie mają wartości NULL.

Poniższy przykład pokazuje sposób deklarowania `AssertValid` funkcji:

```cpp
class CPerson : public CObject
{
protected:
    CString m_strName;
    float   m_salary;
public:
#ifdef _DEBUG
    // Override
    virtual void AssertValid() const;
#endif
    // ...
};
```

Gdy zastąpisz `AssertValid`, wywołaj klasę bazową wersję `AssertValid` przed wykonaniem własne testy. Następnie za makro ASSERT Sprawdź elementy członkowskie unikatowe dla swojej otrzymanej klasy, jak pokazano poniżej:

```cpp
#ifdef _DEBUG
void CPerson::AssertValid() const
{
    // Call inherited AssertValid first.
    CObject::AssertValid();

    // Check CPerson members...
    // Must have a name.
    ASSERT( !m_strName.IsEmpty());
    // Must have an income.
    ASSERT( m_salary > 0 );
}
#endif
```

Dowolny zmiennych Członkowskich przechowywać obiekty, można użyć `ASSERT_VALID` makra w celu testowania ich ważność wewnętrznego (Jeśli zastąpisz ich klasy `AssertValid`).

Rozważmy na przykład klasa `CMyData`, które sklepy [CObList](/cpp/mfc/reference/coblist-class) w jednym z jego zmiennych Członkowskich. `CObList` Zmiennej `m_DataList`, przechowuje kolekcję `CPerson` obiektów. Deklaracja skróconej `CMyData` wygląda podobnie do następującego:

```cpp
class CMyData : public CObject
{
    // Constructor and other members ...
    protected:
        CObList* m_pDataList;
    // Other declarations ...
    public:
#ifdef _DEBUG
        // Override:
        virtual void AssertValid( ) const;
#endif
    // And so on ...
};
```

`AssertValid` Zastąpić w `CMyData` wygląda podobnie do następującego:

```cpp
#ifdef _DEBUG
void CMyData::AssertValid( ) const
{
    // Call inherited AssertValid.
    CObject::AssertValid( );
    // Check validity of CMyData members.
    ASSERT_VALID( m_pDataList );
    // ...
}
#endif
```

`CMyData` używa `AssertValid` mechanizmu, aby sprawdzić poprawność obiekty przechowywane w jego element członkowski danych. Zastępowanie `AssertValid` z `CMyData` wywołuje `ASSERT_VALID` makro dla własnej m_pDataList zmiennej składowej.

Testowanie poprawności nie zatrzymuje się na tym poziomie ponieważ klasy `CObList` zastępuje również `AssertValid`. To zastąpienie wykonuje dodatkowe ważności testowanie na wewnętrzny stan listy. W efekcie ważności Testuj je na `CMyData` obiektu prowadzi do ważności dodatkowe testy dla wewnętrznego stanów przechowywaną `CObList` obiekt listy.

Za pomocą niektórych więcej pracy, można dodać testy poprawności dla `CPerson` również przechowywane na liście obiektów. Można wyprowadzić klasę `CPersonList` z `CObList` i zastąpić `AssertValid`. W przesłonięciu, możesz wywołać `CObject::AssertValid` i następnie iterację liście wywoływania `AssertValid` na każdym `CPerson` obiektu przechowywanego na liście. `CPerson` Zastępuje klasy wyświetlane na początku tego tematu już `AssertValid`.

Jest to zaawansowany mechanizm podczas kompilacji do debugowania. Gdy tworzysz później w wersji, mechanizm jest wyłączony automatycznie.

### <a name="BKMK_Limitations_of_AssertValid"></a> Ograniczenia AssertValid
Wyzwolono asercję wskazuje, że obiekt jest zdecydowanie zły i wykonanie zostanie zatrzymane. Brak potwierdzenia informuje jednak tylko nie znaleziono problemów, że obiekt nie jest gwarantowana dobre.

[W tym temacie](#BKMK_In_this_topic)

## <a name="BKMK_Using_assertions"></a> Za pomocą potwierdzenia

### <a name="BKMK_Catching_logic_errors"></a> Wychwytywanie błędów logicznych
Potwierdzenie można ustawić na warunek, który musi mieć wartość true, zgodnie z logiki programu. Potwierdzenie nie ma wpływu, chyba że wystąpi błąd logiczny.

Załóżmy, że są symulowania cząsteczek gaz w kontenerze, a zmienna `numMols` reprezentuje sumę cząsteczek. Ten numer nie może być mniejsza od zera, dzięki czemu może zawierać instrukcji asercji MFC następująco:

```cpp
ASSERT(numMols >= 0);
```

Lub można umieścić potwierdzenie CRT w następujący sposób:

```cpp
_ASSERT(numMols >= 0);
```

Te instrukcje nie nic robić, jeśli program działa poprawnie. Jeśli powoduje błąd logiczny `numMols` do być mniejsza niż zero, jednak Potwierdzenie zatrzymuje wykonywanie programu i wyświetla [potwierdzenie nie powiodło się — okno dialogowe](../debugger/assertion-failed-dialog-box.md).

[W tym temacie](#BKMK_In_this_topic)

### <a name="BKMK_Checking_results_"></a> Sprawdzanie wyników
Potwierdzenia są przydatne do testowania operacje, których wyniki nie są oczywiste z szybkich kontroli.

Na przykład rozważmy następujący kod, który aktualizuje zmienną `iMols` na podstawie zawartości listy dwukierunkowej, wskazywana przez `mols`:

```cpp
/* This code assumes that type has overloaded the != operator
 with const char *
It also assumes that H2O is somewhere in that linked list.
Otherwise we'll get an access violation... */
while (mols->type != "H2O")
{
    iMols += mols->num;
    mols = mols->next;
}
ASSERT(iMols<=numMols); // MFC version
_ASSERT(iMols<=numMols); // CRT version
```

Liczba cząsteczek zliczane przez `iMols` zawsze musi być mniejsza niż łączna liczba cząsteczki `numMols`. Kontroli wizualnej pętli nie pokazuje, że zawsze będzie to przypadek, więc asercja instrukcja jest używane po pętli do testu dla tego warunku.

[W tym temacie](#BKMK_In_this_topic)

### <a name="BKMK_Testing_error_conditions_"></a> Błędy braku obsługi wyszukiwania
Potwierdzenia można użyć do testowania dla warunków błędu w punkcie, w kodzie, gdzie wszelkie błędy powinny został obsłużony. W poniższym przykładzie procedury graficznego zwraca kod błędu lub zero w celu osiągnięcia sukcesu.

```cpp
myErr = myGraphRoutine(a, b);

/* Code to handle errors and
   reset myErr if successful */

ASSERT(!myErr); -- MFC version
_ASSERT(!myErr); -- CRT version
```

Jeśli kod obsługi błędów działa prawidłowo, powinien zostać obsłużony błąd i `myErr` resetowania zero przed osiągnięciem potwierdzenia. Jeśli `myErr` ma inną wartość, potwierdzenie kończy się niepowodzeniem, zatrzymanie programu i [potwierdzenie nie powiodło się — okno dialogowe](../debugger/assertion-failed-dialog-box.md) pojawia się.

Instrukcje asercji nie są jednak zamiast kodu obsługi błędu. Instrukcję asercja, która może prowadzić do problemów w kodzie ostatecznej wersji można znaleźć w poniższym przykładzie:

```cpp
myErr = myGraphRoutine(a, b);

/* No Code to handle errors */

ASSERT(!myErr); // Don't do this!
_ASSERT(!myErr); // Don't do this, either!
```

Ten kod zależy od instrukcji asercji obsługę warunku błędu. W rezultacie, każdy kod błędu zwrócony przez `myGraphRoutine` zostanie obsłużony w kodzie ostatecznej wersji.

[W tym temacie](#BKMK_In_this_topic)

## <a name="see-also"></a>Zobacz też

- [Zabezpieczenia debugera](../debugger/debugger-security.md)
- [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)
- [Asercje w kodzie zarządzanym](../debugger/assertions-in-managed-code.md)