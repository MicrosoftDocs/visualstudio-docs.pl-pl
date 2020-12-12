---
title: Metody korzystania z szablonów tekstowych
description: Poznaj różne metody narzędziowe szablonu tekstu, które są dostępne podczas pisania kodu w programie Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- text templates, utility methods
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6b0015e68f7d78c2b33eaeb9e0bfb404acaed834
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/12/2020
ms.locfileid: "97362018"
---
# <a name="text-template-utility-methods"></a>Metody korzystania z szablonów tekstowych

Istnieje kilka metod, które są zawsze dostępne, gdy piszesz kod w szablonie tekstu programu Visual Studio. Te metody są zdefiniowane w <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> .

> [!TIP]
> Można również użyć innych metod i usług udostępnianych przez środowisko hosta w zwykłym (niewstępnie przetworzonym) szablonie tekstowym. Można na przykład rozpoznać ścieżki plików, rejestrować błędy i pobrać usługi udostępniane przez program Visual Studio oraz wszystkie załadowane pakiety. Aby uzyskać więcej informacji, zobacz [Uzyskiwanie dostępu do programu Visual Studio z szablonu tekstu](/previous-versions/visualstudio/visual-studio-2010/gg604090\(v\=vs.100\)).

## <a name="write-methods"></a>Metody zapisu

Możesz użyć `Write()` metod i, `WriteLine()` Aby dołączyć tekst wewnątrz standardowego bloku kodu, zamiast używać bloku kodu wyrażenia. Poniższe dwa bloki kodu są funkcjonalnie równoważne.

### <a name="code-block-with-an-expression-block"></a>Blok kodu z blokiem wyrażenia

```
<#
int i = 10;
while (i-- > 0)
    { #>
        <#= i #>
    <# }
#>
```

### <a name="code-block-using-writeline"></a>Blok kodu z użyciem funkcji WriteLine ()

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

Za pomocą metod narzędzi Error i Warning można dodawać komunikaty do Lista błędów programu Visual Studio. Na przykład poniższy kod doda komunikat o błędzie do Lista błędów.

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

Typ `this.Host` zależy od typu hosta, w którym wykonywany jest szablon. W szablonie uruchomionym w programie Visual Studio można rzutować, aby `this.Host` `IServiceProvider` uzyskać dostęp do usług, takich jak środowisko IDE. Na przykład:

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
