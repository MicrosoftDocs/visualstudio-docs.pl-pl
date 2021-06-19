---
title: Generowanie kodu z języka specyficznego dla domeny
description: Dowiedz się, Domain-Specific Language Tools to zaawansowany sposób generowania kodu, dokumentów i innych artefaktów na podstawie danych reprezentowanych w modelach.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6eee4fe2400bac1534bdc9c208fa60d9af8d3cfd
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388844"
---
# <a name="generating-code-from-a-domain-specific-language"></a>Generowanie kodu z języka specyficznego dla domeny

Firma Microsoft oferuje zaawansowany sposób generowania kodu, dokumentów, plików konfiguracji i innych artefaktów na podstawie danych [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] reprezentowanych w modelach. Za pomocą funkcji można utworzyć zestaw klas reprezentujących dane i napisać szablony tekstowe w klasach, których nazwy i właściwości [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] odzwierciedlają te dane.

Na przykład firma Fabrikam ma plik XML z nazwami klientów i adresami e-mail. Deweloperzy tworzą model, w którym klient jest klasą, z nazwą właściwości i adresem e-mail. Zapisują kilka szablonów tekstowych do przetwarzania danych, w tym ten fragment, który tworzy tabelę wszystkich klientów w ramach strony HTML:

```
<table>
<# foreach (Customer c in ContactList) {  #>
  <tr><td> <#= c.FullName #> </td>
      <td> <#= c.EmailAddress #> </td> </tr>
<# } #>  </table>
```

Podczas przetwarzania bazy danych klienta plik XML jest odczytywany do magazynu modeli. Procesor *dyrektywy*, utworzony przy użyciu klasy , udostępnia klasę [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] Customer kodowi w szablonie tekstowym. Wiele szablonów tekstowych można uruchamiać w tym samym magazynie.

Szablony tekstowe są niezbędne w przypadku programu [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] . Są one używane do generowania kodu źródłowego dla elementów modelu domeny, a także dla pakietów VSPackage i kontrolek używanych do integracji narzędzi z Visual Studio.

W tej sekcji omówiono niektóre sposoby tworzenia, modyfikowania i debugowania szablonów tekstowych używanych w programie [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] .

## <a name="in-this-section"></a>W tej sekcji

[Uzyskiwanie dostępu do modeli z szablonów tekstowych](../modeling/accessing-models-from-text-templates.md)\
Zawiera podstawowe informacje dotyczące odwoływania się do języka specyficznego dla domeny w szablonach tekstowych.

[Przewodnik: debugowanie szablonu tekstowego, który uzyskuje dostęp do modelu](../modeling/walkthrough-debugging-a-text-template-that-accesses-a-model.md)\
Opisuje sposób rozwiązywania problemów i debugowania w szablonie tekstowym, który odwołuje się do języka specyficznego dla domeny.

[Przewodnik: łączenie hosta z wygenerowanym procesorem dyrektywy](../modeling/walkthrough-connecting-a-host-to-a-generated-directive-processor.md)\
Opisuje sposób łączenia niestandardowego hosta z wygenerowanym procesorem dyrektywy.

[DslTextTransform polecenia](../modeling/the-dsltexttransform-command.md)\
Opisuje plik polecenia, który wykonuje plik wykonywalny TextTransform w wierszu polecenia dla szablonów tekstowych odwołujące się do języków specyficznych dla domeny.

## <a name="reference"></a>Odwołanie

[Pisanie szablonu tekstowego T4](../modeling/writing-a-t4-text-template.md)\
Zawiera składnię dyrektyw szablonu tekstu i bloków sterujących.

## <a name="related-sections"></a>Sekcje pokrewne

[Generowanie kodu w czasie projektowania przy użyciu szablonów tekstowych T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)\
Objaśnia proces przekształcania szablonu tekstowego.

[Generowanie kodu w procesie kompilacji](../modeling/code-generation-in-a-build-process.md)\
Przeczytaj ten temat, jeśli generujesz pliki z DSL na serwerze kompilacji.
