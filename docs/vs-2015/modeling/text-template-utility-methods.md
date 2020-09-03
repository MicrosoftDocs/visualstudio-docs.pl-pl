---
title: Metody narzędziowe szablonu tekstu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, utility methods
ms.assetid: 8c11f9f7-678b-4f0c-b634-dc78fda699d1
caps.latest.revision: 52
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6c38b15a3b819ce561c098c3b9810ee6884e526b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72658522"
---
# <a name="text-template-utility-methods"></a>Metody korzystania z szablonów tekstowych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Istnieje kilka metod, które są zawsze dostępne, gdy piszesz kod w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] szablonie tekstowym. Te metody są zdefiniowane w <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> .

> [!TIP]
> Można również użyć innych metod i usług udostępnianych przez środowisko hosta w zwykłym (niewstępnie przetworzonym) szablonie tekstowym. Można na przykład rozpoznać ścieżki plików, rejestrować błędy i pobrać usługi udostępniane przez program [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] oraz wszystkie załadowane pakiety.  Aby uzyskać więcej informacji, zobacz [Uzyskiwanie dostępu do programu Visual Studio z szablonu tekstu](https://msdn.microsoft.com/0556f20c-fef4-41a9-9597-53afab4ab9e4).

## <a name="write-methods"></a>Metody zapisu
 Możesz użyć `Write()` metod i, `WriteLine()` Aby dołączyć tekst wewnątrz standardowego bloku kodu, zamiast używać bloku kodu wyrażenia. Poniższe dwa bloki kodu są funkcjonalnie równoważne.

##### <a name="code-block-with-an-expression-block"></a>Blok kodu z blokiem wyrażenia

```
<#
int i = 10;
while (i-- > 0)
    { #>
        <#= i #>
    <# }
#>
```

##### <a name="code-block-using-writeline"></a>Blok kodu z użyciem funkcji WriteLine ()

```
<#
    int i = 10;
    while (i-- > 0)
    {
        WriteLine((i.ToString()));
    }
#>
```

 Przydatne może okazać się użycie jednej z tych metod narzędzi zamiast bloku wyrażenia wewnątrz długiego bloku kodu z zagnieżdżonymi strukturami formantów.

 `Write()`Metody i `WriteLine()` mają dwa przeciążenia, jeden, który przyjmuje jeden parametr ciągu i jeden, który pobiera ciąg formatu złożonego oraz tablicę obiektów do uwzględnienia w ciągu (jak `Console.WriteLine()` Metoda). Poniższe dwa zastosowania `WriteLine()` są funkcjonalnie równoważne:

```
<#
    string msg = "Say: {0}, {1}, {2}";
    string s1 = "hello";
    string s2 = "goodbye";
    string s3 = "farewell";

    WriteLine(msg, s1, s2, s3);
    WriteLine("Say: hello, goodbye, farewell");
#>
```

## <a name="indentation-methods"></a>Metody wcięć
 Możesz użyć metod wcięć, aby sformatować dane wyjściowe szablonu tekstu. <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>Klasa ma `CurrentIndent` właściwość String, która pokazuje bieżące wcięcia w szablonie tekstowym i `indentLengths` pole, które jest listą wcięć, które zostały dodane. Możesz dodać wcięcie z `PushIndent()` metodą i odjąć wcięcie przy użyciu `PopIndent()` metody. Jeśli chcesz usunąć wszystkie wcięcia, użyj `ClearIndent()` metody. Poniższy blok kodu przedstawia sposób korzystania z tych metod:

```
<#
    WriteLine(CurrentIndent + "Hello");
    PushIndent("    ");
    WriteLine(CurrentIndent + "Hello");
    PushIndent("    ");
    WriteLine(CurrentIndent + "Hello");
    ClearIndent();
    WriteLine(CurrentIndent + "Hello");
    PushIndent("    ");
    WriteLine(CurrentIndent + "Hello");
#>
```

 Ten blok kodu generuje następujące dane wyjściowe:

```
Hello
        Hello
                Hello
Hello
        Hello
```

## <a name="error-and-warning-methods"></a>Metody błędów i ostrzeżeń
 Za pomocą metod narzędzi Error i Warning można dodawać komunikaty do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Lista błędów. Na przykład poniższy kod doda komunikat o błędzie do Lista błędów.

```
<#
  try
  {
    string str = null;
    Write(str.Length.ToString());
  }
  catch (Exception e)
  {
    Error(e.Message);
  }
#>
```

## <a name="access-to-host-and-service-provider"></a>Dostęp do hosta i dostawcy usług
 Właściwość `this.Host` może zapewnić dostęp do właściwości uwidocznionych przez hosta, który wykonuje szablon. Aby użyć `this.Host` , należy ustawić `hostspecific` atrybut w `<@template#>` dyrektywie:

 `<#@template ... hostspecific="true" #>`

 Typ `this.Host` zależy od typu hosta, w którym wykonywany jest szablon. W szablonie, który jest uruchomiony w programie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , można rzutować, aby `this.Host` `IServiceProvider` uzyskać dostęp do usług, takich jak IDE. Na przykład:

```
EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)
                       .GetService(typeof(EnvDTE.DTE));
```

## <a name="using-a-different-set-of-utility-methods"></a>Korzystanie z innego zestawu metod narzędzi
 W ramach procesu generowania tekstu plik szablonu jest przekształcany do klasy, która zawsze nazywa się `GeneratedTextTransformation` i dziedziczy po <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> . Jeśli zamiast tego chcesz użyć innego zestawu metod, możesz napisać własną klasę i określić ją w dyrektywie Template. Klasa musi dziedziczyć po elemencie <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> .

```
<#@ template inherits="MyUtilityClass" #>
```

 Użyj `assembly` dyrektywy, aby odwołać się do zestawu, w którym można znaleźć skompilowaną klasę.
