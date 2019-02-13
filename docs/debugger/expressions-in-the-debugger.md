---
title: Wyrażenia w debugerze | Dokumentacja firmy Microsoft
ms.date: 02/07/2017
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
ms.openlocfilehash: 596f36457627e8da435c2a8c4223487aa35c60f4
ms.sourcegitcommit: 22b73c601f88c5c236fe81be7ba4f7f562406d75
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/13/2019
ms.locfileid: "56227397"
---
# <a name="expressions-in-the-visual-studio-debugger"></a>Wyrażenia w debugerze programu Visual Studio
Debuger programu Visual Studio zawiera ewaluatory wyrażeń, które działają przy wprowadzaniu wyrażenia w **QuickWatch** okno dialogowe **Obejrzyj** oknie lub **bezpośrednie** okna. Ewaluatory wyrażeń są również w pracy w **punktów przerwania** okna i wielu innych miejscach w debugerze.

Poniższe sekcje w tym artykule opisano ograniczenia obliczenia wyrażenia dla języków obsługiwanych przez program Visual Studio.

## <a name="f-expressions-are-not-supported"></a>F#wyrażenia nie są obsługiwane.
F#wyrażenia nie są rozpoznawane. Jeśli debugujesz F# kodu, potrzebne jest tłumaczenie wyrażenia do C# składni przed rozpoczęciem wprowadzania wyrażeń w debugerze okno lub okno dialogowe. Podczas tłumaczenia wyrażeń z F# do C#, należy koniecznie pamiętać, że C# używa `==` operatora do testowania pod kątem równości, podczas F# używa pojedynczego `=`.

## <a name="c-expressions"></a>Wyrażeń języka C++
Aby dowiedzieć się, jak przy użyciu operatorów kontekstu przy użyciu wyrażenia w języku C++, zobacz [kontekstu — Operator (C++)](../debugger/context-operator-cpp.md).

### <a name="unsupported-expressions-in-c"></a>Nieobsługiwane wyrażenia w języku C++

#### <a name="constructors-destructors-and-conversions"></a>Konstruktory, destruktory i konwersje
Konstruktor lub destruktor nie można wywołać obiektu, jawnie lub niejawnie. Na przykład poniższe wyrażenie jawnie wywołuje konstruktora i wyników w komunikacie o błędzie:

```C++
my_date( 2, 3, 1985 )
```

Nie można wywołać funkcję konwersji, jeśli docelowy w konwersji jest klasą. Taka konwersja obejmuje konstrukcji obiektu. Na przykład jeśli `myFraction` jest wystąpieniem `CFraction`, który definiuje operator funkcji konwersji `FixedPoint`, poniższe wyrażenie powoduje błąd:

```C++
(FixedPoint)myFraction
```

Nie można wywołać nową lub delete — operatory. Na przykład poniższe wyrażenie nie jest obsługiwana:

```C++
new Date(2,3,1985)
```

#### <a name="preprocessor-macros"></a>Makra preprocesora
Makra preprocesora nie są obsługiwane w debugerze. Na przykład jeśli stałą `VALUE` jest zadeklarowany jako: `#define VALUE 3`, nie można użyć `VALUE` w **Obejrzyj** okna. Aby uniknąć tego ograniczenia, należy zastąpić `#define`użytkownika przy użyciu wyliczeń i funkcji, jeśli to możliwe.

### <a name="using-namespace-declarations"></a>za pomocą deklaracje przestrzeni nazw
Nie można użyć `using namespace` deklaracji.  Aby uzyskać dostęp do nazwy typu lub zmiennej poza bieżącej przestrzeni nazw, należy użyć w pełni kwalifikowana nazwa.

### <a name="anonymous-namespaces"></a>Anonimowe przestrzenie nazw
Przestrzenie nazw anonimowe nie są obsługiwane. Jeśli masz następujący kod, nie można dodać `test` w oknie czujki:

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

### <a name="BKMK_Using_debugger_intrinisic_functions_to_maintain_state"></a> Za pomocą funkcje wewnętrzne debugera do zarządzania stanem
Funkcje wewnętrzne debugera zapewniają sposób wywołać pewne funkcje języka C/C++ w wyrażeniach bez zmiany stanu aplikacji.

Funkcje wewnętrzne debugera:

- Zapewniona jest bezpieczne: wykonanie funkcji wewnętrzne debugera nie spowoduje uszkodzenie procesu, który jest debugowany.

- Są dozwolone w wszystkie wyrażenia, nawet w scenariuszach, gdzie efekty uboczne i obliczanie funkcji nie są dozwolone.

- Praca w scenariuszach, w których wywołania funkcji regularnych nie są dostępne, takich jak debugowania minizrzutu.

  Funkcje wewnętrzne debugera można również ustawić oceny wyrażenia bardziej wygodne. Na przykład `strncmp(str, "asd")` jest znacznie łatwiejsze do zapisu w warunku punktu przerwania niż `str[0] == 'a' && str[1] == 's' && str[2] == 'd'`. )

|Obszar|Funkcje wewnętrzne|
|----------|-------------------------|
|**Długość ciągu**|strlen —, wcslen —, strnlen — wcsnlen —|
|**Porównanie ciągów**|strcmp — wcscmp —, stricmp —, _stricmp —, _strcmpi —, wcsicmp —, _wcscmpi, _wcsnicmp —, strncmp —, wcsncmp —, strnicmp —, wcsnicmp —|
|**Ciąg wyszukiwania**|strchr —, wcschr —, strstr — wcsstr —|
|**Win32**|GetLastError(), TlsGetValue()|
|**Windows 8**|WindowsGetStringLen(), WindowsGetStringRawBuffer()<br /><br /> Te funkcje wymagają procesu, który jest debugowany należy uruchomić w systemie Windows 8. Debugowanie plików zrzutu generowane z urządzenia z systemem Windows 8 również wymaga, aby komputer z programem Visual Studio systemem operacyjnym Windows 8. Jednak jeśli przeprowadzasz debugowanie zdalne urządzenie Windows 8, komputer z programem Visual Studio może być uruchomiony Windows 7.|
|**Różne**|__log2<br /><br /> Zwraca dziennik podstawie 2 określona liczba całkowita zaokrąglona do najbliższej liczby całkowitej. niższe.|

## <a name="ccli---unsupported-expressions"></a>C + +/ interfejsu wiersza polecenia — nieobsługiwane wyrażenia

- Wzory, które obejmują wskaźniki lub zdefiniowanych przez użytkownika rzutowania, nie są obsługiwane.

- Porównanie obiektów i przypisania nie są obsługiwane.

- Przeciążone operatory i funkcje przeciążone są nieobsługiwane.

- Pakowanie i rozpakowywanie są nieobsługiwane.

- `Sizeof` operator nie jest obsługiwany.

## <a name="c---unsupported-expressions"></a>C# — nieobsługiwane wyrażenia

### <a name="dynamic-objects"></a>Obiekty dynamiczne
Można używać zmiennych w wyrażeniach debugera, które są statycznie wpisane jako dynamiczne. Gdy obiekty, które implementują <xref:System.Dynamic.IDynamicMetaObjectProvider> są oceniane w oknie czujki widoku dynamicznego, węzeł zostanie dodany. Węzeł dynamiczny widok pokazuje elementach członkowskich obiektu, ale nie zezwala na edytowanie wartości elementów członkowskich.

Następujące funkcje obiektów dynamicznych nie są obsługiwane:

- Złożone operatory `+=`, `-=`, `%=`, `/=`, i `*=`

- Wiele rzutowania, w tym rzutowania liczbowych i argument typu rzutowania

- Wywołań metod z więcej niż dwóch argumentów

- Metody pobierające właściwości z więcej niż dwóch argumentów

- Metod ustawiających właściwości z argumentami

- Przypisywanie do indeksatora

- Operatory logiczne `&&` i `||`

### <a name="anonymous-methods"></a>Metody anonimowe
Tworzenie nowych metod anonimowych nie jest obsługiwane.

## <a name="visual-basic---unsupported-expressions"></a>Visual Basic - nieobsługiwane wyrażenia

### <a name="dynamic-objects"></a>Obiekty dynamiczne
Można używać zmiennych w wyrażeniach debugera, które są statycznie wpisane jako dynamiczne. Gdy obiekty, które implementują <xref:System.Dynamic.IDynamicMetaObjectProvider> są oceniane w oknie czujki widoku dynamicznego, węzeł zostanie dodany. Węzeł dynamiczny widok pokazuje elementach członkowskich obiektu, ale nie zezwala na edytowanie wartości elementów członkowskich.

Następujące funkcje obiektów dynamicznych nie są obsługiwane:

- Złożone operatory `+=`, `-=`, `%=`, `/=`, i `*=`

- Wiele rzutowania, w tym rzutowania liczbowych i argument typu rzutowania

- Wywołań metod z więcej niż dwóch argumentów

- Metody pobierające właściwości z więcej niż dwóch argumentów

- Metod ustawiających właściwości z argumentami

- Przypisywanie do indeksatora

- Operatory logiczne `&&` i `||`

### <a name="local-constants"></a>Stałe lokalne
Lokalne nie są obsługiwane.

### <a name="import-aliases"></a>Importowanie aliasów
Importowanie aliasów nie są obsługiwane.

### <a name="variable-declarations"></a>Deklaracje zmiennych
Nie można zadeklarować jawne nowych zmiennych w debugerze systemu windows. Jednak można przypisać nowe zmienne niejawne wewnątrz **bezpośrednie** okna. Niejawne zmienne są ograniczone do sesji debugowania i nie są dostępne poza debugerem. Na przykład instrukcja `o = 5` niejawnie tworzy nową zmienną `o` i przypisać jej wartość 5. Takie niejawne zmienne są typu **obiektu** o ile nie można wywnioskować typu przez debuger.

### <a name="unsupported-keywords"></a>Nieobsługiwana słów kluczowych

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

- Namespace lub modułu na poziomie słów kluczowych, takich jak `End Sub` lub `Module`.

## <a name="see-also"></a>Zobacz też
[Specyfikatory formatu w języku C++](../debugger/format-specifiers-in-cpp.md)  
[Operator kontekstu (C++)](../debugger/context-operator-cpp.md)  
[Specyfikatory formatu w języku C#](../debugger/format-specifiers-in-csharp.md)  
[Pseudozmienne](../debugger/pseudovariables.md)
