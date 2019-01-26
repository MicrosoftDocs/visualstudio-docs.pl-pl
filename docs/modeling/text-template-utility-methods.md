---
title: Metody korzystania z szablonów tekstowych
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- text templates, utility methods
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: da35b3d5c605c6974f99a840866d90c025bd4edc
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54992571"
---
# <a name="text-template-utility-methods"></a>Metody korzystania z szablonów tekstowych

Istnieje kilka metod, które są zawsze dostępne dla Ciebie podczas pisania kodu w szablonie tekstu Visual Studio. Te metody są zdefiniowane w <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>.

> [!TIP]
> Można również użyć innych metod i usług udostępnianych przez środowisko hosta w regularnych szablon tekstowy (nieprzetworzony). Na przykład, można rozpoznać ścieżki do plików, rejestrowanie błędów i Pobierz usług dostarczanych przez program Visual Studio i wszystkie załadowane pakietów. Aby uzyskać więcej informacji, zobacz [uzyskiwania dostępu do programu Visual Studio z szablonu tekstowego](/previous-versions/visualstudio/visual-studio-2010/gg604090\(v\=vs.100\)).

## <a name="write-methods"></a>Pisanie metod

Możesz użyć `Write()` i `WriteLine()` metody dołączyć tekst wewnątrz bloku standardowego kodu, zamiast korzystać z blokiem kodu wyrażenia. Poniższe bloki kodu dwa są funkcjonalnie równoważne.

### <a name="code-block-with-an-expression-block"></a>Blok kodu za pomocą bloku wyrażenia

```
<#
int i = 10;
while (i-- > 0)
    { #>
        <#= i #>
    <# }
#>
```

### <a name="code-block-using-writeline"></a>Blok kodu przy użyciu metody WriteLine()

```
<#
    int i = 10;
    while (i-- > 0)
    {
        WriteLine((i.ToString()));
    }
#>
```

Może okazać się przydatne do korzystania z jednej z następujących metod narzędzia zamiast bloku wyrażenia wewnątrz bloku kodu długie przy użyciu zagnieżdżone struktury sterujące.

`Write()` i `WriteLine()` metody mają dwa przeciążenia, ta, która przyjmuje jako parametr ciągu jednego i jeden, który przyjmuje ciąg formatu złożonego, a także tablicę obiektów do uwzględnienia w ciągu (takich jak `Console.WriteLine()` metody). Następujące dwa zastosowania `WriteLine()` są funkcjonalnie równoważne:

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

Wcięcie metody można użyć do formatowania danych wyjściowych szablonu tekstu. <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> Klasa ma `CurrentIndent` ciągu właściwość, która pokazuje bieżącym wcięciu w szablonie tekstowym i `indentLengths` oznacza to pole listy wcięcia, które zostały dodane. Możesz dodać wcięć za pomocą `PushIndent()` — metoda i odejmowanie wcięć za pomocą `PopIndent()` metody. Aby usunąć wszystkie wcięcia, należy użyć `ClearIndent()` metody. Poniższy blok kodu pokazano sposób użycia tych metod:

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

Ten blok kodu generuje następujące wyniki:

```
Hello
        Hello
                Hello
Hello
        Hello
```

## <a name="error-and-warning-methods"></a>Błąd i ostrzeżenie metody

Błąd i ostrzeżenie metody narzędziowe służy do dodawania komunikatów do listy błędów programu Visual Studio. Na przykład poniższy kod doda komunikat o błędzie na liście błędów.

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

## <a name="access-to-host-and-service-provider"></a>Dostęp do hosta i usługodawcy

Właściwość `this.Host` można zapewnić dostęp do właściwości udostępniane przez hosta, który jest wykonywany szablonu. Aby użyć `this.Host`, należy ustawić `hostspecific` atrybutu w `<@template#>` dyrektywy:

`<#@template ... hostspecific="true" #>`

Typ `this.Host` zależy od typu hosta, w którym szablon jest wykonywany. W szablonie, który jest uruchomiony w programie Visual Studio, można rzutować `this.Host` do `IServiceProvider` do uzyskania dostępu do usług, takich jak środowiska IDE. Na przykład:

```
EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)
                       .GetService(typeof(EnvDTE.DTE));
```

## <a name="using-a-different-set-of-utility-methods"></a>Przy użyciu różnych zestaw metod narzędziowych

W ramach procesu tworzenia tekstu, plik szablonu jest przekształcana na klasy, która nosi nazwę zawsze `GeneratedTextTransformation`i dziedziczy <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>. Jeśli chcesz użyć innego zestawu metod zamiast tego można napisać własne klasy i je określić w dyrektywie szablonu. Klasa musi dziedziczyć <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>.

```
<#@ template inherits="MyUtilityClass" #>
```

Użyj `assembly` dyrektywy odwołać się do zestawu, gdzie można znaleźć klasy skompilowany.