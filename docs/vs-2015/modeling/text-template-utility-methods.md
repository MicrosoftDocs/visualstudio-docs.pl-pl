---
title: Metody korzystania z szablonów tekstowych | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, utility methods
ms.assetid: 8c11f9f7-678b-4f0c-b634-dc78fda699d1
caps.latest.revision: 52
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 84f5b5de8b28062023d851e38e26930718d599e7
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54790230"
---
# <a name="text-template-utility-methods"></a>Metody korzystania z szablonów tekstowych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Istnieje kilka metod, które są zawsze dostępne dla Ciebie podczas pisania kodu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] szablonu tekstu. Te metody są zdefiniowane w <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>.  
  
> [!TIP]
>  Można również użyć innych metod i usług udostępnianych przez środowisko hosta w regularnych szablon tekstowy (nieprzetworzony). Na przykład, można rozpoznać ścieżki do plików, rejestrowanie błędów i Pobierz usługi świadczone przez [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] i dowolne załadowane pakietów.  Aby uzyskać więcej informacji, zobacz [uzyskiwania dostępu do programu Visual Studio z szablonu tekstowego](http://msdn.microsoft.com/0556f20c-fef4-41a9-9597-53afab4ab9e4).  
  
## <a name="write-methods"></a>Pisanie metod  
 Możesz użyć `Write()` i `WriteLine()` metody dołączyć tekst wewnątrz bloku standardowego kodu, zamiast korzystać z blokiem kodu wyrażenia. Poniższe bloki kodu dwa są funkcjonalnie równoważne.  
  
##### <a name="code-block-with-an-expression-block"></a>Blok kodu za pomocą bloku wyrażenia  
  
```  
<#  
int i = 10;  
while (i-- > 0)  
    { #>  
        <#= i #>  
    <# }  
#>  
```  
  
##### <a name="code-block-using-writeline"></a>Blok kodu przy użyciu metody WriteLine()  
  
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
 Służy do dodawania komunikatów do błędu i ostrzeżenia metody narzędziowe [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] listy błędów. Na przykład poniższy kod doda komunikat o błędzie na liście błędów.  
  
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
  
 Typ `this.Host` zależy od typu hosta, w którym szablon jest wykonywany. W szablonie, który jest uruchomiony w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], można rzutować `this.Host` do `IServiceProvider` do uzyskania dostępu do usług, takich jak środowiska IDE. Na przykład:  
  
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
