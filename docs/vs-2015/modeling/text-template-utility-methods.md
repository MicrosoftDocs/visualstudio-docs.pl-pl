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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658522"
---
# <a name="text-template-utility-methods"></a>Metody korzystania z szablonów tekstowych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Istnieje kilka metod, które są zawsze dostępne, gdy piszesz kod w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] szablonu tekstu. Te metody są zdefiniowane w <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>.

> [!TIP]
> Można również użyć innych metod i usług udostępnianych przez środowisko hosta w zwykłym (niewstępnie przetworzonym) szablonie tekstowym. Można na przykład rozpoznać ścieżki plików, rejestrować błędy i pobrać usługi udostępniane przez [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] i wszystkie załadowane pakiety.  Aby uzyskać więcej informacji, zobacz [Uzyskiwanie dostępu do programu Visual Studio z szablonu tekstu](https://msdn.microsoft.com/0556f20c-fef4-41a9-9597-53afab4ab9e4).

## <a name="write-methods"></a>Metody zapisu
 Możesz użyć metod `Write()` i `WriteLine()` do dołączania tekstu wewnątrz standardowego bloku kodu, zamiast korzystać z bloku kodu wyrażenia. Poniższe dwa bloki kodu są funkcjonalnie równoważne.

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

 Metody `Write()` i `WriteLine()` mają dwa przeciążenia, jeden, który przyjmuje jeden parametr ciągu i jeden, który pobiera ciąg formatu złożonego i tablicę obiektów do uwzględnienia w ciągu (jak Metoda `Console.WriteLine()`). Poniższe dwa zastosowania `WriteLine()` są funkcjonalnie równoważne:

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
 Możesz użyć metod wcięć, aby sformatować dane wyjściowe szablonu tekstu. Klasa <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> ma właściwość `CurrentIndent` String, która pokazuje bieżące wcięcia w szablonie tekstowym i pole `indentLengths`, które jest listą wcięć, które zostały dodane. Możesz dodać wcięcie z użyciem metody `PushIndent()` i odjąć wcięcie przy użyciu metody `PopIndent()`. Jeśli chcesz usunąć wszystkie wcięcia, użyj metody `ClearIndent()`. Poniższy blok kodu przedstawia sposób korzystania z tych metod:

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
 Za pomocą metod narzędzi Error i Warning można dodawać komunikaty do Lista błędów [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Na przykład poniższy kod doda komunikat o błędzie do Lista błędów.

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
 Właściwość `this.Host` może zapewnić dostęp do właściwości uwidocznionych przez hosta, który wykonuje szablon. Aby użyć `this.Host`, należy ustawić atrybut `hostspecific` w dyrektywie `<@template#>`:

 `<#@template ... hostspecific="true" #>`

 Typ `this.Host` zależy od typu hosta, w którym wykonywany jest szablon. W szablonie, który jest uruchomiony w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], można rzutować `this.Host` do `IServiceProvider` w celu uzyskania dostępu do usług, takich jak IDE. Na przykład:

```
EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)
                       .GetService(typeof(EnvDTE.DTE));
```

## <a name="using-a-different-set-of-utility-methods"></a>Korzystanie z innego zestawu metod narzędzi
 W ramach procesu generowania tekstu plik szablonu jest przekształcany do klasy, która zawsze nosi nazwę `GeneratedTextTransformation`and dziedziczy po <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>. Jeśli zamiast tego chcesz użyć innego zestawu metod, możesz napisać własną klasę i określić ją w dyrektywie Template. Klasa musi dziedziczyć po <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>.

```
<#@ template inherits="MyUtilityClass" #>
```

 Użyj dyrektywy `assembly`, aby odwołać się do zestawu, w którym można znaleźć skompilowaną klasę.
