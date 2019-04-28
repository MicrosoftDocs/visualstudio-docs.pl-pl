---
title: Generowanie plików za pomocą narzędzia TextTransform
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- text templates, TextTransform utility
- TextTransform.exe
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7c7a33f7510eb862ed6af1f1d5337d8d3e2743ba
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62993763"
---
# <a name="generate-files-with-the-texttransform-utility"></a>Generowanie plików za pomocą narzędzia TextTransform

TextTransform.exe jest narzędziem wiersza polecenia, można użyć do przekształcania szablonu tekstu. Jeśli chcesz wywołać TextTransform.exe, należy określić nazwę pliku szablonu tekstu jako argument. TextTransform.exe wywołuje aparat przekształcenia tekstu i przetwarza szablonu tekstu. TextTransform.exe zwykle jest wywoływana przez skrypty. Jednak nie jest zazwyczaj wymagane, ponieważ można dokonać przekształcenia tekstu, w programie Visual Studio lub w procesie kompilacji.

> [!NOTE]
> Jeśli chcesz wykonywać przekształcenia tekstu jako część procesu kompilacji, rozważ użycie zadanie przekształcenia tekstu w MSBuild. Aby uzyskać więcej informacji, zobacz [generowanie kodu w procesie kompilacji](../modeling/code-generation-in-a-build-process.md). Na maszynie, na którym jest zainstalowany program Visual Studio możesz również zapisywać dane aplikacji lub rozszerzenia Visual Studio, które umożliwiają przekształcanie szablonów tekstowych. Aby uzyskać więcej informacji, zobacz [przetwarzanie szablonów tekstowych przy użyciu hosta niestandardowego](../modeling/processing-text-templates-by-using-a-custom-host.md).

 TextTransform.exe znajduje się w następującym katalogu:

 **\Program Files (x86)\Microsoft Visual Studio\2017\Professional\Common7\IDE**

Professional Edition lub

 **\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE**

 Enterprise Edition.

W poprzednich wersjach programu Visual Studio plik znajduje się w następującej lokalizacji:

**\Program Files (x86)\Common Files\Microsoft Shared\TextTemplating\{version}**

gdy {version} zależy od poprzedniej wersji zainstalowanego.

## <a name="syntax"></a>Składnia

```
TextTransform [<options>] <templateName>
```

### <a name="parameters"></a>Parametry

|**Argument**|**Opis**|
|-|-|
|`templateName`|Określa nazwę pliku szablonu, który chcesz przekształcić.|

|**Option**|**Opis**|
|-|-|
|**-out** \<nazwa pliku >|Plik, do której są zapisywane dane wyjściowe transformacji.|
|**-r** \<zestawu >|Zestaw używany do kompilowania i uruchamiania szablonu tekstu.|
|**-u** \<przestrzeni nazw >|Obszar nazw, który jest używany do tworzenia szablonu.|
|**-I** \<includedirectory >|Katalog, który zawiera szablony tekstowe zawarte w szablonie określony tekst.|
|**-P** \<referencepath >|Katalog do przeszukania zestawy określone w szablonie tekstu lub przy użyciu **- r** opcji.<br /><br /> Na przykład aby uwzględnić zestawy używany do Visual Studio API, należy użyć<br /><br /> `-P "%VSSHELLFOLDER%\Common7\IDE\PublicAssemblies"`|
|**-dp** \<processorName>!\<className>!\<assemblyName&#124;codeBase>|Nazwa, pełna nazwa typu i zestawu procesor dyrektywy, który może służyć do przetwarzania niestandardowych dyrektyw szablonu tekstu.|
|**-** [processorName]! [directiveName]! \<parameterName >! \<parameterValue >|Określ wartość parametru dla procesora dyrektywy. Jeśli określisz tylko nazwy parametru i wartości parametru będą dostępne dla wszystkich procesorów dyrektyw. Jeśli określisz procesor dyrektywy, parametr jest dostępna tylko w określonym procesorem. Jeśli określisz nazwę dyrektywy, parametr jest dostępna tylko wtedy, gdy określony dyrektywa jest przetwarzany.<br /><br /> Dostęp do wartości parametrów z procesora dyrektywy lub szablonu tekstu, należy użyć [ITextTemplatingEngineHost.ResolveParameterValue](/previous-versions/visualstudio/visual-studio-2012/bb126369\(v\=vs.110\)). W szablonie tekstu, obejmują `hostspecific` w dyrektywie szablonu i wywołania wiadomości na `this.Host`. Na przykład:<br /><br /> `<#@template language="c#" hostspecific="true"#> [<#= this.Host.ResolveParameterValue("", "", "parameterName") #>]`.<br /><br /> Zawsze wpisać "!" oznacza, nawet jeśli parametr zostanie pominięty, opcjonalny procesora i nazwy dyrektyw. Na przykład:<br /><br /> `-a !!param!value`|
|**-h**|Zawiera Pomoc.|

## <a name="related-topics"></a>Tematy pokrewne

|Zadanie|Temat|
|-|-|
|Generowanie plików w rozwiązaniu Visual Studio.|[Generowanie kodu czasu projektowania przy użyciu szablonów tekstowych T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)|
|Napisz dyrektywy procesorów, którą należy przekształcić źródła danych.|[Dopasowanie przekształcenia tekstu T4](../modeling/customizing-t4-text-transformation.md)|
|Napisz hosta tworzenia szablonów tekstu, który służy do wywołania szablonów tekstowych z własnych aplikacji.|[Przetwarzanie szablonów tekstowych przy użyciu hosta niestandardowego](../modeling/processing-text-templates-by-using-a-custom-host.md)|
