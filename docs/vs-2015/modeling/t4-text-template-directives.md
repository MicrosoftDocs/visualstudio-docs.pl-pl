---
title: Dyrektywy z szablonem tekstu T4 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, import directive
- text templates, include directive
- text templates, assembly directive
- text templates, output directive
- text templates, directives
- text templates, template directive
ms.assetid: 6898ee02-ebb2-4635-a4e9-350774c13cf2
caps.latest.revision: 83
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6d77c7a779afcbf7bc7fc3f8fbd863aa368ee7e6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658537"
---
# <a name="t4-text-template-directives"></a>Dyrektywy T4 dotyczące szablonu tekstowego
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dyrektywy zawierają instrukcje dla aparatu przekształceń szablonu tekstu.

 Składnia dyrektyw jest następująca:

```
<#@ DirectiveName [AttributeName = "AttributeValue"] ... #>
```

 Wszystkie wartości atrybutów muszą być ujęte w podwójny cudzysłów. Jeśli sama wartość zawiera znaki cudzysłowu, muszą je poprzedzać znaki ucieczki \.

 Dyrektywy to zazwyczaj pierwsze elementy w pliku szablonu lub pliku dołączanym. Nie należy umieszczać ich wewnątrz bloku kodu `<#...#>`, ani po `<#+...#>` bloku funkcji klasy.

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

 Ponadto można tworzyć własne dyrektywy. Aby uzyskać więcej informacji, zobacz [Tworzenie niestandardowych procesorów dyrektywy T4](../modeling/creating-custom-t4-text-template-directive-processors.md). Jeśli używasz wizualizacji i modelowania SDK do tworzenia języka specyficznego dla domeny (DSL), procesor dyrektywy zostanie wygenerowany jako część DSL.
