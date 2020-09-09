---
title: Potwierdzenia C/C++ | Microsoft Docs
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
ms.openlocfilehash: abea0f45609c74e02cd95d6c21bbe8879d46eea1
ms.sourcegitcommit: ed4372bb6f4ae64f1fd712b2b253bf91d9ff96bf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/09/2020
ms.locfileid: "89600208"
---
# <a name="cc-assertions"></a>Potwierdzenia C/C++
Instrukcja Assert określa warunek, który powinien być prawdziwy w punkcie w programie. Jeśli ten warunek nie ma wartości true, potwierdzenie nie powiedzie się, wykonywanie programu zostanie przerwane i zostanie wyświetlone okno [dialogowe potwierdzenie nie powiodło](../debugger/assertion-failed-dialog-box.md) się.

Program Visual Studio obsługuje instrukcje potwierdzeń języka C++, które są oparte na następujących konstrukcjach:

- Potwierdzenia MFC dla programów MFC.

- [ATLASSERT](/cpp/atl/reference/debugging-and-error-reporting-macros#atlassert) dla programów korzystających z biblioteki ATL.

- Potwierdzenia CRT dla programów, które używają biblioteki wykonawczej C.

- [Funkcja potwierdzenia](/cpp/c-runtime-library/reference/assert-macro-assert-wassert) ANSI dla innych programów C/C++.

  Można użyć potwierdzeń, aby przechwytywać błędy logiki, sprawdzać wyniki operacji i testować warunki błędów, które powinny być obsługiwane.

## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> W tym temacie
[Jak działają potwierdzenia](#BKMK_How_assertions_work)

[Potwierdzenia w kompilacjach debugowania i wydania](#BKMK_Assertions_in_Debug_and_Release_builds)

[Efekty uboczne używania potwierdzeń](#BKMK_Side_effects_of_using_assertions)

[Potwierdzenia CRT](#BKMK_CRT_assertions)

[Potwierdzenia MFC](#BKMK_MFC_assertions)

- [MFC ASSERT_VALID i CObject:: AssertValid](#BKMK_MFC_ASSERT_VALID_and_CObject__AssertValid)

- [Ograniczenia dotyczące AssertValid](#BKMK_Limitations_of_AssertValid)

  [Używanie potwierdzeń](#BKMK_Using_assertions)

- [Przechwytywanie błędów logiki](#BKMK_Catching_logic_errors)

- [Sprawdzanie wyników](#BKMK_Checking_results_)

- [Znajdowanie nieobsłużonych błędów](#BKMK_Testing_error_conditions_)

## <a name="how-assertions-work"></a><a name="BKMK_How_assertions_work"></a> Jak działają potwierdzenia
Gdy debuger zatrzymuje działanie z powodu potwierdzenia biblioteki wykonawczej MFC lub C, a następnie Jeśli źródło jest dostępne, debuger przechodzi do punktu w pliku źródłowym, w którym wystąpiło potwierdzenie. Komunikat potwierdzenia pojawia się zarówno w [oknie danych wyjściowych](../ide/reference/output-window.md) , jak i w oknie dialogowym **potwierdzenie nie powiodło się** . Możesz skopiować komunikat potwierdzenia z okna **danych wyjściowych** do okna tekstowego, jeśli chcesz go zapisać do użytku w przyszłości. Okno **dane wyjściowe** może również zawierać inne komunikaty o błędach. Uważnie sprawdzaj te komunikaty, ponieważ zapewniają one wskazówki dotyczące przyczyny niepowodzenia potwierdzenia.

Użyj potwierdzeń w celu wykrycia błędów podczas opracowywania. Jako regułę Użyj jednego potwierdzenia dla każdego założenia. Na przykład jeśli założono, że argument nie ma wartości NULL, Użyj potwierdzenia do przetestowania tego założeń.

[W tym temacie](#BKMK_In_this_topic)

## <a name="assertions-in-debug-and-release-builds"></a><a name="BKMK_Assertions_in_Debug_and_Release_builds"></a> Potwierdzenia w kompilacjach debugowania i wydania
Instrukcje Assertion kompilują się tylko wtedy, gdy `_DEBUG` jest zdefiniowana. W przeciwnym razie kompilator traktuje potwierdzenia jako instrukcje o wartości null. W związku z tym instrukcje Assertion nie nakładają kosztów ani kosztu wydajności w końcowym programie wydania i umożliwiają uniknięcie stosowania `#ifdef` dyrektyw.

## <a name="side-effects-of-using-assertions"></a><a name="BKMK_Side_effects_of_using_assertions"></a> Efekty uboczne używania potwierdzeń
Po dodaniu potwierdzeń do kodu upewnij się, że potwierdzenia nie mają efektów ubocznych. Rozważmy na przykład następujące potwierdzenie, które modyfikuje `nM` wartość:

```cpp
ASSERT(nM++ > 0); // Don't do this!
```

Ponieważ `ASSERT` wyrażenie nie jest oceniane w wydanej wersji programu, program `nM` będzie miał różne wartości w wersjach Debug i Release. Aby uniknąć tego problemu w MFC, można użyć [Weryfikuj](/cpp/mfc/reference/diagnostic-services#verify) makro zamiast `ASSERT` . `VERIFY` oblicza wyrażenie we wszystkich wersjach, ale nie sprawdza wynik w wersji wydania.

Należy zwrócić szczególną uwagę na używanie wywołań funkcji w instrukcjach Assert, ponieważ obliczenie funkcji może mieć nieoczekiwane skutki uboczne.

```cpp
ASSERT ( myFnctn(0)==1 ) // unsafe if myFnctn has side effects
VERIFY ( myFnctn(0)==1 ) // safe
```

`VERIFY` wywołania `myFnctn` w wersji Debug i Release, aby można było ich używać. Jednak użycie `VERIFY` nakłada narzuty niepotrzebnego wywołania funkcji w wersji wydanej.

[W tym temacie](#BKMK_In_this_topic)

## <a name="crt-assertions"></a><a name="BKMK_CRT_assertions"></a> Potwierdzenia CRT
CRTDBG. Plik nagłówkowy H definiuje [_ASSERT i _ASSERTE makra](/cpp/c-runtime-library/reference/assert-asserte-assert-expr-macros) do sprawdzania potwierdzenia.

| Makro | Wynik |
|------------| - |
| `_ASSERT` | Jeśli określone wyrażenie zwróci wartość FALSE, nazwa pliku i numer wiersza `_ASSERT` . |
| `_ASSERTE` | Analogicznie jak `_ASSERT` , i ciąg reprezentujący wyrażenie, które zostało potwierdzone. |

`_ASSERTE` jest bardziej wydajny, ponieważ raportuje wyrażenie potwierdzone, które wystąpiło jako FAŁSZ. Może to być wystarczające do zidentyfikowania problemu bez odwoływania się do kodu źródłowego. Jednak wersja do debugowania aplikacji będzie zawierać stałą ciągu dla każdego wyrażenia potwierdzonego za pomocą `_ASSERTE` . Jeśli używasz wielu `_ASSERTE` makr, te wyrażenia ciągu zajmują znaczną ilość pamięci. Jeśli okaże się to problem, użyj, `_ASSERT` Aby zaoszczędzić pamięć.

Gdy `_DEBUG` jest zdefiniowany, `_ASSERTE` makro jest zdefiniowane w następujący sposób:

```cpp
#define _ASSERTE(expr) \
    do { \
        if (!(expr) && (1 == _CrtDbgReport( \
            _CRT_ASSERT, __FILE__, __LINE__, #expr))) \
            _CrtDbgBreak(); \
    } while (0)
```

Jeśli potwierdzone wyrażenie daje w wyniku wartość FALSE, [_CrtDbgReport](/cpp/c-runtime-library/reference/crtdbgreport-crtdbgreportw) jest wywoływana w celu zgłaszania błędu potwierdzenia (domyślnie przy użyciu okna dialogowego komunikatu). W przypadku wybrania opcji **Ponów** w oknie dialogowym komunikat `_CrtDbgReport` zwraca wartość 1 i `_CrtDbgBreak` wywołuje debuger za pomocą polecenia `DebugBreak` .

### <a name="checking-for-heap-corruption"></a>Sprawdzanie uszkodzenia sterty
Poniższy przykład używa [_CrtCheckMemory](/cpp/c-runtime-library/reference/crtcheckmemory) , aby sprawdzić uszkodzenie sterty:

```cpp
_ASSERTE(_CrtCheckMemory());
```

### <a name="checking-pointer-validity"></a>Sprawdzanie poprawności wskaźnika
Poniższy przykład używa [_CrtIsValidPointer](/cpp/c-runtime-library/reference/crtisvalidpointer) , aby sprawdzić, czy dany zakres pamięci jest prawidłowy do odczytu lub zapisu.

```cpp
_ASSERTE(_CrtIsValidPointer( address, size, TRUE );
```

W poniższym przykładzie używa się [_CrtIsValidHeapPointer](/cpp/c-runtime-library/reference/crtisvalidheappointer) , aby sprawdzić, czy wskaźnik wskazuje pamięć w stercie lokalnym (sterta utworzona i zarządzana przez to wystąpienie biblioteki wykonawczej C — Biblioteka DLL może mieć własne wystąpienie biblioteki, a w związku z tym jej własne sterty poza stertą aplikacji). To potwierdzenie przechwytuje nie tylko adresy null lub spoza zakresu, ale również wskaźniki do zmiennych statycznych, zmiennych stosu i innych pamięci nielokalnych.

```cpp
_ASSERTE(_CrtIsValidPointer( myData );
```

### <a name="checking-a-memory-block"></a>Sprawdzanie bloku pamięci
Poniższy przykład używa [_CrtIsMemoryBlock](/cpp/c-runtime-library/reference/crtismemoryblock) , aby sprawdzić, czy blok pamięci jest w stercie lokalnym i ma prawidłowy typ bloku.

```cpp
_ASSERTE(_CrtIsMemoryBlock (myData, size, &requestNumber, &filename, &linenumber));
```

[W tym temacie](#BKMK_In_this_topic)

## <a name="mfc-assertions"></a><a name="BKMK_MFC_assertions"></a> Potwierdzenia MFC
MFC definiuje makro [potwierdzenia](/previous-versions/ew16s3zc(v=vs.140)) do sprawdzenia potwierdzenia. Definiuje również `MFC ASSERT_VALID` `CObject::AssertValid` metody i do sprawdzania stanu wewnętrznego `CObject` obiektu pochodnego.

Jeśli argument makra MFC ma wartość `ASSERT` zero lub false, makro zatrzymuje wykonywanie programu i ostrzega użytkownika; w przeciwnym razie wykonywanie jest kontynuowane.

Gdy potwierdzenie nie powiedzie się, zostanie wyświetlone okno dialogowe komunikatu z nazwą pliku źródłowego oraz numerem wiersza potwierdzenia. W przypadku wybrania opcji ponów w oknie dialogowym wywołanie [AfxDebugBreak](/cpp/mfc/reference/diagnostic-services#afxdebugbreak) powoduje przerwanie działania w debugerze. W tym momencie można sprawdzić stos wywołań i użyć innych obiektów debugera, aby określić, dlaczego potwierdzenie nie powiodło się. Jeśli włączono [debugowanie just-in-Time](../debugger/just-in-time-debugging-in-visual-studio.md), a debuger nie był jeszcze uruchomiony, okno dialogowe może uruchomić debuger.

Poniższy przykład pokazuje, jak używać `ASSERT` do sprawdzania wartości zwracanej przez funkcję:

```cpp
int x = SomeFunc(y);
ASSERT(x >= 0);   //  Assertion fails if x is negative
```

Można użyć potwierdzeń z funkcją [IsKindOf](/cpp/mfc/reference/cobject-class#iskindof) , aby zapewnić sprawdzanie typu argumentów funkcji:

```cpp
ASSERT( pObject1->IsKindOf( RUNTIME_CLASS( CPerson ) ) );
```

`ASSERT`Makro nie daje kodu w wersji wydania. Jeśli chcesz oszacować wyrażenie w wersji wydania, użyj makra [verify](/cpp/mfc/reference/diagnostic-services#verify) zamiast Assert.

### <a name="mfc-assert_valid-and-cobjectassertvalid"></a><a name="BKMK_MFC_ASSERT_VALID_and_CObject__AssertValid"></a> MFC ASSERT_VALID i CObject:: AssertValid
[CObject:: AssertValid](/cpp/mfc/reference/cobject-class#assertvalid) Metoda zapewnia sprawdzenie stanu wewnętrznego obiektu w czasie wykonywania. Chociaż nie jest wymagane przesłonięcie w `AssertValid` przypadku wyprowadzania klasy z `CObject` , można zwiększyć niezawodność klasy. `AssertValid` należy wykonać potwierdzenia wszystkich zmiennych składowych obiektu, aby sprawdzić, czy zawierają one prawidłowe wartości. Na przykład należy sprawdzić, czy zmienne elementu członkowskiego wskaźnika nie są puste.

Poniższy przykład pokazuje, jak zadeklarować `AssertValid` funkcję:

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

Podczas przesłonięcia `AssertValid` należy wywołać wersję klasy bazowej `AssertValid` przed wykonaniem własnych sprawdzeń. Następnie użyj makra ASSERT, aby sprawdzić składowe unikatowe dla klasy pochodnej, jak pokazano poniżej:

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

Jeśli dowolna ze zmiennych składowych przechowuje obiekty, można użyć `ASSERT_VALID` makra do przetestowania ich wewnętrznej ważności (jeśli ich klasy zastępują `AssertValid` ).

Rozważmy na przykład klasę `CMyData` , która przechowuje [CObList](/cpp/mfc/reference/coblist-class) w jednej z jej zmiennych członkowskich. `CObList`Zmienna, `m_DataList` , przechowuje kolekcję `CPerson` obiektów. Skrócona deklaracja wygląda następująco `CMyData` :

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

`AssertValid`Przesłonięcie w następujący `CMyData` sposób:

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

`CMyData` używa `AssertValid` mechanizmu do testowania ważności obiektów przechowywanych w jego składowej danych. Zastąpienie `AssertValid` `CMyData` wywołuje `ASSERT_VALID` makro dla własnej m_pDataList zmiennej składowej.

Testowanie ważności nie jest zatrzymywane na tym poziomie, ponieważ Klasa `CObList` również przesłania `AssertValid` . To zastąpienie wykonuje dodatkowe Testowanie poprawności na wewnętrznym stanie listy. W rezultacie test ważności na `CMyData` obiekcie prowadzi do dodatkowych testów ważności dla Stanów wewnętrznych przechowywanego `CObList` obiektu listy.

W przypadku większej ilości pracy można dodać testy ważności dla `CPerson` obiektów przechowywanych na liście również. Można utworzyć klasy `CPersonList` z `CObList` i przesłonić `AssertValid` . W przesłonięciu należy wywołać, `CObject::AssertValid` a następnie wykonać iterację na liście, wywołując `AssertValid` dla każdego `CPerson` obiektu przechowywanego na liście. `CPerson`Klasa wyświetlana na początku tego tematu już zastępuje `AssertValid` .

Jest to zaawansowany mechanizm podczas kompilowania na potrzeby debugowania. Po późniejszej kompilacji do wydania mechanizm zostanie wyłączony automatycznie.

### <a name="limitations-of-assertvalid"></a><a name="BKMK_Limitations_of_AssertValid"></a> Ograniczenia dotyczące AssertValid
Wyzwolone potwierdzenie wskazuje, że obiekt jest nieskończonie zły i wykonywanie zostanie zatrzymane. Jednakże brak potwierdzenia wskazuje tylko, że nie znaleziono problemu, ale nie ma gwarancji, że obiekt jest dobry.

[W tym temacie](#BKMK_In_this_topic)

## <a name="using-assertions"></a><a name="BKMK_Using_assertions"></a> Używanie potwierdzeń

### <a name="catching-logic-errors"></a><a name="BKMK_Catching_logic_errors"></a> Przechwytywanie błędów logiki
Można ustawić potwierdzenie dla warunku, który musi być spełniony zgodnie z logiką programu. Potwierdzenie nie działa, chyba że wystąpi błąd logiki.

Załóżmy na przykład, że symulowane są cząsteczki gazu w kontenerze, a zmienna `numMols` reprezentuje łączną liczbę cząsteczek. Ta liczba nie może być mniejsza od zera, więc można uwzględnić w niej instrukcję potwierdzenia MFC:

```cpp
ASSERT(numMols >= 0);
```

Może również zawierać potwierdzenie CRT podobne do tego:

```cpp
_ASSERT(numMols >= 0);
```

Te instrukcje nie działają, jeśli program działa poprawnie. Jeśli błąd logiki jest `numMols` mniejszy od zera, to potwierdzenie zatrzymuje wykonywanie programu i wyświetla okno [dialogowe potwierdzenie nie powiodło się](../debugger/assertion-failed-dialog-box.md).

[W tym temacie](#BKMK_In_this_topic)

### <a name="checking-results"></a><a name="BKMK_Checking_results_"></a> Sprawdzanie wyników
Potwierdzenia są przydatne w przypadku operacji testowych, których wyniki nie są oczywiste od szybkiej inspekcji wizualnej.

Rozważmy na przykład poniższy kod, który aktualizuje zmienną `iMols` na podstawie zawartości listy połączonej wskazywanej przez `mols` :

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

Liczba cząsteczek zliczonych przez `iMols` musi być zawsze mniejsza lub równa łącznej liczbie cząsteczek, `numMols` . Kontrola wzrokowa pętli nie pokazuje, że taka sytuacja będzie konieczna, więc instrukcja Assert jest używana po pętli do przetestowania dla tego warunku.

[W tym temacie](#BKMK_In_this_topic)

### <a name="finding-unhandled-errors"></a><a name="BKMK_Testing_error_conditions_"></a> Znajdowanie nieobsłużonych błędów
Za pomocą potwierdzeń można testować w przypadku wystąpienia błędów w punkcie w kodzie, w którym zostały obsłużone wszystkie błędy. W poniższym przykładzie procedura graficzna zwraca kod błędu lub zero dla sukcesu.

```cpp
myErr = myGraphRoutine(a, b);

/* Code to handle errors and
   reset myErr if successful */

ASSERT(!myErr); -- MFC version
_ASSERT(!myErr); -- CRT version
```

Jeśli kod obsługi błędu działa prawidłowo, błąd powinien zostać obsłużony i `myErr` zresetowany do zera przed osiągnięciem potwierdzenia. Jeśli `myErr` ma inną wartość, potwierdzenie kończy się niepowodzeniem, program zostaje zatrzymany i zostanie wyświetlone okno [dialogowe potwierdzenie nie powiodło](../debugger/assertion-failed-dialog-box.md) się.

Instrukcje Assertion nie są jednak substytutem kodu obsługującego błędy. W poniższym przykładzie pokazano instrukcję assertion, która może prowadzić do problemów w końcowym kodzie zlecenia:

```cpp
myErr = myGraphRoutine(a, b);

/* No Code to handle errors */

ASSERT(!myErr); // Don't do this!
_ASSERT(!myErr); // Don't do this, either!
```

Ten kod opiera się na instrukcji Assert, aby obsłużyć warunek błędu. W związku z tym kod błędu zwracany przez nie `myGraphRoutine` zostanie obsłużony w końcowym kodzie zlecenia.

[W tym temacie](#BKMK_In_this_topic)

## <a name="see-also"></a>Zobacz też

- [Zabezpieczenia debugera](../debugger/debugger-security.md)
- [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)
- [Potwierdzenia w zarządzanym kodzie](../debugger/assertions-in-managed-code.md)