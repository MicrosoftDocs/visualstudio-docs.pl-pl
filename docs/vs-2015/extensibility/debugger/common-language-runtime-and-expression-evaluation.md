---
title: Środowisko uruchomieniowe języka wspólnego i Ocena wyrażeń | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, and common language runtime
ms.assetid: b36c1eb5-1aaf-48a6-b287-ee7a273d2b1c
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b75cb1b0604f3611c0e51c6f458939433d2a5470
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64825638"
---
# <a name="common-language-runtime-and-expression-evaluation"></a>Środowisko uruchomieniowe języka wspólnego i ocenianie wyrażeń
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> W programie Visual Studio 2015 ten sposób implementowania oceniania wyrażeń jest przestarzały. Aby uzyskać informacje na temat implementowania oceniania wyrażeń CLR, zobacz [oszacowania wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [zarządzane przykłady ewaluatora wyrażeń](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Kompilatory, takie jak Visual Basic i C# (wymawiane C-Sharp), które są przeznaczone dla środowiska uruchomieniowego języka wspólnego (CLR), generują języka pośredniego (MSIL) firmy Microsoft, który jest później kompilowany do kodu natywnego. Środowisko CLR udostępnia aparat debugowania (DE) do debugowania wyniku w kodzie. Jeśli planujesz zintegrować własny język programowania z programem Visual Studio IDE, możesz wybrać kompilację do MSIL i w związku z tym nie będzie trzeba pisać własnych. Należy jednak napisać ewaluatora wyrażeń (EE), która będzie mogła oceniać wyrażenia w kontekście języka programowania.  
  
## <a name="discussion"></a>Dyskusja  
 Wyrażenia języka komputera są zwykle analizowane w celu utworzenia zestawu obiektów danych i zestawu operatorów używanych do manipulowania nimi. Na przykład wyrażenie "A + B" może być analizowane, aby zastosować operator dodawania (+) do obiektów danych "A" i "B", które prawdopodobnie wystąpiły w innym obiekcie danych. Łączny zbiór obiektów danych, operatorów i ich skojarzeń najczęściej jest przedstawiany w programie jako drzewo, z operatorami w węzłach drzewa i obiekty danych w gałęziach. Wyrażenie, które zostało podzielone do postaci drzewa, jest często nazywane przeanalizowanym drzewem.  
  
 Po przeanalizowaniu wyrażenia jest wywoływany dostawca symboli (SP), aby oszacować każdy obiekt danych. Na przykład jeśli element "A" jest zdefiniowany zarówno w więcej niż jednej metodzie, pytanie " musi być udzielona odpowiedź przed ustaleniem wartości parametru. Odpowiedź zwrócona przez program SP to coś takiego jak "trzeci element w piątej ramce stosu" lub "A o 50 bajtów wykraczających poza początek pamięci statycznej przydzielonej tej metodzie".  
  
 Oprócz tworzenia MSIL dla samego programu, kompilatory CLR mogą również generować bardzo opisowe informacje debugowania, które są zapisywane w pliku bazy danych programu (. pdb). Tak długo, jak i kompilator języka własnościowego generuje informacje debugowania w tym samym formacie co kompilatory CLR, SP środowiska CLR jest w stanie identyfikować obiekty danych o nazwie tego języka. Po zidentyfikowaniu nazwanego obiektu danych, EE używa obiektu spinacza, aby skojarzyć (lub powiązać) obiekt danych z obszarem pamięci, który przechowuje wartość tego obiektu. A następnie można pobrać lub ustawić nową wartość dla obiektu danych.  
  
 Kompilator własnościowy może dostarczyć informacji debugowania CLR przez wywołanie `ISymbolWriter` interfejsu (który jest zdefiniowany w .NET Framework w przestrzeni nazw `System.Diagnostics.SymbolStore` ). Kompilując do języka MSIL i pisząc informacje debugowania za pomocą tych interfejsów, zastrzeżony kompilator może używać środowiska CLR DE i SP. Znacznie upraszcza to integrację zastrzeżonego języka z Visual Studio IDE.  
  
 Gdy środowisko CLR odwołuje się do funkcji EE w celu obliczenia wyrażenia, zawiera on interfejsy EE z interfejsami dla obiektu SP i spinacza. W związku z tym pisanie aparatu debugowania opartego na środowisku CLR oznacza, że konieczne jest tylko wdrożenie odpowiednich interfejsów ewaluatora wyrażeń. środowisko CLR bierze pod uwagę powiązanie i obsługę symboli.  
  
## <a name="see-also"></a>Zobacz też  
 [Pisanie ewaluatora wyrażeń środowiska CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
