---
title: Generowanie plików za pomocą narzędzia TextTransform | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, TextTransform utility
- TextTransform.exe
ms.assetid: 06a48235-fe02-403e-a1cf-2ae70b4db62f
caps.latest.revision: 43
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 18776795fdf693c855edd3f629d674089daaaebd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72666095"
---
# <a name="generating-files-with-the-texttransform-utility"></a>Generowanie plików za pomocą narzędzia TextTransform
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

TextTransform.exe jest narzędziem wiersza polecenia, które służy do przekształcania szablonu tekstu. Podczas wywoływania TextTransform.exe należy określić nazwę pliku szablonu tekstu jako argument. TextTransform.exe wywołuje aparat transformacji tekstu i przetwarza szablon tekstu. TextTransform.exe jest zazwyczaj wywoływana ze skryptów. Jednak zazwyczaj nie jest to wymagane, ponieważ można wykonać transformację tekstu w Visual Studio lub w procesie kompilacji.

> [!NOTE]
> Jeśli chcesz przeprowadzić transformację tekstu jako część procesu kompilacji, rozważ użycie zadania transformacji tekstu programu MSBuild. Aby uzyskać więcej informacji, zobacz [generowanie kodu w procesie kompilacji](../modeling/code-generation-in-a-build-process.md). Na komputerze, na którym [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] jest zainstalowany program, możesz również napisać aplikację lub [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozszerzenie, które może przekształcać szablony tekstowe. Aby uzyskać więcej informacji, zobacz [Przetwarzanie szablonów tekstowych przy użyciu hosta niestandardowego](../modeling/processing-text-templates-by-using-a-custom-host.md).

 TextTransform.exe znajduje się w następującym katalogu:

 **\Program Files\Common Files\Microsoft Shared\TextTemplating\11.0**

## <a name="syntax"></a>Składnia

```
TextTransform [<options>] <templateName>
```

#### <a name="parameters"></a>Parametry

|**Argument**|**Opis**|
|------------------|---------------------|
|`templateName`|Określa nazwę pliku szablonu, który ma zostać przekształcony.|

|**Opcja**|**Opis**|
|----------------|---------------------|
|**-out** \<filename>|Plik, do którego zostanie zapisany wynik transformacji.|
|**-r**\<assembly>|Zestaw używany do kompilowania i uruchamiania szablonu tekstu.|
|**-u**\<namespace>|Przestrzeń nazw, która jest używana do kompilowania szablonu.|
|**-I**\<includedirectory>|Katalog zawierający szablony tekstowe zawarte w określonym szablonie tekstu.|
|**-P**\<referencepath>|Katalog, w którym mają zostać wyszukane zestawy określone w szablonie tekstowym lub przy użyciu opcji **-r** .<br /><br /> Na przykład, aby dołączyć zestawy używane dla interfejsu API programu Visual Studio, użyj<br /><br /> `-P "%VSSHELLFOLDER%\Common7\IDE\PublicAssemblies"`|
|**-DP** \<processorName> ! \<className>\<assemblyName&#124;codeBase>|Nazwa, pełna nazwa typu oraz zestaw procesorów dyrektywy, których można użyć do przetwarzania dyrektyw niestandardowych w ramach szablonu tekstu.|
|**-a** [procesorname]! [dyrektywaname]! \<parameterName> !\<parameterValue>|Określ wartość parametru procesora dyrektywy. W przypadku określenia tylko nazwy parametru i wartości, parametr będzie dostępny dla wszystkich procesorów dyrektywy. Jeśli określisz procesor dyrektywy, parametr jest dostępny tylko dla określonego procesora. Jeśli określisz nazwę dyrektywy, parametr jest dostępny tylko wtedy, gdy określona dyrektywa jest przetwarzana.<br /><br />  W szablonie tekstowym Dołącz do `hostspecific` dyrektywy Template i Wywołaj komunikat `this.Host` . Na przykład:<br /><br /> `<#@template language="c#" hostspecific="true"#> [<#= this.Host.ResolveParameterValue("", "", "parameterName") #>]`.<br /><br /> Zawsze należy wpisywać znaczniki "!", nawet w przypadku pominięcia opcjonalnych nazw procesorów i dyrektyw. Na przykład:<br /><br /> `-a !!param!value`|
|**-h**|Zapewnia pomoc.|

## <a name="related-topics"></a>Powiązane tematy

|Zadanie|Temat|
|----------|-----------|
|Generowanie plików w rozwiązaniu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|[Generowanie kodu czasu projektowania przy użyciu szablonów tekstowych T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)|
|Napisz procesory dyrektywy, aby przekształcić własne źródła danych.|[Dopasowanie transformacji tekstu T4](../modeling/customizing-t4-text-transformation.md)|
|Napisz hosta tworzenia szablonów tekstu, który umożliwia wywoływanie szablonów tekstowych z własnej aplikacji.|[Przetwarzanie szablonów tekstowych przy użyciu hosta niestandardowego](../modeling/processing-text-templates-by-using-a-custom-host.md)|
