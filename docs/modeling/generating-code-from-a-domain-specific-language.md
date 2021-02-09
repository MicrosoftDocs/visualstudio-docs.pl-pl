---
title: Generowanie kodu z języka specyficznego dla domeny
description: Dowiedz się, jak narzędzia języka Domain-Specific zapewniają zaawansowany sposób generowania kodu, dokumentów i innych artefaktów z danych przedstawionych w modelach.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0f74a08f5bc4e2a5baded0ac4830b60406289661
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99902723"
---
# <a name="generating-code-from-a-domain-specific-language"></a>Generowanie kodu z języka specyficznego dla domeny

Firma Microsoft [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] zapewnia zaawansowany sposób generowania kodu, dokumentów, plików konfiguracji i innych artefaktów z danych przedstawionych w modelach. Za pomocą programu [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] można utworzyć zestaw klas, które reprezentują dane, i można napisać szablony tekstowe w klasach, których nazwy i właściwości odzwierciedlają te dane.

Na przykład firma Fabrikam ma plik XML z nazwami klientów i adresami e-mail. Deweloperzy tworzą model, w którym klient jest klasą z właściwościami nazwa i adres e-mail. Piszą one kilka szablonów tekstowych do przetwarzania danych, w tym ten fragment, który tworzy tabelę wszystkich klientów w ramach strony HTML:

```
<table>
<# foreach (Customer c in ContactList) {  #>
  <tr><td> <#= c.FullName #> </td>
      <td> <#= c.EmailAddress #> </td> </tr>
<# } #>  </table>
```

Podczas przetwarzania bazy danych klienta plik XML jest odczytywany do magazynu modeli. *Procesor dyrektywy* utworzony przy użyciu [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] , sprawia, że Klasa klienta jest dostępna dla kodu w szablonie tekstu. Wiele szablonów tekstowych można uruchamiać w ramach tego samego magazynu.

Szablony tekstowe mają kluczowe znaczenie [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] . Są one używane do generowania kodu źródłowego dla elementów modelu domeny, a także dla pakietu VSPackage i formantów, które są używane do integracji narzędzi z programem Visual Studio.

W tej sekcji omówiono niektóre sposoby tworzenia, modyfikowania i debugowania szablonów tekstu używanych w programie [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] .

## <a name="in-this-section"></a>W tej sekcji

[Uzyskiwanie dostępu do modeli z szablonów tekstowych](../modeling/accessing-models-from-text-templates.md)\
Zawiera podstawowe informacje dotyczące odwoływania się do języka specyficznego dla domeny w szablonach tekstowych.

[Przewodnik: Debugowanie szablonu tekstu, który uzyskuje dostęp do modelu](../modeling/walkthrough-debugging-a-text-template-that-accesses-a-model.md)\
Opisuje sposób rozwiązywania problemów i debugowania dla szablonu tekstu, który odwołuje się do języka specyficznego dla domeny.

[Przewodnik: łączenie hosta z wygenerowanym procesorem dyrektywy](../modeling/walkthrough-connecting-a-host-to-a-generated-directive-processor.md)\
Opisuje sposób nawiązywania połączenia z hostem niestandardowym z wygenerowanym procesorem dyrektywy.

[Polecenie DslTextTransform](../modeling/the-dsltexttransform-command.md)\
Opisuje plik poleceń, który wykonuje element wykonywalny TextTransform w wierszu polecenia dla szablonów tekstowych, które odwołują się do języków specyficznych dla domeny.

## <a name="reference"></a>Dokumentacja

[Pisanie szablonu tekstowego T4](../modeling/writing-a-t4-text-template.md)\
Zawiera składnię dyrektyw szablonu tekstu i bloków sterujących.

## <a name="related-sections"></a>Sekcje pokrewne

[Generowanie kodu w czasie projektowania przy użyciu szablonów tekstowych T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)\
Wyjaśnia proces transformacji szablonu tekstu.

[Generowanie kodu w procesie kompilacji](../modeling/code-generation-in-a-build-process.md)\
Zapoznaj się z tym tematem, Jeśli generujesz pliki z DSL na serwerze kompilacji.
