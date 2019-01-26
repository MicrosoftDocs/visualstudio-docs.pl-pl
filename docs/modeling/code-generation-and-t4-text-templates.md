---
title: Generowanie kodu i szablony tekstowe T4
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.TextTemplating.TextTemplating
helpviewer_keywords:
- generating text
- .tt files
- code generation
- text templates
- generating code
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2c3f4e654c5bcaf373d8358201c856cc8667043d
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55034489"
---
# <a name="code-generation-and-t4-text-templates"></a>Generowanie kodu i szablony tekstowe T4

W programie Visual Studio *szablonu tekstowego T4* różne bloki tekstu i logiki formantu, który można wygenerować pliku tekstowego. Logiki formantu są zapisywane jako fragmenty kodu programu w [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] lub [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]. Program Visual Studio 2015 Update 2 lub nowszy można użyć funkcji w wersji 6.0 C# w dyrektywach szablony T4. Wygenerowany plik może być tekst dowolnego rodzaju, np. strony sieci web lub plik zasobu lub kodu źródłowego programu w dowolnym języku.

Istnieją dwa rodzaje szablonów tekstowych T4: Uruchom czas i w czasie projektowania.

## <a name="run-time-t4-text-templates"></a>Szablony tekstowe T4 czasu wykonania

Znany także jako "wstępnie przetworzony" szablonów, szablony czasu uruchamiania są wykonywane w aplikacji w celu tworzenia ciągów tekstowych, zwykle jako części jego danych wyjściowych. Na przykład można utworzyć szablon, aby zdefiniować strony HTML:

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

Aplikację można uruchomić na komputerze, który nie ma zainstalowanego programu Visual Studio.

Aby utworzyć szablon czasu wykonywania, Dodaj **szablon tekstowy preprocesora** plik do projektu. Alternatywnie możesz dodać plik tekstowy i ustawić jej **narzędzie niestandardowe** właściwości **TextTemplatingFilePreprocessor**.

Aby uzyskać więcej informacji, zobacz [Generowanie tekstu czasu wykonywania przy użyciu szablonów tekstowych T4](../modeling/run-time-text-generation-with-t4-text-templates.md). Aby uzyskać więcej informacji na temat składni szablonów, zobacz [pisanie szablonu tekstowego T4](../modeling/writing-a-t4-text-template.md).

## <a name="design-time-t4-text-templates"></a>Projektowanie szablonów tekstowych T4 czasu

Szablony czasu projektowania zdefiniować część kodu źródłowego i innych zasobów aplikacji. Zazwyczaj kilka szablonów, które odczytują dane w jednym pliku wejściowego lub bazy danych użycia i wygenerować niektóre z Twojej *.cs*, *.vb*, lub w innych plikach źródłowych. Każdy szablon generuje jeden plik. Są one wykonywane w ramach programu Visual Studio lub programu MSBuild.

Dane wejściowe można na przykład plik XML w danych konfiguracji. Zawsze, gdy edytujesz plik XML podczas tworzenia szablonów tekstowych ponownie wygenerować część kodu aplikacji. Jeden z szablonów może wyglądać następująco:

```
<#@ output extension=".cs" #>
<#@ assembly name="System.Xml" #>
<#
 System.Xml.XmlDocument configurationData = ...; // Read a data file here.
#>
namespace Fabrikam.<#= configurationData.SelectSingleNode("jobName").Value #>
{
  ... // More code here.
}
```

W zależności od wartości w pliku XML, wygenerowany *.cs* plik będzie wyglądać podobnie do poniższego:

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
> Termin *modelu* jest czasami używane do opisywania danych odczytanych przez co najmniej jeden szablon. Model może być w dowolnym formacie, w dowolnych plików lub bazy danych. Nie ma być modelu UML lub model języka specyficznego dla domeny. Po prostu "Model" wskazuje, czy danych można zdefiniować w warunkach użytkowania koncepcji biznesowych, a nie przypominającą kod.

Funkcja przekształcania szablonu tekstu o nazwie *T4*.

## <a name="see-also"></a>Zobacz też

- [Generowanie kodu z języka specyficznego dla domeny](../modeling/generating-code-from-a-domain-specific-language.md)
