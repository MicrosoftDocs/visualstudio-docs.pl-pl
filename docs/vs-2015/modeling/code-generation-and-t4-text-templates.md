---
title: Generowanie kodu i szablony tekstowe T4 | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.TextTemplating.TextTemplating
helpviewer_keywords:
- generating text
- .tt files
- code generation
- text templates
- generating code
ms.assetid: 74a0a748-5b11-4999-8bea-49572967827d
caps.latest.revision: 84
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9967b0cb47bd397b7b0fa752eb2fff2518865b14
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2019
ms.locfileid: "56840612"
---
# <a name="code-generation-and-t4-text-templates"></a>Generowanie kodu i szablony tekstowe T4
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], *szablonu tekstowego T4* różne bloki tekstu i logiki formantu, który można wygenerować pliku tekstowego. Logiki formantu są zapisywane jako fragmenty kodu programu w [!INCLUDE[csprcs](../includes/csprcs-md.md)] lub [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]. Program Visual Studio 2015 Update 2 lub nowszy można użyć funkcji w wersji 6.0 C# w dyrektywach szablony T4. Wygenerowany plik może być tekst dowolnego rodzaju, np. strony sieci Web lub plik zasobu lub kodu źródłowego programu w dowolnym języku.  
  
 Istnieją dwa rodzaje szablonów tekstowych T4:  
  
 **Szablony tekstowe T4 czasu wykonania** ("wstępnie przetworzony" Szablony) są wykonywane w aplikacji w celu tworzenia ciągów tekstowych, zwykle jako części jego danych wyjściowych.  
 Na przykład można utworzyć szablon, aby zdefiniować strony HTML:  
  
```  
<html><body>  
 The date and time now is: <#= DateTime.Now #>  
</body></html>  
```  
  
 Należy zauważyć, że szablon jest podobny wygenerowanych danych wyjściowych. Podobieństwa szablon, aby dane wyjściowe pomaga uniknąć pomyłek, gdy chcesz je zmienić.  
  
 Ponadto szablon zawiera fragmenty kodu programu. Powtarzaj fragmentów tekstu, aby zapewnić sekcje warunkowe i wyświetlić dane z aplikacji, można użyć tych fragmentów.  
  
 Aby wygenerować dane wyjściowe, Twoja aplikacja wywołuje funkcję, która jest generowana przez szablon. Na przykład:  
  
```csharp  
string webResponseText = new MyTemplate().TransformText();  
  
```  
  
 Aplikację można uruchomić na komputerze, na którym nie ma [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zainstalowane.  
  
 Aby utworzyć szablon czasu wykonywania, Dodaj **szablon tekstowy preprocesora** plik do projektu. Alternatywnie możesz dodać plik tekstowy i ustawić jej **narzędzie niestandardowe** właściwości **TextTemplatingFilePreprocessor**.  
  
 Aby uzyskać więcej informacji, zobacz [Generowanie tekstu czasu wykonywania przy użyciu szablonów tekstowych T4](../modeling/run-time-text-generation-with-t4-text-templates.md). Aby uzyskać więcej informacji na temat składni szablonów, zobacz [pisanie szablonu tekstowego T4](../modeling/writing-a-t4-text-template.md).  
  
 **Szablony tekstowe T4 projektowania** są wykonywane w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zdefiniować część kodu źródłowego i innych zasobów aplikacji.  
 Zazwyczaj będzie używać kilka szablonów, które odczytują dane w jednym pliku wejściowego lub bazy danych i wygenerować niektóre z Twojej `.cs`, `.vb`, lub w innych plikach źródłowych. Każdy szablon generuje jeden plik. Są one wykonywane w ramach [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] lub [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)].  
  
 Dane wejściowe można na przykład plik XML w danych konfiguracji. Zawsze, gdy edytujesz plik XML podczas tworzenia szablonów tekstowych spowoduje ponowne wygenerowanie część kodu aplikacji. Jeden z szablonów może wyglądać następująco:  
  
```  
<#@ output extension=".txt" #>  
<#@ assembly name="System.Xml" #>  
<#  
 System.Xml.XmlDocument configurationData = ...; // Read a data file here.  
#>  
namespace Fabrikam.<#= configurationData.SelectSingleNode("jobName").Value #>  
{  
  ... // More code here.   
}  
  
```  
  
 Zależny od wartości w pliku XML, wygenerowany `.cs` plik będzie wyglądać podobnie do poniższego:  
  
```  
namespace Fabrikam.FirstJob  
{  
  ... // More code here.   
}  
```  
  
 Inny przykład danych wejściowych może być diagramu przepływu pracy w działalności biznesowej. Zmiana ich biznesowego przepływu pracy lub rozpocząć pracę przy użyciu nowych użytkowników, którzy mają inny przepływ pracy, to proste ponownie wygenerować kod, aby dopasować nowego modelu.  
  
 Szablonów czasu projektowania ułatwiają szybsze i bardziej niezawodne, aby zmienić konfigurację, gdy zmienią się wymagania. Zwykle dane wejściowe zdefiniowano pod względem wymagań biznesowych, tak jak w przykładzie przepływ pracy. Ta funkcja ułatwia omówić zmiany z użytkownikami. Szablony projektowania w związku z tym są użytecznym narzędziem w procesie programowanie metodą agile.  
  
 Aby utworzyć szablon czasu projektowania, należy dodać **szablon tekstowy** plik do projektu. Alternatywnie możesz dodać plik tekstowy i ustawić jej **narzędzie niestandardowe** właściwości **TextTemplatingFileGenerator**.  
  
 Aby uzyskać więcej informacji, zobacz [generowanie kodu czasu projektowania przy użyciu szablonów tekstowych T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md). Aby uzyskać więcej informacji na temat składni szablonów, zobacz [pisanie szablonu tekstowego T4](../modeling/writing-a-t4-text-template.md).  
  
> [!NOTE]
>  Termin *modelu* jest czasami używane do opisywania danych odczytanych przez co najmniej jeden szablon. Model może być w dowolnym formacie, w dowolnych plików lub bazy danych. Nie ma być modelu UML lub model języka specyficznego dla domeny. Po prostu "Model" wskazuje, czy danych można zdefiniować w warunkach użytkowania koncepcji biznesowych, a nie przypominającą kod.  
  
 Funkcja przekształcania szablonu tekstu o nazwie *T4*.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Generowanie tekstu czasu wykonywania przy użyciu szablonów tekstowych T4](../modeling/run-time-text-generation-with-t4-text-templates.md)  
 W aplikacji, które generuje pliki tekstowe tekst wstępnie skompilowane szablony są proste i niezawodne metody definiowania tekstu. Jednak ta metoda nie można użyć dla szablonów tekstowych, które zmieniają się w czasie wykonywania.  
  
 [Generowanie kodu czasu projektowania przy użyciu szablonów tekstowych T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)  
 Generowanie kodu i innych zasobów na podstawie modelu pozwala zaktualizować aplikację, aktualizując model.  
  
 [Generowanie kodu w procesie kompilacji](../modeling/code-generation-in-a-build-process.md)  
 Jeśli zainstalowano [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] wizualizacji i modelowania SDK, należy zapewnić wygenerowanego oprogramowania przechowuje na bieżąco ze zmianami w modelu.  
  
 [Pisanie szablonu tekstowego T4](../modeling/writing-a-t4-text-template.md)  
 Składnia pliku szablonu tekstu.  
  
 [Przewodnik: Generowanie kodu przy użyciu szablonów tekstowych](../modeling/walkthrough-generating-code-by-using-text-templates.md)  
 Pokaz jeden ze sposobów użycia generowania kodu.  
  
 [Debugowanie szablonu tekstowego T4](../modeling/debugging-a-t4-text-template.md)  
 Jak debugować szablonów tekstowych i typowych błędów szablonu tekstu.  
  
 [Generowanie plików za pomocą narzędzia TextTransform](../modeling/generating-files-with-the-texttransform-utility.md)  
 Narzędzie wiersza polecenia można użyć do uruchamiania przekształceń szablonu tekstu.  
  
 [Dopasowanie przekształcenia tekstu T4](../modeling/customizing-t4-text-transformation.md)  
 Jak napisać procesorów dyrektyw i hosty szablonów niestandardowych dla źródeł danych.  
  
## <a name="see-also"></a>Zobacz też  
 [Generowanie plików z modelu UML](../modeling/generate-files-from-a-uml-model.md)   
 [Generowanie kodu z języka specyficznego dla domeny](../modeling/generating-code-from-a-domain-specific-language.md)
