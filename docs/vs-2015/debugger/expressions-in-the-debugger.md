---
title: Wyrażenia w debugerze | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302526"
---
# <a name="expressions-in-the-debugger"></a>Wyrażenia w debugerze
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Debuger programu Visual Studio zawiera oceniające wyrażenia, które działają po wprowadzeniu wyrażenia w oknie dialogowym **QuickWatch,** **Watch** lub **natychmiastowe** okno. Oceniający wyrażenia są również w pracy w oknie **Punkty przerwania** i wiele innych miejsc w debugerze.  
  
 W poniższych sekcjach podano szczegółowe informacje na temat wyrażeń w różnych językach.  
  
## <a name="f-expressions-are-not-supported"></a>Wyrażenia F# nie są obsługiwane  
 Wyrażenia F# nie są rozpoznawane. Jeśli debugowanie kodu F#, należy przetłumaczyć wyrażenia na składnię języka C# przed wprowadzeniem wyrażeń do okna debugera lub okna dialogowego. Podczas tłumaczenia wyrażeń z F# na C#, należy `==` pamiętać, że C# używa operatora do `=`testowania równości, podczas gdy F# używa pojedynczego .  
  
## <a name="c-expressions"></a>Wyrażenia języka C++  
 Aby uzyskać informacje na temat używania operatorów kontekstu z wyrażeniami w języku C++, zobacz [Operator kontekstu (C++)](../debugger/context-operator-cpp.md).  
  
### <a name="unsupported-expressions-in-c"></a>Nieobsługiwały wyrażenia w języku C++  
  
#### <a name="constructors-destructors-and-conversions"></a>Konstruktory, destruktory i konwersje  
 Nie można wywołać konstruktora lub destruktora dla obiektu, jawnie lub niejawnie. Na przykład następujące wyrażenie jawnie wywołuje konstruktora i powoduje komunikat o błędzie:  
  
```cpp  
my_date( 2, 3, 1985 )  
```  
  
 Nie można wywołać funkcji konwersji, jeśli miejscem docelowym konwersji jest klasa. Taka konwersja wiąże się z budową obiektu. Na przykład, `myFraction` jeśli jest `CFraction`to wystąpienie , `FixedPoint`które definiuje operator funkcji konwersji, następujące wyrażenie powoduje błąd:  
  
```cpp  
(FixedPoint)myFraction  
```  
  
 Nie można wywołać nowych lub usunąć operatorów. Na przykład następujące wyrażenie nie jest obsługiwane:  
  
```cpp  
new Date(2,3,1985)  
```  
  
#### <a name="preprocessor-macros"></a>Makra preprocesora  
 Makra preprocesora nie są obsługiwane w debugerze. Na przykład, jeśli `VALUE` stała jest `#define VALUE 3`zadeklarowana `VALUE` jako: , nie można używać w oknie **Czujka.** Aby uniknąć tego ograniczenia, `#define`należy zastąpić 's wyliczenia i funkcje, gdy jest to możliwe.  
  
### <a name="using-namespace-declarations"></a>używanie deklaracji obszaru nazw  
 Nie można `using namespace` użyć deklaracji.  Aby uzyskać dostęp do nazwy typu lub zmiennej poza bieżącą przestrzenią nazw, należy użyć w pełni kwalifikowanej nazwy.  
  
### <a name="anonymous-namespaces"></a>Anonimowe przestrzenie nazw  
 Anonimowe przestrzenie nazw nie są obsługiwane. Jeśli masz następujący kod, nie `test` można dodać do okna czujki:  
  
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
  
### <a name="using-debugger-intrinsic-functions-to-maintain-state"></a><a name="BKMK_Using_debugger_intrinisic_functions_to_maintain_state"></a>Używanie wewnętrznych funkcji debugera do utrzymania stanu  
 Funkcje wewnętrzne debugera umożliwiają wywołanie niektórych funkcji C/C++ w wyrażeniach bez zmiany stanu aplikacji.  
  
 Funkcje wewnętrzne debugera:  
  
- Są gwarantowane być bezpieczne: wykonywanie funkcji wewnętrznej debugera nie spowoduje uszkodzenia procesu, który jest debugowany.  
  
- Są dozwolone we wszystkich wyrażeniach, nawet w scenariuszach, w których skutki uboczne i ocena funkcji nie są dozwolone.  
  
- Praca w scenariuszach, w których wywołania funkcji regularnych nie są możliwe, takie jak debugowanie minidump.  
  
  Debuger wewnętrzne funkcje mogą również oceniać wyrażenia bardziej wygodne. Na przykład `strncmp(str, “asd”)` jest znacznie łatwiejsze do zapisania `str[0] == ‘a’ && str[1] == ‘s’ && str[2] == ‘d’`w stanie punktu przerwania niż . )  
  
|Obszar|Funkcje wewnętrzne|  
|----------|-------------------------|  
|**Długość ciągu**|strlen, wcslen, strnlen, wcsnlen|  
|**Porównanie ciągów**|strcmp, wcscmp, stricmp, _stricmp, _strcmpi, wcsicmp, _wcscmpi, _wcsnicmp, strncmp, wcsncmp, strnicmp, wcsnicmp|  
|**Wyszukiwanie ciągów**|strchr, wcschr, strstr, wcsstr|  
|**Win32**|GetLastError(), TlsGetValue()|  
|**Windows 8**|WindowsGetStringLen(), WindowsGetStringRawBuffer()<br /><br /> Te funkcje wymagają, aby proces, który jest debugowany, był uruchomiony w systemie Windows 8. Debugowanie plików zrzutu generowane z urządzenia z systemem Windows 8 wymaga również, aby na komputerze programu Visual Studio był uruchomiony system Windows 8. Jeśli jednak debugowanie urządzenia z systemem Windows 8 jest zdalnie debugowane, na komputerze z programu Visual Studio może być uruchomiony system Windows 7.|  
|**Różne**|__log2<br /><br /> Zwraca wartość 2 bazy dziennika określonej liczby całkowitej, zaokrągloną do najbliższej dolnej liczby całkowitej.|  
  
## <a name="ccli---unsupported-expressions"></a>C++/CLI — nieobsługiwały wyrażeń  
  
- Rzuty, które obejmują wskaźniki lub rzutnia zdefiniowane przez użytkownika, nie są obsługiwane.  
  
- Porównywanie i przypisywanie obiektów nie są obsługiwane.  
  
- Przeciążonych operatorów i przeciążonych funkcji nie są obsługiwane.  
  
- Boks i rozpakowywanie nie są obsługiwane.  
  
- `Sizeof`operator nie jest obsługiwany.  
  
## <a name="c---unsupported-expressions"></a>C# — nieobsługiwały wyrażenia  
  
### <a name="dynamic-objects"></a>Obiekty dynamiczne  
 Zmiennych można używać w wyrażeniach debugera, które są statycznie wpisywane jako dynamiczne. Gdy obiekty, <xref:System.Dynamic.IDynamicMetaObjectProvider> które implementują są oceniane w oknie Czujki, dodaje się węzeł widoku dynamicznego. Węzeł Widok dynamiczny pokazuje elementy członkowskie obiektu, ale nie zezwala na edytowanie wartości elementów członkowskich.  
  
 Następujące funkcje obiektów dynamicznych nie są obsługiwane:  
  
- Podmioty zuszne `+=`, `-=`, `%=` `/=`, i`*=`  
  
- Wiele rzutów, w tym rzuty numeryczne i rzuty argumentów typu  
  
- Wywołanie metody z więcej niż dwoma argumentami  
  
- Osoby wywszuszczarki właściwości z więcej niż dwoma argumentami  
  
- Ustawianie właściwości z argumentami  
  
- Przypisywanie do indeksatora  
  
- Operatorzy `&&` logiczni i`||`  
  
### <a name="anonymous-methods"></a>Metody anonimowe  
 Tworzenie nowych metod anonimowych nie jest obsługiwane.  
  
## <a name="visual-basic---unsupported-expressions"></a>Visual Basic — nieobsługiwały wyrażenia  
  
### <a name="dynamic-objects"></a>Obiekty dynamiczne  
 Zmiennych można używać w wyrażeniach debugera, które są statycznie wpisywane jako dynamiczne. Gdy obiekty, <xref:System.Dynamic.IDynamicMetaObjectProvider> które implementują są oceniane w oknie Czujki, dodaje się węzeł widoku dynamicznego. Węzeł Widok dynamiczny pokazuje elementy członkowskie obiektu, ale nie zezwala na edytowanie wartości elementów członkowskich.  
  
 Następujące funkcje obiektów dynamicznych nie są obsługiwane:  
  
- Podmioty zuszne `+=`, `-=`, `%=` `/=`, i`*=`  
  
- Wiele rzutów, w tym rzuty numeryczne i rzuty argumentów typu  
  
- Wywołanie metody z więcej niż dwoma argumentami  
  
- Osoby wywszuszczarki właściwości z więcej niż dwoma argumentami  
  
- Ustawianie właściwości z argumentami  
  
- Przypisywanie do indeksatora  
  
- Operatorzy `&&` logiczni i`||`  
  
### <a name="local-constants"></a>Stałe lokalne  
 Stałe lokalne nie są obsługiwane.  
  
### <a name="import-aliases"></a>Importowanie aliasów  
 Importowanie aliasów nie jest obsługiwane.  
  
### <a name="variable-declarations"></a>Deklaracje zmiennych  
 Nie można zadeklarować jawnych nowych zmiennych w oknach debugera. Można jednak przypisać nowe zmienne niejawne wewnątrz okna **Immediate.** Te niejawne zmienne są ograniczone do sesji debugowania i nie są dostępne poza debugerem. Na przykład instrukcja `o = 5` niejawnie `o` tworzy nową zmienną i przypisz do niej wartość 5. Takie zmienne niejawne są typu **Object,** chyba że typ można wywnioskować przez debugera.  
  
### <a name="unsupported-keywords"></a>Nieobsługiwały słowa kluczowe  
  
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
  
- Słowa kluczowe obszaru nazw lub `End Sub` modułu, takie jak lub `Module`.  
  
## <a name="see-also"></a>Zobacz też  
 [Formatowanie specyfikatorów w języku C++](../debugger/format-specifiers-in-cpp.md)   
 [Operator kontekstu (C++)](../debugger/context-operator-cpp.md)   
 [Formatowanie specyfikatorów w C #](../debugger/format-specifiers-in-csharp.md)   
 [Pseudozmienne](../debugger/pseudovariables.md)
