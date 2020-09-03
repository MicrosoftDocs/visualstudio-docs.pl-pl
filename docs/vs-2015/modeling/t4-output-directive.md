---
title: Dyrektywa wyjściowa T4 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 03a14993-47ad-4f2e-8032-57db28d5842a
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 149370bfee1b142876dff881625d08083afadea4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72652312"
---
# <a name="t4-output-directive"></a>Dyrektywa T4 Output
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] szablonach tekstowych `output` dyrektywa służy do definiowania rozszerzenia nazwy pliku i kodowania przekształconego pliku.

 Na przykład, jeśli [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projekt zawiera plik szablonu o nazwie **MyTemplate.tt** , który zawiera następującą dyrektywę:

 `<#@output extension=".cs"#>`

 następnie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] wygeneruje plik o nazwie **MyTemplate.cs**

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
