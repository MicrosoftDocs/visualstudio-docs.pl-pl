---
title: Dyrektywa T4 Output
description: Dowiedz się, Visual Studio szablonów tekstowych dyrektywa output służy do definiowania rozszerzenia nazwy pliku i kodowania przekształconego pliku.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8105edc57e68aa7cedcb612ec4f6bcd0ef367d2f
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386114"
---
# <a name="t4-output-directive"></a>Dyrektywa T4 Output

W Visual Studio tekstowych dyrektywa służy do definiowania rozszerzenia nazwy pliku i kodowania `output` przekształconego pliku.

 Jeśli na przykład projekt Visual Studio zawiera plik szablonu o **nazwie MyTemplate.tt** który zawiera następującą dyrektywę:

 `<#@output extension=".cs"#>`

 następnie Visual Studio wygeneruje plik o **nazwie MyTemplate.cs**

 Dyrektywa nie jest wymagana w szablonie tekstowym czasu działania `output` (wstępnie przetworzonym). Zamiast tego aplikacja uzyskuje wygenerowany ciąg, `TextTransform()` wywołując . Aby uzyskać więcej informacji, zobacz Run-Time Text Generation with T4 Text Templates (Generowanie tekstu [w czasie uruchamiania za pomocą szablonów tekstowych T4).](../modeling/run-time-text-generation-with-t4-text-templates.md)

## <a name="using-the-output-directive"></a>Korzystanie z dyrektywy Output

```
<#@ output extension=".fileNameExtension" [encoding="encoding"] #>
```

 W każdym szablonie tekstowym nie powinna być więcej `output` niż jedna dyrektywa.

## <a name="extension-attribute"></a>atrybut rozszerzenia
 Określa rozszerzenie nazwy pliku wygenerowanego tekstowego pliku wyjściowego.

 Wartość domyślna to **cs**

 Przykłady: `<#@ output extension=".txt" #>`

 `<#@ output extension=".htm" #>`

 `<#@ output extension=".cs" #>`

 `<#@ output extension=".vb" #>`

 Dopuszczalne wartości: dowolne prawidłowe rozszerzenie nazwy pliku.

## <a name="encoding-attribute"></a>atrybut kodowania
 Określa kodowanie do użycia podczas generowania pliku wyjściowego. Na przykład:

 `<#@ output encoding="utf-8"#>`

 Wartość domyślna to kodowanie używane przez plik szablonu tekstowego.

 Dopuszczalne wartości: `us-ascii`

 `utf-16BE`

 `utf-16`

 `utf-8`

 `utf-7`

 `utf-32`

 `0` (Wartość domyślna systemu)

 Ogólnie rzecz biorąc, można użyć ciągu WebName lub numeru CodePage dowolnego kodowania zwróconego przez parametr <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=fullName> .
