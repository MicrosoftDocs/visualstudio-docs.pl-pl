---
title: Generowanie plików za pomocą narzędzia TextTransform
description: Dowiedz się, jak narzędzie TextTransform to narzędzie wiersza polecenia, za pomocą których można przekształcić szablon tekstowy.
ms.custom: SEO-VS-2020
ms.date: 07/26/2019
ms.topic: conceptual
helpviewer_keywords:
- text templates, TextTransform utility
- TextTransform.exe
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 743b7deb118bb3506773ec1a82d2331633afa7bc
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388831"
---
# <a name="generate-files-with-the-texttransform-utility"></a>Generowanie plików za pomocą narzędzia TextTransform

TextTransform.exe to narzędzie wiersza polecenia, za pomocą których można przekształcić szablon tekstowy. Po wywołaniu TextTransform.exe należy określić nazwę pliku szablonu tekstowego jako argument. TextTransform.exe wywołuje aparat przekształcania tekstu i przetwarza szablon tekstowy. TextTransform.exe jest zwykle wywoływana ze skryptów. Jednak zazwyczaj nie jest to wymagane, ponieważ można wykonać transformację tekstu w Visual Studio lub w procesie kompilacji.

> [!NOTE]
> Jeśli chcesz wykonać transformację tekstu w ramach procesu kompilacji, rozważ użycie zadania przekształcania tekstu w programie MSBuild. Aby uzyskać więcej informacji, zobacz [Generowanie kodu w procesie kompilacji](../modeling/code-generation-in-a-build-process.md). Na komputerze, na którym Visual Studio jest zainstalowany program , można również napisać aplikację lub rozszerzenie Visual Studio, które może przekształcać szablony tekstowe. Aby uzyskać więcej informacji, zobacz Processing Text Templates by using a Custom Host (Przetwarzanie szablonów [tekstowych przy użyciu hosta niestandardowego).](../modeling/processing-text-templates-by-using-a-custom-host.md)

TextTransform.exe znajduje się w następującym katalogu:

::: moniker range=">=vs-2019"

**\Program Files (x86)\Microsoft Visual Studio\2019\Professional\Common7\IDE**

dla wersji Professional lub

**\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE**

w wersji Enterprise.

::: moniker-end

::: moniker range="vs-2017"

**\Program Files (x86)\Microsoft Visual Studio\2017\Professional\Common7\IDE**

dla wersji Professional lub

**\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE**

w wersji Enterprise.

W poprzednich Visual Studio pliku znajduje się w następującej lokalizacji:

**\Program Files (x86)\Common Files\Microsoft Shared\TextTemplating \{ version}**

gdzie {version} zależy od zainstalowanej poprzedniej wersji.

::: moniker-end

## <a name="syntax"></a>Składnia

```
TextTransform [<options>] <templateName>
```

### <a name="parameters"></a>Parametry

|**Argument**|**Opis**|
|-|-|
|`templateName`|Określa nazwę pliku szablonu, który chcesz przekształcić.|

|**Opcja**|**Opis**|
|-|-|
|**— na zewnątrz**\<filename>|Plik, w którym zapisywane są dane wyjściowe przekształcenia.|
|**-r**\<assembly>|Zestaw używany do kompilowania i uruchamiania szablonu tekstu.|
|**-u**\<namespace>|Przestrzeń nazw używana do kompilowania szablonu.|
|**-I**\<includedirectory>|Katalog zawierający szablony tekstowe zawarte w określonym szablonie tekstowym.|
|**-P**\<referencepath>|Katalog do wyszukiwania zestawów określonych w szablonie tekstowym lub do używania **opcji -r.**<br /><br /> Aby na przykład uwzględnić zestawy używane dla Visual Studio API, użyj<br /><br /> `-P "%VSSHELLFOLDER%\Common7\IDE\PublicAssemblies"`|
|**-dp** \<processorName> ! ! \<className> !\<assemblyName&#124;codeBase>|Nazwa, pełna nazwa typu i zestaw procesora dyrektywy, który może służyć do przetwarzania dyrektyw niestandardowych w szablonie tekstowym.|
|**-a** [processorName]! [nazwa_dyrektywy]! \<parameterName> !\<parameterValue>|Określ wartość parametru dla procesora dyrektywy. Jeśli określisz tylko nazwę i wartość parametru, parametr będzie dostępny dla wszystkich procesorów dyrektyw. Jeśli określisz procesor dyrektywy, parametr jest dostępny tylko dla określonego procesora. Jeśli określisz nazwę dyrektywy, parametr jest dostępny tylko wtedy, gdy określona dyrektywa jest przetwarzana.<br /><br /> Aby uzyskać dostęp do wartości parametrów z procesora dyrektywy lub szablonu tekstu, użyj [ITextTemplatingEngineHost.ResolveParameterValue](/previous-versions/visualstudio/visual-studio-2012/bb126369\(v\=vs.110\)). W szablonie tekstowym `hostspecific` uwzględnij w dyrektywie template i wywołaj komunikat w pliku `this.Host` . Na przykład:<br /><br /> `<#@template language="c#" hostspecific="true"#> [<#= this.Host.ResolveParameterValue("", "", "parameterName") #>]`.<br /><br /> Zawsze należy wpisywać znaki "!", nawet jeśli pominięto opcjonalne nazwy procesorów i dyrektyw. Na przykład:<br /><br /> `-a !!param!value`|
|**-h**|Zapewnia pomoc.|

## <a name="related-topics"></a>Powiązane tematy

|Zadanie|Temat|
|-|-|
|Generowanie plików w Visual Studio rozwiązania.|[Generowanie kodu czasu projektowania przy użyciu szablonów tekstowych T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)|
|Pisanie procesorów dyrektyw w celu przekształcania własnych źródeł danych.|[Dopasowanie transformacji tekstu T4](../modeling/customizing-t4-text-transformation.md)|
|Napisz hosta tworzenia szablonów tekstu, który umożliwia wywoływanie szablonów tekstowych z własnej aplikacji.|[Przetwarzanie szablonów tekstowych przy użyciu hosta niestandardowego](../modeling/processing-text-templates-by-using-a-custom-host.md)|
