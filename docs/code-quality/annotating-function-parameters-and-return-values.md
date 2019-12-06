---
title: Dodawanie adnotacji do parametrów funkcji i zwracanych wartości
ms.date: 10/15/2019
ms.topic: conceptual
f1_keywords:
- _Outptr_opt_result_bytebuffer_to_
- _Inout_updates_all_opt_
- _Post_equal_to_
- _Outptr_opt_result_maybenull_
- _Out_writes_bytes_all_
- _Out_writes_all_opt_
- _In_opt_
- _Outptr_
- _Outptr_result_maybenull_
- _Outref_result_bytebuffer_all_maybenull_
- _Inout_updates_opt_z_
- _Inout_updates_z_
- _Out_writes_
- _Out_writes_to_ptr_opt_z_
- _In_reads_to_ptr_opt_
- _Ret_writes_to_maybenull_
- _Outref_result_maybenull_
- _Ret_writes_bytes_
- _Outptr_result_bytebuffer_
- _Out_writes_opt_
- _Inout_updates_bytes_opt_
- _In_z_
- _Inout_updates_to_
- _Ret_maybenull_
- _Ret_writes_bytes_to_
- _Ret_z_
- _COM_Outptr_
- _Ret_maybenull_z_
- _Out_opt_
- _In_reads_opt_z_
- _Outptr_result_bytebuffer_to_
- _Ret_notnull_
- _COM_Outptr_opt_result_maybenull_
- _Inout_updates_to_opt_
- _Inout_updates_
- _Outptr_opt_result_buffer_
- _Outptr_result_buffer_to_
- _Out_writes_to_ptr_opt_
- _Out_writes_bytes_all_opt_
- _Inout_updates_all_
- _Deref_inout_range_
- _Ret_writes_
- _Out_writes_z_
- _Ret_writes_to_
- _Out_writes_to_ptr_z_
- _Out_writes_bytes_to_opt_
- _In_reads_or_z_
- _Inout_updates_bytes_to_
- _In_reads_z_
- _In_opt_z_
- _Outref_result_buffer_maybenull_
- _Ret_range_
- _COM_Outptr_opt_
- _Ouptr_opt_result_maybenull_z_
- _In_reads_opt_
- _Inout_
- _Field_range_
- _Ret_writes_z_
- _Out_writes_to_
- _Out_writes_to_ptr_
- _Inout_opt_z_
- _Outref_
- _Deref_out_range_
- _Outref_result_buffer_
- _Outref_result_buffer_to_
- _Outref_result_bytebuffer_to_maybenull_
- _In_reads_bytes_
- _Outptr_opt_result_buffer_to_
- _Outref_result_buffer_all_
- _Out_writes_bytes_to_
- _Result_zeroonfailure_
- _In_reads_bytes_opt_
- _Outref_result_buffer_to_maybenull_
- _Outref_result_bytebuffer_all_
- _Outref_result_buffer_all_maybenull_
- _Ret_writes_maybenull_z_
- _In_range_
- _Inout_updates_bytes_all_opt_
- _Outref_result_bytebuffer_to_
- _Inout_updates_bytes_to_opt_
- _Pre_equal_to_
- _Ret_writes_bytes_maybenull_
- _COM_Outptr_result_maybenull_
- _Ret_writes_maybenull_
- _Out_writes_bytes_
- _Outptr_opt_
- _Out_writes_opt_z_
- _Outref_result_nullonfailure_
- _Outptr_opt_result_z_
- _Inout_opt_
- _Deref_in_range_
- _Outptr_result_z_
- _In_reads_to_ptr_opt_z_
- _Struct_size_bytes_
- _Outptr_result_nullonfailure_
- _In_
- _Inout_updates_bytes_
- _In_reads_to_ptr_z_
- _Ret_writes_bytes_to_maybenull
- _Outptr_opt_result_nullonfailure_
- _In_reads_to_ptr_
- _Outptr_result_buffer_
- _Out_
- _Outref_result_bytebuffer_maybenull_
- _Outptr_result_maybenull_z_
- _In_reads_
- _Inout_updates_opt_
- _Out_writes_to_opt_
- _Outptr_opt_result_bytebuffer_
- _Out_writes_all_
- _Out_range_
- _Inout_updates_bytes_all_
- _Inout_z_
- _Outref_result_bytebuffer_
- _Result_nullonfailure_
- _Ret_null_
- _Scanf_format_string_
- _Scanf_s_format_string_
- _Printf_format_string_
ms.assetid: 82826a3d-0c81-421c-8ffe-4072555dca3a
author: mikeblome
ms.author: mblome
manager: markl
ms.workload:
- multiple
ms.openlocfilehash: 16e7ffb30dc7ec4ae1b78647a0964b81932617ab
ms.sourcegitcommit: 174c992ecdc868ecbf7d3cee654bbc2855aeb67d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/06/2019
ms.locfileid: "74879272"
---
# <a name="annotating-function-parameters-and-return-values"></a>Dodawanie adnotacji do parametrów funkcji i zwracanych wartości
W tym artykule opisano typowe zastosowania adnotacji dla prostych parametrów funkcji — skalarnych i wskaźników do struktur i klas — i większości rodzajów buforów.  W tym artykule przedstawiono również typowe wzorce użycia dla adnotacji. Aby uzyskać dodatkowe adnotacje dotyczące funkcji, zobacz [Dodawanie adnotacji do zachowania funkcji](../code-quality/annotating-function-behavior.md).

## <a name="pointer-parameters"></a>Parametry wskaźnika
W przypadku adnotacji w poniższej tabeli, gdy wskaźnik jest dodawany do parametru wskaźnika, Analizator zgłosi błąd, jeśli wskaYnik ma wartość null.  Dotyczy to wskaźników i do dowolnego elementu danych, który jest wskazywany przez.

**Adnotacje i opisy**

- `_In_`

     Adnotuj parametry wejściowe, które są skalarne, struktury, wskaźniki do struktur i podobne.  Jawnie może być używany w prostych wartościach skalarnych.  Parametr musi być prawidłowy w stanie sprzed i nie zostanie zmodyfikowany.

- `_Out_`

     Umożliwia dodawanie adnotacji do parametrów wyjściowych, które są skalarne, struktury, wskaźniki do struktur i podobne.  Nie stosuj tego do obiektu, który nie może zwrócić wartości — na przykład skalarnej, która jest przenoszona przez wartość.  Parametr nie musi być prawidłowy w stanie wstępnym, ale powinien być prawidłowy w stanie post-State.

- `_Inout_`

     Adnotuj parametr, który zostanie zmieniony przez funkcję.  Musi być prawidłowy zarówno w stanie sprzed, jak i w stanie, ale zakłada się, że mają różne wartości przed i po wywołaniu. Należy zastosować do modyfikowalnej wartości.

- `_In_z_`

     Wskaźnik do ciągu zakończonego wartością null, który jest używany jako dane wejściowe.  Ciąg musi być prawidłowy w stanie sprzed.  Preferowane są różne odmiany `PSTR`, które mają już poprawne adnotacje.

- `_Inout_z_`

     Wskaźnik do tablicy znaków zakończonych znakiem null, który zostanie zmodyfikowany.  Musi być on prawidłowy przed i po wywołaniu, ale przyjęto, że wartość została zmieniona.  Terminator o wartości null można przenieść, ale można uzyskać dostęp tylko do elementów do oryginalnego terminatora o wartości null.

- `_In_reads_(s)`

     `_In_reads_bytes_(s)`

     Wskaźnik do tablicy, który jest odczytywany przez funkcję.  Tablica ma rozmiar `s` elementy, które muszą być prawidłowe.

     Wariant `_bytes_`u daje rozmiar w bajtach, a nie elementy. Użyj tego tylko, jeśli rozmiar nie może być wyrażony jako element.  Na przykład ciągi `char` używają `_bytes_` Variant tylko wtedy, gdy Podobna funkcja, która używa `wchar_t` będzie.

- `_In_reads_z_(s)`

     Wskaźnik do tablicy, która jest zakończona zerem i ma znany rozmiar. Elementy do terminatora o wartości null lub `s`, jeśli nie ma terminatora null — muszą być prawidłowe w stanie sprzed.  Jeśli rozmiar jest znany w bajtach, Skaluj `s` według rozmiaru elementu.

- `_In_reads_or_z_(s)`

     Wskaźnik do tablicy, która jest zakończona wartością null lub ma znany rozmiar lub oba te elementy. Elementy do terminatora o wartości null lub `s`, jeśli nie ma terminatora null — muszą być prawidłowe w stanie sprzed.  Jeśli rozmiar jest znany w bajtach, Skaluj `s` według rozmiaru elementu.  (Używane dla rodziny `strn`).

- `_Out_writes_(s)`

     `_Out_writes_bytes_(s)`

     Wskaźnik do tablicy `s` elementów (centr. Bytes), który zostanie zapisany przez funkcję.  Elementy tablicy nie muszą być prawidłowe w stanie wstępnym, a liczba elementów, które są prawidłowe w stanie post, jest nieokreślona.  Jeśli istnieją adnotacje w typie parametru, są one stosowane w stanie post. Rozważmy na przykład poniższy kod.

     ```cpp
     typedef _Null_terminated_ wchar_t *PWSTR;
     void MyStringCopy(_Out_writes_(size) PWSTR p1, _In_ size_t size, _In_ PWSTR p2);
     ```

     W tym przykładzie obiekt wywołujący udostępnia bufor elementów `size` dla `p1`.  `MyStringCopy` sprawia, że niektóre z tych elementów są prawidłowe. Co ważniejsze, adnotacja `_Null_terminated_` na `PWSTR` oznacza, że `p1` jest zakończonych znakiem null w stanie post.  W ten sposób liczba prawidłowych elementów jest nadal zdefiniowana, ale określona liczba elementów nie jest wymagana.

     Wariant `_bytes_`u daje rozmiar w bajtach, a nie elementy. Użyj tego tylko, jeśli rozmiar nie może być wyrażony jako element.  Na przykład ciągi `char` używają `_bytes_` Variant tylko wtedy, gdy Podobna funkcja, która używa `wchar_t` będzie.

- `_Out_writes_z_(s)`

     Wskaźnik do tablicy elementów `s`.  Elementy nie muszą być prawidłowe w stanie sprzed.  W Stanach końcowych elementy przez terminator wartości null, które muszą być obecne — muszą być prawidłowe.  Jeśli rozmiar jest znany w bajtach, Skaluj `s` według rozmiaru elementu.

- `_Inout_updates_(s)`

     `_Inout_updates_bytes_(s)`

     Wskaźnik do tablicy, który jest odczytywany i zapisywana w funkcji.  Ma rozmiar `s` elementów i jest prawidłowy w stanie sprzed i po nim.

     Wariant `_bytes_`u daje rozmiar w bajtach, a nie elementy. Użyj tego tylko, jeśli rozmiar nie może być wyrażony jako element.  Na przykład ciągi `char` używają `_bytes_` Variant tylko wtedy, gdy Podobna funkcja, która używa `wchar_t` będzie.

- `_Inout_updates_z_(s)`

     Wskaźnik do tablicy, która jest zakończona zerem i ma znany rozmiar. Elementy w górę przez terminator o wartości null — które muszą być obecne — muszą być prawidłowe w stanie sprzed i po nim.  Wartość w stanie post jest zapuszczalna jako inna niż wartość w stanie sprzed; obejmuje to lokalizację terminatora o wartości null. Jeśli rozmiar jest znany w bajtach, Skaluj `s` według rozmiaru elementu.

- `_Out_writes_to_(s,c)`

     `_Out_writes_bytes_to_(s,c)`

     `_Out_writes_all_(s)`

     `_Out_writes_bytes_all_(s)`

     Wskaźnik do tablicy elementów `s`.  Elementy nie muszą być prawidłowe w stanie sprzed.  W stanie post elementy do `c`ego elementu muszą być prawidłowe.  `_bytes_` Variant można użyć, jeśli rozmiar jest znany w bajtach, a nie na liczbie elementów.
     
     Na przykład:

     ```cpp
     void *memcpy(_Out_writes_bytes_all_(s) char *p1, _In_reads_bytes_(s) char *p2, _In_ int s); 
     void *wordcpy(_Out_writes_all_(s) DWORD *p1, _In_reads_(s) DWORD *p2, _In_ int s);
     ```

- `_Inout_updates_to_(s,c)`

     `_Inout_updates_bytes_to_(s,c)`

     Wskaźnik do tablicy, który jest odczytywany i zapisywana przez funkcję.  Jest to rozmiar `s` elementy, które muszą być prawidłowe w stanie sprzed, a elementy `c` muszą być prawidłowe w stanie post-State.

     Wariant `_bytes_`u daje rozmiar w bajtach, a nie elementy. Użyj tego tylko, jeśli rozmiar nie może być wyrażony jako element.  Na przykład ciągi `char` używają `_bytes_` Variant tylko wtedy, gdy Podobna funkcja, która używa `wchar_t` będzie.

- `_Inout_updates_all_(s)`

     `_Inout_updates_bytes_all_(s)`

     Wskaźnik do tablicy, który jest odczytywany i zapisywana przez funkcję rozmiaru `s` elementów. Zdefiniowane jako równoważne:

     `_Inout_updates_to_(_Old_(s), _Old_(s))    _Inout_updates_bytes_to_(_Old_(s), _Old_(s))`

     Innymi słowy, każdy element, który istnieje w buforze do `s` w stanie wstępnym, jest prawidłowy w stanie sprzed i po nim.

     Wariant `_bytes_`u daje rozmiar w bajtach, a nie elementy. Użyj tego tylko, jeśli rozmiar nie może być wyrażony jako element.  Na przykład ciągi `char` używają `_bytes_` Variant tylko wtedy, gdy Podobna funkcja, która używa `wchar_t` będzie.

- `_In_reads_to_ptr_(p)`

     Wskaźnik do tablicy, dla której `p - _Curr_` (czyli `p` minus `_Curr_`) jest prawidłowym wyrażeniem.  Elementy przed `p` muszą być prawidłowe w stanie sprzed.

    Na przykład:
    ```cpp
    int ReadAllElements(_In_reads_to_ptr_(EndOfArray) const int *Array, const int *EndOfArray);
    ```

- `_In_reads_to_ptr_z_(p)`

     Wskaźnik do tablicy zakończonych znakiem null, dla którego wyrażenie `p - _Curr_` (czyli `p` minus `_Curr_`) jest prawidłowym wyrażeniem.  Elementy przed `p` muszą być prawidłowe w stanie sprzed.

- `_Out_writes_to_ptr_(p)`

     Wskaźnik do tablicy, dla której `p - _Curr_` (czyli `p` minus `_Curr_`) jest prawidłowym wyrażeniem.  Elementy przed `p` nie muszą być prawidłowe w stanie sprzed i muszą być prawidłowe w stanie post.

- `_Out_writes_to_ptr_z_(p)`

     Wskaźnik do tablicy zakończonych znakiem null, dla którego `p - _Curr_` (czyli `p` minus `_Curr_`) jest prawidłowym wyrażeniem.  Elementy przed `p` nie muszą być prawidłowe w stanie sprzed i muszą być prawidłowe w stanie post.

## <a name="optional-pointer-parameters"></a>Opcjonalne parametry wskaźnika

Gdy adnotacja parametru wskaźnika zawiera `_opt_`, wskazuje, że parametr może mieć wartość null. W przeciwnym razie adnotacja jest taka sama jak wersja, która nie zawiera `_opt_`. Poniżej znajduje się lista `_opt_` wariantów adnotacji parametrów wskaźnika:

||||
|-|-|-|
|`_In_opt_`<br /><br /> `_Out_opt_`<br /><br /> `_Inout_opt_`<br /><br /> `_In_opt_z_`<br /><br /> `_Inout_opt_z_`<br /><br /> `_In_reads_opt_`<br /><br /> `_In_reads_bytes_opt_`<br /><br /> `_In_reads_opt_z_`|`_Out_writes_opt_`<br /><br /> `_Out_writes_opt_z_`<br /><br /> `_Inout_updates_opt_`<br /><br /> `_Inout_updates_bytes_opt_`<br /><br /> `_Inout_updates_opt_z_`<br /><br /> `_Out_writes_to_opt_`<br /><br /> `_Out_writes_bytes_to_opt_`<br /><br /> `_Out_writes_all_opt_`<br /><br /> `_Out_writes_bytes_all_opt_`|`_Inout_updates_to_opt_`<br /><br /> `_Inout_updates_bytes_to_opt_`<br /><br /> `_Inout_updates_all_opt_`<br /><br /> `_Inout_updates_bytes_all_opt_`<br /><br /> `_In_reads_to_ptr_opt_`<br /><br /> `_In_reads_to_ptr_opt_z_`<br /><br /> `_Out_writes_to_ptr_opt_`<br /><br /> `_Out_writes_to_ptr_opt_z_`|

## <a name="output-pointer-parameters"></a>Parametry wskaźnika wyjściowego
Parametry wskaźnika danych wyjściowych wymagają specjalnej notacji, aby odróżnić wartość null-stałość na parametrze i lokalizacji wskazywanej.

**Adnotacje i opisy**

- `_Outptr_`

   Parametr nie może mieć wartości null, a w stanie wskazywanym nie może mieć wartości null i musi być prawidłowy.

- `_Outptr_opt_`

   Parametr może mieć wartość null, ale w stanie wskazywanym nie może mieć wartości null i musi być prawidłowy.

- `_Outptr_result_maybenull_`

   Parametr nie może mieć wartości null, a w stanie wskazywanym przez wartość null.

- `_Outptr_opt_result_maybenull_`

   Parametr może mieć wartość null, a w stanie wskazywanym przez wpis wartość null.

  W poniższej tabeli dodatkowe podciągi są wstawiane do nazwy adnotacji, aby dodatkowo zakwalifikować znaczenie adnotacji.  Różne podciągi to `_z`, `_COM_`, `_buffer_`, `_bytebuffer_`i `_to_`.

> [!IMPORTANT]
> Jeśli dodajesz Dodawanie adnotacji do interfejsu COM, użyj formularza COM tych adnotacji. Nie używaj adnotacji COM z żadnym innym interfejsem typu.

**Adnotacje i opisy**

- `_Outptr_result_z_`

   `_Outptr_opt_result_z_`

   `_Outptr_result_maybenull_z_`

   `_Ouptr_opt_result_maybenull_z_`

   Zwrócony wskaźnik ma `_Null_terminated_` adnotację.

- `_COM_Outptr_`

   `_COM_Outptr_opt_`

   `_COM_Outptr_result_maybenull_`

   `_COM_Outptr_opt_result_maybenull_`

   Zwrócony wskaźnik ma semantykę modelu COM i w związku z tym przenosi `_On_failure_` warunek końcowy, który zwrócony wskaźnik ma wartość null.

- `_Outptr_result_buffer_(s)`

   `_Outptr_result_bytebuffer_(s)`

   `_Outptr_opt_result_buffer_(s)`

   `_Outptr_opt_result_bytebuffer_(s)`

   Zwrócony wskaźnik wskazuje prawidłowy bufor rozmiaru `s` elementów lub bajtów.

- `_Outptr_result_buffer_to_(s, c)`

   `_Outptr_result_bytebuffer_to_(s, c)`

   `_Outptr_opt_result_buffer_to_(s,c)`

   `_Outptr_opt_result_bytebuffer_to_(s,c)`

   Zwrócony wskaźnik wskazuje bufor rozmiaru `s` elementów lub bajtów, z których pierwszy `c` jest prawidłowy.

  Niektóre konwencje interfejsu zakładają, że parametry wyjściowe są nullified w przypadku niepowodzenia.  W przypadku jawnego kodu COM formularze w poniższej tabeli są preferowane.  W przypadku kodu COM Użyj odpowiednich formularzy COM, które są wymienione w poprzedniej sekcji.

  **Adnotacje i opisy**

- `_Result_nullonfailure_`

   Modyfikuje inne adnotacje. Jeśli funkcja nie powiedzie się, wynik zostanie ustawiony na wartość null.

- `_Result_zeroonfailure_`

   Modyfikuje inne adnotacje. Jeśli funkcja nie powiedzie się, wynik zostanie ustawiony na zero.

- `_Outptr_result_nullonfailure_`

   Zwrócony wskaźnik wskazuje prawidłowy bufor, jeśli funkcja się powiedzie, lub wartość null, jeśli funkcja się nie powiedzie. Adnotacja jest dla nieopcjonalnego parametru.

- `_Outptr_opt_result_nullonfailure_`

   Zwrócony wskaźnik wskazuje prawidłowy bufor, jeśli funkcja się powiedzie, lub wartość null, jeśli funkcja się nie powiedzie. Ta adnotacja jest dla opcjonalnego parametru.

- `_Outref_result_nullonfailure_`

   Zwrócony wskaźnik wskazuje prawidłowy bufor, jeśli funkcja się powiedzie, lub wartość null, jeśli funkcja się nie powiedzie. Ta adnotacja dotyczy parametru Reference.

## <a name="output-reference-parameters"></a>Parametry odwołania wyjściowego

Typowym zastosowaniem parametru reference jest dla parametrów wyjściowych.  W przypadku prostych parametrów referencyjnych wyjściowych, takich jak `int&`, `_Out_` zapewnia poprawną semantykę.  Jeśli jednak wartość wyjściowa jest wskaźnikiem, takim jak `int *&`, równoważne adnotacje wskaźnika, takie jak `_Outptr_ int **`, nie zapewniają właściwej semantyki.  Aby zwięzłie przedstawić semantykę parametrów referencyjnych wyjściowych dla typów wskaźnika, użyj następujących adnotacji złożonych:

**Adnotacje i opisy**

- `_Outref_`

     Wynik musi być prawidłowy w stanie post i nie może mieć wartości null.

- `_Outref_result_maybenull_`

     Wynik musi być prawidłowy w stanie post, ale może mieć wartość null w stanie post.

- `_Outref_result_buffer_(s)`

     Wynik musi być prawidłowy w stanie post i nie może mieć wartości null. Wskazuje prawidłowy bufor rozmiaru `s` elementów.

- `_Outref_result_bytebuffer_(s)`

     Wynik musi być prawidłowy w stanie post i nie może mieć wartości null. Wskazuje prawidłowy bufor rozmiaru `s` bajtów.

- `_Outref_result_buffer_to_(s, c)`

     Wynik musi być prawidłowy w stanie post i nie może mieć wartości null. Wskazuje bufor elementów `s`, z których pierwszy `c` jest prawidłowy.

- `_Outref_result_bytebuffer_to_(s, c)`

     Wynik musi być prawidłowy w stanie post i nie może mieć wartości null. Wskazuje bufor `s` bajtów, z których pierwszy `c` jest prawidłowy.

- `_Outref_result_buffer_all_(s)`

     Wynik musi być prawidłowy w stanie post i nie może mieć wartości null. Wskazuje prawidłowy bufor rozmiaru `s` prawidłowymi elementami.

- `_Outref_result_bytebuffer_all_(s)`

     Wynik musi być prawidłowy w stanie post i nie może mieć wartości null. Wskazuje prawidłowy bufor `s` bajtów prawidłowych elementów.

- `_Outref_result_buffer_maybenull_(s)`

     Wynik musi być prawidłowy w stanie post, ale może mieć wartość null w stanie post. Wskazuje prawidłowy bufor rozmiaru `s` elementów.

- `_Outref_result_bytebuffer_maybenull_(s)`

     Wynik musi być prawidłowy w stanie post, ale może mieć wartość null w stanie post. Wskazuje prawidłowy bufor rozmiaru `s` bajtów.

- `_Outref_result_buffer_to_maybenull_(s, c)`

     Wynik musi być prawidłowy w stanie post, ale może mieć wartość null w stanie post. Wskazuje bufor elementów `s`, z których pierwszy `c` jest prawidłowy.

- `_Outref_result_bytebuffer_to_maybenull_(s,c)`

     Wynik musi być prawidłowy w stanie post, ale może mieć wartość null w stanie post. Wskazuje bufor `s` bajtów, z których pierwszy `c` jest prawidłowy.

- `_Outref_result_buffer_all_maybenull_(s)`

     Wynik musi być prawidłowy w stanie post, ale może mieć wartość null w stanie post. Wskazuje prawidłowy bufor rozmiaru `s` prawidłowymi elementami.

- `_Outref_result_bytebuffer_all_maybenull_(s)`

     Wynik musi być prawidłowy w stanie post, ale może mieć wartość null w stanie post. Wskazuje prawidłowy bufor `s` bajtów prawidłowych elementów.

## <a name="return-values"></a>Wartości zwrócone

Wartość zwracana przez funkcję przypomina parametr `_Out_`, ale znajduje się na innym poziomie nieodniesienia i nie trzeba traktować koncepcji wskaźnika do wyniku.  Dla następujących adnotacji wartość zwracana jest obiektem z adnotacjami — skalarnym, wskaźnikiem do struktury lub wskaźnikiem do buforu. Te adnotacje mają tę samą semantykę co odpowiadająca `_Out_` adnotacja.

|||
|-|-|
|`_Ret_z_`<br /><br /> `_Ret_writes_(s)`<br /><br /> `_Ret_writes_bytes_(s)`<br /><br /> `_Ret_writes_z_(s)`<br /><br /> `_Ret_writes_to_(s,c)`<br /><br /> `_Ret_writes_maybenull_(s)`<br /><br /> `_Ret_writes_to_maybenull_(s)`<br /><br /> `_Ret_writes_maybenull_z_(s)`|`_Ret_maybenull_`<br /><br /> `_Ret_maybenull_z_`<br /><br /> `_Ret_null_`<br /><br /> `_Ret_notnull_`<br /><br /> `_Ret_writes_bytes_to_`<br /><br /> `_Ret_writes_bytes_maybenull_`<br /><br /> `_Ret_writes_bytes_to_maybenull_`|

## <a name="format-string-parameters"></a>Parametry formatu ciągu

- `_Printf_format_string_` wskazuje, że parametr jest ciągiem formatu do użycia w wyrażeniu `printf`.

     **Przykład**

    ```cpp
    int MyPrintF(_Printf_format_string_ const wchar_t* format, ...)
    {
           va_list args;
           va_start(args, format);
           int ret = vwprintf(format, args);
           va_end(args);
           return ret;
    }
    ```

- `_Scanf_format_string_` wskazuje, że parametr jest ciągiem formatu do użycia w wyrażeniu `scanf`.

     **Przykład**

    ```cpp
    int MyScanF(_Scanf_format_string_ const wchar_t* format, ...)
    {
           va_list args;
           va_start(args, format);
           int ret = vwscanf(format, args);
           va_end(args);
           return ret;
    }
    ```

- `_Scanf_s_format_string_` wskazuje, że parametr jest ciągiem formatu do użycia w wyrażeniu `scanf_s`.

     **Przykład**

    ```cpp
    int MyScanF_s(_Scanf_s_format_string_ const wchar_t* format, ...)
    {
           va_list args;
           va_start(args, format);
           int ret = vwscanf_s(format, args);
           va_end(args);
           return ret;
    }
    ```

## <a name="other-common-annotations"></a>Inne typowe adnotacje

**Adnotacje i opisy**

- `_In_range_(low, hi)`

     `_Out_range_(low, hi)`

     `_Ret_range_(low, hi)`

     `_Deref_in_range_(low, hi)`

     `_Deref_out_range_(low, hi)`

     `_Deref_inout_range_(low, hi)`

     `_Field_range_(low, hi)`

     Parametr, pole lub wynik znajduje się w zakresie (włącznie) z `low`, aby `hi`.  Odpowiednik `_Satisfies_(_Curr_ >= low && _Curr_ <= hi)`, który jest stosowany do obiektu z adnotacjami wraz z odpowiednimi warunkami stanu sprzed lub po stanie.

    > [!IMPORTANT]
    > Chociaż nazwy zawierają wartości "in" i "out", semantyka `_In_` i `_Out_` **nie** mają zastosowania do tych adnotacji.

- `_Pre_equal_to_(expr)`

     `_Post_equal_to_(expr)`

     Wartość z adnotacjami jest dokładnie `expr`.  Odpowiednik `_Satisfies_(_Curr_ == expr)`, który jest stosowany do obiektu z adnotacjami wraz z odpowiednimi warunkami stanu sprzed lub po stanie.

- `_Struct_size_bytes_(size)`

     Dotyczy deklaracji klasy lub struktury.  Wskazuje, że prawidłowy obiekt tego typu może być większy niż zadeklarowany typ, z liczbą bajtów podawaną przez `size`.  Na przykład:

     `typedef _Struct_size_bytes_(nSize) struct MyStruct {    size_t nSize;    ... };`

     Rozmiar buforu w bajtach `pM` parametru typu `MyStruct *` jest następnie traktowany jako:

     `min(pM->nSize, sizeof(MyStruct))`

## <a name="related-resources"></a>Powiązane zasoby

[Blog zespołu ds. analizy kodu](https://blogs.msdn.microsoft.com/codeanalysis/)

## <a name="see-also"></a>Zobacz także

- [Korzystanie z adnotacji SAL w celu zmniejszenia liczby defektów kodu C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
- [Informacje o języku SAL](../code-quality/understanding-sal.md)
- [Zachowanie funkcji dodawania adnotacji](../code-quality/annotating-function-behavior.md)
- [Dodawanie adnotacji do struktur i klas](../code-quality/annotating-structs-and-classes.md)
- [Dodawanie adnotacji do zachowania blokującego](../code-quality/annotating-locking-behavior.md)
- [Określanie miejsca i warunków stosowania adnotacji](../code-quality/specifying-when-and-where-an-annotation-applies.md)
- [Funkcje wewnętrzne](../code-quality/intrinsic-functions.md)
- [Najlepsze rozwiązania i przykłady](../code-quality/best-practices-and-examples-sal.md)
