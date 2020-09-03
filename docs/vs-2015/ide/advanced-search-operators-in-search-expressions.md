---
title: Operatory wyszukiwania zaawansowanego w wyrażeniach wyszukiwania | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Help Viewer 2.0, searching for keywords
- Help Viewer 2.0, searching code
- Help Viewer 2.0, searching code by programming language
- Help Viewer 2.0, searching titles
- searching code [Help Viewer 2.0]
- searching titles [Help Viewer 2.0]
ms.assetid: 0cdc1746-8481-45ec-9c53-d0d89cdcbd5e
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c5088fc04f4440260bdb9d3f040d99061c05d243
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72620334"
---
# <a name="advanced-search-operators-in-search-expressions"></a>Operatory wyszukiwania zaawansowanego w wyrażeniach wyszukiwania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Korzystając z zaawansowanych operatorów wyszukiwania, można uściślić Wyszukiwanie zawartości, tworząc bardziej skomplikowane wyrażenia wyszukiwania na podstawie prostszych. Jak przedstawiono w poniższej tabeli, te operatory ograniczają kontekst, w którym jest uruchamiane zapytanie.

> [!WARNING]
> Należy wprowadzić zaawansowane Operatory wyszukiwania z końcowym dwukropkiem i bez odstępu przed dwukropkiem, aby aparat wyszukiwania mógł je rozpoznać.

|Aby wyszukać|Zastosowanie|Przykład|Wynik|
|-------------------|---------|-------------|------------|
|Termin w tytule tematu|title:|Tytuł: BinaryReader|Tematy zawierające "BinaryReader" w ich tytułach.|
|Termin w przykładowym kodzie|— kod:|kod: readDouble|Tematy zawierające "readDouble" w przykładowym kodzie.|
|Termin z przykładu określonego języka programowania|kod: VB:|kod: VB: ciąg|Tematy zawierające ciąg "String" w Visual Basic przykładzie.|
|Temat, który jest skojarzony z określonym indeksem słowa kluczowego|kodu|słowo kluczowe: ReadByte|Tematy, które są skojarzone ze słowem kluczowym "ReadByte".|

 Możesz użyć operatora Code:, aby znaleźć zawartość dla dowolnego z kilku języków programowania, ale zwraca wyniki tylko dla zawartości oznaczonej przy użyciu określonego języka programowania. W poniższej tabeli wymieniono Języki programowania obsługiwane przez ten operator:

|Język programowania|Zastosowanie|
|--------------------------|---------|
|Visual Basic|kod: VB<br /><br /> lub<br /><br /> kod: VisualBasic|
|C#|kod: c #<br /><br /> lub<br /><br /> kod: CSharp|
|C++|kod: CPP<br /><br /> lub<br /><br /> kod: c++<br /><br /> lub<br /><br /> kod: cplusplus|
|F#|kod: f #<br /><br /> lub<br /><br /> kod: FSharp|
|JavaScript|kod: JavaScript<br /><br /> lub<br /><br /> kod: JS|
|XAML|kod: XAML|

## <a name="see-also"></a>Zobacz też
 [Operatory logiczne w wyrażeniach wyszukiwania](../ide/logical-operators-in-search-expressions.md) [pełnotekstowe porady dotyczące wyszukiwania](../ide/full-text-search-tips.md)
