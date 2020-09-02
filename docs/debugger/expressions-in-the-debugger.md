---
title: Wyrażenia w debugerze | Microsoft Docs
ms.date: 03/02/2020
ms.topic: conceptual
f1_keywords:
- vs.debug.expressions
helpviewer_keywords:
- expressions [debugger]
- debugging [Visual Studio], expressions
- expression evaluation, debugger evaluator
- native expression evaluation
- expression evaluators
- debugger, evaluating expressions
- debugging [Visual Studio], expression evaluation
- debugging [Visual Studio], variable evaluation
ms.assetid: 70f9b531-44c7-4d77-980d-5eddbf2bff41
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4ab66f288ad8442b6f2b5aab3499e2c1f3857632
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "89311459"
---
# <a name="expressions-in-the-visual-studio-debugger"></a>Wyrażenia w debugerze programu Visual Studio
Debuger programu Visual Studio zawiera oszacowania wyrażeń, które działają po wprowadzeniu wyrażenia w oknie dialogowym **QuickWatch** , oknie **czujki** lub w oknie **bezpośrednim** . Oceny wyrażeń są również w pracy w oknie **punkty przerwania** i wiele innych miejsc w debugerze.

W poniższych sekcjach opisano ograniczenia obliczeń wyrażeń dla języków obsługiwanych przez program Visual Studio.

## <a name="f-expressions-are-not-supported"></a>Wyrażenia języka F # nie są obsługiwane
Wyrażenia języka F # nie są rozpoznawane. Jeśli debugujesz kod F #, musisz przetłumaczyć wyrażenia na składnię języka C# przed wprowadzeniem wyrażeń do okna debugera lub w oknie dialogowym. W przypadku tłumaczenia wyrażeń z języka F # do języka C# należy pamiętać, że C# używa `==` operatora do testowania równości, podczas gdy F # używa jednego `=` .

## <a name="c-expressions"></a>Wyrażenia języka C++
Aby uzyskać informacje o używaniu operatorów kontekstu z wyrażeniami w języku C++, zobacz [operator kontekstu (C++)](../debugger/context-operator-cpp.md).

### <a name="unsupported-expressions-in-c"></a>Nieobsługiwane wyrażenia w języku C++

#### <a name="constructors-destructors-and-conversions"></a>Konstruktory, destruktory i konwersje
Nie można wywołać konstruktora ani destruktora dla obiektu, jawnie lub niejawnie. Na przykład następujące wyrażenie jawnie wywołuje konstruktora i skutkuje komunikatem o błędzie:

```C++
my_date( 2, 3, 1985 )
```

Nie można wywołać funkcji konwersji, jeśli miejsce docelowe konwersji jest klasą. Taka konwersja obejmuje Konstruowanie obiektu. Na przykład, jeśli `myFraction` jest wystąpieniem `CFraction` , które definiuje operator funkcji konwersji `FixedPoint` , następujące wyrażenie powoduje błąd:

```C++
(FixedPoint)myFraction
```

Nie można wywoływać operatora new lub DELETE. Na przykład następujące wyrażenie nie jest obsługiwane:

```C++
new Date(2,3,1985)
```

#### <a name="preprocessor-macros"></a>Makra preprocesora
Makra preprocesora nie są obsługiwane w debugerze. Na przykład, jeśli stała `VALUE` jest zadeklarowana jako: `#define VALUE 3` , nie można użyć `VALUE` w oknie **czujka** . Aby uniknąć tego ograniczenia, należy zamienić na `#define` wyliczenia i funkcje, jeśli jest to możliwe.

### <a name="using-namespace-declarations"></a>Korzystanie z deklaracji przestrzeni nazw
Nie można używać `using namespace` deklaracji.  Aby uzyskać dostęp do nazwy typu lub zmiennej poza bieżącą przestrzenią nazw, należy użyć w pełni kwalifikowanej nazwy.

### <a name="anonymous-namespaces"></a>Anonimowe przestrzenie nazw
Anonimowe przestrzenie nazw nie są obsługiwane. Jeśli masz Poniższy kod, nie możesz dodać `test` go do okna Czujka:

```C++
namespace mars
{
    namespace
    {
        int test = 0;
    }
}
int main()
{
    // Adding a watch on test does not work.
    mars::test++;
    return 0;
}

```

### <a name="using-debugger-intrinsic-functions-to-maintain-state"></a><a name="BKMK_Using_debugger_intrinisic_functions_to_maintain_state"></a> Używanie funkcji wewnętrznych debugera do utrzymania stanu
Funkcje wewnętrzne debugera umożliwiają wywoływanie niektórych funkcji języka C/C++ w wyrażeniach bez zmiany stanu aplikacji.

Funkcje wewnętrzne debugera:

- Gwarantowane jest bezpieczne: wykonanie funkcji wewnętrznej debugera nie spowoduje uszkodzenia debugowanego procesu.

- Są dozwolone we wszystkich wyrażeniach, nawet w scenariuszach, w których efekty uboczne i obliczanie funkcji są niedozwolone.

- Pracuj w scenariuszach, w których regularne wywołania funkcji nie są możliwe, na przykład debugowanie minizrzutu.

  Funkcje wewnętrzne debugera mogą również bardziej wygodnie oceniać wyrażenia. Na przykład, `strncmp(str, "asd")` jest znacznie łatwiejsze do zapisu w warunku punktu przerwania niż `str[0] == 'a' && str[1] == 's' && str[2] == 'd'` . )

|Obszar|Funkcje wewnętrzne|
|----------|-------------------------|
|**Długość ciągu**|[strlen, wcslen](https://docs.microsoft.com/cpp/c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l), [strnlen, wcsnlen](https://docs.microsoft.com/cpp/c-runtime-library/reference/strnlen-strnlen-s)|
|**Porównanie ciągów**|[strcmp, wcscmp](https://docs.microsoft.com/cpp/c-runtime-library/reference/strcmp-wcscmp-mbscmp), [stricmp, wcsicmp](https://docs.microsoft.com/cpp/c-runtime-library/reference/stricmp-wcsicmp), [_stricmp, _strcmpi, _wcsicmp, _wcscmpi](https://docs.microsoft.com/cpp/c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l), [strncmp, wcsncmp](https://docs.microsoft.com/cpp/c-runtime-library/reference/strncmp-wcsncmp-mbsncmp-mbsncmp-l), [strnicmp, wcsnicmp](https://docs.microsoft.com/cpp/c-runtime-library/reference/strnicmp-wcsnicmp), [_strnicmp, _wcsnicmp](https://docs.microsoft.com/cpp/c-runtime-library/reference/strnicmp-wcsnicmp-mbsnicmp-strnicmp-l-wcsnicmp-l-mbsnicmp-l)|
|**Wyszukiwanie ciągów**|[strchr, wcschr](https://docs.microsoft.com/cpp/c-runtime-library/reference/strchr-wcschr-mbschr-mbschr-l), [memchr, wmemchr](https://docs.microsoft.com/cpp/c-runtime-library/reference/memchr-wmemchr), [strstr, wcsstr](https://docs.microsoft.com/cpp/c-runtime-library/reference/strstr-wcsstr-mbsstr-mbsstr-l)|
|**Win32**|[CoDecodeProxy](https://docs.microsoft.com/windows/win32/api/combaseapi/nf-combaseapi-codecodeproxy), [DecodePointer](https://docs.microsoft.com/previous-versions/bb432242%28v%3dvs.85%29), [GetLastError](https://docs.microsoft.com/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror), [TlsGetValue](https://docs.microsoft.com/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsgetvalue)|
|**Windows 8**|[RoInspectCapturedStackBackTrace](https://docs.microsoft.com/windows/win32/api/roerrorapi/nf-roerrorapi-roinspectcapturedstackbacktrace), [WindowsCompareStringOrdinal](https://docs.microsoft.com/windows/win32/api/winstring/nf-winstring-windowscomparestringordinal), [WindowsGetStringLen](https://docs.microsoft.com/windows/win32/api/winstring/nf-winstring-windowsgetstringlen), [WindowsGetStringRawBuffer](https://docs.microsoft.com/windows/win32/api/winstring/nf-winstring-windowsgetstringrawbuffer)<br /><br /> Funkcje te wymagają, aby proces, który jest debugowany, był uruchomiony w systemie Windows 8. Debugowanie plików zrzutu wygenerowanych z urządzenia z systemem Windows 8 wymaga również, aby na komputerze z programem Visual Studio był uruchomiony system Windows 8. Jednak w przypadku zdalnego debugowania urządzenia z systemem Windows 8 na komputerze z programem Visual Studio może działać system Windows 7.|
|**Różne**|__log2//zwraca bazę logarytmiczną 2 z określonej liczby całkowitej zaokrągloną do najbliższej mniejszej liczby całkowitej.<br /><br />__findNonNull, DecodeHString, DecodeWinRTRestrictedException, DynamicCast, DynamicMemberLookup, GetEnvBlockLength<br /><br />Stdext_HashMap_Int_OperatorBracket_idx, Std_UnorderedMap_Int_OperatorBracket_idx<br /><br />ConcurrencyArray_OperatorBracket_idx//concurrency:: Array<>:: operator [index<>] i operator (indeks<>)<br /><br />ConcurrencyArray_OperatorBracket_int//concurrency:: Array<>:: operator (int, int,...)<br /><br />ConcurrencyArray_OperatorBracket_tidx//concurrency:: Array<>:: operator [tiled_index<>] i operator (tiled_index<>)<br /><br />ConcurrencyArrayView_OperatorBracket_idx//concurrency:: array_view<>:: operator [index<>] i operator (index<>)<br /><br />ConcurrencyArrayView_OperatorBracket_int//concurrency:: array_view<>:: operator (int, int,...)<br /><br />ConcurrencyArrayView_OperatorBracket_tidx//concurrency:: array_view<>:: operator [tiled_index<>] i operator (tiled_index<>)<br /><br />TreeTraverse_Init//Inicjuje nowe przechodzenie drzewa<br /><br />TreeTraverse_Next//zwraca węzły w drzewie<br /><br />TreeTraverse_Skip//pomija węzły w oczekującym przechodzeniu drzewa "|

## <a name="ccli---unsupported-expressions"></a>C++/CLI — nieobsługiwane wyrażenia

- Rzutowania obejmujące wskaźniki lub rzuty zdefiniowane przez użytkownika nie są obsługiwane.

- Porównywanie i przypisywanie obiektów nie są obsługiwane.

- Przeciążone operatory i przeciążone funkcje nie są obsługiwane.

- Pakowanie i rozpakowywanie nie są obsługiwane.

- `Sizeof` Operator nie jest obsługiwany.

## <a name="c---unsupported-expressions"></a>C# — nieobsługiwane wyrażenia

### <a name="dynamic-objects"></a>Obiekty dynamiczne
W wyrażeniach debugera, które są statycznie wpisane jako dynamiczne, można używać zmiennych. Gdy obiekty, które implementują <xref:System.Dynamic.IDynamicMetaObjectProvider> , są oceniane w okno wyrażeń kontrolnych, dodawany jest dynamiczny węzeł widoku. Węzeł Widok dynamiczny zawiera elementy członkowskie obiektów, ale nie zezwala na edytowanie wartości elementów członkowskich.

Następujące funkcje obiektów dynamicznych nie są obsługiwane:

- Operatory złożone `+=` , `-=` ,, `%=` `/=` i `*=`

- Wiele rzutowania, w tym rzutowania liczbowego i rzutowania argumentów typu

- Wywołania metody z więcej niż dwoma argumentami

- Metody pobierające właściwości z więcej niż dwoma argumentami

- Metody ustawiające właściwości z argumentami

- Przypisywanie do indeksatora

- Operatory logiczne `&&` i `||`

### <a name="anonymous-methods"></a>Metody anonimowe
Tworzenie nowych metod anonimowych nie jest obsługiwane.

## <a name="visual-basic---unsupported-expressions"></a>Visual Basic — nieobsługiwane wyrażenia

### <a name="dynamic-objects"></a>Obiekty dynamiczne
W wyrażeniach debugera, które są statycznie wpisane jako dynamiczne, można używać zmiennych. Gdy obiekty implementujące program <xref:System.Dynamic.IDynamicMetaObjectProvider> są oceniane w okno wyrażeń kontrolnych, dodawany jest dynamiczny węzeł widoku. Węzeł Widok dynamiczny zawiera elementy członkowskie obiektów, ale nie zezwala na edytowanie wartości elementów członkowskich.

Następujące funkcje obiektów dynamicznych nie są obsługiwane:

- Operatory złożone `+=` , `-=` ,, `%=` `/=` i `*=`

- Wiele rzutowania, w tym rzutowania liczbowego i rzutowania argumentów typu

- Wywołania metody z więcej niż dwoma argumentami

- Metody pobierające właściwości z więcej niż dwoma argumentami

- Metody ustawiające właściwości z argumentami

- Przypisywanie do indeksatora

- Operatory logiczne `&&` i `||`

### <a name="local-constants"></a>Stałe lokalne
Stałe lokalne nie są obsługiwane.

### <a name="import-aliases"></a>Zaimportuj aliasy
Aliasy importowania nie są obsługiwane.

### <a name="variable-declarations"></a>Deklaracje zmiennych
Nie można zadeklarować jawnych nowych zmiennych w oknach debugera. Można jednak przypisywać nowe zmienne niejawne w oknie **bezpośrednim** . Te niejawne zmienne są objęte zakresem sesji debugowania i nie są dostępne poza debugerem. Na przykład instrukcja `o = 5` niejawnie tworzy nową zmienną `o` i przypisuje jej wartość 5. Takie niejawne zmienne są typu **Object** , chyba że ten typ może zostać wywnioskowany przez debuger.

### <a name="unsupported-keywords"></a>Nieobsługiwane słowa kluczowe

- `AddressOf`

- `End`

- `Error`

- `Exit`

- `Goto`

- `On Error`

- `Resume`

- `Return`

- `Select/Case`

- `Stop`

- `SyncLock`

- `Throw`

- `Try/Catch/Finally`

- `With`

- Słowa kluczowe na poziomie przestrzeni nazw lub modułu, takie jak `End Sub` lub `Module` .

## <a name="see-also"></a>Zobacz też
- [Specyfikatory formatu w języku C++](../debugger/format-specifiers-in-cpp.md)
- [Operator kontekstu (C++)](../debugger/context-operator-cpp.md)
- [Specyfikatory formatu w C#](../debugger/format-specifiers-in-csharp.md)
- [Pseudozmienne](../debugger/pseudovariables.md)
