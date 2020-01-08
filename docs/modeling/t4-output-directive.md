---
title: Dyrektywa T4 Output
ms.date: 11/04/2016
ms.topic: reference
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eb1634da6374ad49f1386be4403e72e8edeff2ca
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591817"
---
# <a name="t4-output-directive"></a>Dyrektywa T4 Output

W szablonach tekstu programu Visual Studio dyrektywa `output` jest używana do definiowania rozszerzenia nazwy pliku i kodowania przekształconego pliku.

 Na przykład, jeśli projekt programu Visual Studio zawiera plik szablonu o nazwie **MyTemplate.tt** , który zawiera następującą dyrektywę:

 `<#@output extension=".cs"#>`

 Następnie program Visual Studio wygeneruje plik o nazwie **MyTemplate.cs**

 Dyrektywa `output` nie jest wymagana w szablonie tekstowym czasu wykonywania (wstępnie przetworzonym). Zamiast tego aplikacja uzyskuje wygenerowany ciąg, wywołując `TextTransform()`. Aby uzyskać więcej informacji, zobacz [Generowanie tekstu w czasie wykonywania przy użyciu szablonów tekstowych T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

## <a name="using-the-output-directive"></a>Używanie dyrektywy Output

```
<#@ output extension=".fileNameExtension" [encoding="encoding"] #>
```

 Każdy szablon tekstowy nie powinien zawierać więcej niż jednej dyrektywy `output`.

## <a name="extension-attribute"></a>Atrybut rozszerzenia
 Określa rozszerzenie nazwy pliku dla wygenerowanego pliku wyjściowego tekstu.

 Wartość domyślna to **. cs**

 Przykłady: `<#@ output extension=".txt" #>`

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

 `0` (system domyślny)

 Ogólnie rzecz biorąc, można użyć ciągu WebName lub numeru strony kodowej dowolnego kodowania zwracanego przez <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=fullName>.
