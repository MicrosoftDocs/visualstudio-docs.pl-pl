---
title: Dyrektywy T4 dotyczące szablonu tekstowego
description: Dowiedz się więcej o dyrektywach szablonu testowego T4 i o tym, jak zapewniają instrukcje dla aparatu przekształcania szablonu tekstu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, import directive
- text templates, include directive
- text templates, assembly directive
- text templates, output directive
- text templates, directives
- text templates, template directive
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0d9b7ca189ced11eea57e175a06b81161090070b
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388740"
---
# <a name="t4-text-template-directives"></a>Dyrektywy T4 dotyczące szablonu tekstowego

Dyrektywy zawierają instrukcje dla aparatu przekształceń szablonu tekstu.

Składnia dyrektyw jest następująca:

```
<#@ DirectiveName [AttributeName = "AttributeValue"] ... #>
```

Wszystkie wartości atrybutów muszą być ujęte w podwójny cudzysłów. Jeśli sama wartość zawiera znaki cudzysłowu, muszą je poprzedzać znaki ucieczki \.

Dyrektywy to zazwyczaj pierwsze elementy w pliku szablonu lub pliku dołączanym. Nie należy umieszczać ich wewnątrz bloku kodu `<#...#>` ani po bloku cech klasy `<#+...#>` .

[Dyrektywa T4 dotycząca szablonu](../modeling/t4-template-directive.md)

```
<#@ template [language="VB"] [hostspecific="true|TrueFromBase"] [debug="true"] [inherits="templateBaseClass"] [culture="code"] [compilerOptions="options"] [visibility="internal"] [linePragmas="false"] #>
```

[Dyrektywa T4 dotycząca parametru](../modeling/t4-parameter-directive.md)

```
<#@ parameter type="Full.TypeName" name="ParameterName" #>
```

[Dyrektywa T4 dotycząca danych wyjściowych](../modeling/t4-output-directive.md)

```
<#@ output extension=".fileNameExtension" [encoding="encoding"] #>
```

[Dyrektywa T4 dotycząca zestawu](../modeling/t4-assembly-directive.md)

```
<#@ assembly name="[assembly strong name|assembly file name]" #>
```

[Dyrektywa T4 dotycząca importowania](../modeling/t4-import-directive.md)

```
<#@ import namespace="namespace" #>
```

[Dyrektywa T4 dotycząca dołączania](../modeling/t4-include-directive.md)

```
<#@ include file="filePath" #>
```

[Dyrektywa T4 CleanUpBehavior](../modeling/t4-cleanupbehavior-directive.md)

```
<#@ CleanupBehavior processor="T4VSHost" CleanupAfterProcessingtemplate="true" #>
```

Ponadto można tworzyć własne dyrektywy. Aby uzyskać więcej informacji, zobacz Creating Custom T4 Text Template Directive Processors (Tworzenie niestandardowych procesorów [dyrektyw szablonów tekstowych T4).](../modeling/creating-custom-t4-text-template-directive-processors.md) Jeśli używasz wizualizacji i modelowania SDK do tworzenia języka specyficznego dla domeny (DSL), procesor dyrektywy zostanie wygenerowany jako część DSL.
