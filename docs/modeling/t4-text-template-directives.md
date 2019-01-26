---
title: Dyrektywy T4 dotyczące szablonu tekstowego
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, import directive
- text templates, include directive
- text templates, assembly directive
- text templates, output directive
- text templates, directives
- text templates, template directive
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: f0772342f4770a4c9f6e378abe1e9a8c856fc411
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54966098"
---
# <a name="t4-text-template-directives"></a>Dyrektywy T4 dotyczące szablonu tekstowego
Dyrektywy zawierają instrukcje dla aparatu przekształceń szablonu tekstu.

 Składnia dyrektyw jest następująca:

```
<#@ DirectiveName [AttributeName = "AttributeValue"] ... #>
```

 Wszystkie wartości atrybutów muszą być ujęte w podwójny cudzysłów. Jeśli sama wartość zawiera znaki cudzysłowu, muszą je poprzedzać znaki ucieczki \.

 Dyrektywy to zazwyczaj pierwsze elementy w pliku szablonu lub pliku dołączanym. Nie należy ich umieszczać wewnątrz bloku kodu `<#...#>`, ani po bloku funkcji klasy `<#+...#>`.

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

 [Dyrektywa T4 dotycząca działania CleanUpBehavior](../modeling/t4-cleanupbehavior-directive.md)
 ```
<#@ CleanupBehavior processor="T4VSHost" CleanupAfterProcessingtemplate="true" #>
```

 Ponadto można tworzyć własne dyrektywy. Aby uzyskać więcej informacji, zobacz [Tworzenie niestandardowych procesorów T4 dotyczącej tekstu szablonu dyrektywy](../modeling/creating-custom-t4-text-template-directive-processors.md). Jeśli używasz wizualizacji i modelowania SDK do tworzenia języka specyficznego dla domeny (DSL), procesor dyrektywy zostanie wygenerowany jako część DSL.