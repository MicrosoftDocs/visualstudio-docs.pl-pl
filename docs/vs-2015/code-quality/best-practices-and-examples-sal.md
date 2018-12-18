---
title: Najlepsze praktyki i przykłady (SAL) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 666276fb-99c2-4dc9-8bac-d74861c203ea
caps.latest.revision: 14
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9327ab850bb5f62158e48abc4c8445d3f9b6fe9b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51743737"
---
# <a name="best-practices-and-examples-sal"></a>Najlepsze praktyki i przykłady (SAL)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Oto kilka sposobów, aby wykorzystać poza języka adnotacji kodu źródłowego (SAL) i uniknąć niektórych typowych problemów.  
  
## <a name="in"></a>\_W\_
 Jeśli funkcja powinna zapisu do elementu, użyj `_Inout_` zamiast `_In_`. Jest to szczególnie istotne w przypadku zautomatyzowanych konwersja starsze makra na SAL. Przed SAL, wielu programistów używał makra w postaci komentarzy — makra, które zostały nazwane `IN`, `OUT`, `IN_OUT`, lub odmiany tych nazw. Mimo że firma Microsoft zaleca SAL przekonwertowanie tych makr, również zachęcamy do należy zachować ostrożność podczas ich konwersji, ponieważ kod mógł ulec zmianie, ponieważ prototyp oryginalnego zostało zapisane, a stare makro może nie odzwierciedlają, co dany kod realizuje. Należy zachować szczególną ostrożność o `OPTIONAL` komentarz makra, ponieważ często jest nieprawidłowo umieszczony — na przykład na problem po stronie przecinka.  
  
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
  
## <a name="opt"></a>\_opt\_  
 Jeśli obiekt wywołujący nie może przejść w pustym wskaźnikiem, użyj `_In_` lub `_Out_` zamiast `_In_opt_` lub `_Out_opt_`. Dotyczy to nawet w przypadku funkcji, która sprawdza poprawność parametrów i zwraca błąd, jeśli ma wartość NULL, gdy nie powinny być. Mimo że funkcja Sprawdź parametrem Nieoczekiwana pusta i zwraca bez problemu zmieniała jest dobrą praktyką programowania obrony, nie oznacza to, że adnotacja parametru może być opcjonalnie typu (\_*Xxx*_opt —\_).  
  
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
  
## <a name="predefensive-and-postdefensive"></a>\_Pre_defensive\_ i \_Post_defensive\_  
 Jeśli funkcja znajduje się na granicy zaufania i firma Microsoft zaleca używanie `_Pre_defensive_` adnotacji.  Modyfikator "obrony" modyfikuje pewne adnotacje wskazanie, że w momencie wywołania, interfejsu, które powinny być sprawdzane ściśle, ale w treści implementacji go powinien przyjęto założenie, nieprawidłowe parametry mogą być przekazywane. W takim przypadku `_In_ _Pre_defensive_` jest preferowany w granicy zaufania, aby wskazać, że chociaż obiekt wywołujący, otrzymają komunikat o błędzie, gdy podejmowana jest próba przekazania wartości NULL, treści funkcji będą analizowane tak, jakby parametru może być NULL, a wszystkie próby cofnąć odwołanie wskaźnika bez uprzedniego Sprawdzanie wartości NULL zostanie oflagowana.  A `_Post_defensive_` adnotacji jest również dostępne dla wywołań zwrotnych, gdzie zaufanego strona zakłada, że obiekt wywołujący, a niezaufanego kodu to dzwonić kodu.  
  
## <a name="outwrites"></a>\_Out_writes\_  
 W poniższym przykładzie pokazano wspólnej nadużycie `_Out_writes_`.  
  
```cpp  
  
// Incorrect  
void Func1(_Out_writes_(size) CHAR *pb,   
    DWORD size  
);  
  
```  
  
 Adnotacja `_Out_writes_` oznacza, że masz bufora. Ma ona `cb` bajtów przydzielonych za pomocą pierwszego bajtu zainicjowana na wyjściu. Ta adnotacja nie jest ściśle problem i warto express przydzielony rozmiar. Jednak program nie nakazuje ile elementy są inicjowane przez funkcję.  
  
 W kolejnym przykładzie pokazano trzy sposoby poprawna, aby w pełni określić dokładny rozmiar zainicjowane część buforu.  
  
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
  
## <a name="out-pstr"></a>\_Limit\_ PSTR  
 Korzystanie z `_Out_ PSTR` prawie zawsze jest nieprawidłowy. To jest interpretowane jako parametr wyjściowy, który wskazuje na buforu znaków i jest zakończony znakiem NULL.  
  
```cpp  
  
// Incorrect  
void Func1(_Out_ PSTR pFileName, size_t n);  
  
// Correct  
void Func2(_Out_writes_(n) PSTR wszFileName, size_t n);  
  
```  
  
 Adnotacja, takich jak `_In_ PCSTR` to typowe i przydatne. Wskazuje ciągu wejściowego, który ma zakończenia o wartości NULL, ponieważ warunek wstępny elementu `_In_` umożliwia rozpoznawanie ciąg zakończony znakiem NULL.  
  
## <a name="in-wchar-p"></a>\_W\_ WCHAR * p  
 `_In_ WCHAR* p` Określa, czy jest wskaźnik danych wejściowych `p` wskazującej jeden znak. Jednak w większości przypadków to prawdopodobnie nie jest specyfikacja która jest przeznaczony. Zamiast tego co prawdopodobnie jest przeznaczony jest specyfikacja tablicą zakończoną znakiem NULL; Aby to zrobić, należy użyć `_In_ PWSTR`.  
  
```cpp  
  
// Incorrect  
void Func1(_In_ WCHAR* wszFileName);  
  
// Correct  
void Func2(_In_ PWSTR wszFileName);  
  
```  
  
 Brak prawidłowego określenia zakończenia o wartości NULL jest powszechne. To zrobić w odpowiednim `STR` wersji, aby zastąpić ten typ, jak pokazano w poniższym przykładzie.  
  
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
  
## <a name="outrange"></a>\_Out_range\_  
 Jeśli parametr jest wskaźnik, a użytkownik chce wyrażenia zakresu wartość elementu, który jest wskazywany przez wskaźnik, należy użyć `_Deref_out_range_` zamiast `_Out_range_`. W poniższym przykładzie zakres * pcbFilled jest wyrażona, nie pcbFilled.  
  
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
  
 `_Deref_out_range_(0, cbSize)` nie jest bezwzględnie konieczne w niektórych narzędzi, ponieważ można go wywnioskować na podstawie `_Out_writes_to_(cbSize,*pcbFilled)`, ale jest wyświetlany tutaj aby informacje były kompletne.  
  
## <a name="wrong-context-in-when"></a>Nieprawidłowy kontekst w \_po\_  
 Inny powszechnym błędem jest do użytku po stanie oceny warunków wstępnych. W poniższym przykładzie `_Requires_lock_held_` jest warunkiem wstępnym.  
  
```cpp  
  
// Incorrect  
_When_(return == 0, _Requires_lock_held_(p->cs))  
int Func1(_In_ MyData *p, int flag);  
  
// Correct  
_When_(flag == 0, _Requires_lock_held_(p->cs))  
int Func2(_In_ MyData *p, int flag);  
  
```  
  
 Wyrażenie `result` odnosi się do wartości stanu końcowego, która nie jest dostępna w stanie wstępnego.  
  
## <a name="true-in-success"></a>Wartość TRUE w \_sukces\_  
 Jeśli funkcja się powiedzie, gdy zwracana wartość jest różna od zera, użyj `return != 0` jako warunek powodzenia zamiast `return == TRUE`. NonZero nie musi oznaczać równoważności do rzeczywistej wartości, który kompilator zapewnia `TRUE`. Parametr `_Success_` jest wyrażeniem, a poniższe wyrażenia są obliczane jako równoważne: `return != 0`, `return != false`, `return != FALSE`, i `return` bez parametrów lub porównań.  
  
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
  
## <a name="reference-variable"></a>Odwołanie do zmiennej  
 Odwołanie do zmiennej, poprzednia wersja SAL używana dorozumianych wskaźnika jako cel adnotacji i wymagane dodanie `__deref` do adnotacji, które są dołączone do zmiennej odwołania. Ta wersja wykorzystuje samego obiektu i nie wymaga dodatkowych `_Deref_`.  
  
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
  
## <a name="annotations-on-return-values"></a>Adnotacje na wartości zwracane  
 Poniższy przykład przedstawia typowy problem w zwracanej wartości adnotacji.  
  
```cpp  
  
// Incorrect  
_Out_opt_ void *MightReturnNullPtr1();  
  
// Correct  
_Ret_maybenull_ void *MightReturnNullPtr2();  
  
```  
  
 W tym przykładzie `_Out_opt_` mówi wskaźnik może mieć wartości NULL jako część warunku wstępnego. Jednak warunki wstępne nie można zastosować do wartości zwracanej. W tym przypadku jest poprawny adnotacji `_Ret_maybenull_`.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z adnotacji SAL w celu zmniejszenia liczby błędów kodu C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Informacje o języku SAL](../code-quality/understanding-sal.md)   
 [Dodawanie adnotacji do parametrów funkcji i zwracanych wartości](../code-quality/annotating-function-parameters-and-return-values.md)   
 [Zachowanie funkcji dodawania adnotacji](../code-quality/annotating-function-behavior.md)   
 [Dodawanie adnotacji do struktur i klas](../code-quality/annotating-structs-and-classes.md)   
 [Dodawanie adnotacji do zachowania blokującego](../code-quality/annotating-locking-behavior.md)   
 [Określanie miejsca i warunków stosowania adnotacji](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Funkcje wewnętrzne](../code-quality/intrinsic-functions.md)



