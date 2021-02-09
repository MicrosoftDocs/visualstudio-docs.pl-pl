---
title: Dyrektywa T4 Output
description: Dowiedz się, że w szablonach tekstowych programu Visual Studio dyrektywa wyjściowa służy do definiowania rozszerzenia nazwy pliku i kodowania przekształconego pliku.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 58e7c255d767e9b35764e03a76f9cda516dbe606
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99899598"
---
# <a name="t4-output-directive"></a>Dyrektywa T4 Output

W szablonach tekstu programu Visual Studio `output` dyrektywa jest używana do definiowania rozszerzenia nazwy pliku i kodowania przekształconego pliku.

 Na przykład, jeśli projekt programu Visual Studio zawiera plik szablonu o nazwie **MyTemplate.tt** , który zawiera następującą dyrektywę:

 `<#@output extension=".cs"#>`

 Następnie program Visual Studio wygeneruje plik o nazwie **MyTemplate.cs**

 `output`Dyrektywa nie jest wymagana w szablonie tekstowym czasu wykonywania (wstępnie przetworzonym). Zamiast tego aplikacja uzyskuje wygenerowany ciąg przez wywołanie metody `TextTransform()` . Aby uzyskać więcej informacji, zobacz [Generowanie tekstu w czasie wykonywania przy użyciu szablonów tekstowych T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

## <a name="using-the-output-directive"></a>Używanie dyrektywy Output

```
<#@ output extension=".fileNameExtension" [encoding="encoding"] #>
```

 W każdym szablonie tekstowym nie powinna istnieć więcej niż jedna `output` dyrektywa.

## <a name="extension-attribute"></a>Atrybut rozszerzenia
 Określa rozszerzenie nazwy pliku dla wygenerowanego pliku wyjściowego tekstu.

 Wartość domyślna to **. cs**

 Pokazują `<#@ output extension=".txt" #>`

 `<#@ output extension=".htm" #>`

 `<#@ output extension=".cs" #>`

 `<#@ output extension=".vb" #>`

 Akceptowalne wartości: Dowolne prawidłowe rozszerzenie nazwy pliku.

## <a name="encoding-attribute"></a>atrybut kodowania
 Określa kodowanie, które ma być używane podczas generowania pliku wyjściowego. Na przykład:

 `<#@ output encoding="utf-8"#>`

 Wartość domyślna to kodowanie używane przez plik szablonu tekstu.

 Akceptowalne wartości: `us-ascii`

 `utf-16BE`

 `utf-16`

 `utf-8`

 `utf-7`

 `utf-32`

 `0` (System domyślny)

 Ogólnie rzecz biorąc, można użyć ciągu WebName lub numeru strony kodowej dowolnego kodowania zwracanego przez <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=fullName> .
