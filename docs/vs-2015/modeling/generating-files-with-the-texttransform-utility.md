---
title: Generowanie plików za pomocą narzędzia TextTransform | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, TextTransform utility
- TextTransform.exe
ms.assetid: 06a48235-fe02-403e-a1cf-2ae70b4db62f
caps.latest.revision: 43
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 75438b5a2ffa5917f667ab3fdc3a9bd3528f0e55
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54802107"
---
# <a name="generating-files-with-the-texttransform-utility"></a>Generowanie plików za pomocą narzędzia TextTransform
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

TextTransform.exe jest narzędziem wiersza polecenia, można użyć do przekształcania szablonu tekstu. Jeśli chcesz wywołać TextTransform.exe, należy określić nazwę pliku szablonu tekstu jako argument. TextTransform.exe wywołuje aparat przekształcenia tekstu i przetwarza szablonu tekstu. TextTransform.exe zwykle jest wywoływana przez skrypty. Jednak nie jest zazwyczaj wymagane, ponieważ można dokonać przekształcenia tekstu, w programie Visual Studio lub w procesie kompilacji.  
  
> [!NOTE]
>  Jeśli chcesz wykonywać przekształcenia tekstu jako część procesu kompilacji, rozważ użycie zadanie przekształcenia tekstu w MSBuild. Aby uzyskać więcej informacji, zobacz [generowanie kodu w procesie kompilacji](../modeling/code-generation-in-a-build-process.md). W komputerze, na którym [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] jest zainstalowana, można także napisać aplikację lub [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozszerzenia, które umożliwiają przekształcanie szablonów tekstowych. Aby uzyskać więcej informacji, zobacz [przetwarzanie szablonów tekstowych przy użyciu hosta niestandardowego](../modeling/processing-text-templates-by-using-a-custom-host.md).  
  
 TextTransform.exe znajduje się w następującym katalogu:  
  
 **\Program Files\Common Files\Microsoft Shared\TextTemplating\11.0**  
  
## <a name="syntax"></a>Składnia  
  
```  
TextTransform [<options>] <templateName>  
```  
  
#### <a name="parameters"></a>Parametry  
  
|**Argument**|**Opis**|  
|------------------|---------------------|  
|`templateName`|Określa nazwę pliku szablonu, który chcesz przekształcić.|  
  
|**Option**|**Opis**|  
|----------------|---------------------|  
|**-out** \<nazwa pliku >|Plik, do której są zapisywane dane wyjściowe transformacji.|  
|**-r** \<zestawu >|Zestaw używany do kompilowania i uruchamiania szablonu tekstu.|  
|**-u** \<przestrzeni nazw >|Obszar nazw, który jest używany do tworzenia szablonu.|  
|**-I** \<includedirectory >|Katalog, który zawiera szablony tekstowe zawarte w szablonie określony tekst.|  
|**-P** \<referencepath >|Katalog do przeszukania zestawy określone w szablonie tekstu lub przy użyciu **- r** opcji.<br /><br /> Na przykład aby uwzględnić zestawy używany do Visual Studio API, należy użyć<br /><br /> `-P "%VSSHELLFOLDER%\Common7\IDE\PublicAssemblies"`|  
|**-dp** \<processorName>!\<className>!\<assemblyName&#124;codeBase>|Nazwa, pełna nazwa typu i zestawu procesor dyrektywy, który może służyć do przetwarzania niestandardowych dyrektyw szablonu tekstu.|  
|**-** [processorName]! [directiveName]! \<parameterName >! \<parameterValue >|Określ wartość parametru dla procesora dyrektywy. Jeśli określisz tylko nazwy parametru i wartości parametru będą dostępne dla wszystkich procesorów dyrektyw. Jeśli określisz procesor dyrektywy, parametr jest dostępna tylko w określonym procesorem. Jeśli określisz nazwę dyrektywy, parametr jest dostępna tylko wtedy, gdy określony dyrektywa jest przetwarzany.<br /><br />  W szablonie tekstu, obejmują `hostspecific` w dyrektywie szablonu i wywołania wiadomości na `this.Host`. Na przykład:<br /><br /> `<#@template language="c#" hostspecific="true"#> [<#= this.Host.ResolveParameterValue("", "", "parameterName") #>]`.<br /><br /> Zawsze wpisać "!" oznacza, nawet jeśli parametr zostanie pominięty, opcjonalny procesora i nazwy dyrektyw. Na przykład:<br /><br /> `-a !!param!value`|  
|**-h**|Zawiera Pomoc.|  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Zadanie|Temat|  
|----------|-----------|  
|Generowanie plików w rozwiązaniu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|[Generowanie kodu czasu projektowania przy użyciu szablonów tekstowych T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)|  
|Napisz dyrektywy procesorów, którą należy przekształcić źródła danych.|[Dopasowanie przekształcenia tekstu T4](../modeling/customizing-t4-text-transformation.md)|  
|Napisz hosta tworzenia szablonów tekstu, który służy do wywołania szablonów tekstowych z własnych aplikacji.|[Przetwarzanie szablonów tekstowych przy użyciu hosta niestandardowego](../modeling/processing-text-templates-by-using-a-custom-host.md)|
