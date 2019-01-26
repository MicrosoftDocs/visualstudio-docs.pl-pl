---
title: Środowisko uruchomieniowe języka wspólnego i ocenianie wyrażeń | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, and common language runtime
ms.assetid: b36c1eb5-1aaf-48a6-b287-ee7a273d2b1c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4151f00a9c482036d4aaea8d4ba557ff282287c5
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54976852"
---
# <a name="common-language-runtime-and-expression-evaluation"></a>Typowe obliczenia środowiska uruchomieniowego i wyrażenia języka
> [!IMPORTANT]
>  W programie Visual Studio 2015 ten sposób implementowania ewaluatory wyrażeń jest przestarzały. Informacje o implementowaniu ewaluatory wyrażeń CLR, zobacz [ewaluatory wyrażeń CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) i [przykładowe ewaluatora wyrażeń zarządzane](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Kompilatory, takie jak Visual Basic i C# (Wymowa C sharp), przeznaczonych dla środowiska uruchomieniowego języka wspólnego (CLR), należy utworzyć Microsoft Intermediate Language (MSIL), która jest nowsza kompilowane do kodu natywnego. Środowisko CLR oferuje aparat debugowania (DE), aby debugować kod wynikowy. Jeśli planujesz integracji własności język programowania w środowisku IDE programu Visual Studio można skompilować do MSIL i dlatego nie trzeba napisać własne DE. Należy zapisać ewaluatora wyrażeń (EE), który jest w stanie oceny wyrażenia w kontekście języka programowania.  
  
## <a name="discussion"></a>Dyskusja  
 Wyrażenia języka komputera zazwyczaj są parsowane do tworzenia zestawu danych obiektów i ich zestaw operatorów, używane do manipulowania nimi. Na przykład wyrażenie, które "A + B" może być można przeanalizować, aby zastosować operator dodawania (+) danych obiektów "A" i "B", przez co inny obiekt danych. Łączna liczba zbiór obiektów danych, operatorów i ich skojarzenia w większości przypadków są reprezentowane w programie jako drzewo, za pomocą operatorów w węzłach drzewa i obiekty danych, w gałęzi. Wyrażenie, które zostały podzielone w formie drzewa jest często określany mianem przeanalizowany drzewa.  
  
 Po przeanalizowaniu wyrażenie do oceny, każdy obiekt danych nosi nazwę dostawca symboli (SP). Na przykład, jeśli "" jest zdefiniowany w więcej niż jednej metody, pytanie "Która A?" Musisz udzielić odpowiedzi, zanim można ustalić wartości A. Odpowiedź zwrócona przez PS jest podobny do "Trzeci element na piątym ramce stosu" lub "A, o 50 bajtów poza początek pamięci statycznej przydzielony do tej metody."  
  
 Oprócz tworzenia MSIL dla samego programu, kompilatory CLR może utworzyć również bardzo opisowe informacje debugowania, który jest zapisywany w bazie danych programu (*.pdb*) pliku. Tak długo, jak kompilator języka zastrzeżonej generuje informacje o debugowaniu w tym samym formacie jak kompilatory CLR, SP CLR jest możliwość określenia, czy języka o nazwie obiektów danych. Po zidentyfikowaniu obiektu danych o nazwie EE używa obiekt integratora skojarzyć (lub powiązać) obiekt danych do obszaru pamięci, która zawiera wartość tego obiektu. DE można pobrać lub ustawić nową wartość dla obiektu danych.  
  
 Zastrzeżone kompilator może zapewnić CLR, informacje o debugowaniu, wywołując `ISymbolWriter` interfejsu (który jest zdefiniowany w .NET Framework w przestrzeni nazw `System.Diagnostics.SymbolStore`). Kompilowanie na język MSIL i zapisywania informacji debugowania za pomocą tych interfejsów, kompilator własności CLR DE i użyć SP. Znacznie upraszcza to integrowanie własności języka środowiska IDE programu Visual Studio.  
  
 Gdy CLR DE wywołuje własności EE można obliczyć wyrażenia, DE dostarcza EE z interfejsami SP i obiekt integratora. W związku z tym zapisywanie oznacza aparat debugowania na podstawie środowiska CLR jest konieczne tylko implementować interfejsy ewaluatora wyrażeń odpowiednie; Środowisko CLR dba o powiązania i symbol obsługi dla Ciebie.  
  
## <a name="see-also"></a>Zobacz także  
 [Pisanie ewaluatora wyrażeń środowiska CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)