---
title: Najlepsze praktyki i przykłady (SAL)
ms.date: 11/04/2016
ms.topic: conceptual
author: mikeblome
ms.author: mblome
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 27570e282c230d4bec47e70aa1bcdd053b75597c
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236756"
---
# <a name="best-practices-and-examples-sal"></a>Najlepsze praktyki i przykłady (SAL)
Oto kilka sposobów, aby maksymalnie wykorzystać możliwości języka z adnotacjami kodu źródłowego (SAL) i uniknąć niektórych typowych problemów.

## <a name="_in_"></a>\_W\_

Jeśli funkcja powinna zapisywać w elemencie, użyj `_Inout_` `_In_`zamiast. Jest to szczególnie istotne w przypadku zautomatyzowanej konwersji ze starszych makr na SAL. Przed sal, wielu programistów używa makr jako komentarzy — makra o nazwach `IN` `OUT` `IN_OUT`,, lub odmianach tych nazw. Chociaż zalecamy przekonwertowanie tych makr na SAL, Zachęcamy również do pomyślnego przeprowadzenia konwersji, ponieważ kod może ulec zmianie od momentu zapisania oryginalnego prototypu, a stare makro może nie odzwierciedlać tego kodu. Należy zwrócić szczególną uwagę `OPTIONAL` na to, że makro komentarza jest często umieszczane nieprawidłowo — na przykład po niewłaściwej stronie przecinka.

```cpp

// Incorrect
void Func1(_In_ int *p1)
{
    if (p1 == NULL)
        return;

    *p1 = 1;
}

// Correct
void Func2(_Inout_ PCHAR p1)
{
    if (p1 == NULL)
        return;

    *p1 = 1;
}
```

## <a name="_opt_"></a>\_opt\_

Jeśli obiekt wywołujący nie może przekazać wskaźnika `_In_` o wartości null, użyj lub `_Out_` zamiast `_In_opt_` lub `_Out_opt_`. Ma to zastosowanie nawet do funkcji, która sprawdza jej parametry i zwraca błąd, jeśli ma wartość NULL, gdy nie powinna być. Chociaż posiadanie funkcji sprawdza jej parametr pod kątem nieoczekiwanej wartości NULL i jest bezpiecznie zwracać, dobrze jest dobrym praktycznym sposobem kodowania, nie oznacza to, że adnotacja parametru może być`_*Xxx*_opt_`typu opcjonalnego ().

```cpp

// Incorrect
void Func1(_Out_opt_ int *p1)
{
    *p = 1;
}

// Correct
void Func2(_Out_ int *p1)
{
    *p = 1;
}
```

## <a name="_pre_defensive_-and-_post_defensive_"></a>\_Przed\_\_ obroną i\_ogłoszeniem\_obronnym\_

Jeśli funkcja pojawia się na granicy zaufania, zalecamy użycie `_Pre_defensive_` adnotacji.  Modyfikator "obrony" modyfikuje niektóre adnotacje, aby wskazać, że w punkcie wywołania interfejs powinien być dokładnie sprawdzony, ale w treści implementacji należy założyć, że można przekazywać nieprawidłowe parametry. W takim przypadku `_In_ _Pre_defensive_` jest preferowany na granicy zaufania, aby wskazać, że chociaż obiekt wywołujący otrzyma błąd, jeśli próbuje przekazać wartość null, treść funkcji zostanie przeanalizowana tak, jakby parametr może mieć wartość null, a wszystkie próby odwołujące się do wskaźnika bez uprzedniego sprawdzenie, czy dla wartości NULL zostanie oflagowane.  `_Post_defensive_` Adnotacja jest również dostępna do użycia w wywołaniach zwrotnych, w przypadku których zakłada się, że jest to obiekt wywołujący, a niezaufany kod jest wywoływanym kodem.

## <a name="_out_writes_"></a>\_Zapisy\_na zewnątrz\_

Poniższy przykład ilustruje typowe nadużycie `_Out_writes_`.

```cpp

// Incorrect
void Func1(_Out_writes_(size) CHAR *pb,
    DWORD size
);
```

Adnotacja `_Out_writes_` oznacza, że masz bufor. Ma `cb` przydzieloną liczbę bajtów z pierwszym bajtem zainicjowanym przy zamykaniu. Ta Adnotacja nie jest ściśle zła i warto wyrazić przydzieloną wielkość. Nie informuje jednak o tym, ile elementów jest inicjowanych przez funkcję.

W następnym przykładzie pokazano trzy poprawne sposoby w pełni określić dokładny rozmiar zainicjowanej części buforu.

```cpp

// Correct
void Func1(_Out_writes_to_(size, *pCount) CHAR *pb,
    DWORD size,
    PDWORD pCount
);

void Func2(_Out_writes_all_(size) CHAR *pb,
    DWORD size
);

void Func3(_Out_writes_(size) PSTR pb,
    DWORD size
);
```

## <a name="_out_-pstr"></a>\_PSTR\_ out

Użycie `_Out_ PSTR` jest niemal zawsze błędne. Jest interpretowany jako mający parametr wyjściowy, który wskazuje bufor znaków i jest zakończony znakiem NULL.

```cpp

// Incorrect
void Func1(_Out_ PSTR pFileName, size_t n);

// Correct
void Func2(_Out_writes_(n) PSTR wszFileName, size_t n);
```

Adnotacja `_In_ PCSTR` taka jest powszechna i przydatna. Wskazuje ciąg wejściowy, który ma zakończenie o wartości null, ponieważ warunek wstępny `_In_` umożliwia rozpoznanie ciągu zakończonego wartością null.

## <a name="_in_-wchar-p"></a>\_W\_ WCHAR * p

`_In_ WCHAR* p`wskazuje, że istnieje wskaźnik `p` wejściowy wskazujący na jeden znak. Jednak w większości przypadków jest to prawdopodobnie nie jest to specyfikacja, która jest zamierzona. Zamiast tego najprawdopodobniej zamierzone jest określenie tablicy zakończonej zerem; w tym celu należy użyć `_In_ PWSTR`.

```cpp

// Incorrect
void Func1(_In_ WCHAR* wszFileName);

// Correct
void Func2(_In_ PWSTR wszFileName);
```

Brak prawidłowej specyfikacji zakończenia o wartości NULL jest wspólna. Użyj odpowiedniej `STR` wersji, aby zamienić typ, jak pokazano w poniższym przykładzie.

```cpp

// Incorrect
BOOL StrEquals1(_In_ PCHAR p1, _In_ PCHAR p2)
{
    return strcmp(p1, p2) == 0;
}

// Correct
BOOL StrEquals2(_In_ PSTR p1, _In_ PSTR p2)
{
    return strcmp(p1, p2) == 0;
}
```

## <a name="_out_range_"></a>\_Zakres\_poza\_

Jeśli parametr jest wskaźnikiem i chcesz przedstawić zakres wartości elementu, który jest wskazywany przez wskaźnik, użyj `_Deref_out_range_` `_Out_range_`zamiast. W poniższym przykładzie zakres * pcbFilled jest wyrażony jako, a nie pcbFilled.

```cpp

// Incorrect
void Func1(
    _Out_writes_bytes_to_(cbSize, *pcbFilled) BYTE *pb,
    DWORD cbSize,
    _Out_range_(0, cbSize) DWORD *pcbFilled
);

// Correct
void Func2(
    _Out_writes_bytes_to_(cbSize, *pcbFilled) BYTE *pb,
    DWORD cbSize,
    _Deref_out_range_(0, cbSize) _Out_ DWORD *pcbFilled
);
```

`_Deref_out_range_(0, cbSize)`nie są absolutnie wymagane w przypadku niektórych narzędzi, ponieważ mogą być wywnioskowane `_Out_writes_to_(cbSize,*pcbFilled)`z, ale w tym miejscu są wyświetlane w celu kompletności.

## <a name="wrong-context-in-_when_"></a>Błędny kontekst w \_czasie\_

Innym często używanym błędem jest użycie oceny końcowej w warunkach wstępnych. W poniższym przykładzie `_Requires_lock_held_` jest warunkiem wstępnym.

```cpp

// Incorrect
_When_(return == 0, _Requires_lock_held_(p->cs))
int Func1(_In_ MyData *p, int flag);

// Correct
_When_(flag == 0, _Requires_lock_held_(p->cs))
int Func2(_In_ MyData *p, int flag);
```

Wyrażenie `result` odwołuje się do wartości po stanie, która jest niedostępna w stanie sprzed.

## <a name="true-in-_success_"></a>Prawda w \_sukcesie\_

Jeśli funkcja powiedzie się, gdy wartość zwracana jest różna od zera, `return != 0` Użyj jako warunku sukcesu `return == TRUE`zamiast. Wartość różna od zera nie musi oznaczać równoważności do wartości rzeczywistej, która zapewnia `TRUE`kompilator. Parametr `_Success_` jest wyrażeniem, a następujące wyrażenia są oceniane jako równoważne: `return != 0`, `return != false`, `return != FALSE`, i `return` bez parametrów i porównań.

```cpp

// Incorrect
_Success_(return == TRUE, _Acquires_lock_(*lpCriticalSection))
BOOL WINAPI TryEnterCriticalSection(
  _Inout_ LPCRITICAL_SECTION lpCriticalSection
);

// Correct
_Success_(return != 0, _Acquires_lock_(*lpCriticalSection))
BOOL WINAPI TryEnterCriticalSection(
  _Inout_ LPCRITICAL_SECTION lpCriticalSection
);
```

## <a name="reference-variable"></a>Zmienna odwołania

W przypadku zmiennej referencyjnej Poprzednia wersja sal używała wskaźnika implikowanego jako elementu docelowego adnotacji i wymaga dodania `__deref` do adnotacji, które są dołączone do zmiennej odwołania. Ta wersja używa samego obiektu i nie wymaga dodatkowych `_Deref_`.

```cpp

// Incorrect
void Func1(
    _Out_writes_bytes_all_(cbSize) BYTE *pb,
    _Deref_ _Out_range_(0, 2) _Out_ DWORD &cbSize
);

// Correct
void Func2(
    _Out_writes_bytes_all_(cbSize) BYTE *pb,
    _Out_range_(0, 2) _Out_ DWORD &cbSize
);
```

## <a name="annotations-on-return-values"></a>Adnotacje dla zwracanych wartości

Poniższy przykład przedstawia typowy problem w adnotacjach wartości zwracanej.

```cpp

// Incorrect
_Out_opt_ void *MightReturnNullPtr1();

// Correct
_Ret_maybenull_ void *MightReturnNullPtr2();
```

W tym przykładzie mówi `_Out_opt_` , że wskaźnik może mieć wartość null w ramach warunku wstępnego. Nie można jednak zastosować warunków wstępnych do wartości zwracanej. W takim przypadku poprawną adnotacją jest `_Ret_maybenull_`.

## <a name="see-also"></a>Zobacz także

[Korzystanie z adnotacji SAL w celu zmniejszenia liczby defektów kodu C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)  
[Informacje o języku SAL](../code-quality/understanding-sal.md)  
[Dodawanie adnotacji do parametrów funkcji i zwracanych wartości](../code-quality/annotating-function-parameters-and-return-values.md)  
[Zachowanie funkcji dodawania adnotacji](../code-quality/annotating-function-behavior.md)  
[Dodawanie adnotacji do struktur i klas](../code-quality/annotating-structs-and-classes.md)  
[Dodawanie adnotacji do zachowania blokującego](../code-quality/annotating-locking-behavior.md)  
[Określanie miejsca i warunków stosowania adnotacji](../code-quality/specifying-when-and-where-an-annotation-applies.md)  
[Funkcje wewnętrzne](../code-quality/intrinsic-functions.md)  
