---
title: Wyrażenia w debugerze | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.expressions
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VBScript
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
caps.latest.revision: 30
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3999737a2fad04c9b513722ae11608574a72c410
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78406334"
---
# <a name="expressions-in-the-debugger"></a>Wyrażenia w debugerze
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Debuger programu Visual Studio zawiera oszacowania wyrażeń, które działają po wprowadzeniu wyrażenia w oknie dialogowym **QuickWatch** , oknie **czujki** lub w oknie **bezpośrednim** . Oceny wyrażeń są również w pracy w oknie **punkty przerwania** i wiele innych miejsc w debugerze.  
  
 Poniższe sekcje zawierają szczegółowe informacje o wyrażeniach w różnych językach.  
  
## <a name="f-expressions-are-not-supported"></a>F#wyrażenia nie są obsługiwane  
 F#wyrażenia nie są rozpoznawane. Jeśli debugujesz F# kod, musisz przetłumaczyć wyrażenia na C# składnię przed wprowadzeniem wyrażeń do okna debugera lub w oknie dialogowym. W przypadku tłumaczenia wyrażeń z F# do C#, należy pamiętać, że C# program używa operatora `==`, aby sprawdzić równość, podczas gdy F# używa jednego `=`.  
  
## <a name="c-expressions"></a>C++Wyrażeń  
 Aby uzyskać informacje o używaniu operatorów kontekstu z C++wyrażeniami w, zobacz [operator kontekstu (C++)](../debugger/context-operator-cpp.md).  
  
### <a name="unsupported-expressions-in-c"></a>Nieobsługiwane wyrażenia wC++  
  
#### <a name="constructors-destructors-and-conversions"></a>Konstruktory, destruktory i konwersje  
 Nie można wywołać konstruktora ani destruktora dla obiektu, jawnie lub niejawnie. Na przykład następujące wyrażenie jawnie wywołuje konstruktora i skutkuje komunikatem o błędzie:  
  
```cpp  
my_date( 2, 3, 1985 )  
```  
  
 Nie można wywołać funkcji konwersji, jeśli miejsce docelowe konwersji jest klasą. Taka konwersja obejmuje Konstruowanie obiektu. Na przykład jeśli `myFraction` jest wystąpieniem `CFraction`, które definiuje `FixedPoint`operatora funkcji konwersji, następujące wyrażenie powoduje błąd:  
  
```cpp  
(FixedPoint)myFraction  
```  
  
 Nie można wywoływać operatora new lub DELETE. Na przykład następujące wyrażenie nie jest obsługiwane:  
  
```cpp  
new Date(2,3,1985)  
```  
  
#### <a name="preprocessor-macros"></a>Makra preprocesora  
 Makra preprocesora nie są obsługiwane w debugerze. Na przykład jeśli stała `VALUE` jest zadeklarowana jako: `#define VALUE 3`, nie można użyć `VALUE` w oknie **czujki** . Aby uniknąć tego ograniczenia, należy zamienić `#define`na wyliczenia i funkcje, jeśli jest to możliwe.  
  
### <a name="using-namespace-declarations"></a>Korzystanie z deklaracji przestrzeni nazw  
 Nie można używać deklaracji `using namespace`.  Aby uzyskać dostęp do nazwy typu lub zmiennej poza bieżącą przestrzenią nazw, należy użyć w pełni kwalifikowanej nazwy.  
  
### <a name="anonymous-namespaces"></a>Anonimowe przestrzenie nazw  
 Anonimowe przestrzenie nazw nie są obsługiwane. Jeśli masz Poniższy kod, nie możesz dodać `test` do okna Czujka:  
  
```cpp  
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
  
### <a name="BKMK_Using_debugger_intrinisic_functions_to_maintain_state"></a>Używanie funkcji wewnętrznych debugera do utrzymania stanu  
 Funkcje wewnętrzne debugera umożliwiają wywoływanie niektórych funkcji języka C/C++ Functions w wyrażeniach bez zmiany stanu aplikacji.  
  
 Funkcje wewnętrzne debugera:  
  
- Gwarantowane jest bezpieczne: wykonanie funkcji wewnętrznej debugera nie spowoduje uszkodzenia debugowanego procesu.  
  
- Są dozwolone we wszystkich wyrażeniach, nawet w scenariuszach, w których efekty uboczne i obliczanie funkcji są niedozwolone.  
  
- Pracuj w scenariuszach, w których regularne wywołania funkcji nie są możliwe, na przykład debugowanie minizrzutu.  
  
  Funkcje wewnętrzne debugera mogą również bardziej wygodnie oceniać wyrażenia. Na przykład `strncmp(str, “asd”)` jest znacznie łatwiejszy do zapisu w warunku punktu przerwania niż `str[0] == ‘a’ && str[1] == ‘s’ && str[2] == ‘d’`. )  
  
|Obszar|Funkcje wewnętrzne|  
|----------|-------------------------|  
|**Długość ciągu**|strlen, wcslen, strnlen, wcsnlen|  
|**Porównanie ciągów**|strcmp, wcscmp, stricmp, _stricmp, _strcmpi, wcsicmp, _wcscmpi, _wcsnicmp, strncmp, wcsncmp, strnicmp, wcsnicmp|  
|**Wyszukiwanie ciągów**|strchr, wcschr, strstr, wcsstr|  
|**System**|GetLastError(), TlsGetValue()|  
|**System Windows 8**|WindowsGetStringLen(), WindowsGetStringRawBuffer()<br /><br /> Funkcje te wymagają, aby proces, który jest debugowany, był uruchomiony w systemie Windows 8. Debugowanie plików zrzutu wygenerowanych z urządzenia z systemem Windows 8 wymaga również, aby na komputerze z programem Visual Studio był uruchomiony system Windows 8. Jednak w przypadku zdalnego debugowania urządzenia z systemem Windows 8 na komputerze z programem Visual Studio może działać system Windows 7.|  
|**Różne**|__log2<br /><br /> Zwraca bazę logarytmiczną 2 z określonej liczby całkowitej zaokrągloną do najbliższej mniejszej liczby całkowitej.|  
  
## <a name="ccli---unsupported-expressions"></a>C++/CLI — nieobsługiwane wyrażenia  
  
- Rzutowania obejmujące wskaźniki lub rzuty zdefiniowane przez użytkownika nie są obsługiwane.  
  
- Porównywanie i przypisywanie obiektów nie są obsługiwane.  
  
- Przeciążone operatory i przeciążone funkcje nie są obsługiwane.  
  
- Pakowanie i rozpakowywanie nie są obsługiwane.  
  
- operator `Sizeof` nie jest obsługiwany.  
  
## <a name="c---unsupported-expressions"></a>C#-Nieobsługiwane wyrażenia  
  
### <a name="dynamic-objects"></a>Obiekty dynamiczne  
 W wyrażeniach debugera, które są statycznie wpisane jako dynamiczne, można używać zmiennych. Gdy obiekty implementujące <xref:System.Dynamic.IDynamicMetaObjectProvider> są oceniane w okno wyrażeń kontrolnych, dodawany jest dynamiczny węzeł widoku. Węzeł Widok dynamiczny zawiera elementy członkowskie obiektów, ale nie zezwala na edytowanie wartości elementów członkowskich.  
  
 Następujące funkcje obiektów dynamicznych nie są obsługiwane:  
  
- Operatory złożone `+=`, `-=`, `%=`, `/=`i `*=`  
  
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
 W wyrażeniach debugera, które są statycznie wpisane jako dynamiczne, można używać zmiennych. Gdy obiekty implementujące <xref:System.Dynamic.IDynamicMetaObjectProvider> są oceniane w okno wyrażeń kontrolnych, dodawany jest dynamiczny węzeł widoku. Węzeł Widok dynamiczny zawiera elementy członkowskie obiektów, ale nie zezwala na edytowanie wartości elementów członkowskich.  
  
 Następujące funkcje obiektów dynamicznych nie są obsługiwane:  
  
- Operatory złożone `+=`, `-=`, `%=`, `/=`i `*=`  
  
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
 Nie można zadeklarować jawnych nowych zmiennych w oknach debugera. Można jednak przypisywać nowe zmienne niejawne w oknie **bezpośrednim** . Te niejawne zmienne są objęte zakresem sesji debugowania i nie są dostępne poza debugerem. Na przykład, instrukcja `o = 5` niejawnie tworzy nową zmienną `o` i przypisuje do niej wartość 5. Takie niejawne zmienne są typu **Object** , chyba że ten typ może zostać wywnioskowany przez debuger.  
  
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
  
- Słowa kluczowe na poziomie przestrzeni nazw lub modułu, takie jak `End Sub` lub `Module`.  
  
## <a name="see-also"></a>Zobacz też  
 [Specyfikatory formatu w C++ ](../debugger/format-specifiers-in-cpp.md)   
 [Operator kontekstu (C++)](../debugger/context-operator-cpp.md)   
 [Specyfikatory formatu w C# ](../debugger/format-specifiers-in-csharp.md)   
 [Pseudozmienne](../debugger/pseudovariables.md)
