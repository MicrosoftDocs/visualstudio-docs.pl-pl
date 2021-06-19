---
title: Metody korzystania z szablonów tekstowych
description: Dowiedz się więcej o różnych metodach narzędzi szablonu tekstu, które są dostępne podczas pisania kodu w Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- text templates, utility methods
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b45bf6418562da5315c986a64a1295c137e982d6
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388688"
---
# <a name="text-template-utility-methods"></a>Metody korzystania z szablonów tekstowych

Istnieje kilka metod, które są zawsze dostępne podczas pisania kodu w Visual Studio szablonu tekstowego. Te metody są zdefiniowane w <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> .

> [!TIP]
> W zwykłym (nieprzetworzonej) szablonie tekstowym można również użyć innych metod i usług oferowanych przez środowisko hosta. Można na przykład rozwiązać problemy ze ścieżkami plików, rejestrować błędy i uzyskać usługi udostępniane przez Visual Studio i wszelkie załadowane pakiety. Aby uzyskać więcej informacji, zobacz Accessing Visual Studio from a Text Template (Uzyskiwanie dostępu [do Visual Studio z szablonu tekstowego).](/previous-versions/visualstudio/visual-studio-2010/gg604090\(v\=vs.100\))

## <a name="write-methods"></a>Metody zapisu

Możesz użyć metod i , aby dołączyć tekst wewnątrz standardowego bloku kodu, zamiast `Write()` używać bloku kodu `WriteLine()` wyrażenia. Poniższe dwa bloki kodu są funkcjonalnie równoważne.

### <a name="code-block-with-an-expression-block"></a>Blok kodu z blokiem wyrażeń

```
<#
int i = 10;
while (i-- > 0)
    { #>
        <#= i #>
    <# }
#>
```

### <a name="code-block-using-writeline"></a>Blok kodu przy użyciu funkcji WriteLine()

```
<#
    int i = 10;
    while (i-- > 0)
    {
        WriteLine((i.ToString()));
    }
#>
```

Pomocne może okazać się użycie jednej z tych metod narzędziowych zamiast bloku wyrażeń wewnątrz długiego bloku kodu z zagnieżdżoną strukturą kontrolną.

Metody i mają dwa przeciążenia: jedno, które przyjmuje jeden parametr ciągu, i jedno, które przyjmuje ciąg formatu złożonego oraz tablicę obiektów do dołączyć do ciągu (na przykład `Write()` `WriteLine()` metodę `Console.WriteLine()` ). Następujące dwa zastosowania funkcji `WriteLine()` są funkcjonalnie równoważne:

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

## <a name="indentation-methods"></a>Metody wcięcia

Metody wcięcia mogą być stosowane do formatowania danych wyjściowych szablonu tekstu. Klasa ma właściwość ciągu, która pokazuje bieżące wcięcia w szablonie tekstu i pole, które jest listą dodanych <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> `CurrentIndent` wcięć. `indentLengths` Możesz dodać wcięcie za pomocą `PushIndent()` metody i odjąć wcięcie za pomocą `PopIndent()` metody . Jeśli chcesz usunąć wszystkie wcięcia, użyj `ClearIndent()` metody . Poniższy blok kodu przedstawia użycie tych metod:

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

Możesz użyć metod narzędzia do obsługi błędów i ostrzeżeń, aby dodać komunikaty do Visual Studio listy błędów. Na przykład poniższy kod spowoduje dodanie komunikatu o błędzie do listy błędów.

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

Właściwość może `this.Host` zapewnić dostęp do właściwości ujawnionych przez hosta wykonującego szablon. Aby użyć `this.Host` , należy ustawić atrybut w `hostspecific` `<@template#>` dyrektywie :

`<#@template ... hostspecific="true" #>`

Typ zależy od typu hosta, na `this.Host` którym jest wykonywany szablon. W szablonie uruchomionym w Visual Studio można rzutować na , aby uzyskać dostęp do usług, `this.Host` `IServiceProvider` takich jak ide. Na przykład:

```
EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)
                       .GetService(typeof(EnvDTE.DTE));
```

## <a name="using-a-different-set-of-utility-methods"></a>Używanie innego zestawu metod narzędziowych

W ramach procesu generowania tekstu plik szablonu jest przekształcany w klasę, która jest zawsze nazwana i `GeneratedTextTransformation` dziedziczy z <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> klasy . Jeśli zamiast tego chcesz użyć innego zestawu metod, możesz napisać własną klasę i określić ją w dyrektywie template. Klasa musi dziedziczyć z <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> klasy .

```
<#@ template inherits="MyUtilityClass" #>
```

Użyj dyrektywy `assembly` , aby odwołać się do zestawu, w którym można znaleźć skompilowaną klasę.
