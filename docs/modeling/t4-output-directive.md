---
title: Dyrektywa T4 Output
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dfbe77f5b6e2bbda6a51d392c4dd16b079100e81
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62856248"
---
# <a name="t4-output-directive"></a>Dyrektywa T4 Output

W szablonach tekstowych programu Visual Studio `output` dyrektywa jest używany do definiowania rozszerzenia nazwy pliku i kodowanie pliku przekształcone.

 Na przykład, jeśli projekt programu Visual Studio zawiera plik szablonu o nazwie **MyTemplate.tt** zawierający poniższe dyrektywy:

 `<#@output extension=".cs"#>`

 następnie program Visual Studio wygeneruje plik o nazwie **MyTemplate.cs**

 `output` Dyrektywy nie jest wymagany w szablon tekstowy (wstępnie przetworzony) czasu wykonywania. Zamiast tego aplikacja uzyskuje wygenerowany ciąg przez wywołanie metody `TextTransform()`. Aby uzyskać więcej informacji, zobacz [Generowanie tekstu czasu wykonywania przy użyciu szablonów tekstowych T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

## <a name="using-the-output-directive"></a>Za pomocą dane wyjściowe — dyrektywa

```
<#@ output extension=".fileNameExtension" [encoding="encoding"] #>
```

 Powinna istnieć nie więcej niż jednego `output` dyrektywy w każdym szablonie tekstu.

## <a name="extension-attribute"></a>Atrybut rozszerzenia
 Określa rozszerzenie nazwy pliku wyjściowego pliku wygenerowanego tekstu.

 Wartość domyślna to **.cs**

 Przykłady: `<#@ output extension=".txt" #>`

 `<#@ output extension=".htm" #>`

 `<#@ output extension=".cs" #>`

 `<#@ output extension=".vb" #>`

 Dopuszczalne wartości: Wszelkie nieprawidłowe rozszerzenie nazwy pliku.

## <a name="encoding-attribute"></a>Atrybut kodowania
 Określa kodowanie do użycia podczas generowania pliku wyjściowego. Na przykład:

 `<#@ output encoding="utf-8"#>`

 Wartość domyślna to kodowanie używane przez plik szablonu tekstu.

 Dopuszczalne wartości: `us-ascii`

 `utf-16BE`

 `utf-16`

 `utf-8`

 `utf-7`

 `utf-32`

 `0` (Ustawienie domyślne systemu)

 Ogólnie rzecz biorąc, można użyć ciągu nazwasieciweb lub numer strony kodowej dowolnego kodowania zwrócony przez <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=fullName>.