---
title: Typowy język środowiska uruchomieniowego i oceny wyrażeń | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, and common language runtime
ms.assetid: b36c1eb5-1aaf-48a6-b287-ee7a273d2b1c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 013579473189dd9310501b76d2de0d5cf6fa5822
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739110"
---
# <a name="common-language-runtime-and-expression-evaluation"></a>Wspólne środowisko wykonawcze języka i ocena wyrażeń
> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania oceniających wyrażenia jest przestarzały. Aby uzyskać informacje na temat implementowania oceniających wyrażenia CLR, zobacz [oceniający wyrażenia CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [przykład oceniającego zarządzane wyrażenia](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Kompilatory, takie jak Visual Basic i C# (wymawiane C-sharp), które są przeznaczone dla wspólnego środowiska wykonawczego języka (CLR), produkcji Microsoft Intermediate Language (MSIL), który jest później kompilowany do kodu macierzystego. CLR udostępnia aparat debugowania (DE) do debugowania kodu wynikowego. Jeśli planujesz zintegrować swój własny język programowania do środowiska IDE programu Visual Studio, można wybrać do kompilacji do MSIL i dlatego nie będzie musiał pisać własne DE. Jednak trzeba będzie napisać oceniającego wyrażenie (EE), który jest zdolny do oceny wyrażeń w kontekście języka programowania.

## <a name="discussion"></a>Dyskusji
 Wyrażenia języka komputerowego są zazwyczaj analizowane w celu utworzenia zestawu obiektów danych i zestawu operatorów używanych do manipulowania nimi. Na przykład wyrażenie "A + B" może być analizowane w celu zastosowania operatora dodawania (+) do obiektów danych "A" i "B", co może spowodować powstanie innego obiektu danych. Całkowity zestaw obiektów danych, operatorów i ich skojarzenia są najczęściej reprezentowane w programie jako drzewo, z operatorami w węzłach drzewa i obiektami danych w gałęziach. Wyrażenie, które zostało podzielone na formę drzewa jest często nazywane analizowane drzewa.

 Po przeanalizowaniu wyrażenia dostawca symboli (SP) jest wywoływany do oceny każdego obiektu danych. Na przykład, jeśli "A" jest zdefiniowany zarówno w więcej niż jednej metodzie, pytanie "Które A?" przed ustaleniem wartości A. Odpowiedź zwrócona przez SP jest coś takiego jak "Trzeci element na piątej ramce stosu" lub "A, który jest 50 bajtów poza rozpoczęciem pamięci statycznej przydzielone do tej metody."

 Oprócz produkcji MSIL dla samego programu, kompilatory CLR mogą również tworzyć bardzo opisowe informacje debugowania, które są zapisywane w pliku DataBase programu *(pdb).* Tak długo, jak kompilator języka zastrzeżonego produkuje informacje debugowania w tym samym formacie co kompilatory CLR, SP CLR jest w stanie zidentyfikować nazwane obiekty danych tego języka. Po zidentyfikowaniu nazwanego obiektu danych EE używa obiektu spinacza do skojarzenia (lub powiązania) obiektu danych z obszarem pamięci, który przechowuje wartość tego obiektu. DE można następnie uzyskać lub ustawić nową wartość dla obiektu danych.

 Kompilator własności może dostarczyć informacji debugowania `ISymbolWriter` CLR, wywołując interfejs (który jest zdefiniowany w .NET Framework w obszarze nazw). `System.Diagnostics.SymbolStore` Kompilując do MSIL i zapisując informacje debugowania za pośrednictwem tych interfejsów, kompilator własności można użyć CLR DE i SP. Znacznie upraszcza to integrowanie zastrzeżonego języka z ideą programu Visual Studio.

 Gdy CLR DE wywołuje własności EE do oceny wyrażenia, DE dostarcza EE z interfejsów do SP i obiektu spinacza. W związku z tym pisanie aparatu debugowania opartego na programie CLR oznacza, że jest konieczne tylko do zaimplementowania interfejsów ewaluatora odpowiedniewyrażeń; clr zajmuje się oprawą i obsługą symboli.

## <a name="see-also"></a>Zobacz też
- [Napisz ewaluatora wyrażenia CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
