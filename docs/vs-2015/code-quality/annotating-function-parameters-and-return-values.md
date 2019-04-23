---
title: Dodawanie adnotacji do parametrów funkcji i zwracanych wartości | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
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
ms.assetid: 82826a3d-0c81-421c-8ffe-4072555dca3a
caps.latest.revision: 17
author: mikeblome
ms.author: mblome
manager: jillfra
ms.openlocfilehash: f16859b3c879e2d3abb64105c50f8ec4934d17e5
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60061518"
---
# <a name="annotating-function-parameters-and-return-values"></a>Dodawanie adnotacji do parametrów funkcji i zwracanych wartości
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym artykule opisano typowe zastosowania adnotacji dla parametrów funkcji proste — wartości skalarnych, a wskaźniki do struktur i klas — i większość typów buforów.  Ten artykuł zawiera również typowe wzorce użycia na potrzeby adnotacji. Dla dodatkowych adnotacji that are related to funkcji, zobacz [zachowanie funkcji dodawania adnotacji](../code-quality/annotating-function-behavior.md)  
  
## <a name="pointer-parameters"></a>Parametry wskaźnika  
 Dla adnotacji w poniższej tabeli gdy jest on adnotację parametru wskaźnika, analizator zgłasza błąd, jeśli wskaźnik jest równa null.  Dotyczy to wskaźniki i dowolnego elementu danych, który jest wskazywany.  
  
 **Adnotacje i opisów**  
  
- `_In_`  
  
     Oznacza stosowanym parametrów wejściowych, które są wartości skalarnych, struktury, wskaźniki do struktur i podobne.  Jawnie może być używana dla prostych wartości skalarnych.  Parametr musi być prawidłowy stan wstępnej i nie zostaną zmodyfikowane.  
  
- `_Out_`  
  
     Oznacza stosowanym parametrów danych wyjściowych, które są wartości skalarnych, struktury, wskaźniki do struktur i podobne.  Dotyczy to obiekt, który nie może zwracać wartość — na przykład, który jest przekazywany przez wartość skalarną.  Parametr musi być prawidłowy stan wstępnego, ale muszą być prawidłowe w stanie po.  
  
- `_Inout_`  
  
     Oznacza stosowanym parametru, która ma zostać zmieniona przez funkcję.  Muszą być prawidłowe w stanu przed i po stanie, ale przyjęto, że mają różne wartości przed i po wywołaniu. Należy zastosować do modyfikowalnych wartości.  
  
- `_In_z_`  
  
     Wskaźnik na ciąg zakończony znakiem null, który jest używany jako dane wejściowe.  Ciąg musi być prawidłowy stan wstępnego.  Warianty `PSTR`, które już mają poprawne adnotacji, są preferowane.  
  
- `_Inout_z_`  
  
     Wskaźnik do tablicy znaków zakończony znakiem null, która będzie modyfikowana.  Musi być prawidłową przed i po wywołaniu metody, ale przyjęto, że wartość uległy zmianie.  Terminator o wartości null, które mogą być przenoszone, ale mogą być używane tylko elementy do oryginalnej terminator o wartości null.  
  
- `_In_reads_(s)`  
  
     `_In_reads_bytes_(s)`  
  
     Wskaźnik do tablicy, który zostanie odczytany przez funkcję.  Tablica ma wielkość `s` elementów, które muszą być prawidłowe.  
  
     `_bytes_` Wariant zapewnia rozmiar w bajtach, zamiast elementów. Użyj tego, tylko wtedy, gdy rozmiar nie może być wyrażona jako elementy.  Na przykład `char` użyć ciągów `_bytes_` korzysta z wariantu tylko wtedy, gdy funkcja podobny `wchar_t` będzie.  
  
- `_In_reads_z_(s)`  
  
     Wskaźnik do tablicy jest zakończony znakiem null, która ma rozmiar znane. Elementy do terminatora null — lub `s` przypadku nie terminatora null — musi być prawidłowy stan wstępnego.  Jeśli rozmiar jest znany w bajtach, skalowanie `s` przez wielkość elementu.  
  
- `_In_reads_or_z_(s)`  
  
     Wskaźnik do tablicy, który jest zakończony znakiem null lub ma znane rozmiaru i / lub. Elementy do terminatora null — lub `s` przypadku nie terminatora null — musi być prawidłowy stan wstępnego.  Jeśli rozmiar jest znany w bajtach, skalowanie `s` przez wielkość elementu.  (Używane dla `strn` rodziny.)  
  
- `_Out_writes_(s)`  
  
     `_Out_writes_bytes_(s)`  
  
     Wskaźnik do tablicy `s` elementów (w bajtach komp), które będą zapisywane przez funkcję.  Elementy tablicy nie trzeba mieć prawidłowy stan wstępnego i liczbę elementów, które są prawidłowe w stanie po jest nieokreślona.  W przypadku adnotacje na typ parametru są stosowane po stanie. Rozważmy na przykład, poniższy kod.  
  
     `typedef _Null_terminated_ wchar_t *PWSTR; void MyStringCopy(_Out_writes_ (size) PWSTR p1,    _In_ size_t size,    _In_ PWSTR p2);`  
  
     W tym przykładzie obiekt wywołujący udostępnia bufor `size` elementy `p1`.  `MyStringCopy` sprawia, że niektóre z tych elementów prawidłowe. Co ważniejsze `_Null_terminated_` adnotacja `PWSTR` oznacza, że `p1` jest zakończony znakiem null w stanie po wydaniu.  W ten sposób liczbę elementów prawidłowe jest nadal dobrze zdefiniowanych, ale liczba określony element nie jest wymagana.  
  
     `_bytes_` Wariant zapewnia rozmiar w bajtach, zamiast elementów. Użyj tego, tylko wtedy, gdy rozmiar nie może być wyrażona jako elementy.  Na przykład `char` użyć ciągów `_bytes_` korzysta z wariantu tylko wtedy, gdy funkcja podobny `wchar_t` będzie.  
  
- `_Out_writes_z_(s)`  
  
     Wskaźnik do tablicy `s` elementów.  Elementy nie muszą znajdować się prawidłowy w stanu wstępnego.  W stanie po elementy się za pośrednictwem terminatora null — musi być obecny — muszą być prawidłowe.  Jeśli rozmiar jest znany w bajtach, skalowanie `s` przez wielkość elementu.  
  
- `_Inout_updates_(s)`  
  
     `_Inout_updates_bytes_(s)`  
  
     Wskaźnik do tablicy, która jest czytać i zapisywane w funkcji.  Jest on rozmiar `s` elementy i prawidłowy w stanie przed i po stanie.  
  
     `_bytes_` Wariant zapewnia rozmiar w bajtach, zamiast elementów. Użyj tego, tylko wtedy, gdy rozmiar nie może być wyrażona jako elementy.  Na przykład `char` użyć ciągów `_bytes_` korzysta z wariantu tylko wtedy, gdy funkcja podobny `wchar_t` będzie.  
  
- `_Inout_updates_z_(s)`  
  
     Wskaźnik do tablicy jest zakończony znakiem null, która ma rozmiar znane. Elementy się za pośrednictwem terminatora null — musi być obecny — muszą być prawidłowe w stanu przed i po stanie.  Wartość w stanie po zakłada, że różni się od wartości w stanie wstępnego; obejmuje to lokalizacja terminator o wartości null. Jeśli rozmiar jest znany w bajtach, skalowanie `s` przez wielkość elementu.  
  
- `_Out_writes_to_(s,c)`  
  
     `_Out_writes_bytes_to_(s,c)`  
  
     `_Out_writes_all_(s)`  
  
     `_Out_writes_bytes_all_(s)`  
  
     Wskaźnik do tablicy `s` elementów.  Elementy nie muszą znajdować się prawidłowy w stanu wstępnego.  W stanie po, elementy do `c`- Ty element musi być prawidłowy.  Jeśli rozmiar jest znany w bajtach, skalowanie `s` i `c` przez wielkość elementu lub użyj `_bytes_` wariant, który jest zdefiniowany jako:  
  
     `_Out_writes_to_(_Old_(s), _Old_(s))    _Out_writes_bytes_to_(_Old_(s), _Old_(s))`  
  
     Innymi słowy, każdy element, który znajduje się w buforze do `s` w stanie wstępnego jest prawidłowy w stanie po wydaniu.  Na przykład:  
  
     `void *memcpy(_Out_writes_bytes_all_(s) char *p1,    _In_reads_bytes_(s) char *p2,    _In_ int s); void * wordcpy(_Out_writes_all_(s) DWORD *p1,     _In_reads_(s) DWORD *p2,    _In_ int s);`  
  
- `_Inout_updates_to_(s,c)`  
  
     `_Inout_updates_bytes_to_(s,c)`  
  
     Wskaźnik do tablicy, która jest zarówno odczytywana i zapisywana przez funkcję.  Jest on rozmiar `s` elementów, które musi być prawidłowy stan wstępnego, i `c` elementy muszą być prawidłowe w stanie po.  
  
     `_bytes_` Wariant zapewnia rozmiar w bajtach, zamiast elementów. Użyj tego, tylko wtedy, gdy rozmiar nie może być wyrażona jako elementy.  Na przykład `char` użyć ciągów `_bytes_` korzysta z wariantu tylko wtedy, gdy funkcja podobny `wchar_t` będzie.  
  
- `_Inout_updates_z_(s)`  
  
     Wskaźnik do tablicy jest zakończony znakiem null, która ma rozmiar znane. Elementy się za pośrednictwem terminatora null — musi być obecny — muszą być prawidłowe w stanu przed i po stanie.  Wartość w stanie po zakłada, że różni się od wartości w stanie wstępnego; obejmuje to lokalizacja terminator o wartości null. Jeśli rozmiar jest znany w bajtach, skalowanie `s` przez wielkość elementu.  
  
- `_Out_writes_to_(s,c)`  
  
     `_Out_writes_bytes_to_(s,c)`  
  
     `_Out_writes_all_(s)`  
  
     `_Out_writes_bytes_all_(s)`  
  
     Wskaźnik do tablicy `s` elementów.  Elementy nie muszą znajdować się prawidłowy w stanu wstępnego.  W stanie po, elementy do `c`- Ty element musi być prawidłowy.  Jeśli rozmiar jest znany w bajtach, skalowanie `s` i `c` przez wielkość elementu lub użyj `_bytes_` wariant, który jest zdefiniowany jako:  
  
     `_Out_writes_to_(_Old_(s), _Old_(s))    _Out_writes_bytes_to_(_Old_(s), _Old_(s))`  
  
     Innymi słowy, każdy element, który znajduje się w buforze do `s` w stanie wstępnego jest prawidłowy w stanie po wydaniu.  Na przykład:  
  
     `void *memcpy(_Out_writes_bytes_all_(s) char *p1,    _In_reads_bytes_(s) char *p2,    _In_ int s); void * wordcpy(_Out_writes_all_(s) DWORD *p1,     _In_reads_(s) DWORD *p2,    _In_ int s);`  
  
- `_Inout_updates_to_(s,c)`  
  
     `_Inout_updates_bytes_to_(s,c)`  
  
     Wskaźnik do tablicy, która jest zarówno odczytywana i zapisywana przez funkcję.  Jest on rozmiar `s` elementów, które musi być prawidłowy stan wstępnego, i `c` elementy muszą być prawidłowe w stanie po.  
  
     `_bytes_` Wariant zapewnia rozmiar w bajtach, zamiast elementów. Użyj tego, tylko wtedy, gdy rozmiar nie może być wyrażona jako elementy.  Na przykład `char` użyć ciągów `_bytes_` korzysta z wariantu tylko wtedy, gdy funkcja podobny `wchar_t` będzie.  
  
- `_Inout_updates_all_(s)`  
  
     `_Inout_updates_bytes_all_(s)`  
  
     Wskaźnik do tablicy, która jest zarówno odczytywana i zapisywana przez funkcję rozmiar `s` elementów. Zdefiniowane jako równoważne:  
  
     `_Inout_updates_to_(_Old_(s), _Old_(s))    _Inout_updates_bytes_to_(_Old_(s), _Old_(s))`  
  
     Innymi słowy, każdy element, który znajduje się w buforze do `s` w stanie wstępnego jest prawidłowy w stanie przed i po stanie.  
  
     `_bytes_` Wariant zapewnia rozmiar w bajtach, zamiast elementów. Użyj tego, tylko wtedy, gdy rozmiar nie może być wyrażona jako elementy.  Na przykład `char` użyć ciągów `_bytes_` korzysta z wariantu tylko wtedy, gdy funkcja podobny `wchar_t` będzie.  
  
- `_In_reads_to_ptr_(p)`  
  
     Wskaźnik do tablicy, dla której wyrażenie `p` — `_Curr_` (oznacza to, że `p` minus `_Curr_`) jest definiowany przez odpowiedni język standardowych.  Elementy w programach starszych niż program `p` muszą być prawidłowe w stanie wstępnego.  
  
- `_In_reads_to_ptr_z_(p)`  
  
     Wskaźnik do tablicy o zakończony znakiem null, dla której wyrażenie `p` — `_Curr_` (oznacza to, że `p` minus `_Curr_`) jest definiowany przez odpowiedni język standardowych.  Elementy w programach starszych niż program `p` muszą być prawidłowe w stanie wstępnego.  
  
- `_Out_writes_to_ptr_(p)`  
  
     Wskaźnik do tablicy, dla której wyrażenie `p` — `_Curr_` (oznacza to, że `p` minus `_Curr_`) jest definiowany przez odpowiedni język standardowych.  Elementy w programach starszych niż program `p` nie trzeba mieć prawidłowy stan wstępnego i musi być w stanie po prawidłowy.  
  
- `_Out_writes_to_ptr_z_(p)`  
  
     Wskaźnik do tablicy o zakończony znakiem null, dla której wyrażenie `p` — `_Curr_` (oznacza to, że `p` minus `_Curr_`) jest definiowany przez odpowiedni język standardowych.  Elementy w programach starszych niż program `p` nie trzeba mieć prawidłowy stan wstępnego i musi być w stanie po prawidłowy.  
  
## <a name="optional-pointer-parameters"></a>Parametry opcjonalne wskaźnika  
 Kiedy zawiera adnotację parametru wskaźnika `_opt_`, oznacza to, że parametr może mieć wartości null. W przeciwnym razie adnotacja wykonuje taka sama jak wersja, która nie obejmuje `_opt_`. W tym miejscu znajduje się lista `_opt_` wariantów adnotacji parametru wskaźnika:  
  
||||  
|-|-|-|  
|`_In_opt_`<br /><br /> `_Out_opt_`<br /><br /> `_Inout_opt_`<br /><br /> `_In_opt_z_`<br /><br /> `_Inout_opt_z_`<br /><br /> `_In_reads_opt_`<br /><br /> `_In_reads_bytes_opt_`<br /><br /> `_In_reads_opt_z_`|`_Out_writes_opt_`<br /><br /> `_Out_writes_opt_z_`<br /><br /> `_Inout_updates_opt_`<br /><br /> `_Inout_updates_bytes_opt_`<br /><br /> `_Inout_updates_opt_z_`<br /><br /> `_Out_writes_to_opt_`<br /><br /> `_Out_writes_bytes_to_opt_`<br /><br /> `_Out_writes_all_opt_`<br /><br /> `_Out_writes_bytes_all_opt_`|`_Inout_updates_to_opt_`<br /><br /> `_Inout_updates_bytes_to_opt_`<br /><br /> `_Inout_updates_all_opt_`<br /><br /> `_Inout_updates_bytes_all_opt_`<br /><br /> `_In_reads_to_ptr_opt_`<br /><br /> `_In_reads_to_ptr_opt_z_`<br /><br /> `_Out_writes_to_ptr_opt_`<br /><br /> `_Out_writes_to_ptr_opt_z_`|  
  
## <a name="output-pointer-parameters"></a>Parametry wskaźnika danych wyjściowych  
 Parametry wskaźnika wyjściowe wymagają specjalnych Notacja do odróżniania null-ness na parametr i lokalizacji wskazanej.  
  
 **Adnotacje i opisów**  
  
- `_Outptr_`  
  
   Parametr nie może mieć wartości null, a w stanie po lokalizacji wskazanej nie może mieć wartości null i muszą być prawidłowe.  
  
- `_Outptr_opt_`  
  
   Parametr może mieć wartości null, ale w stanie po lokalizacji wskazanej nie może mieć wartości null i muszą być prawidłowe.  
  
- `_Outptr_result_maybenull_`  
  
   Parametr nie może mieć wartości null, a następnie w stanie po lokalizacji wskazanej może mieć wartości null.  
  
- `_Outptr_opt_result_maybenull_`  
  
   Parametr może mieć wartości null, a następnie w stanie po lokalizacji wskazanej może mieć wartości null.  
  
  W poniższej tabeli dodatkowe podciągi są wstawiane do nazwę adnotacji, aby bardziej szczegółowo. znaczenie adnotacji.  Różne podciągi są `_z`, `_COM_`, `_buffer_`, `_bytebuffer_`, i `_to_`.  
  
> [!IMPORTANT]
>  Jeśli interfejs, który jest dodawanie adnotacji do modelu COM, należy użyć formy COM tych adnotacji. Nie należy używać adnotacje COM za pomocą dowolnego typu interfejsu.  
  
 **Adnotacje i opisów**  
  
- `_Outptr_result_z_`  
  
   `_Outptr_opt_result_z_`  
  
   `_Outptr_result_maybenull_z_`  
  
   `_Ouptr_opt_result_maybenull_z_`  
  
   Został zwrócony wskaźnik `_Null_terminated_` adnotacji.  
  
- `_COM_Outptr_`  
  
   `_COM_Outptr_opt_`  
  
   `_COM_Outptr_result_maybenull_`  
  
   `_COM_Outptr_opt_result_maybenull_`  
  
   Zwrócony wskaźnik ma semantykę COM i dlatego `_On_failure_` po warunek, że zwrócony wskaźnik ma wartość null.  
  
- `_Outptr_result_buffer_(s)`  
  
   `_Outptr_result_bytebuffer_(s)`  
  
   `_Outptr_opt_result_buffer_(s)`  
  
   `_Outptr_opt_result_bytebuffer_(s)`  
  
   Zwrócony wskaźnik wskazuje na prawidłową bufor o rozmiarze `s` elementów lub liczbę bajtów.  
  
- `_Outptr_result_buffer_to_(s, c)`  
  
   `_Outptr_result_bytebuffer_to_(s, c)`  
  
   `_Outptr_opt_result_buffer_to_(s,c)`  
  
   `_Outptr_opt_result_bytebuffer_to_(s,c)`  
  
   Zwrócony wskaźnik wskazuje bufor o rozmiarze `s` elementów lub liczbę bajtów, z których pierwszy `c` są prawidłowe.  
  
  Niektóre konwencje interfejsu zakładają, że parametry wyjściowe są zniesione w przypadku niepowodzenia.  Z wyjątkiem jawnie kodu COM formularze w poniższej tabeli są preferowane.  Dla kodu COM należy użyć odpowiedniej formularzy COM, które są wymienione w poprzedniej sekcji.  
  
  **Adnotacje i opisów**  
  
- `_Result_nullonfailure_`  
  
   Modyfikuje innych adnotacji. Wynik jest ustawiany na wartość null, jeśli funkcja kończy się niepowodzeniem.  
  
- `_Result_zeroonfailure_`  
  
   Modyfikuje innych adnotacji. Wynik jest ustawiany na zero, jeśli funkcja zawiedzie.  
  
- `_Outptr_result_nullonfailure_`  
  
   Zwrócony wskaźnik wskazuje na prawidłowego buforu, jeśli funkcja się powiedzie, lub wartość null, jeśli funkcja kończy się niepowodzeniem. Ta adnotacja jest parametru — opcjonalne.  
  
- `_Outptr_opt_result_nullonfailure_`  
  
   Zwrócony wskaźnik wskazuje na prawidłowego buforu, jeśli funkcja się powiedzie, lub wartość null, jeśli funkcja kończy się niepowodzeniem. Ta adnotacja jest parametrem opcjonalnym.  
  
- `_Outref_result_nullonfailure_`  
  
   Zwrócony wskaźnik wskazuje na prawidłowego buforu, jeśli funkcja się powiedzie, lub wartość null, jeśli funkcja kończy się niepowodzeniem. Ta adnotacja jest parametr przekazany przez odwołanie.  
  
## <a name="output-reference-parameters"></a>Parametry odwołania danych wyjściowych  
 Zazwyczaj jest używane, parametru odwołania dla parametrów wyjściowych.  Dla parametrów odwołania proste dane wyjściowe — na przykład `int&`—`_Out_` zapewnia semantykę, poprawna.  Jednak, gdy wartość wyjściowa jest wskaźnikiem — na przykład `int *&`— adnotacje równoważne wskaźnika, takich jak `_Outptr_ int **` nie zapewniają poprawne semantyki.  Aby zwięźle wyrazić semantykę parametrów odwołania danych wyjściowych dla typów wskaźnika, należy użyć tych złożonych adnotacji:  
  
 **Adnotacje i opisów**  
  
- `_Outref_`  
  
     Wynik musi być w stanie po prawidłowy i nie może mieć wartości null.  
  
- `_Outref_result_maybenull_`  
  
     Wynik musi być w stanie po prawidłowy, ale może mieć wartości null w stanie po.  
  
- `_Outref_result_buffer_(s)`  
  
     Wynik musi być w stanie po prawidłowy i nie może mieć wartości null. Wskazuje nieprawidłowy bufor o rozmiarze `s` elementów.  
  
- `_Outref_result_bytebuffer_(s)`  
  
     Wynik musi być w stanie po prawidłowy i nie może mieć wartości null. Wskazuje nieprawidłowy bufor o rozmiarze `s` bajtów.  
  
- `_Outref_result_buffer_to_(s, c)`  
  
     Wynik musi być w stanie po prawidłowy i nie może mieć wartości null. Wskazuje bufor `s` elementów, z których pierwszy `c` są prawidłowe.  
  
- `_Outref_result_bytebuffer_to_(s, c)`  
  
     Wynik musi być w stanie po prawidłowy i nie może mieć wartości null. Wskazuje bufor `s` bajtów, z których pierwszy `c` są prawidłowe.  
  
- `_Outref_result_buffer_all_(s)`  
  
     Wynik musi być w stanie po prawidłowy i nie może mieć wartości null. Wskazuje nieprawidłowy bufor o rozmiarze `s` prawidłowe elementy.  
  
- `_Outref_result_bytebuffer_all_(s)`  
  
     Wynik musi być w stanie po prawidłowy i nie może mieć wartości null. Wskazuje nieprawidłowy bufor `s` bajtów prawidłowe elementy.  
  
- `_Outref_result_buffer_maybenull_(s)`  
  
     Wynik musi być w stanie po prawidłowy, ale może mieć wartości null w stanie po. Wskazuje nieprawidłowy bufor o rozmiarze `s` elementów.  
  
- `_Outref_result_bytebuffer_maybenull_(s)`  
  
     Wynik musi być w stanie po prawidłowy, ale może mieć wartości null w stanie po. Wskazuje nieprawidłowy bufor o rozmiarze `s` bajtów.  
  
- `_Outref_result_buffer_to_maybenull_(s, c)`  
  
     Wynik musi być w stanie po prawidłowy, ale może mieć wartości null w stanie po. Wskazuje bufor `s` elementów, z których pierwszy `c` są prawidłowe.  
  
- `_Outref_result_bytebuffer_to_maybenull_(s,c)`  
  
     Wynik musi być w stanie po prawidłowy, ale może mieć wartości null w stanie post. Wskazuje bufor `s` bajtów, z których pierwszy `c` są prawidłowe.  
  
- `_Outref_result_buffer_all_maybenull_(s)`  
  
     Wynik musi być w stanie po prawidłowy, ale może mieć wartości null w stanie post. Wskazuje nieprawidłowy bufor o rozmiarze `s` prawidłowe elementy.  
  
- `_Outref_result_bytebuffer_all_maybenull_(s)`  
  
     Wynik musi być w stanie po prawidłowy, ale może mieć wartości null w stanie post. Wskazuje nieprawidłowy bufor `s` bajtów prawidłowe elementy.  
  
## <a name="return-values"></a>Wartości zwrócone  
 Wartość zwracana przez funkcję przypomina `_Out_` parametru, ale jest na innym poziomie de-reference i nie trzeba wziąć pod uwagę koncepcji wskaźnik do wyniku.  Dla następujących adnotacji, wartość zwracana jest obiektem adnotacjami — skalarną, wskaźnik do struktury lub wskaźnik do buforu. Adnotacje mieć tą samą semantyką jako odpowiednie `_Out_` adnotacji.  
  
|||  
|-|-|  
|`_Ret_z_`<br /><br /> `_Ret_writes_(s)`<br /><br /> `_Ret_writes_bytes_(s)`<br /><br /> `_Ret_writes_z_(s)`<br /><br /> `_Ret_writes_to_(s,c)`<br /><br /> `_Ret_writes_maybenull_(s)`<br /><br /> `_Ret_writes_to_maybenull_(s)`<br /><br /> `_Ret_writes_maybenull_z_(s)`|`_Ret_maybenull_`<br /><br /> `_Ret_maybenull_z_`<br /><br /> `_Ret_null_`<br /><br /> `_Ret_notnull_`<br /><br /> `_Ret_writes_bytes_to_`<br /><br /> `_Ret_writes_bytes_maybenull_`<br /><br /> `_Ret_writes_bytes_to_maybenull_`|  
  
## <a name="other-common-annotations"></a>Inne typowe adnotacji  
 **Adnotacje i opisów**  
  
- `_In_range_(low, hi)`  
  
     `_Out_range_(low, hi)`  
  
     `_Ret_range_(low, hi)`  
  
     `_Deref_in_range_(low, hi)`  
  
     `_Deref_out_range_(low, hi)`  
  
     `_Deref_inout_range_(low, hi)`  
  
     `_Field_range_(low, hi)`  
  
     Parametr, pole lub wynik jest z zakresu (włącznie) z `low` do `hi`.  Odpowiednikiem `_Satisfies_(_Curr_ >= low && _Curr_ <= hi)` mający zastosowanie do adnotacjami obiektu wraz z odpowiednią wstępnie stanu lub stanu końcowego warunków.  
  
    > [!IMPORTANT]
    >  Mimo że nazwy zawierają "in" i "out", semantyka `_In_` i `_Out_` czy **nie** dotyczy tych adnotacji.  
  
- `_Pre_equal_to_(expr)`  
  
     `_Post_equal_to_(expr)`  
  
     Wartość adnotacjami jest dokładnie `expr`.  Odpowiednikiem `_Satisfies_(_Curr_ == expr)` mający zastosowanie do adnotacjami obiektu wraz z odpowiednią wstępnie stanu lub stanu końcowego warunków.  
  
- `_Struct_size_bytes_(size)`  
  
     Ma zastosowanie do deklaracji struktury lub klasy.  Wskazuje, że prawidłowy obiekt tego typu mogą być większe niż zadeklarowanym typem z liczbą bajtów, które są określone przez `size`.  Na przykład:  
  
     `typedef _Struct_size_bytes_(nSize) struct MyStruct {    size_t nSize;    ... };`  
  
     Rozmiar buforu w bajtach parametr `pM` typu `MyStruct *` zostaje następnie przeniesiony za:  
  
     `min(pM->nSize, sizeof(MyStruct))`  
  
## <a name="related-resources"></a>Powiązane zasoby  
 [Blog zespołu ds. analizy kodu](http://go.microsoft.com/fwlink/?LinkId=251197)  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z adnotacji SAL w celu zmniejszenia liczby błędów kodu C/C++](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [Informacje o języku SAL](../code-quality/understanding-sal.md)   
 [Zachowanie funkcji dodawania adnotacji](../code-quality/annotating-function-behavior.md)   
 [Dodawanie adnotacji do struktur i klas](../code-quality/annotating-structs-and-classes.md)   
 [Dodawanie adnotacji do zachowania blokującego](../code-quality/annotating-locking-behavior.md)   
 [Określanie miejsca i warunków stosowania adnotacji](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [Funkcje wewnętrzne](../code-quality/intrinsic-functions.md)   
 [Najlepsze rozwiązania i przykłady](../code-quality/best-practices-and-examples-sal.md)
