---
title: Środowisko uruchomieniowe języka wspólnego i Ocena wyrażeń | Microsoft Docs
description: Dowiedz się, jak środowisko uruchomieniowe języka wspólnego współdziała z aparatem debugowania oraz jak zintegrować własny język programowania z programem Visual Studio IDE.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, and common language runtime
ms.assetid: b36c1eb5-1aaf-48a6-b287-ee7a273d2b1c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cddf09eac5f887e0c5615af76e6956b590576786
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99930671"
---
# <a name="common-language-runtime-and-expression-evaluation"></a>Środowisko uruchomieniowe języka wspólnego i Ocena wyrażeń
> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania oceniania wyrażeń jest przestarzały. Aby uzyskać informacje na temat implementowania oceniania wyrażeń CLR, zobacz [oszacowania wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane przykłady ewaluatora wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Kompilatory, takie jak Visual Basic i C# (wymawiane C-Sharp), które są przeznaczone dla środowiska uruchomieniowego języka wspólnego (CLR), generują języka pośredniego (MSIL) firmy Microsoft, który jest później kompilowany do kodu natywnego. Środowisko CLR udostępnia aparat debugowania (DE) do debugowania wyniku w kodzie. Jeśli planujesz zintegrować własny język programowania z programem Visual Studio IDE, możesz wybrać kompilację do MSIL i w związku z tym nie będzie trzeba pisać własnych. Należy jednak napisać ewaluatora wyrażeń (EE), która będzie mogła oceniać wyrażenia w kontekście języka programowania.

## <a name="discussion"></a>Dyskusja
 Wyrażenia języka komputera są zwykle analizowane w celu utworzenia zestawu obiektów danych i zestawu operatorów używanych do manipulowania nimi. Na przykład wyrażenie "A + B" może być analizowane, aby zastosować operator dodawania (+) do obiektów danych "A" i "B", które prawdopodobnie wystąpiły w innym obiekcie danych. Łączny zbiór obiektów danych, operatorów i ich skojarzeń najczęściej jest przedstawiany w programie jako drzewo, z operatorami w węzłach drzewa i obiekty danych w gałęziach. Wyrażenie, które zostało podzielone do postaci drzewa, jest często nazywane przeanalizowanym drzewem.

 Po przeanalizowaniu wyrażenia jest wywoływany dostawca symboli (SP), aby oszacować każdy obiekt danych. Na przykład jeśli element "A" jest zdefiniowany zarówno w więcej niż jednej metodzie, pytanie " musi być udzielona odpowiedź przed ustaleniem wartości parametru. Odpowiedź zwrócona przez program SP to coś takiego jak "trzeci element w piątej ramce stosu" lub "A o 50 bajtów wykraczających poza początek pamięci statycznej przydzielonej tej metodzie".

 Oprócz tworzenia MSIL dla samego programu, kompilatory CLR mogą również generować bardzo opisowe informacje debugowania, które są zapisywane w pliku bazy danych programu (*. pdb*). Tak długo, jak i kompilator języka własnościowego generuje informacje debugowania w tym samym formacie co kompilatory CLR, SP środowiska CLR jest w stanie identyfikować obiekty danych o nazwie tego języka. Po zidentyfikowaniu nazwanego obiektu danych, EE używa obiektu spinacza, aby skojarzyć (lub powiązać) obiekt danych z obszarem pamięci, który przechowuje wartość tego obiektu. A następnie można pobrać lub ustawić nową wartość dla obiektu danych.

 Kompilator własnościowy może dostarczyć informacji debugowania CLR przez wywołanie `ISymbolWriter` interfejsu (który jest zdefiniowany w .NET Framework w przestrzeni nazw `System.Diagnostics.SymbolStore` ). Kompilując do języka MSIL i pisząc informacje debugowania za pomocą tych interfejsów, zastrzeżony kompilator może używać środowiska CLR DE i SP. Znacznie upraszcza to integrację zastrzeżonego języka z Visual Studio IDE.

 Gdy środowisko CLR odwołuje się do funkcji EE w celu obliczenia wyrażenia, zawiera on interfejsy EE z interfejsami dla obiektu SP i spinacza. W związku z tym pisanie aparatu debugowania opartego na środowisku CLR oznacza, że jest to konieczne tylko w celu wdrożenia odpowiednich interfejsów ewaluatora wyrażeń. środowisko CLR bierze pod uwagę powiązanie i obsługę symboli.

## <a name="see-also"></a>Zobacz też
- [Napisz ewaluatora wyrażeń CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
